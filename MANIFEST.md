# MANIFEST — File inventory + checksums

Snapshot taken: **2026-09-14**
Total size: **24 MB** (52 files tracked in git)

## Root files

| File | Purpose |
|---|---|
| `00_WAKE_UP.md` | First-read overview |
| `REVIVAL.md` | Rebuild instructions + pinned versions |
| `VAULT.md` | Credentials (gitignored, local only) |
| `MANIFEST.md` | This file |
| `MEMORY.md` | Chronological build log (~285 lines) |
| `README.md` | Minimal GitHub landing |
| `netlify.toml` | Netlify hosting config (publish = ".") |
| `.gitignore` | Excludes `.claude/`, `.vscode/`, `VAULT.md`, OS junk |
| `index.html` | Homepage |
| `about.html` | Founder, mission, accreditations, timeline |
| `courses.html` | 13 filterable course cards |
| `placements.html` | Success stories, KPIs, sector partners, world map, process infographic |
| `contact.html` | Form, 6 campus cards, Google Maps embed |

## Folder counts

| Folder | Count | Contents |
|---|---|---|
| `css/` | 1 | `style.css` — ~2600 lines mobile-first stylesheet |
| `js/` | 1 | `main.js` — vanilla, 10 numbered sections (nav, filter, cursor, click-spark, etc.) |
| `images/` | 17 | Founder photo, 14 category photos, 2 Panache brand SVGs |
| `logos/` | 23 | 20 partner logos (Emirates, Qatar, Taj, etc.) + 3 social icons (Facebook/Instagram/LinkedIn) |
| `video/` | 1 | `Hero_Banner.mp4` — 9 MB looping homepage hero |

## Checksums — irreplaceable files

These files cannot be trivially regenerated. If corruption is suspected, verify against these SHA-256 hashes.

```
f37a800b5c91a30bab37d8cc25193bb75c98f5d8015337e8c86d3bcf118b5b65  video/Hero_Banner.mp4
89736403cbcb1aafd44ddd1716dbbeeb9c138389f3b732b37b797842a846497a  images/panache-logo-01.svg
406d898fc8c6e3469b8fe30d8571f31b5af952d09f14e5169542d0f4650da4a6  images/panache-logo-02.svg
988bd8febf0ccff6aa6f399425065594922650361f62c7bd224d436b073e2c1b  images/khushnum-avari.jpg
```

To verify:
```powershell
cd "D:\03_Clients\01_Panache_Academy"
sha256sum video/Hero_Banner.mp4 images/panache-logo-01.svg images/panache-logo-02.svg images/khushnum-avari.jpg
```

If any hash differs, restore the file from git history:
```powershell
git log --all --oneline -- video/Hero_Banner.mp4
git checkout <commit-hash> -- video/Hero_Banner.mp4
```

## Recoverable files (if lost, can be re-fetched)

| File pattern | Original source |
|---|---|
| `images/khushnum-avari.jpg` | Was fetched from `panacheacademy.com/wp-content/uploads/2022/03/panache-Khushnum-Avari.jpg`. Live site may still serve it. |
| `images/course-*.jpg`, `images/hero-aviation.jpg` | Unsplash. Original URLs are recorded in `MEMORY.md` under "Image inventory" entries. |
| `logos/*.svg`, `logos/*.png` | Partner brand sites (Emirates, Qatar Airways, etc.). Each partner's official press-kit page has the current logo. |
| `logos/instagram.svg`, `logos/facebook.svg`, `logos/linkedin.svg` | User-provided, but simple brand marks — easy to redownload from the platforms' brand pages. |

## Truly irreplaceable

- **`video/Hero_Banner.mp4`** — user-generated with a specific AI video tool at a specific time. Cannot be recreated identically. Back up separately.
- **`images/panache-logo-01.svg` + `-02.svg`** — the academy's actual branded logos, provided by the user from Google Drive (`G:\My Drive\Work\Panache\`). If lost, the source is on the user's Google Drive.
- **`MEMORY.md`** — the whole build story. Cannot be recreated without redoing the entire project. Git history preserves it too.

## Where to find external copies

- **Google Drive backup:** `G:\My Drive\Work\Panache\Panache_Logo-01.svg`, `Panache_Logo-02.svg` (same files as `images/panache-logo-01.svg`, `-02.svg`)
- **GitHub mirror:** `https://github.com/kmrabhay1996/panache-academy` — everything except `VAULT.md`
- **Live deploy #1:** `https://kmrabhay1996.github.io/panache-academy/`
- **Live deploy #2 (Netlify):** URL depends on the Netlify site name chosen at setup (see `VAULT.md`)
