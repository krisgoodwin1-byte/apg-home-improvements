# APG Home Improvements — preview publish status

**Repo:** https://github.com/krisgoodwin1-byte/apg-home-improvements  
**Intended Pages URL:** https://krisgoodwin1-byte.github.io/apg-home-improvements/

## Done
- All HTML pages, `css/styles.css`, `js/main.js` at repo root
- `README.md` preview note
- `.nojekyll`
- `.github/workflows/pages.yml` (official Pages deploy)
- `.github/workflows/decode-images.yml` (reassembles `_image_b64/*` → commits real `images/*`)

## Blocked / incomplete: binary images
GitHub MCP `create_or_update_file` UTF-8-encodes strings before base64, so `latin-1` binary upload **corrupts** JPEG/PNG (magic bytes wrong).

Fallback: ASCII base64 chunks under `_image_b64/` + Actions decode. Chunk upload is in progress but **not complete**; `images/logo.png` and `images/hero.jpg` are not yet on `main` as real binaries.

**Fastest manual fix for the client preview:**
1. Open the repo on github.com → Add file → Upload files
2. Upload the local `images/` folder (logo.png, hero.jpg, bath1–8.jpg, kitchen1.jpg) to path `images/`
3. Settings → Pages → Source: **GitHub Actions** (or Deploy from branch `main` / `/`)
4. Wait for the Pages workflow; open the Pages URL

## Verify after images exist
- `https://krisgoodwin1-byte.github.io/apg-home-improvements/` → 200
- raw `images/logo.png` → PNG magic `89 50 4E 47`, size 24558
- raw `images/hero.jpg` → JPEG magic `FF D8 FF`, size 160482
