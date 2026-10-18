# Stage 3 — testing guide

Stage 3 makes the **Settings** page editable for owners, adds a **key renewal reminder**, fixes bug **B2** (Add to calendar now uses what is showing in the details panel) changes the tray's **All** filter to **Past 12 months** (Nice to Have 6), and lets each club have its **own session times** for each group (Nice to Have 8).

**Updated 17 Oct, 2:30pm:** per-club times added. If you uploaded the earlier Stage 3 zip, upload `index.html` (and `docs`) from `planner-stage3-test-v2.zip` over it.

Test it on the **test copy** first, as for Stage 2. The test copy keeps its own plan, so nothing here touches the real board.

## Part A — put Stage 3 on the test copy (about 3 minutes)

1. Open **github.com/FornhamCC/planner-test** → **Add file → Upload files**.
2. Unzip `planner-stage3-test-v2.zip`. From the `planner` folder inside it, drag in **index.html**, **README.md** and the **docs** folder. Do **not** upload a `data` folder.
3. **Commit changes**. After a minute or two, reload **https://fornhamcc.github.io/planner-test/** on the PC and the iPad (on the iPad, close and reopen the tab if the old version still shows).

## Part B — what to try

Unlock and turn **Edit** on, then open **Settings**. Each card has its own **Save changes** and **Discard** buttons, which wake up as soon as you change something in that card. Every save can be undone with **Undo** on the Board page.

| # | Check | PC | iPad |
|---|---|---|---|
| 1 | With **Edit** off, Settings shows the values read-only with a note "Turn on Edit…". With Edit on, the five cards become editable | ☐ | ☐ |
| 2 | **Board and clubs**: change the board title or a club's short name → **Save changes**. The heading at the top changes | ☐ | ☐ |
| 3 | Go to the Board page → **Undo**. The old title comes back | ☐ | ☐ |
| 4 | **Discard**: type something in a card, press Discard. The saved values return | ☐ | ☐ |
| 5 | Clear the board title and Save: a red message explains, nothing is saved | ☐ | ☐ |
| 6 | **Groups and times**: rename a group (e.g. "GBCC Windows Beginners") → Save. Tiles' details and commit messages use the new name | ☐ | ☐ |
| 7 | **Per-club times**: Groups and times shows **GBCC starts / ends** and **FCC starts / ends** for each category. Set FCC Beginners to your real Fornham times → Save. Empty FCC cells, new FCC tiles and Add to calendar use them; GBCC keeps its own | ☐ | ☐ |
| 7a | **Change a session time** (e.g. GBCC Windows Beginners to start 12:45) on a group that has future tiles → **"Update future tiles too?"** lists them. **Update tiles too**: future tiles change; past tiles and tiles you have moved by hand stay. Undo reverses settings and tiles together | ☐ | ☐ |
| 8 | Same kind of change, choose **Settings only**: the setting changes; those tiles keep their times and show **Moved**, and are not offered again | ☐ | ☐ |
| 9 | Make a group end before it starts → a red message explains, nothing is saved. (Beginners and Main may overlap; that is allowed.) | ☐ | ☐ |
| 10 | **Weeks and breaks**: tick a month that has tiles in it → refused with a message naming the month. Tick an empty month → it becomes a hatched break band on the board. Untick it again afterwards | ☐ | ☐ |
| 11 | Switch the week rule to **Both clubs use the same two weeks** → in November 2026 the board offers to move GBCC tiles from Mon 30 / 23 Nov to the week before. Undo, or switch back | ☐ | ☐ |
| 12 | **Closures**: **Add a closure** for Mon 31 May 2027 (Spring Bank Holiday), GBCC only, note "Bank holiday" → Save. The GBCC cells that day show the note; a tile already placed that day shows a red **Closed** chip | ☐ | ☐ |
| 13 | **Presenters**: **Add a presenter** (two letters, any case; it saves in capitals) → Save. New topic now offers them | ☐ | ☐ |
| 14 | A presenter used by a topic shows **In use** and has no delete button. Untick **Active** → Save: they disappear from New topic's list but stay on existing topics | ☐ | ☐ |
| 15 | Type in a card, then press **Refresh** at the top: your typing is still there | ☐ | — |
| 16 | **Key expiry**: Editing access shows the expiry date and days left. If it says "Not shown to the board by GitHub", type the date from GitHub's key page → **Save date** | ☐ | ☐ |
| 17 | **Key reminder** (try on the test copy only): type an expiry date about 2 weeks ahead → **Save date**. A reminder appears at the top with **Renew key on GitHub**, **Paste new key** and **Later**. Put the real date back afterwards | ☐ | ☐ |
| 18 | **B2 – Add to calendar**: open a tile, change its start time, **don't** Save, press **Add to calendar**. The calendar entry has the new time, and a message reminds you to press Save | ☐ | ☐ |
| 19 | **Tray – Past 12 months**: the third tray filter is now **Past 12 months**: upcoming topics plus topics taught in the last year | ☐ | ☐ |
| 20 | Readers (private window): Settings is read-only, with no Save buttons | ☐ | ☐ |

Note anything odd (what you did, what you expected, what happened) and send it over.

## Part C — making it live

When you are happy with the test copy:

1. Open **github.com/FornhamCC/planner** → **Add file → Upload files**.
2. Drag in **index.html**, **README.md** and the **docs** folder from the same zip, and **Commit changes**. This time please include README.md and docs: the live repository still has the Stage 1 versions.
3. **Never upload a `data` folder to the real repository.**
4. Reload https://fornhamcc.github.io/planner/ on each device.
