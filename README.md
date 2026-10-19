# Ceenu George – personal website

A plain HTML site with no build step, hosted for free on GitHub Pages.

## Files

| File | What it is |
|---|---|
| `index.html` | The page: research, about, career, contact |
| `publications.js` | Your publication list. **This is the file you'll edit most.** |
| `images/ceenu.jpg` | Your portrait |
| `media/` | Videos and GIFs for publication previews |

## Put it online (one time, ~15 minutes)

1. Create a free account at github.com. The username decides your address: `username.github.io`.
2. Click **+ → New repository**. Name it exactly `username.github.io` (with your username), set it to **Public**, and click **Create repository**.
3. On the new repository page, click **uploading an existing file**. Drag in everything from this folder, including the `images` and `media` folders, then click **Commit changes**.
4. Go to **Settings → Pages**. Under "Build and deployment", choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
5. After a minute or two, your site is live at `https://username.github.io`.

## Add a new paper

1. On GitHub, open `publications.js` and click the pencil icon (**Edit**).
2. Copy the template from the top of the file, paste it as the first entry in the list, and fill it in.
3. Click **Commit changes**. The site updates within a minute.

## Add a video or GIF to a paper

1. Make a short silent loop, 5–10 seconds, about 640 px wide and under 2 MB. MP4 is far smaller than GIF for the same clip.
   - Free tools: HandBrake, or `ffmpeg -i input.mov -t 8 -vf "scale=640:-2" -an -crf 28 output.mp4`.
2. On GitHub, open the `media` folder → **Add file → Upload files**, and upload it (for example `invisible-boundaries.mp4`).
3. In `publications.js`, add a line to that paper: `video: "media/invisible-boundaries.mp4",` (or `gif: "media/....gif",`).

Videos play silently while they're on screen, and they pause when the visitor has reduced motion turned on. Papers with media get a small orange dot, and visitors can filter for them with **With video**.

## Use your own domain (optional)

Buy a domain (for example `ceenugeorge.com`) from a registrar such as Cloudflare, Porkbun or Namecheap. In **Settings → Pages → Custom domain**, enter it, then follow GitHub's instructions to add the DNS records at your registrar.
