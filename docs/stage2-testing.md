# Stage 2 — testing guide

Stage 2 adds the topic tray, New topic, placing by drag and drop or by tapping, pairing GBCC and FCC, moving and swapping, copy and paste, removing and deleting, undo, and four items from the Nice to Have list: the board fits the iPad's width, an "Invitations sent" tick on each tile, an "Add to calendar" button, and a Delete that keeps past sessions.

**Stage 2 fixes (17 Oct 2026)**, after the first round of iPad testing:
- **Invitations sent** is now ticked per tile (each tile is one email group), not per topic (bug B1).
- Safari no longer turns dates into links, so press-and-hold on a tile always gives the board's menu; a tile's details have an **Add to calendar** button instead (Nice to Have 4).
- **Delete topic** offers to keep sessions that have already taken place (Nice to Have 5).

To try the fixes on the test copy, see **Part A2** below, then re-check rows 18 and 25 to 30.

Test it on a **test copy** first, so the real plan is never disturbed. The same `index.html` works in both places: it saves to whichever repository it was opened from, and a brown **TEST COPY** banner shows across the top of the test copy.

## Part A — make the test copy (about 10 minutes, once)

1. Sign in to GitHub in Chrome and open the **FornhamCC** organization.
2. **New repository** → name it `planner-test`, choose **Public**, leave everything else unticked → **Create repository**.
3. On the empty repository's page choose **uploading an existing file**. Unzip `planner-test-full.zip` on your PC, open the `planner` folder inside it, select **everything in it** (index.html, README.md and the data, docs, fonts and tests folders) and drag it all onto the page. Wait for the files to list, then **Commit changes**.
4. **Settings → Pages**: Source **Deploy from a branch**, Branch **main**, folder **/ (root)** → **Save**. After a minute or two the test copy is at **https://fornhamcc.github.io/planner-test/**
5. Let your access key reach the test copy: open **github.com/settings/personal-access-tokens**, choose your planner key → **Edit** → under Repository access, **Only select repositories**, add `planner-test` alongside `planner` → **Update**. The key's text does not change, so nothing needs pasting again on the PC.
6. Open the test address on the PC and on the iPad. Each device treats it as a separate site, so press **Unlock editing** and paste the key once on each.

The test copy starts with a copy of the real plan. Change anything you like there.

## Part A2 — put the 17 Oct fixes on the test copy (about 3 minutes)

1. Open **github.com/FornhamCC/planner-test** → **Add file → Upload files**.
2. Unzip `planner-test-fixes-17oct.zip`. Drag in **index.html**, **README.md** and the **docs** folder (it holds this guide). Do **not** upload any `data` folder: the test copy keeps the plan you have been testing with.
3. **Commit changes**. After a minute or two, reload **https://fornhamcc.github.io/planner-test/** on the PC and the iPad (on the iPad, pull down to reload, or close and reopen the tab). Your key is still remembered.

Ticks you made yesterday were stored on the topic. The new version ignores them, so no tile shows "Invites sent" until you tick it again.

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
| 18 | **Invitations sent** (per tile): open a tile; in **This session** tick "Invitations sent to GBCC Windows Beginners" (or whichever group) → Save. Only **that** tile shows "Invites sent"; the other club's tile does not. The tray card shows "Invites 1 of 2" | ☐ | ☐ |
| 19 | **Delete topic** (in the details) on a topic with no past dates asks first, removes its tiles; Undo brings it back | ☐ | ☐ |
| 20 | Tray filters: **Needs placing**, **Upcoming**, **All** | ☐ | ☐ |
| 21 | With **Edit** off: no tray, no editing tools; tapping a tile shows read-only details | ☐ | ☐ |
| 22 | Change something on the PC; press Refresh on the iPad; it appears | ☐ | ☐ |
| 23 | The test copy's saves appear under **planner-test → Commits** with readable messages | ☐ | — |
| 24 | Open the test address in a private window (never unlocked): it reads correctly with no editing controls | ☐ | ☐ |
| 25 | **Tick cleared on move**: tick a tile, then drag it (or **Move to…**) to another month. The toast says the tick was cleared, and the tile no longer shows "Invites sent". Undo brings the tick back | ☐ | ☐ |
| 26 | **Tick cleared on a date change**: tick a tile, then change its date in the details → Save. The tick is cleared | ☐ | ☐ |
| 27 | **No iOS date menu**: press and hold on the date line of a tile → the board's own menu appears, not Apple's "Add to Calendar / Copy / Ask Siri" menu | — | ☐ |
| 28 | **Add to calendar**: open a tile → **Add to calendar**. PC: a .ics file downloads; open it and Outlook shows the meeting at the right date and time. iPad: Calendar offers to add the event (or it appears in Downloads; tap it there). Check the time is right for both a winter and a summer meeting | ☐ | ☐ |
| 29 | **Add to calendar for readers**: in a private window (not unlocked), tap a tile → **Add to calendar** works there too | ☐ | ☐ |
| 30 | **Safer Delete**: on a topic that has a tile in **September 2026** (already past) and one later, press **Delete topic** → "Keep the past sessions?" with **Remove future tiles only**, **Delete everything** and **Cancel**. Choose **Remove future tiles only**: the later tile goes, the September tile and the topic stay. Undo puts it back. On a topic whose tiles are **all** past, Delete offers **Keep it** or **Delete everything** | ☐ | ☐ |

Tip for row 30: show September with the month range (press the month range label and choose **Sep 2026** as From), then place a topic in a September cell; past cells can still be filled.

Also worth a look on the iPad in **portrait**: the board scrolls sideways for all eight columns, and the **Windows** or **iPad** filter shows four columns that fit.

Note anything odd (what you did, what you expected, what happened) and send it over; small fixes go into this stage before it goes live.

## Part C — making it live

Once you are happy with the test copy:

1. Open the real **planner** repository → **Add file → Upload files**.
2. Use the **index.html**, **README.md** and **docs** folder from `planner-test-fixes-17oct.zip` (the same files you tested). Drag those onto the page, keeping the `docs` folder, and **Commit changes**.
3. **Never upload `data/plan.json` to the real repository.** The real plan lives there and has moved on since the zip was made.
4. After a minute or two, reload https://fornhamcc.github.io/planner/ on each device. Your key is still remembered there.

The test copy can stay for future stages, or be deleted from its Settings page.
