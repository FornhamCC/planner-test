# Stage 4a — testing guide (PDFs)

Stage 4a makes the **PDFs** page work. Anyone with the board's address can make these PDFs, unlocked or not:

| Choice | What you get |
| --- | --- |
| **One group** | A list of one group's meetings (portrait): date, time, topic, presenter and a clickable **Open notes** link. Tick **Include each topic's members' briefing** to print the briefing under each topic. |
| **One club** | That club's four groups side by side, a row per month (landscape). |
| **The whole plan** | Every group side by side, as on the board (landscape). Choose all groups, Windows only or iPad only. |
| **All eight groups in one file** | The eight group lists in one PDF, each starting on a new page. The easiest way on an iPad. |
| **All eight groups as separate files** | Eight group PDFs, downloaded one after another. The browser may ask once to allow several downloads. |

**Months:** From and To, with quick buttons for this year, next year, or the months shown on the board. It starts on next year's January–December (from September onwards; before that, this year). A line under the choices says what the PDF will hold, e.g. "9 meeting months, 3 break. 14 of 18 meetings have a topic so far."

In every PDF: break months are one shaded row; a cancelled meeting says **Cancelled**; a month with no topic yet shows its usual date and **To be arranged**; a closure from Settings shows **Closed: …**. Colours match the board, with the group name always in text so it reads on a black-and-white printer. Each page has the title, months, page number and the date it was printed. The "Invitations sent" tick is left out.

This release adds a new **vendor** folder holding the two PDF libraries (jsPDF and AutoTable, free MIT licence). It must be uploaded along with index.html.

## Part A — put Stage 4a on the test copy (about 3 minutes)

1. Open **github.com/FornhamCC/planner-test** → **Add file → Upload files**.
2. Unzip `planner-stage4a-test.zip`. From the `planner` folder inside it, drag in **index.html**, the **vendor** folder and the **docs** folder. Do **not** upload a `data` folder.
3. **Commit changes**. After a minute or two, reload **https://fornhamcc.github.io/planner-test/** on the PC and the iPad (on the iPad, close and reopen the tab if the old version still shows).

The test copy's plan has only a few topics. For a fuller check, place a few topics in 2027 on the test copy first (they do not affect the real board).

## Part B — what to try

| # | Check | PC | iPad |
|---|---|---|---|
| 1 | **PDFs** tab: the page shows the five choices, From / To and **Make PDF** | ☐ | ☐ |
| 2 | **One group**, e.g. GBCC Windows Beginners, 2027 → **Make PDF**. Open it: dates, times, topics, presenters, break rows | ☐ | ☐ |
| 3 | In that PDF, tap or click **Open notes** on a topic that has a notes link: the OneDrive file opens | ☐ | ☐ |
| 4 | Tick **Include each topic's members' briefing** → Make PDF: briefings appear under the topics | ☐ | ☐ |
| 5 | **One club** (landscape): the four groups side by side, coloured like the board | ☐ | ☐ |
| 6 | **The whole plan**: all eight groups; then **Windows groups only** and **iPad groups only** | ☐ | ☐ |
| 7 | **All eight groups in one file**: one PDF, a page (or more) per group | ☐ | ☐ |
| 8 | **All eight groups as separate files**: eight files arrive (allow several downloads if asked) | ☐ | ☐ |
| 9 | iPad: after **Download**, open the file from the downloads arrow in Safari's address bar → **Share → Save to Files** → OneDrive | — | ☐ |
| 10 | Quick buttons **2026**, **2027** and **Months shown on the board** set From / To; choosing To before From shows a message and greys out Make PDF | ☐ | ☐ |
| 11 | Print one PDF in black and white: is it still easy to read? | ☐ | — |
| 12 | In a private window (not unlocked), PDFs can still be made | ☐ | ☐ |

Note anything odd (what you did, what you expected, what happened) and send it over. Comments on the look of the PDFs are welcome too: what to add, remove or make bigger.

## Part C — making it live

When you are happy with the test copy:

1. Open **github.com/FornhamCC/planner** → **Add file → Upload files**.
2. Drag in **index.html**, the **vendor** folder and the **docs** folder from the same zip, and **Commit changes**.
3. **Never upload a `data` folder to the real repository.**
4. Reload https://fornhamcc.github.io/planner/ on each device.
