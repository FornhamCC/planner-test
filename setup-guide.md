# Topic Planning Board — Setup Guide

This guide puts the board online for the first time. It takes about an hour, done once. You need your personal GitHub account, your Bluehost login, and the files from the Stage 1 delivery.

The work is in five parts:

| Part | What you do | Can wait? |
| --- | --- | --- |
| A | Create the FornhamCC organization and allow access keys | No |
| B | Create the planner repository, upload the files, switch on GitHub Pages | No |
| C | Make your access key and unlock the board | No |
| D | Point fornhamcomputerclub.com at GitHub (Bluehost) | Yes — any time before the domain renewal on 30 Dec 2026 |
| E | Check everything works | No |

After parts A to C the board is already live at **https://fornhamcc.github.io/planner/**. Part D only moves it to fornhamcomputerclub.com/planner.

---

## Part A — The club organization

### A1. Create the organization

1. Sign in to github.com with your personal account.
2. Click your picture (top right) → **Your organizations** → **New organization**.
3. Choose the **Free** plan.
4. Organization name: **FornhamCC**. Contact email: your own.
5. "This organization belongs to": **My personal account**.
6. Complete the check and click **Next**, then skip inviting members (**Complete setup**).

You are now the owner of FornhamCC.

### A2. Allow fine-grained access keys

GitHub calls the access key a *fine-grained personal access token*. Organizations must allow them once.

1. Go to **github.com/FornhamCC** → **Settings** (top menu of the organization).
2. In the left menu, under **Personal access tokens**, click **Settings**.
3. On the **Fine-grained tokens** tab:
   - Choose **Allow access via fine-grained personal access tokens**.
   - Under approval, choose **Do not require administrator approval**. (You are the only editor; approval would only add a step.)
   - If there is a maximum lifetime setting, leave it at the longest, or no limit.
4. Click **Save** / **Enroll**.
5. On the **Tokens (classic)** tab, choosing **Restrict access via personal access tokens (classic)** is good practice; the board does not use classic tokens.

---

## Part B — The planner repository

### B1. Create the repository

1. Go to **github.com/FornhamCC** → **Repositories** → **New repository**.
2. Owner: **FornhamCC**. Repository name: **planner**.
3. Visibility: **Public** (GitHub Pages is free only for public repositories; the plan holds nothing private).
4. Tick **Add a README file** (so the repository starts with a `main` branch).
5. Click **Create repository**.

### B2. Upload the files

The Stage 1 delivery contains these files and folders:

```
index.html
README.md
.nojekyll
data/plan.json
fonts/  (two .woff2 files and OFL-LICENSE.txt)
tests/index.html
docs/setup-guide.md
```

1. In the planner repository, click **Add file** → **Upload files**.
2. On your PC, open the delivered `planner` folder in File Explorer, select **everything inside it** (Ctrl+A), and drag it onto the GitHub page. Edge and Chrome keep the folders (`data`, `fonts`, `tests`, `docs`) as they are.
3. Check the list shows `data/plan.json` with its folder name. If the delivered README.md replaces GitHub's, that is intended.
4. Commit message: "Stage 1 of the Topic Planning Board". Choose **Commit directly to the main branch** and click **Commit changes**.

> **The `.nojekyll` file.** Windows hides files whose names start with a dot, and it may not be dragged across. If it is missing from the repository after uploading: **Add file** → **Create new file**, name it `.nojekyll`, leave it empty, **Commit changes**. It tells GitHub to publish the files exactly as they are.

### B3. Switch on GitHub Pages

1. In the planner repository: **Settings** → **Pages** (left menu).
2. Under **Build and deployment**, Source: **Deploy from a branch**.
3. Branch: **main**, folder **/ (root)**. Click **Save**.
4. Wait two or three minutes, then refresh the page. It shows "Your site is live at https://fornhamcc.github.io/planner/".

Open that address. You should see the board with the Club AGM in both Fornham Windows columns in January 2027.

### B4. Run the date tests

Open **https://fornhamcc.github.io/planner/tests/**. A green bar should say all tests passed. These check every meeting date from September 2026 to July 2028.

---

## Part C — Your access key

The key lets the board save the plan for you. It works only for the planner repository and only for its files.

### C1. Make the key

