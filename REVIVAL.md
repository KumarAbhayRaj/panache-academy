# REVIVAL — Rebuild from nothing

Instructions to bring this project back to life on a fresh machine.

## Pinned versions (what it was built and tested on)

| Component | Version |
|---|---|
| OS | Windows 11 Home Single Language 10.0.26200 |
| Git | 2.53.0.windows.1 |
| Python | 3.11.9 (only needed for the local dev server, nothing else) |
| Browser tested | Chrome / Edge (any Chromium 120+ works) |
| Node.js | Not required |
| npm | Not required |

The website itself has **zero build-time dependencies**. It is plain HTML/CSS/JS.

## Run locally

```powershell
# From the project root
cd "D:\03_Clients\01_Panache_Academy"

# Start a local server on port 5500
python -m http.server 5500

# Open in browser
start http://localhost:5500
```

Any static server works — `npx serve`, `php -S`, VS Code's Live Server extension, etc. Use whatever you have.

## Deploy again from scratch

If both GitHub Pages and Netlify get lost, here is how to rebuild deployment.

### GitHub

1. Create a new empty public repo at github.com/new. Name: `panache-academy` (or anything).
2. From the project root:
   ```powershell
   git remote remove origin
   git remote add origin https://github.com/<username>/panache-academy.git
   git push -u origin main
   ```
3. Repo Settings → Pages → Source: **Deploy from a branch** → Branch: `main` / `(root)` → Save.
4. Wait ~60 seconds. Site is live at `https://<username>.github.io/panache-academy/`.

### Netlify

1. Open `https://app.netlify.com`. Log in (GitHub OAuth is simplest).
2. **Add new site** → **Import an existing project** → **Deploy with GitHub**.
3. Pick the `panache-academy` repo.
4. Build settings: leave everything blank. `netlify.toml` in the repo sets `publish = "."` — that is all Netlify needs.
5. Click **Deploy**. Site is live at `https://<generated-name>.netlify.app` in ~30 seconds.
6. In the site's Settings → Change site name to `panache-academy` (or claim any other free `.netlify.app` name).

### Netlify Drop (fastest fallback, no login)

If GitHub is gone entirely: zip the project folder, drop it on `https://app.netlify.com/drop`. You get a random URL in 20 seconds. Sign in later to claim it.

## Known bugs and quirks (do not think these are your fault)

- **Google Maps iframes cannot be screenshotted** by Chrome DevTools' automated snapshot API. This is a cross-origin frame restriction. The maps render fine for real users — this only affects headless screenshot tools during dev.
- **Windows CRLF warnings** on every git commit. Harmless. Git normalizes on push.
- **Video autoplays silently** on every page load because the `<video>` tag has `muted` — required by all modern browsers to allow autoplay. Do not remove the `muted` attribute or the video will not play on first load.
- **The 2 unidentified logo files** (`Og2.png`, `idUVfgCKoQ_logos.png`) that were originally in `logos/` have been deleted. They were never referenced in any HTML.
- **The Panache Academy owner has NOT approved the pitch yet.** This site is speculative. Do not send it to anyone claiming it is the academy's official site — it is not.

## Adding future changes

```powershell
cd "D:\03_Clients\01_Panache_Academy"
# make edits
git add .
git commit -m "your message"
git push
```

GitHub Pages rebuilds in ~30 seconds. Netlify rebuilds in ~30 seconds. Both auto-triggered by the push.

## If Netlify or GitHub Pages ever silently stops

1. Push a trivial commit (`git commit --allow-empty -m "kick"`).
2. Check the deploy log in the respective dashboard.
3. If the log shows an auth or scope error, the git host access token expired — reconnect the repo in the deploy provider settings.

## Original build history

Every design decision, every color migration, every logo sizing round is logged chronologically in `MEMORY.md`. That file is 285+ lines. If you are wondering "why is X the way it is" — search MEMORY.md first.
