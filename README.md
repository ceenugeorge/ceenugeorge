# Ceenu George – personal website

A plain HTML site hosted for free on GitHub Pages. Every Monday GitHub checks your ORCID and adds new papers automatically.

## Files

| File | What it is | Do you edit it? |
|---|---|---|
| `index.html` | The page: research, about, career, contact | Occasionally |
| `publications.js` | Papers not on ORCID, plus videos, awards and "Selected" marks | **Yes, this is your main file** |
| `publications-orcid.js` | Papers fetched from ORCID | No, it's rewritten automatically |
| `orcid-config.json` | Your ORCID iD and ORCID entries to hide | Rarely |
| `images/ceenu.jpg` | Your portrait | – |
| `media/` | Videos and GIFs for papers | You add files here |
| `scripts/`, `.github/` | The automation | No |

---

## Set up the site (once, about 15 minutes)

### 1. Create the repository
1. Sign in at github.com. Your site address will be `username.github.io`.
2. Click **+ → New repository**.
3. Name it exactly `username.github.io` (your own username), choose **Public**, and click **Create repository**.

### 2. Upload the files
The automation lives in a folder called `.github`. macOS hides folders whose names start with a dot, so make them visible first.

1. Unzip `ceenu-george-website.zip` and open the `site` folder.
2. **Mac:** press **Cmd + Shift + .** (full stop) in Finder. The `.github` folder appears.
   **Windows:** in File Explorer, choose **View → Show → Hidden items**.
3. On the empty repository page, click **uploading an existing file**.
4. Select **everything inside** the `site` folder, including `.github`, and drag it into the browser.
5. Check the file list: `index.html` must be at the top level (not inside `site/`), and you should see `.github/workflows/update-site.yml`.
6. Click **Commit changes**.

If `.github` didn't upload, see "Adding the workflow by hand" at the end.

### 3. Switch on publishing
1. In the repository, open **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **GitHub Actions**. (Not "Deploy from a branch".)

### 4. Run it for the first time
1. Open the **Actions** tab. If GitHub asks, click **I understand my workflows, go ahead and enable them**.
2. Click **Update publications and publish site** on the left, then **Run workflow → Run workflow**.
3. After about a minute it shows a green tick. Your site is live at `https://username.github.io`.

From now on, GitHub updates the site on its own:
- **Every Monday**, it checks ORCID and adds any new papers.
- **Whenever you change a file** on GitHub, it republishes the site within a minute or two.

---

## Everyday tasks

### A new paper came out
Do nothing. Once it's on your ORCID, it appears on the site the following Monday. To get it sooner, go to **Actions → Update publications and publish site → Run workflow**.

Tip: in ORCID, use **Works → Add → Search & link → Crossref Metadata Search** and allow automatic updates. New papers with a DOI will then reach ORCID without you adding them.

### Add a video or GIF to a paper
1. Make a short silent loop: 5–10 seconds, about 640 px wide, under 2 MB. MP4 is much smaller than GIF.
   With ffmpeg: `ffmpeg -i input.mov -t 8 -vf "scale=640:-2" -an -crf 28 output.mp4`
2. On GitHub, open the `media` folder → **Add file → Upload files** and upload it.
3. Open `publications.js` → pencil icon (**Edit**) and add a short entry with the paper's DOI:
   ```js
   { doi: "10.1145/3772318.3791241", video: "media/avatars.mp4" },
   ```
   If the paper has no DOI, use its title instead: `{ title: "Exact paper title", video: "media/x.mp4" },`
4. Click **Commit changes**.

The same short form works for `award: "Best Paper"` or `selected: true`.

### Fix how an ORCID paper is shown
Add an entry for it to `publications.js` with the same DOI or title, plus the corrected fields. Your version always wins.

### Hide an ORCID entry
Open `orcid-config.json`, add part of its title to the `ignore` list, and commit.

### Add a paper that isn't on ORCID
Copy the template at the top of `publications.js`, paste it into the list, and fill it in.

---

## If something goes wrong

- **Red cross on the Actions tab:** click the failed run to see which step failed. If ORCID was only briefly unreachable, the site keeps the last good list and the next run fixes itself.
- **"This scheduled workflow is disabled because there hasn't been activity…":** GitHub pauses weekly jobs in repositories with no changes for 60 days. It emails you first; click **Enable workflow** on the Actions tab to restart it.
- **The site shows an old version:** wait two minutes, then reload with Cmd + Shift + R (Ctrl + Shift + R on Windows).

## Adding the workflow by hand

If the `.github` folder didn't upload:
1. In the repository, click **Add file → Create new file**.
2. In the name field, type `.github/workflows/update-site.yml`. The slashes create the folders.
3. Open `update-site.yml` from the zip in a text editor (TextEdit or Notepad), copy everything, and paste it in.
4. Click **Commit changes**, then continue with step 3 above.

## Use your own domain (optional)

Buy a domain (for example `ceenugeorge.com`) from Cloudflare, Porkbun or Namecheap. In **Settings → Pages → Custom domain**, enter it and follow GitHub's instructions for the DNS records.