1. Click your picture (top right) → **Settings**.
2. Left menu, at the bottom: **Developer settings** → **Personal access tokens** → **Fine-grained tokens**.
3. Click **Generate new token**.
4. Token name: **Topic Planning Board**. Description: "Saving the club topic plan".
5. **Resource owner: FornhamCC** (not your personal account — this is the step most often missed).
6. Expiration: choose **Custom** and pick a date about a year ahead, or the longest GitHub offers. The board reminds you before it runs out.
7. Repository access: **Only select repositories** → choose **FornhamCC/planner**.
8. Permissions → **Repository permissions** → **Contents: Read and write**. Leave everything else as it is. ("Metadata: Read-only" is added automatically; that is expected.)
9. Click **Generate token**, check the summary, and confirm.
10. **Copy the key now.** It starts `github_pat_` and GitHub shows it only once.

Save it in your password manager (for example Bitwarden), named "Topic Planning Board key". You will paste it into each device you edit on.

### C2. Unlock the board

On your PC, then on your iPad:

1. Open the board.
2. Click **Unlock editing** (top right) and paste the key. Click **Unlock**.
3. The header shows **Owner**, the save status shows "Up to date · saved for everyone", and the **Edit** switch is on.

The device remembers the key. Next time the board opens in View mode; turn on **Edit** when you want to change something.

### C3. Try a save

1. With Edit on, tap the **Club AGM** tile in January.
2. Change something small (for example the briefing) and press **Save**.
3. The status shows "Saving…" then "Up to date · saved for everyone".
4. On GitHub, open the planner repository → **Commits** (or the clock icon beside the file list). Your save is there, with a message such as *Edit topic "Club AGM"*.

The public copy members see catches up within a few minutes.

---

## Part D — The club domain (Bluehost)

> ### Before starting Part D
> - **Renewal:** fornhamcomputerclub.com is registered with Bluehost until **30 December 2026**. Renew it before then (and turn on auto-renew in Bluehost), or the board's address stops working. The board itself keeps working at https://fornhamcc.github.io/planner/ whatever happens to the domain.
> - **Name servers:** the domain's name servers still point to SiteGround (NS1.GUK1006.SITEGROUND.EU), left over from the cancelled hosting. While they do, records added in Bluehost have no effect. Step D3 switches them back to Bluehost.
> - There is no current website at the address, so nothing is lost by changing its records.
> - **Email:** if any club email addresses @fornhamcomputerclub.com are still in use, say so before changing the name servers; their mail records would need re-creating in Bluehost. (With the hosting cancelled, they are probably not working now.)

### D1. Create the organization's main site

The domain belongs to the organization's main site. GitHub then serves the board beneath it at /planner.

1. **github.com/FornhamCC** → **New repository**.
2. Name it exactly **FornhamCC.github.io**. Public. Tick **Add a README file**. Create.
3. **Add file** → **Upload files**: upload `index.html` and `CNAME` from the delivered **site-placeholder** folder. Commit to main.
4. **Settings** → **Pages**: Source **Deploy from a branch**, branch **main**, **/ (root)**, **Save**.

### D2. Verify the domain with GitHub

Verifying stops anyone else using your domain on GitHub. Do it before changing the address records.

1. **github.com/FornhamCC** → **Settings** → **Pages** (left menu, under Code, planning, and automation).
2. Click **Add a domain**, enter **fornhamcomputerclub.com**, click **Add domain**.
3. GitHub shows a **TXT record** to create: a host name like `_github-pages-challenge-FornhamCC` and a long value. Keep this page open.
4. In Bluehost (next step), add that TXT record. Then come back and click **Verify**. It can take from a few minutes up to a day for GitHub to see it; you can leave the page and come back.

### D3. Point the name servers back to Bluehost, then add the records

Bluehost redesigns its pages from time to time, so the menu names may differ slightly. Do this step before clicking **Verify** in D2, because GitHub can only see the TXT record once Bluehost is answering for the domain.

