# Stage 4b — testing guide (backup, history and the yearly archive)

Stage 4b adds a **Backup, history and archive** card to **Settings**, below Editing access. It appears only on unlocked devices.

| Part | Who | What it does |
| --- | --- | --- |
| **Download backup** | Any editor | Saves the whole plan (as last saved) as a file, e.g. `Topic Planning Board backup 2026-10-18.json`, to keep in OneDrive. Each device remembers when it last made one. After 90 days without one, a reminder appears at the top of the board. |
| **Restore from a backup file…** | Owners, Edit on | Choose a backup file. The board checks it, says what it holds and what it will replace, then saves it as a new version. Undo reverses it, and the replaced plan stays in GitHub's history. |
| **History** | Owners | **Show recent saves** lists the last 30 saves (date, who, what). **View** shows what a version holds, with **Download this version** and (Edit on) **Restore this version**. |
| **Yearly archive** | Owners | Once a calendar year has ended, its sessions can move to a separate file, `data/archive/2026.json`, so the board and the topic tray stay short. From January the board asks **"2026 has ended. Archive it now?"** with **Archive now** / **Not yet**; nothing moves until you confirm. A topic that also has later sessions stays on the board with those sessions. Undo puts the sessions back on the board (the archive keeps its copy, so archiving again is safe). |
| **Viewing an archive** | Everyone | Once a year is archived, **Showing** appears in the second header bar. Choose **2026 archive** to see that year on the board, read-only, and make its PDFs on the PDFs page. **Back to the current plan** returns. |

Also in this release: the board's month range now goes back at most 12 months (Nice to Have 6), unless older sessions are still in the plan.

**This zip includes Stage 4a** (the PDFs). If you have not uploaded Stage 4a yet, this upload covers both.

## Part A — put Stage 4b on the test copy (about 3 minutes)

1. Open **github.com/FornhamCC/planner-test** → **Add file → Upload files**.
2. Unzip `planner-stage4b-test.zip`. From the `planner` folder inside it, drag in **index.html**, **README.md**, the **vendor** folder and the **docs** folder. Do **not** upload a `data` folder.
3. **Commit changes**. After a minute or two, reload **https://fornhamcc.github.io/planner-test/** on the PC and the iPad.

**Test copy only:** the real board only offers to archive a year once it has ended (the first prompt will be in January 2027). So that you can try it now, the test copy's card also offers **Archive 2026…**, with a note saying so.

## Part B — what to try

Unlock and turn **Edit** on, then open **Settings**.

| # | Check | PC | iPad |
|---|---|---|---|
| 1 | The **Backup, history and archive** card is under Editing access. In a private window (not unlocked) it is not shown | ☐ | ☐ |
| 2 | **Download backup**: a .json file arrives; the card now says "Last backup downloaded on this device: … (today)". iPad: save it to OneDrive with Share → Save to Files | ☐ | ☐ |
| 3 | Make a small change on the board (e.g. rename a topic), then **Restore from a backup file…** and choose the backup from check 2. The message says what it holds; **Replace the plan** puts the old name back | ☐ | ☐ |
| 4 | Board page → **Undo**: the change from check 3 comes back | ☐ | ☐ |
| 5 | **Show recent saves**: your recent saves are listed, newest first, marked "(latest)" | ☐ | ☐ |
| 6 | **View** on an older save: it says what it held; **Download this version** saves it; **Restore this version** brings it back (Undo reverses) | ☐ | ☐ |
| 7 | Turn **Edit** off: Restore and Archive buttons are greyed out; Download backup and View still work | ☐ | ☐ |
| 8 | **Archive 2026…** (test copy only): the message says how many sessions and topics move. **Archive 2026** → those tiles leave the board and the tray | ☐ | ☐ |
| 9 | On GitHub, the test repository now has **data/archive/2026.json** | ☐ | — |
| 10 | **Showing → 2026 archive**: the board shows 2026, read-only, with a banner; tiles open their details; there is no Edit switch | ☐ | ☐ |
| 11 | While on the archive, open **PDFs**: it is set to 2026; make a group PDF of the archived year | ☐ | ☐ |
| 12 | **Back to the current plan**: the board and the Edit switch return | ☐ | ☐ |
| 13 | Board page → **Undo**: the archived tiles return to the board. (Archiving again afterwards is fine.) | ☐ | ☐ |
| 14 | In a private window, **Showing → 2026 archive** works for a member too | ☐ | ☐ |
| 15 | Afterwards, put the test copy back as you like it: Undo, or Restore the backup from check 2 | ☐ | ☐ |

Note anything odd (what you did, what you expected, what happened) and send it over.

## Part C — making it live

When you are happy with the test copy:

1. Open **github.com/FornhamCC/planner** → **Add file → Upload files**.
2. Drag in **index.html**, **README.md**, the **vendor** folder and the **docs** folder from the same zip, and **Commit changes**.
3. **Never upload a `data` folder to the real repository.** The board creates `data/archive/` itself when a year is first archived.
4. Reload https://fornhamcc.github.io/planner/ on each device, then download a first backup to OneDrive.
