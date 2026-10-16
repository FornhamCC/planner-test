# Stage 2 — testing guide

Stage 2 adds the topic tray, New topic, placing by drag and drop or by tapping, pairing GBCC and FCC, moving and swapping, copy and paste, removing and deleting, undo, and two items from the Nice to Have list: the board fits the iPad's width, and an "Invitations sent" tick on each topic.

Test it on a **test copy** first, so the real plan is never disturbed. The same `index.html` works in both places: it saves to whichever repository it was opened from, and a brown **TEST COPY** banner shows across the top of the test copy.

## Part A — make the test copy (about 10 minutes, once)

1. Sign in to GitHub in Chrome and open the **FornhamCC** organization.
2. **New repository** → name it `planner-test`, choose **Public**, leave everything else unticked → **Create repository**.
3. On the empty repository's page choose **uploading an existing file**. Unzip `planner-test-full.zip` on your PC, open the `planner` folder inside it, select **everything in it** (index.html, README.md and the data, docs, fonts and tests folders) and drag it all onto the page. Wait for the files to list, then **Commit changes**.
4. **Settings → Pages**: Source **Deploy from a branch**, Branch **main**, folder **/ (root)** → **Save**. After a minute or two the test copy is at **https://fornhamcc.github.io/planner-test/**
5. Let your access key reach the test copy: open **github.com/settings/personal-access-tokens**, choose your planner key → **Edit** → under Repository access, **Only select repositories**, add `planner-test` alongside `planner` → **Update**. The key's text does not change, so nothing needs pasting again on the PC.
6. Open the test address on the PC and on the iPad. Each device treats it as a separate site, so press **Unlock editing** and paste the key once on each.

The test copy starts with a copy of the real plan. Change anything you like there.

## Part B — what to try

Turn **Edit** on first. Tick each box on both devices.

| # | Check | PC (Chrome or Edge) | iPad (Safari, landscape) |
|---|---|---|---|
| 1 | All eight group columns fit across the screen without sideways scrolling | ☐ | ☐ |
| 2 | **New topic** (top right): give a title, category and presenter → it appears in the tray, selected, with the cells it can go in lit up | ☐ | ☐ |
| 3 | **Topics** opens and closes the tray (on the iPad it slides over the board) | ☐ | ☐ |
| 4 | **Tap to place**: tap a topic in the tray, then tap a lit cell | ☐ | ☐ |
| 5 | **Pairing**: after placing at GBCC, the strip offers the FCC date in the same month → **Place on …** | ☐ | ☐ |
| 6 | **Drag**: drag a tray topic onto a lit cell (iPad: press and hold about a third of a second, then move) | ☐ | ☐ |
| 7 | A quick swipe that starts on a tile scrolls the board and does not move the tile | — | ☐ |
| 8 | **Move**: drag a placed tile to another month; the date and times follow the meeting pattern; the strip offers to move the other club's tile too | ☐ | ☐ |
| 9 | Dragging near the top or bottom edge scrolls the board | ☐ | ☐ |
| 10 | **Swap**: drop a tile on a lit tile → **Swap** | ☐ | ☐ |
| 11 | A tile dropped on the wrong kind of column is refused, with a message | ☐ | ☐ |
| 12 | **Replace**: place a tray topic on a filled lit cell → **Replace**; the old topic stays in the tray | ☐ | ☐ |
| 13 | **Copy and paste**: tap a tile → **Copy** → tap a lit cell. PC: also Ctrl+C, click an empty cell, Ctrl+V | ☐ | ☐ |
| 14 | **Empty cell**: tap an empty cell → **New topic here** creates and places it in one go | ☐ | ☐ |
| 15 | **Remove from board**: select a tile → **Remove from board** (PC: Delete key; or drag the tile onto the tray). The topic stays in the tray | ☐ | ☐ |
| 16 | **Undo** reverses the last action (PC: Ctrl+Z), several times in a row | ☐ | ☐ |
| 17 | **Details**: tap a selected tile again (or tap a tray topic twice) → details open; edit and **Save** | ☐ | ☐ |
| 18 | **Invitations sent**: tick it in the details → every tile of that topic, GBCC and FCC, shows "Invites sent" | ☐ | ☐ |
| 19 | **Delete topic** (in the details) asks first, removes its tiles; Undo brings it back | ☐ | ☐ |
| 20 | Tray filters: **Needs placing**, **Upcoming**, **All** | ☐ | ☐ |
| 21 | With **Edit** off: no tray, no editing tools; tapping a tile shows read-only details | ☐ | ☐ |
| 22 | Change something on the PC; press Refresh on the iPad; it appears | ☐ | ☐ |
| 23 | The test copy's saves appear under **planner-test → Commits** with readable messages | ☐ | — |
| 24 | Open the test address in a private window (never unlocked): it reads correctly with no editing controls | ☐ | ☐ |

Also worth a look on the iPad in **portrait**: the board scrolls sideways for all eight columns, and the **Windows** or **iPad** filter shows four columns that fit.

Note anything odd (what you did, what you expected, what happened) and send it over; small fixes go into this stage before it goes live.

## Part C — making it live

Once you are happy with the test copy:

1. Open the real **planner** repository → **Add file → Upload files**.
2. Unzip `planner-live-update.zip`. It holds **only** `index.html`, `README.md` and `docs/stage2-testing.md`. Drag those onto the page, keeping the `docs` folder, and **Commit changes**.
3. **Never upload `data/plan.json` to the real repository.** The real plan lives there and has moved on since the zip was made.
4. After a minute or two, reload https://fornhamcc.github.io/planner/ on each device. Your key is still remembered there.

The test copy can stay for future stages, or be deleted from its Settings page.