1. Sign in at **bluehost.com** → **Domains** (left menu) → choose **fornhamcomputerclub.com**.
2. Find **Name servers** (often under the **DNS** tab, or **Manage** → **Name servers**). It shows NS1.GUK1006.SITEGROUND.EU and NS2.GUK1006.SITEGROUND.EU.
3. Choose **Use Bluehost defaults** (or **Bluehost name servers**), which are ns1.bluehost.com and ns2.bluehost.com, and save. The switch can take a few hours, occasionally up to two days, to take effect everywhere.
4. Open the **DNS** tab (sometimes **Advanced DNS** or **DNS records**). With Bluehost's name servers in use, the records you add here are the ones that count. Bluehost may have filled in some default records; the steps below say which to change.

Now make these changes:

**TXT record (for verification, from D2)**

| Type | Host / Name | Value | TTL |
| --- | --- | --- | --- |
| TXT | `_github-pages-challenge-FornhamCC` | the value GitHub showed | default |

(If Bluehost adds the domain name to the host automatically, enter only the part shown above.)

**A records for the bare domain (@)**: edit the existing A record for `@` to the first address, then add three more:

| Type | Host / Name | Points to | TTL |
| --- | --- | --- | --- |
| A | @ | 185.199.108.153 | 1 hour |
| A | @ | 185.199.109.153 | 1 hour |
| A | @ | 185.199.110.153 | 1 hour |
| A | @ | 185.199.111.153 | 1 hour |

Remove any *other* A record for `@` (for example one Bluehost added by default, pointing to a Bluehost address). (These four are GitHub's published Pages addresses. Optional AAAA records for IPv6, if Bluehost offers them: 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153.)

**www**: edit (or add) the `www` record so it is a CNAME:

| Type | Host / Name | Points to | TTL |
| --- | --- | --- | --- |
| CNAME | www | fornhamcc.github.io | 1 hour |

If `www` is currently an A record, delete it and add the CNAME.

### D4. Connect the domain to the main site

1. Back in GitHub, click **Verify** on the organization's Pages settings (D2) if you have not yet.
2. Open the **FornhamCC.github.io** repository → **Settings** → **Pages**.
3. Under **Custom domain**, it should already show **fornhamcomputerclub.com** (from the CNAME file). If not, type it and click **Save**.
4. Wait for the DNS check to show a green tick. This can take from a few minutes to a few hours while the change spreads.
5. When it becomes available, tick **Enforce HTTPS**. GitHub gets the security certificate for you, free; this step can take up to an hour after the tick appears.

The board is now at **https://fornhamcomputerclub.com/planner/**, and the old address redirects there automatically. Your access key keeps working: it belongs to the repository, not the address. Devices that were unlocked at the old address need the key pasting in once more, because browsers keep saved data separately for each address.

---

## Part E — Final checks

1. Open the board on a phone or a device that has never been unlocked. It shows the plan, "View only" in the header, and no Edit switch.
2. On your iPad: unlock, turn on Edit, open the Club AGM tile, change the briefing, save. On your PC, press the refresh button in the header (or wait a minute): the change appears.
3. Open **/planner/tests/** and confirm all tests pass.

## When the key needs renewing

GitHub emails you about a week before the key expires, and the board's **Settings** page shows the expiry date and a **Renew key on GitHub** button. (A reminder on the board a month ahead arrives in Stage 3.) On GitHub, open the key and click **Regenerate token**, choose the new date, copy the new key, then on each device use **Settings** → **Paste new key**. If a key does run out, the board shows a "Paste new key" box rather than an error, and any change not yet saved is kept until the new key is in.

## If something goes wrong

| What you see | What to do |
| --- | --- |
| "This key cannot see the FornhamCC/planner repository" | The key was made with your personal account as the Resource owner. Make a new key with **FornhamCC** as the owner (step C1.5). |
| "This key is not allowed to save…" | The key lacks **Contents: Read and write**. Edit the key on GitHub and set it. |
| Unlock fails with an approval message | Fine-grained keys need allowing in the organization settings (Part A2). |
| The board loads but shows an older plan | Readers' copies catch up within a few minutes of a save. Press the refresh button. |
| fornhamcomputerclub.com does not open, or GitHub cannot verify it | Name server and DNS changes spread slowly. Wait a few hours; check Bluehost shows its own name servers (not SiteGround's) and the A records above. |
| "Domain does not resolve to the GitHub Pages server" | One of the A records is wrong or an old Bluehost A record is still present. |
| Opening index.html from your PC shows a message instead of the plan | Expected: browsers block a page opened as a file from reading the plan. Use the web address. |
