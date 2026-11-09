# 🚀 Setup Nordic Team Page on Hivebrite

## Quick Start

1. **Copy the skeleton:** paste the full content of [`pages/nordic-team/skeleton.html`](pages/nordic-team/skeleton.html).

2. **In Hivebrite:**
   - Edit the Nordic Team page
   - Find the HTML editor block where you want the content
   - Paste the skeleton above
   - Save & Publish
   - Hard refresh browser (Cmd+Shift+R or Ctrl+Shift+Delete + refresh)

3. **For German (DE) page:** Change `window.LANG = "en"` to `window.LANG = "de"`

4. **For French (FR) page:** Change `window.LANG = "en"` to `window.LANG = "fr"`

5. **Add the sponsor footer:** add a second HTML block at the bottom of the page. Paste the full content of [`footer/sponsors.html`](footer/sponsors.html). Unlike the main content, the footer does **not** update from GitHub: after changing the file, paste it again.

## How It Works

- The skeleton sets `window.LANG` and `window.BASE`, fetches `page-content.html` from GitHub via jsDelivr, injects it, and re-creates the `<script>` tags so they run.
- Do **not** load `page-content.html` with `<script src>`: jsDelivr serves `.html` as `text/plain` with `nosniff`, so the browser refuses to run it.
- Hivebrite removes all line breaks when saving. Never use `//` comments in pasted scripts (they comment out everything after them); use `/* */`.
- Do **not** embed the HTML in a JS string: the first inner `</script>` ends the outer script.
- This works because Hivebrite's CSP is in report-only mode (same as the old page with `sas_users-with-css.js`). If Hivebrite ever enforces it, ask them to whitelist `cdn.jsdelivr.net` in `script-src` and `connect-src`.
- All text comes from language-specific JSON files (labels)
- Images are hosted on Hivebrite (not in this repo)
- Athletes load dynamically from `athlete-info.json`

## To Update Content

Just push changes to GitHub - **no need to re-paste the skeleton**. (Exception: the sponsor footer must be re-pasted after changes.)

```bash
# Edit text/labels
$ vim pages/nordic-team/labels/en.json

# Push to GitHub
$ git add pages/nordic-team/labels/en.json
$ git commit -m "Update welcome text"
$ git push origin main

# Refresh the Hivebrite page in your browser - new text appears automatically
```

## Troubleshooting

**No text appears?**
- Open browser console (F12)
- Look for errors or fetch failures
- Try a hard refresh (Cmd+Shift+R)

**jsDelivr cache is stale?**
- jsDelivr caches `@main` for up to ~12 hours.
- Purge each changed file by opening its purge URL, e.g. https://purge.jsdelivr.net/gh/mleibi/sas-nordic-website@main/pages/nordic-team/page-content.html

**Images not loading?**
- Images are hosted on `sas-ski.ch/storage/...` URLs
- Make sure Hivebrite can access these URLs

## Files

- `skeleton.html` - Paste this into Hivebrite
- `page-content.html` - All content, structure, styling (auto-loaded)
- `labels/en.json`, `labels/fr.json`, `labels/de.json` - Text translations
- `athlete-info.json` - Athlete extra info for flip cards
- `footer/sponsors.html` - Sponsor footer (blue band with white logos). Paste into its own HTML block at the bottom of the page

