# Key help — testing guide

This small release adds **Key help** (Nice to Have 10): a plain-English guide to the editing key, built into the board. It explains why there is a key, how to renew it each year, what to do if it has expired, how to make a brand-new one, and how to keep it safe. Nothing else on the board changes, and the plan file is not touched.

Key help is in three places, each opening the guide at the most useful section:

- **Settings → Editing access**, beside **Paste new key** (or **Unlock editing** on a view-only device).
- The **renewal reminder** at the top of the board (from 30 days before the key expires).
- The **Unlock editing** box, bottom left (it replaces the old "How to make a key" link; the full setup guide is still linked from inside Key help).

## Part A — put it on the test copy (about 3 minutes)

1. Open **github.com/FornhamCC/planner-test** → **Add file → Upload files**.
2. Unzip `planner-keyhelp-test.zip`. From the `planner` folder inside it, drag in **index.html** and the **docs** folder. Do **not** upload a `data` folder.
3. **Commit changes**. After a minute or two, reload **https://fornhamcc.github.io/planner-test/** on the PC and the iPad (on the iPad, close and reopen the tab if the old version still shows).

## Part B — what to try

| # | Check | PC | iPad |
|---|---|---|---|
| 1 | **Settings → Editing access → Key help** opens the guide over the page | ☐ | ☐ |
| 2 | The five chips at the top (Why there is a key … Keeping it safe) jump to each section | ☐ | ☐ |
| 3 | The middle of the guide scrolls; the three buttons at the foot stay in view | ☐ | ☐ |
| 4 | **Open my keys on GitHub** opens GitHub's key page in a new tab | ☐ | ☐ |
| 5 | **Full setup guide** opens the setup guide in a new tab | ☐ | ☐ |
| 6 | **Paste new key** closes the guide and opens the Unlock box, ready to paste | ☐ | ☐ |
| 7 | The ✕, Escape (PC) or a tap outside the guide closes it | ☐ | ☐ |
| 8 | **Unlock editing** box (on a view-only device or a private window): **Key help** at bottom left opens the guide on top; closing it returns to the Unlock box | ☐ | ☐ |
| 9 | Optional, as in Stage 3 check 17: type a key expiry date about 2 weeks ahead in Settings → **Save date**. The reminder at the top now has **Key help**, opening at "Renewing it". Put the real date back afterwards | ☐ | ☐ |
| 10 | Read the guide through: is anything unclear, or worded differently from what you see on GitHub? | ☐ | — |

Note anything odd (what you did, what you expected, what happened) and send it over.

## Part C — making it live

When you are happy with the test copy:

1. Open **github.com/FornhamCC/planner** → **Add file → Upload files**.
2. Drag in **index.html** and the **docs** folder from the same zip, and **Commit changes**.
3. **Never upload a `data` folder to the real repository.**
4. Reload https://fornhamcc.github.io/planner/ on each device.
