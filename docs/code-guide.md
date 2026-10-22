# Topic Planning Board — Code Guide

How the board is built, what each part of the code does, and how to make the common changes. For how to *use* the board, see the [user manual](user-manual.md).

*Describes the code as of October 2026 (Stage 5). Line numbers drift with every release, so this guide points to each part by its **banner comment** — search `index.html` for the words in capitals (e.g. `5. DATA LAYER`).*

---

## Contents

1. [The big picture](#1-the-big-picture)
2. [What is in the repository](#2-what-is-in-the-repository)
3. [How a visit runs](#3-how-a-visit-runs)
4. [The data model](#4-the-data-model)
5. [A tour of index.html, section by section](#5-a-tour-of-indexhtml-section-by-section)
6. [How saving works](#6-how-saving-works)
7. [Security](#7-security)
8. [Testing](#8-testing)
9. [Releasing a new version](#9-releasing-a-new-version)
10. [Common changes](#10-common-changes)
11. [Glossary](#11-glossary)

---

## 1. The big picture

The whole board is **one file, `index.html`**, with its styles and script inside it. There is no server of our own, no database, no build step and no framework:

- **GitHub Pages** publishes the repository as a website. Members' browsers fetch `index.html` and the plan file `data/plan.json` from it, read-only.
- **Editors save through GitHub's API.** Each save is a commit that rewrites `data/plan.json`. GitHub keeps every version, which is what makes History and Restore possible.
- **The editing key** (a fine-grained personal access token) proves to GitHub that the editor may write. It is kept in the browser's local storage on that device and sent only to `api.github.com`.

```
 Member's browser ──GET──▶ GitHub Pages  (fornhamcc.github.io/planner)
                            index.html, data/plan.json, vendor/, fonts/

 Editor's browser ──GET──▶ GitHub Pages  (the page itself)
                  ──API──▶ api.github.com  (read the newest plan, save commits)
                                 │
                                 └──▶ repository FornhamCC/planner  ──rebuilds──▶ GitHub Pages
```

Why this shape (decided at the design stage): it costs nothing, needs no maintenance, members need no accounts, and every change is recorded and reversible. The only moving part is the yearly key renewal.

The same `index.html` runs from the **test copy** repository `planner-test`: it works out from its own address which repository it is in (`repoNameFromAddress`), saves there, and shows a TEST COPY banner.

---

## 2. What is in the repository

| Path | Contents |
| --- | --- |
| `index.html` | The board: markup, styles and script, in numbered sections |
| `data/plan.json` | The plan: settings, topics and sessions. **Only the board writes to it.** Never replace it during a release |
| `data/archive/YYYY.json` | One file per archived calendar year, created by the board's yearly archive |
| `vendor/` | jsPDF 4.2.1 and jsPDF-AutoTable 5.0.9 (MIT licence), loaded only when PDFs are made. See `vendor/README.md` |
| `fonts/` | Atkinson Hyperlegible (body text) and Montserrat 700/800 (headings, header bar; added with the Oct 2026 restyle), both SIL Open Font License, self-hosted so the page needs no other website |
| `tests/index.html` | The date-engine tests, run in the browser |
| `docs/` | Setup guide, user manual, this guide, and the testing guides from each stage |
| `README.md` | Short description and build history |
| `.nojekyll` | Tells GitHub Pages to publish the files exactly as they are |

---

## 3. How a visit runs

`start()` (section **11. START-UP**) runs once when the page opens:

1. **Wire up the controls** (`bindControls`) and load this device's remembered choices (`loadPrefs`: filter, columns, tray).
2. **Is there a key on this device?** (`storeGet(STORE.key)`)
   - **Yes — an editor.** `verifyKey()` asks GitHub who the key belongs to and what it may do (`/user`, then `/repos/FornhamCC/planner`, whose `permissions` say *push* = Editor, *admin* = Owner). Then `fetchPlanFromApi()` reads the newest plan through the API, with its *sha* (GitHub's version id, needed to save).
   - **No — a member** (or the key failed). `loadPublishedPlan()` reads `data/plan.json` from the site itself.
3. **Check the file** (`validatePlan`). A damaged or unknown file is never drawn as if it were a plan.
4. **Fill in defaults** (`withDefaults`) for anything an older file lacks, then **draw** (`render`).
5. **Keep up to date** (`startPolling`): editors check GitHub every minute (cheaply, with an ETag, so an unchanged file costs almost nothing); members reload the published copy every 5 minutes.

From then on, two things change the screen:

- **Changing the view** (a filter, a page, the month range) updates `state` and calls `render()`.
- **Changing the plan** always goes through `commit()` → `queueOps()` (section 6).

---

## 4. The data model

`data/plan.json` has four parts:

```json
{
  "meta":     { "format": "gbcc-fcc-topic-board", "version": 1, "savedAt": "…", "savedBy": "bernieonline" },
  "settings": { … },
  "topics":   { "t_ab12cd34": { … }, … },
  "sessions": { "2027-02_GBCC_IB": { … }, … }
}
```

### Topics — *what* is taught

Keyed by a random id (`t_` + 8 characters, `newTopicId`).

| Field | Meaning |
| --- | --- |
| `title` | Up to 120 characters |
| `category` | `WB`, `WM`, `IB`, `IM` or `EV` (club event) |
| `presenter` | Two-letter code, or empty |
| `notesUrl`, `slidesUrl` | `https://` links only (up to 2,000 characters) |
| `briefing` | Members' briefing (up to 5,000 characters) |
| `updatedAt`, `updatedBy` | When and by whom it was last changed |

### Sessions — *when* it is taught (one tile each)

Keyed by **cell**: `MONTH_CLUB_CATEGORY`, e.g. `2027-02_GBCC_IB`. So there is **at most one meeting per group per month** — the key *is* the cell on the board.

| Field | Meaning |
| --- | --- |
| `topicId` | The topic taught |
| `club`, `category`, `month` | Repeat the key, for convenience |
| `date`, `start`, `end` | The actual date and times (`2027-02-22`, `12:45`, `14:00`) |
| `status` | `planned` or `cancelled` |
| `moved` | `true` when not on the pattern date/time (shows **Moved**) |
| `invitesSent`, `invitesSentAt` | The "Invitations sent" tick, per tile |
| `updatedAt`, `updatedBy` | When and by whom |

One topic taught at both clubs is **one topic and two sessions** pointing to it.

### Settings

| Field | Meaning |
| --- | --- |
| `boardTitle` | Heading at the top |
| `websiteUrl` | Optional club website address (must be `https://`). When present, `renderHeader()` shows the **Club website** pill (`#siteLink`); edited in Settings › Board and clubs |
| `clubs[]` | `{ code, name, shortName, meetingDay }` — codes `GBCC`, `FCC` are fixed |
| `categories[]` | `{ code, name, platform, start, end, weekFromEnd, colours }` — `weekFromEnd` 2 = second-last meeting week (Windows), 1 = last (iPad) |
| `groupTimes` | Optional per-club times: `{ "GBCC_WB": { start, end }, … }`, overriding the category's |
| `groupNames` | Optional names per group: `{ "GBCC_WB": "GBCC Windows Beginners", … }` |
| `clubEvent` | Name and colours of the club-event category |
| `weekRule` | `eachClub` (in use) or `sameWeek` — see the user manual, section 11 |
| `breakMonths`, `breakNames` | `[7, 8, 12]` and their labels |
| `closures[]` | `{ date, club, note }` — `club` empty means both |
| `presenters[]` | `{ code, name, active }` |
| `firstMonth` | Where a brand-new board starts |
| `archivedYears[]` | Years moved to `data/archive/` |

`DEFAULT_SETTINGS` (section 3) is used only if a file has no settings at all.

### Archive files

`data/archive/2026.json` holds that year's sessions, copies of the topics they used, and the settings at the time, in the same shapes as above. Archiving merges into an existing file, never overwrites it.

### On each device (local storage)

| Name | Holds |
| --- | --- |
| `tpb.accessKey` | The editing key (unlocked devices only) |
| `tpb.keyExpiry` | Key expiry typed in Settings, if GitHub doesn't report it |
| `tpb.prefs` | Filter, columns, tray filter, tray open |
| `tpb.lastBackup`, `tpb.backupSeen` | For the 90-day backup reminder |

Every read and write of local storage goes through `storeGet` / `storeSet` / `storeRemove`, which never throw (storage can be blocked in private browsing).

---

## 5. A tour of index.html, section by section

Each section starts with a banner comment like this:

```
/* =====================================================================
   5. DATA LAYER
   ===================================================================== */
```

| # | Section | What it does | Key functions |
| --- | --- | --- | --- |
| — | `<head>` | Content Security Policy, the iPad date-link switch-off, page title and icon | — |
| 1 | **STYLES** | Colour and size tokens (`:root`), the header bars, grid, tiles, tray, dialogs, Settings and PDF pages, and iPad / narrow-screen adjustments. Sub-banners such as `/* --- Tiles ---` | — |
| 2 | **PAGE MARKUP** | Empty containers only (`#board`, `#tray`, `#pdfsInner`, `#settingsInner`, the dialogs). The Key help text is written here, so it opens even when GitHub can't be reached | — |
| 3 | **CONSTANTS AND DEFAULTS** | Repository details, storage names, timings, text limits, the earliest month, category order, icons, drag settings, `DEFAULT_SETTINGS` | `repoNameFromAddress` |
| 4 | **DATE ENGINE** | Pure date rules: break months, meeting days, the week rule, each session's date and times, date formatting. No side effects, so it can be tested on its own. Wrapped in `DATE-ENGINE-START` / `END` markers, which the test page reads | `DateEngine.sessionDate`, `groupTimes`, `meetingWeeks`, `clubMeetingDays`, `isBreakMonth` |
| 4b | **CALENDAR FILE** | Builds the `.ics` file for Add to calendar: UK local time with a time-zone block, escaping and line folding as the standard requires | `CalendarFile.build` |
| 5 | **DATA LAYER** | Reading the plan, talking to GitHub, operations, the save queue and conflict handling | `loadPublishedPlan`, `github`, `verifyKey`, `fetchPlanFromApi`, `putPlanToApi`, `makeOp`, `applyOps`, `queueOps`, `runSave`, `dropConflict` |
| 6 | **APP STATE** | The single `state` object (everything the page shows), remembered preferences, and small look-ups | `canEdit`, `settings`, `groupName`, `clubShortName`, `describeSession`, `visibleColumns`, `selectableMonths` |
| 7 | **RENDERING** | Draws the header, the month grid, tiles, the tray and the placing strip from `state` | `render`, `renderHeader`, `setSaveStatus`, `renderBoard`, `renderTile`, `renderTray`, `renderStrip` |
| 7b | **SETTINGS PAGE** | The five settings cards, Editing access, the key reminder, Key help, and the details panel (read-only and editable) | `settingsCard` with `build…Card` / `collect…Card` pairs, `applySettingsChange`, `renderDetails`, `downloadCalendarEntry` |
| 8 | **INTERACTIONS** | Taps, the right-click / press-and-hold menu, placing, moving, swapping, pairing, copy and paste, removing and deleting, New topic, dragging, keyboard shortcuts, unlocking, the month range | `handleTileTap`, `handleCellTap`, `performDrop`, `placeTopic`, `moveSession`, `offerPairing`, `copyTopic`, `pasteInto`, `removeSession`, `deleteTopic`, `commit`, `undoLast`, `onPointerDown/Move/Up`, `onKeyDown`, `confirmUnlock` |
| 9 | **PDFs** | The PDFs page (simple three-step choices and More options), the rows each PDF holds, and drawing them with jsPDF | `renderPdfs` → `renderPdfsSimple` / `renderPdfsAdvanced`, `buildPdfs`, `pdfMonthRows`, `PdfDraw.groupPlan`, `PdfDraw.gridPlan` |
| 10 | **BACKUP, HISTORY AND THE YEARLY ARCHIVE** | Download / restore a backup, the last 30 saves, archiving a year, viewing an archive | `downloadBackup`, `restorePlan`, `loadHistory`, `viewVersion`, `archiveYear`, `showArchive`, `leaveArchive` |
| 11 | **START-UP** | Refresh, polling and `start()` | `refreshPlan`, `startPolling`, `start` |

### Patterns used throughout

- **`el(tag, props, …children)`** builds every element. It sets text with `textContent`, never `innerHTML`, so nothing typed into the plan can ever run as code (see section 7). `icon(name)` adds one of the fixed SVG icons from `ICONS`.
- **One `state`, one `render()`.** Code changes `state`, then calls `render()`, which redraws the visible page. While a tile is being dragged, redrawing waits until the drop; an editable details panel or a Settings card with unsaved typing is never redrawn under the user.
- **Colours come from settings.** `colourVars(category)` turns a category's colours into CSS custom properties (`--fill`, `--line`, `--strong`, `--ink`) on a tile or button, and the stylesheet uses those.
- **Club website look (Oct 2026 restyle).** The brand colours are `:root` tokens beside the bronze ones: `--charcoal`, `--cream`, `--gold` (with `--gold-grad` for 3D buttons), `--brand-rule` (the gold → amber → ember stripe under the header) and `--heading` (Montserrat). The charcoal header is `.bar1`; controls inside it have `.bar1 …` rules so the same buttons keep their light look elsewhere. Gold is never used for text on white. The group colours are untouched: they still come only from settings. In the PDFs, `pageFrame()` draws the charcoal heading band (`CHARCOAL`, `GOLD`) above the group's colour strip. On screens up to 1,300 px wide the month names fall back to Atkinson so they fit the narrow month column.
- **Settings cards** each have a `build…Card(editable)` that draws the card and a `collect…Card(card, settings)` that reads it back, checks it, and returns new settings or throws an `Error('message')` that is shown in red. `settingsCard()` adds Save / Discard and calls `applySettingsChange()`.
- **Questions** use `ask(title, text, buttons)`, which returns the chosen button's value (a `<dialog>`, so Escape and focus work properly).
- **Dragging** uses Pointer Events, so one set of code serves mouse, finger and Apple Pencil. A mouse drag starts after 6 px of movement; a finger drag after a 300 ms press-and-hold (so a swipe still scrolls). Press-and-hold then lift without moving opens the menu. Settings in `DRAG` (section 3).

---

## 6. How saving works

### Operations

Every change to the plan is a list of **operations** (`makeOp`), each touching one item:

```js
{ kind: 'session', id: '2027-02_GBCC_IB', before: {…} or null, after: {…} or null, label: 'Place “…” at …', group: 'g…' }
```

- `kind` is `topic`, `session`, `settings` (the whole settings block) or `plan` (a restore replaces everything).
- `before` is the item as the editor saw it; `after` the new item (`null` = delete).
- `label` becomes the commit message on GitHub.
- Operations made by one action share a `group` (a move is two: out of one cell, into another).

`commit(ops, label)` gives the operations a shared `group`, records them as an **undo entry**, and passes them to `queueOps`.

### The save queue

1. `queueOps` adds them to `state.pending`, redraws at once (`rebuildLocalPlan`: newest GitHub copy + pending operations), shows **Unsaved changes**, and starts a 2-second timer, so a burst of changes becomes one save.
2. `runSave` takes the newest copy known from GitHub, **re-applies the pending operations, checking each `before`** against what is there now (`applyOps(…, true)`), and sends the result with that copy's sha (`putPlanToApi`, a `PUT /repos/…/contents/data/plan.json`).
3. **If someone else saved in between**, GitHub refuses (409 / 422: the sha is stale). The board fetches their version and goes back to step 2 — on top of *their* changes, so nothing of theirs is lost.
4. **If an operation no longer fits** (its item was changed elsewhere), `dropConflict` drops it — and the rest of its group, so a move is never half done — removes its undo entry, and explains in a message.
5. **If the network fails**, everything stays queued and is retried after 5 s, 15 s, 30 s, then every 60 s (**Not saved — retrying**).
6. **If GitHub refuses the key** (401), `handleKeyRejected` forgets it, switches to view-only, keeps the queue, and opens the Unlock box. The queue saves once a new key is in.

### Undo

`undoLast()` takes the newest undo entry, turns each operation round (before ↔ after, in reverse order) and queues those, which save like any other change. If the items have changed since (perhaps on another device), it refuses and explains rather than overwrite. Up to 50 entries (`UNDO_LIMIT`), kept for the visit only.

---

## 7. Security

| Risk | How it is handled |
| --- | --- |
| The key leaking | Sent only in the `Authorization` header to `api.github.com`. The Content Security Policy's `connect-src 'self' https://api.github.com` means even faulty code could not send it anywhere else. `referrer: no-referrer` |
| What the key can do | Fine-grained: only `planner` and `planner-test`, only **Contents: read and write**, expires after a year. Regenerating it kills the old one at once |
| Text in the plan running as code | All text is set with `textContent` (`el()`); icons are constant strings in the code, never data. CSP blocks scripts from any other site |
| Bad links | Only `https://` links are accepted and opened (`isSafeUrl`), with `rel="noopener noreferrer"` |
| Oversized or damaged data | Text limits in `LIMITS`; `validatePlan` checks every file loaded (including backups and restores) before use |
| Two editors at once | sha-checked saves and per-item `before` checks (section 6) |
| Owner-only actions | Settings, Restore and Archive are only offered to owners (`isOwner` from GitHub's permissions). This is enforced **in the page**: an editor with write access could still change the file directly on GitHub. Only add trusted editors; every change is in the history and reversible |
| The plan is public | Intended; nothing private goes in it |

---

## 8. Testing

### In the repository

**`tests/index.html`** — the date-engine tests. Open `…/planner/tests/` (or `…/planner-test/tests/`) in a browser. It reads the engine straight out of `index.html` (between the `DATE-ENGINE-START` / `END` markers) and the board's own settings from `data/plan.json`, and checks every month from September 2026 to July 2028: break months, the last-two-weeks rule, month-end cases such as November 2026, both week rules, and that each group's times follow Settings (including per-club times). The page lists each check as Pass or FAIL.

### In the Claude project (`claude/planner-dev/`)

Automated browser tests written with Playwright (Python), run against a local copy of the repository. They load a simulated plan and simulate GitHub, so they never touch the real data.

| Script | Covers |
| --- | --- |
| `board_test.py`, `run_tests.py` | Stage 1: grid, unlocking, saving, conflict retry |
| `stage2_test.py` | Tray, placing, dragging (mouse and touch), pairing, copy/paste, undo, invitations, Add to calendar, Safer Delete |
| `stage3_test.py` | Settings cards, per-club times, key reminder |
| `keyhelp_test.py` | Key help on PC, iPad and phone sizes |
| `stage4a_test.py` | Every PDF type, via More options |
| `stage4b_test.py` | Backup, restore, history, archive, archive view |
| `stage4c_test.py` | The simple PDF choices, including the merged-club wording and short names from Settings |
| `readonly_test.py` | A never-unlocked device on PC and iPad: no editing anywhere, nothing sent, no key stored, PDFs and Add to calendar still work |
| `plan_sample.py` | The fuller 2027 sample plan the PDF tests share |

To run one: serve the repository folder (`python3 -m http.server 8765` inside it), then `python3 stage4c_test.py`. Needs `pip install playwright pypdf` and `playwright install chromium`; the PDF checks also use `pdftotext`.

Each stage also has a hand-testing guide in `docs/` (`stage2-testing.md` … `stage4c-testing.md`, `keyhelp-testing.md`).

---

## 9. Releasing a new version

1. **Change and test on the test copy first** (`FornhamCC/planner-test`, https://fornhamcc.github.io/planner-test/). It has its own plan, so nothing real is disturbed.
2. When it is right, **copy `index.html`, `README.md`, `docs/` and (if changed) `vendor/` to `FornhamCC/planner`**.
3. **Never copy `data/plan.json` or `data/archive/`** — the real plan lives there and has moved on.
4. GitHub Pages republishes within a minute or two. Reload on each device (on the iPad, close and reopen the tab).

Since October 2026 Claude pushes releases directly: changes go to planner-test, and to planner only when Bernard says "make it live". By hand, the GitHub website's **Add file → Upload files** does the same (open the target folder first; press **Commit changes** before leaving the page).

Any earlier release can be brought back from the repository's history, and a release never touches the plan.

---

## 10. Common changes

Most everyday changes need **no code** — they are in **Settings**: club and group names, short names, meeting days, session times (per club), which week each kind of group meets, the week rule, break months, closures and presenters. The changes below are for when Settings is not enough.

### Change a group's colours

The colours are stored in the plan's settings (`settings.categories[].colours`), not in the code. Edit them in `data/plan.json` on GitHub (pencil icon), keeping the four values per category:

| Key | Used for |
| --- | --- |
| `fill` | Tile and header background |
| `line` | Tile border |
| `strong` | The coloured bar across the column header |
| `ink` | Text on the tile |

Choose an `ink` dark enough to read on its `fill`. Also update `DEFAULT_SETTINGS` (section 3) so a brand-new board matches. The PDFs pick up the same colours automatically.

### Show more months ahead, or start earlier

`MONTHS_AHEAD` (24) and `EARLIEST_MONTH` (`'2026-09'`) in section 3. The month range also never goes back more than 12 months unless older sessions remain (`selectableMonths`, section 6).

### Change how often the board refreshes or saves

`SAVE_DELAY`, `EDITOR_POLL`, `READER_POLL` and `RETRY_DELAYS` in section 3.

### Change text limits

`LIMITS` in section 3 (title, briefing, link).

### Change the wording of the PDFs page

`renderPdfsSimple()` in section 9 holds the three questions, the button labels and the trail line. Club names on it come from `clubShortName()` (section 6), which uses Settings → Clubs short names.

### Change what goes in a PDF

`pdfMonthRows()` decides what each month's row holds (meeting, break, cancelled, To be arranged, closed). `PdfDraw.groupPlan()` draws the one-group list and `PdfDraw.gridPlan()` the side-by-side layouts. Page heading and footer: `PdfDraw`'s `pageFrame()`. Fonts are jsPDF's built-in Helvetica, which only has Western European characters — `text()` swaps or drops anything else (an emoji in a title, say).

### Add a field to topics (e.g. "Room")

1. Add it to the editable details panel in `renderDetails()` (section 7b) and read it back in `saveDetails()` (section 8).
2. Show it read-only in `renderDetails()` too.
3. If it should print, add it in `pdfMonthRows()` / `PdfDraw`.
4. Older topics simply lack it — always treat a missing value as empty.

### Add a setting

1. Add it to `DEFAULT_SETTINGS` (section 3) and, if old files need it, to `withDefaults()` (section 5).
2. Show and read it in the right card's `build…Card` / `collect…Card` pair (section 7b).
3. Use it through `settings()`.

### Rename the GitHub organization or repository

`REPO.owner` in section 3; `GUIDE_URL`; and `repoNameFromAddress()` if the repository name no longer starts with `planner`. Editors' keys must be remade for the new location.

### Add a new kind of group (a fifth category)

Bigger: the codes `WB`, `WM`, `IB`, `IM` are fixed in `CATEGORY_ORDER`, and session keys and colours depend on them. It needs a new code in `CATEGORY_ORDER` and `DEFAULT_SETTINGS`, the matching entry in the plan's `settings.categories`, and checking the PDF layouts still fit the page width. A "Combined topic" was considered and put on hold (Nice to Have 3); a **Club event** placed in each column does the same job today.

### Update the PDF libraries

Download the new jsPDF UMD build and jsPDF-AutoTable into `vendor/` with the same file names (or change `PDF_LIBS` in section 9), update `vendor/README.md`, and run `stage4a_test.py` and `stage4c_test.py`.

### Connect the club domain

No code change. In the repository's **Settings → Pages**, set the custom domain, and add the DNS records at the domain's registrar or DNS host (setup guide, Part D). The board works out its own address, so links in PDFs follow.

---

## 11. Glossary

| Term | Meaning |
| --- | --- |
| **Topic** | What is taught: title, category, presenter, links, briefing |
| **Session** / **tile** | One meeting: a topic in one cell, with its date and times |
| **Cell** | One group in one month; its key is `MONTH_CLUB_CATEGORY` |
| **Category** | WB Windows Beginners · WM Windows Main · IB iPad Beginners · IM iPad Main · EV Club event |
| **Group** | A category at one club, e.g. GBCC Windows Beginners (eight in all) |
| **Meeting pattern** | The usual date and times worked out by the date engine from Settings |
| **Operation** | One change to one item, with before and after copies |
| **sha** | GitHub's id for one version of a file; a save must name the version it builds on |
| **Commit** | One saved change on GitHub, with a message |
| **GitHub Pages** | GitHub's free website hosting, which publishes the repository |
| **Fine-grained personal access token** | GitHub's name for the editing key |
| **Owner / Editor** | Admin of the repository (can change Settings, restore, archive) / write access only |
| **Test copy** | The `planner-test` repository, a separate board for trying changes |
