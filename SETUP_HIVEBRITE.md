# 🚀 Setup Nordic Team Page on Hivebrite

## Quick Start

1. **Copy this skeleton HTML:**

```html
<div id="sas-nordic-welcome" style="font-family: inherit; max-width: 800px; margin: 0 auto; line-height: 1.6;"></div>
<script>
(function() {
  var LANG = "en";
  var BASE = "https://cdn.jsdelivr.net/gh/mleibi/sas-nordic-website@main/pages/nordic-team/";
  var ts = Date.now();
  var url = BASE + "page-content.html?t=" + ts;
  fetch(url)
    .then(r => r.text())
    .then(html => {
      document.getElementById("sas-nordic-welcome").innerHTML = html;
      document.querySelectorAll("#sas-nordic-welcome script").forEach(old => {
        var s = document.createElement("script");
        Array.from(old.attributes).forEach(attr => s.setAttribute(attr.name, attr.value));
        s.textContent = old.textContent;
        old.parentNode.replaceChild(s, old);
      });
    })
    .catch(e => console.error("Failed to load Nordic page:", e));
})();
</script>
```

2. **In Hivebrite:**
   - Edit the Nordic Team page
   - Find the HTML editor block where you want the content
   - Paste the skeleton above
   - Save & Publish
   - Hard refresh browser (Cmd+Shift+R or Ctrl+Shift+Delete + refresh)

3. **For German (DE) page:** Change `var LANG = "en"` to `var LANG = "de"`

4. **For French (FR) page:** Change `var LANG = "en"` to `var LANG = "fr"`

## How It Works

- The skeleton fetches the latest content from GitHub via jsDelivr
- All text comes from language-specific JSON files (labels)
- Images are hosted on Hivebrite (not in this repo)
- Athletes load dynamically from `athlete-info.json`

## To Update Content

Just push changes to GitHub - **no need to re-paste the skeleton**:

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
- The skeleton includes `?t=` timestamp parameter to force fresh fetches
- If still stale, ask jsDelivr to purge: https://purge.jsdelivr.net/gh/mleibi/sas-nordic-website/pages/nordic-team/

**Images not loading?**
- Images are hosted on `sas-ski.ch/storage/...` URLs
- Make sure Hivebrite can access these URLs

## Files

- `skeleton-final.html` - Paste this into Hivebrite
- `page-content.html` - All content, structure, styling (auto-loaded)
- `labels/en.json`, `labels/fr.json`, `labels/de.json` - Text translations
- `athlete-info.json` - Athlete extra info for flip cards

