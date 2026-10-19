# Topic Planning Board — User Manual

For members, presenters and the board's owner at Great Barton Computer Club (GBCC) and Fornham Computer Club (FCC).

**The board's address:** https://fornhamcc.github.io/planner/
(later also https://fornhamcomputerclub.com/planner/ once the club domain is connected)

*Written for the board as it stands in October 2026 (Stage 5). The companion [code guide](code-guide.md) explains how the board is built.*

---

## Contents

1. [What the board is](#1-what-the-board-is)
2. [Who can do what](#2-who-can-do-what)
3. [A tour of the screen](#3-a-tour-of-the-screen)
4. [Reading the board (everyone)](#4-reading-the-board-everyone)
5. [Making a PDF (everyone)](#5-making-a-pdf-everyone)
6. [Editing: getting started](#6-editing-getting-started)
7. [Editing: topics and tiles](#7-editing-topics-and-tiles)
8. [Editing: the details panel](#8-editing-the-details-panel)
9. [Undo, saving, and working on two devices](#9-undo-saving-and-working-on-two-devices)
10. [Settings (owner)](#10-settings-owner)
11. [The meeting dates and the week rule](#11-the-meeting-dates-and-the-week-rule)
12. [The editing key](#12-the-editing-key)
13. [Backup, history and the yearly archive (owner)](#13-backup-history-and-the-yearly-archive-owner)
14. [Linking tutorial notes from OneDrive](#14-linking-tutorial-notes-from-onedrive)
15. [Adding another editor (owner)](#15-adding-another-editor-owner)
16. [Troubleshooting](#16-troubleshooting)
17. [Quick reference](#17-quick-reference)

---

## 1. What the board is

The board plans the clubs' tutorial topics about a year ahead. It is a web page, so it works in any browser on a PC, an iPad or a phone, with nothing to install.

- **Each row is a month.** July, August and December are breaks, shown as a single shaded band.
- **Each column is one of the eight groups:** Windows Beginners, Windows Main, iPad Beginners and iPad Main, at each club.
- **Each tile is one meeting:** the topic, its date and times, and the presenter's two-letter code.

The four kinds of group each have their own colour, used on the board and in the PDFs:

| Group | Colour |
| --- | --- |
| Windows Beginners | Light blue |
| Windows Main | Deeper blue |
| iPad Beginners | Light green |
| iPad Main | Deeper green |
| Club event (e.g. an AGM) | Warm bronze |

A **topic** (for example "Spotting scam emails") is usually taught to the same kind of group at both clubs, on different days. So one topic normally appears as **two tiles**: one in the GBCC column and one in the FCC column of the same month. Change the topic's title, notes or briefing once and both tiles follow.

---

## 2. Who can do what

| | Members | Editors (presenters) | Owner (Bernard) |
| --- | --- | --- | --- |
| Read the board, open a meeting's details | ✓ | ✓ | ✓ |
| Open tutorial notes and slides | ✓ | ✓ | ✓ |
| Add a meeting to their own calendar | ✓ | ✓ | ✓ |
| Make PDFs | ✓ | ✓ | ✓ |
| Look at an archived year | ✓ | ✓ | ✓ |
| Create, place, move and edit topics | | ✓ | ✓ |
| Download a backup | | ✓ | ✓ |
| Change Settings (names, times, breaks, presenters…) | | | ✓ |
| Restore a backup or an earlier version; archive a year | | | ✓ |

Members need no account and no password. Editing needs a GitHub account and an **editing key** pasted once into each device you edit from (section 12). The board shows **Owner** or **Editor** at the top right once a device is unlocked.

---

## 3. A tour of the screen

### The top bar

From left to right:

- **The board's name** and the clubs' names (both can be changed in Settings).
- **Board · PDFs · Settings** — the three pages.
- **The save status.** Members see **View only · updated 17:22** (when the plan was last read). Editors see whether their changes are saved (section 9).
- **↻ Refresh** — reads the newest copy of the plan now. (It also refreshes by itself: every 5 minutes for members, every minute for editors.)
- **Unlock editing** — on a device that has no key yet. Once unlocked, this becomes the **Owner** / **Editor** label and the **Edit** switch.

On the test copy a brown **TEST COPY** banner runs across the very top: changes there never affect the real plan.

### The second bar (Board page only)

- **All · Windows · iPad** — show every group, or only the Windows or only the iPad groups. On an iPad held upright, choosing Windows or iPad makes the four columns fit the screen.
- **‹ Oct 2026 – Sep 2027 ›** — the months shown. The arrows step a month at a time; tap the dates themselves to choose **From** and **To**.
- **This month** — jumps back to the current month.
- **Showing** — appears only once a year has been archived (section 13); picks the current plan or an archived year.
- **Columns: By category / By club** — *By category* puts GBCC and FCC side by side under each kind of group (the usual view: it shows both clubs' tiles for a topic next to each other). *By club* puts all four GBCC groups first, then all four FCC groups.
- **Undo · Topics · New topic** — editing tools, shown only while **Edit** is on.

Your choices of filter, columns and tray are remembered on each device.

---

## 4. Reading the board (everyone)

### What a tile shows

- The **date and times**, e.g. *Mon 18 Jan · 12:30–2:00*.
- The **topic title**.
- The **presenter's code** (e.g. **BG**, **RC**) in a dark chip at the top right.
- Small symbols: 📎 a paperclip means **tutorial notes are linked**; 📄 a page means a **members' briefing** has been written.
- Chips that may appear:
  - **Invites sent** (green) — the email invitations for that meeting have gone out.
  - **Moved** — the meeting is not on its usual date or time.
  - **Cancelled** — the meeting will not take place.
  - **Closed** (red) — the hall is closed that day (a closure from Settings).
  - **Club event** — an AGM or similar.

The current month has a bronze **This month** label. An empty cell with a faint date is a meeting with no topic yet ("To be arranged" in the PDFs).

### Opening a meeting's details

**Click or tap any tile.** A panel slides in from the right with:

- the topic and its kind of group;
- **This session**: the club, the group, the full date and times, and whether it is planned or cancelled;
- **Add to calendar** — downloads a calendar entry for that meeting, with the topic, times, club and presenter, and the notes link. On a PC, open the downloaded file and Outlook (or your calendar app) adds it. On an iPad, Calendar offers to add it (or tap it in Safari's downloads list). Times are right in both winter and summer;
- **Open tutorial notes** and **Open slides**, when linked;
- the **members' briefing**, when written;
- **Also at:** the same topic's other meeting (for example the FCC date), which you can tap to jump to.

Close the panel with **Close**, the **✕**, or Escape on a PC.

### Looking at another part of the year

Use **‹ ›** to step through months, or tap the month range to choose exactly which months to show. The board offers months from up to a year ago to two years ahead.

---

## 5. Making a PDF (everyone)

Open **PDFs** at the top. The page asks up to three short questions, each with large buttons.

**1. Which group?** — **Great Barton**, **Fornham** or **Both**.
Choosing **Both** gives the whole plan and goes straight to question 3.

**2. Which session?** — **Windows Beginners**, **Windows Main**, **iPad Beginners**, **iPad Main** (in their board colours), or **All four**.

- One session gives that group's list of meetings (upright page): date, time, topic, presenter and an **Open notes** link you can click in the PDF.
- **All four** gives that club's four groups side by side, one row per month (sideways page).

**3. Which year?** — starts on the current year. Use **‹ ›** to step to next year (or back). For a single session you can also tick **Include each topic's members' briefing**. A line underneath says what the PDF will hold, e.g. *"9 meeting months, 3 break. 14 of 18 meetings have a topic so far."*

Then press **Make PDF**.

A line under the heading shows your choices so far, e.g. **Fornham › FCC iPad Beginners**, and **Back** goes back one question.

### Saving the PDF

- **PC:** it goes to your **Downloads** folder.
- **iPad:** Safari asks to download it — tap **Download**, then open it from the downloads arrow at the top of Safari and use **Share → Save to Files** to put it in OneDrive (or **Share → Print**).

### More options

**More options…** (top right of the panel) opens the full PDF page, for anything the three questions don't cover:

| Choice | What you get |
| --- | --- |
| One group | As above |
| One club | As above |
| The whole plan | Every group side by side; or Windows groups only, or iPad groups only |
| All eight groups in one file | The eight group lists in one PDF, each starting on a new page (easiest on an iPad) |
| All eight groups as separate files | Eight PDFs, one after another (the browser may ask once to allow several downloads) |

Here you choose **From** and **To** months freely, with quick buttons for a whole year. **Simple choices** returns to the three questions.

### In every PDF

Break months are one shaded row; a cancelled meeting says **Cancelled**; a meeting with no topic yet says **To be arranged**; a closed day says **Closed: …**. Colours match the board, and every group name is also printed in words, so a black-and-white printout still reads clearly. Each page shows the title, the months, the page number and the date printed. PDFs show the plan as it is now. A calendar year with very long topic titles can run onto a second page.

---

## 6. Editing: getting started

### Unlock the device (once per device)

1. Press **Unlock editing** (top right).
2. Paste your editing key and press **Unlock**.

The device remembers the key, so you only do this once on each PC or iPad (and once more on the test copy, which counts as a separate site). Section 12 explains the key, and **Key help** in the Unlock box opens a step-by-step guide.

### Turn on Edit

The **Edit** switch (top right) turns editing on and off. With Edit **off**, an unlocked device behaves exactly like a member's, which is handy for checking what members see. With Edit **on**:

- the **Undo**, **Topics** and **New topic** buttons appear;
- the topic **tray** can open;
- tiles can be dragged, and tapping a tile opens its details ready to edit.

---

## 7. Editing: topics and tiles

### The topic tray

**Topics** opens the tray: the list of topics, grouped by kind of group. On a wide screen it sits beside the board; on an iPad it slides over the board and gets out of the way when you pick a topic.

Three filters at the top of the tray:

- **Needs placing** — topics not yet on the board (or only at one club).
- **Upcoming** (the usual view) — topics with meetings from today on, plus any not yet placed.
- **Past 12 months** — upcoming topics plus those taught in the last year.

Each card shows the title, presenter and badges per club, such as **GBCC ✓ Mon 16 Nov** (placed) or **+1** (more than one meeting), and **Invites 1 of 2** when invitations have gone to one of its two groups.

### Creating a topic

**New topic** (top right), or tap an **empty cell** and choose **New topic here** (which creates and places it in one go).

Give it a **Title** (up to 120 characters), a **Category** (Windows Beginners, Windows Main, iPad Beginners, iPad Main, or **Club event**) and a **Presenter**, then **Create topic**. Notes links, slides and the members' briefing are added afterwards in its details.

A topic can only go in a column of its own category. A **Club event** (an AGM, a social, a combined session) can go in any column.

### Placing a topic on the board

Two ways, whichever is easier:

- **Tap to place:** tap the topic in the tray. The cells it can go in light up. Tap a lit cell.
- **Drag:** drag the topic from the tray onto a lit cell. *On an iPad, press and hold for about a third of a second until it lifts, then move.* A quick swipe that starts on a tile just scrolls the board, as usual.

The tile takes the meeting's usual date and times for that club and month.

**Pairing.** After you place a topic at one club, a strip above the board offers the other club's meeting in the same month, e.g. *"Also place Spotting scam emails at FCC Windows Beginners on Tue 17 Nov?"* → **Place on Tue 17 Nov** or **Not now**.

### Moving a tile

- **Drag** it to another lit cell; or
- choose **Move to…** (from the tile's menu or its details), then tap a lit cell.

The date and times follow the meeting pattern for the new month. The strip then offers to move the other club's tile too. Dragging near the top or bottom edge scrolls the board.

- **Swap:** drop a tile on another filled lit cell → **Swap** exchanges them.
- **Replace:** place a tray topic on a filled cell → **Replace**. The old topic stays in the tray.
- A tile dropped on the wrong kind of column is refused, with a message saying why.

### The tile's menu

- **PC:** right-click a tile (or a tray topic).
- **iPad:** press and hold, then lift without moving.

For a tile: **Edit details · Move to… · Copy · Remove from board**.
For a tray topic: **Place on board… · Edit details · Copy · Delete topic**.

### Copy and paste

Choose **Copy** on a tile or topic, then tap a lit cell to paste it there. Or tap an empty cell and choose **Paste "…"** in the strip. On a PC: Ctrl+C on a selected tile, click an empty cell, Ctrl+V.

A pasted tile is **the same topic** in another cell (for example the same topic again at another time of year). To make a *different* topic based on an old one, create a new topic.

### Removing and deleting

- **Remove from board** takes one tile off the board. The topic stays in the tray. (PC: select and press Delete; or drag the tile onto the tray.)
- **Delete topic** (in its details or the tray menu) removes the topic and its tiles. To protect the record of what was taught:
  - If **none** of its meetings has happened yet, it simply asks once.
  - If **some have happened and some are still to come**, it asks *"Keep the past sessions?"* → **Remove future tiles only** (the usual choice; the topic and its past meetings stay), **Delete everything**, or **Cancel**.
  - If **all** its meetings are in the past, it explains that this is the teaching record → **Keep it** (the usual choice) or **Delete everything**.

Everything can be undone (section 9).

---

## 8. Editing: the details panel

With **Edit** on, click or tap a tile to open its details for editing. The panel has two parts.

### The topic (shared by all its tiles)

- **Topic title**, **Category** and **Presenter**.
- **Tutorial notes (OneDrive link)** and **Slides (optional)** — paste a share link (section 14).
- **Members' briefing** — a short note for members, shown in the details and optionally printed in a group's PDF.

Changes here appear on **every** tile of the topic.

### This session (only this tile)

- **Date**, **Start** and **End** — change these if a meeting is not on its usual day. The tile then shows **Moved**. **Reset to meeting pattern** puts it back to the usual date and times.
- **Status** — **Planned** or **Cancelled**.
- **Invitations sent to GBCC Windows Beginners** (or whichever group) — tick when the email invitations have gone out. Only this tile shows **Invites sent**. If the tile later moves to another date, the tick is cleared (the members need a new invitation).

At the foot: **Save**, plus **Move to…**, **Copy**, **Remove from board**, **Delete topic** and **Add to calendar**. **Add to calendar** uses what is in the boxes, even before you press Save (it reminds you to save).

If the board refreshes while you are typing in the panel, your typing is kept.

---

## 9. Undo, saving, and working on two devices

### Saving

There is no Save button for the board itself: **every change saves on its own** a couple of seconds after you make it. The status at the top right tells you where things stand:

| Status | Meaning |
| --- | --- |
| **Unsaved changes** | Waiting a moment, so a burst of changes saves together |
| **Saving…** | Sending to GitHub |
| **Up to date · saved for everyone** | Saved. Members see it within a few minutes |
| **Not saved — retrying** | No internet or GitHub is busy. Your changes are kept on this device and retried automatically |
| **Not saved — needs a new key** | The key has expired or been removed. Paste a new key (section 12); your changes then save |

Each save is recorded on GitHub with a readable description (for example *Place “Spotting scam emails” at GBCC Windows Beginners, Nov 2026*), and nothing is ever lost: earlier versions can be restored (section 13).

### Undo

**Undo** (PC: Ctrl+Z) reverses your last action — a placement, a move, a deletion, a settings change — and can be pressed repeatedly. It remembers your last 50 actions until you reload or close the page. Hover over Undo on a PC to see what it will undo.

### Editing on two devices

You can edit from the PC and the iPad, or two editors can work at once. Each save is built on top of the newest copy, so one device never overwrites another's work. In the rare case that both change **the same tile or topic** at the same moment, the second change is not saved and a message explains; the board shows the newer version and you can make your change again if still needed. Press **↻ Refresh** to see another device's changes straight away.

### Keyboard shortcuts (PC)

| Keys | Action |
| --- | --- |
| Ctrl+Z | Undo |
| Ctrl+C | Copy the selected or focused tile's topic |
| Ctrl+V | Paste into the clicked or focused empty cell |
| Delete | Remove the selected tile from the board |
| Escape | Cancel a selection; close a panel or menu |
| Menu key or Shift+F10 | Open the menu of a focused tile |

(Cmd instead of Ctrl with an iPad keyboard.) Shortcuts are ignored while you are typing in a box.

---

## 10. Settings (owner)

Everyone can open **Settings** to read them. To change them you must be the owner, with **Edit** on.

Each card has its own **Save changes** and **Discard** buttons, which wake up when you change something in that card. Each save is one change on the board's Undo list, and a red message explains anything that needs correcting before it can save.

| Card | What you can change |
| --- | --- |
| **Board and clubs** | The board's title; each club's **full name**, **short name** and **meeting day**. The short names ("Great Barton", "Fornham") are used in the heading and on the PDFs page. The codes GBCC and FCC cannot change, because every tile refers to them |
| **Groups and times** | Each group's name (e.g. "GBCC Windows Beginners"), which week of the month each kind of group meets, and the **start and end times for each club separately** (GBCC starts/ends, FCC starts/ends) |
| **Weeks and breaks** | The week rule (section 11); the break months and their names (a month that already holds tiles cannot become a break) |
| **Closures** | Days a hall is closed (e.g. a bank holiday), for one club or both, with a short note |
| **Presenters** | Two-letter codes and names. A presenter used by a topic shows **In use** and can't be deleted, but can be made **inactive** so they no longer appear in New topic |

**Changing times or the meeting pattern.** If the change affects tiles already placed in the future, the board asks *"Update future tiles too?"* and lists them:

- **Update tiles too** — future tiles move to the new times or dates. Past tiles, and tiles you have moved by hand, are left alone.
- **Settings only** — the setting changes, and those tiles keep their old times and are marked **Moved**.

Beginners and Main sessions are allowed to overlap; the board does not stop you.

**If the clubs merge one day:** change the club names in **Board and clubs** and the group names in **Groups and times**. The PDFs page already asks "Which group?" / "Which session?", so its wording still makes sense.

Further down the page:

- **Editing access** — who this device is unlocked as, the key's expiry date and days left, **Paste new key**, **Key help**, and **Remove key from this device**. If GitHub does not report the expiry date, type it from GitHub's key page and press **Save date**, so the reminder works.
- **Backup, history and archive** — section 13.
- **About this plan** — when it was last saved and by whom, how many topics and sessions it holds, and which repository it saves to.

---

## 11. The meeting dates and the week rule

### The usual pattern

- GBCC meets on **Mondays**, FCC on **Tuesdays**.
- Meetings are in the **last two weeks of the month**: the **Windows** week first, then the **iPad** week.
- Each meeting day has **Beginners** (early afternoon) then **Main** (later afternoon). The exact times for each club are in Settings.
- No meetings in **July, August and December**.

So in a typical month, GBCC Windows is on the second-last Monday, FCC Windows the next day, and the iPad groups a week later. For example, March 2027: GBCC Windows Mon 22, FCC Windows Tue 23, GBCC iPad Mon 29, FCC iPad Tue 30.

The board works out every date from these settings, so a new tile always gets the right date and times.

### Why Settings offers two week rules

The two rules give **identical dates in almost every month**. They differ only in a month whose **last day is a Monday**: GBCC can meet on that last Monday, but there is no Tuesday after it in the month for FCC. That happens two or three times a year — **November 2026**, **May 2027** and **January 2028** in the board's current range.

- **Each club uses its own last two weeks** (the clubs' practice, and the board's setting): GBCC keeps its last two Mondays, including the last day of the month; FCC uses its last two Tuesdays. So in those months **FCC meets the week before GBCC** for each topic.
- **Both clubs use the same two weeks**: GBCC gives up that last Monday so that FCC always meets the day after GBCC.

November 2026, side by side:

| Group | Each club (the setting in use) | Same week |
| --- | --- | --- |
| GBCC Windows | Mon 23 Nov | Mon 16 Nov |
| FCC Windows | Tue 17 Nov | Tue 17 Nov |
| GBCC iPad | Mon 30 Nov | Mon 23 Nov |
| FCC iPad | Tue 24 Nov | Tue 24 Nov |

The board applies the chosen rule automatically in those months; it is **not** switched month by month. The choice exists only so that the clubs' practice could be changed one day without anyone touching the code. If it is changed, the board offers to move the affected future tiles.

A single meeting that has to be different (a hall booking clash, say) is simply edited in its details — it then shows **Moved**.

---

## 12. The editing key

Members only read the board, so they need nothing. **Saving** a change means writing to the plan file on GitHub, and GitHub only allows that with proof of who you are. The **editing key** (GitHub calls it a *fine-grained personal access token*) is that proof.

- It works only for the **planner** and **planner-test** repositories, and only for their files. It cannot touch anything else in your GitHub account.
- It **expires after a year**, so a lost or forgotten key stops working by itself.
- Each device remembers it. It is sent only to GitHub and never stored in the plan.

### Renewing it each year (about 5 minutes)

GitHub emails a week before the key expires, and the board shows a reminder at the top from **30 days** before, with **Renew key on GitHub**, **Paste new key**, **Key help** and **Later**.

1. **Open my keys on GitHub** (in Key help) and sign in if asked.
2. Under **Fine-grained tokens**, choose the planner key.
3. Press **Regenerate token**, choose a year, and confirm.
4. **Copy the new key straight away** — GitHub shows it only once. Keeping a copy in your password manager is a good idea.
5. On **each** device you edit from: **Settings → Paste new key**, paste, **Unlock**.

The old key stops working the moment you regenerate, so a device still holding it will ask for the new one. Nothing is lost.

### If it has already expired

The board goes view-only and shows a **Paste new key** box. Changes not yet saved stay on that device and save once the new key is in. An expired key can still be regenerated, as above.

### Making a brand-new key

Only if the old one was deleted. On GitHub's key page, **Generate new token** under Fine-grained tokens:

| Setting | Choose |
| --- | --- |
| Token name | Planner (anything you will recognise) |
| Resource owner | **FornhamCC** (not your own name) |
| Expiration | A year |
| Repository access | Only select repositories: **planner** and **planner-test** |
| Permissions | Repository permissions → **Contents: Read and write** (nothing else) |

### Keeping it safe

Paste it only into the board and your password manager — never email or message it. If you think someone has seen it, or a device is lost, regenerate it on GitHub: the old key stops working at once. **Settings → Remove key from this device** makes a device view-only again.

All of this is also built into the board: press **Key help** in Settings, in the Unlock box, or on the renewal reminder. It opens even when GitHub can't be reached.

---

## 13. Backup, history and the yearly archive (owner)

This card in **Settings** appears only on unlocked devices.

### Backups

**Download backup** saves the whole plan as one file, e.g. `Topic Planning Board backup 2026-10-19.json`. Keep it in OneDrive (on an iPad: **Share → Save to Files**). Each device remembers when it last made one, and after **90 days** without one a reminder appears on the board.

GitHub already keeps every version of the plan, so backups are a second safety net in case anything happened to the GitHub account.

**Restore from a backup file…** (owner, Edit on) — choose a backup file. The board checks it, tells you what it holds and what it will replace, then saves it as a new version. Undo reverses it, and the replaced plan stays in GitHub's history.

### History

**Show recent saves** lists the last 30 saves (date, who, what), newest first. **View** shows what that version held, with **Download this version** and (Edit on) **Restore this version**. Useful if something was changed by mistake some days ago.

### The yearly archive

So the board and the tray stay short, a finished calendar year can move to its own archive file.

- From **January**, the board asks the owner *"2026 has ended. Archive it now?"* → **Archive now** or **Not yet**. Nothing moves until you confirm, and the question returns on later visits until it is done. (The first time will be January 2027.)
- Archiving moves that year's meetings into `data/archive/2026.json`. A topic that also has meetings in the new year stays on the board with those.
- Undo puts the meetings back on the board. Archiving again later is safe; nothing is overwritten.

**Looking at an archived year (everyone):** once a year is archived, **Showing** appears in the second bar. Choose **2026 archive** to see that year on the board, read-only, with a banner across the top, and make its PDFs on the PDFs page. **Back to the current plan** returns.

The board's month range goes back at most 12 months, unless older meetings are still in the plan (a year not yet archived stays reachable).

---

## 14. Linking tutorial notes from OneDrive

Members open notes straight from a tile, past or future, so each topic's notes need a link anyone can open.

On the iPad (the OneDrive app):

1. Find the notes PDF → **⋯** → **Share**.
2. Choose **Anyone with the link** (view only; downloads allowed).
3. **Copy link**.
4. On the board, open the topic's details (Edit on) and paste into **Tutorial notes (OneDrive link)**. **Save**.

On a PC the steps are the same in OneDrive on the web or File Explorer (right-click → **Share**).

The tile then shows a paperclip, the details show **Open tutorial notes**, and group PDFs carry a clickable **Open notes** link. If a member is refused when opening the notes, the link was probably made for specific people only — make it again with **Anyone with the link**.

---

## 15. Adding another editor (owner)

A future presenter who will edit needs:

1. **A GitHub account** of their own (free).
2. To be **added to the FornhamCC organization** (github.com/FornhamCC → **People** → **Invite member**), and given **Write** access to the **planner** repository (repository **Settings → Collaborators and teams**). Add **planner-test** too if they will try things on the test copy. Check GitHub's current wording when doing this; the menus change from time to time.
3. **Their own editing key**, made in their account exactly as in section 12 (resource owner **FornhamCC**).

They will appear as **Editor**: they can do everything on the board, but not change Settings, restore or archive. Every save is signed with their GitHub name, so you can always see who changed what. To remove an editor, remove them from the organization; their key stops working at once.

---

## 16. Troubleshooting

**Members don't see my change yet.** Members' copies update within a few minutes of a save (GitHub republishes the site), and their board checks every 5 minutes. They can press **↻ Refresh**.

**The iPad still shows the old version of the board after a release.** Close the Safari tab and open the address again (or pull down to reload).

**"Not saved — retrying".** No internet connection, or GitHub is briefly busy. Leave the page open; it keeps trying and saves as soon as it can. Your changes are not lost.

**"Not saved — needs a new key" or the board asks for a key.** The key has expired or been regenerated. Paste the current key (section 12).

**"Your change was not saved, because … was changed on another device first."** Two devices changed the same thing at the same moment. The board now shows the other device's version; make your change again if still needed.

**A topic won't go into a cell.** It belongs to another kind of group (a Windows Beginners topic can only go in a Windows Beginners column), there is no meeting that month, or it's already there. The message says which. Make it a **Club event** if it really belongs in every kind of group.

**There's no Edit switch.** The device isn't unlocked (press **Unlock editing**), or you are looking at an archived year (choose **Back to the current plan**).

**Pressing and holding on the iPad shows Apple's own menu.** This was fixed in Stage 2; if it ever reappears, reload the page.

**A PDF has run onto a second page.** Usually long topic titles in a full calendar year. Shorter titles, or a shorter range under **More options**, keep it to one page.

**The PDF button seems to do nothing on the iPad.** Look for Safari's download prompt or the downloads arrow at the top of the screen.

**Something is badly wrong with the plan.** Settings → **Backup, history and archive** → **Show recent saves** → **View** a version from before the problem → **Restore this version**. Undo reverses a restore.

---

## 17. Quick reference

| I want to… | Do this |
| --- | --- |
| See a meeting's details | Click or tap its tile |
| Put a meeting in my calendar | Tile → **Add to calendar** |
| Make a group's PDF for the year | **PDFs** → club → session → year → **Make PDF** |
| Start editing | **Unlock editing** (once per device), then switch **Edit** on |
| Add a topic | **New topic**, or tap an empty cell → **New topic here** |
| Place it | Tap it in the tray, tap a lit cell (or drag) |
| Place it at the other club too | Accept the strip's **Place on …** offer |
| Move a meeting | Drag the tile, or menu → **Move to…** |
| Change one meeting's date or time | Tile → **This session** → change → **Save** |
| Mark invitations sent | Tile → **This session** → tick **Invitations sent** → **Save** |
| Cancel a meeting | Tile → **Status: Cancelled** → **Save** |
| Take a tile off the board | Menu → **Remove from board** |
| Undo | **Undo** (Ctrl+Z) |
| Open the tile menu | PC: right-click · iPad: press, hold, lift |
| Renew the key | Settings → **Key help** → *Renewing it each year* |
| Make a backup | Settings → **Download backup** |
| Change times or names | Settings (owner, Edit on) → the card → **Save changes** |
