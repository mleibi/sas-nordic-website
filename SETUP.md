# SAS Nordic Team Page - Setup & Status

## ✅ What's Working

- **Local preview** (`preview.html`) displays correctly with all text labels
- All images load (hero, disciplines, athletes)
- All i18n labels populate correctly
- Page content structure is complete

## ❌ What's Not Working

- **Hivebrite integration**: The skeleton HTML pasted into Hivebrite's page editor is not executing
- `<script>` tags appear to be stripped or not executed by Hivebrite
- This prevents dynamic content loading from jsDelivr

## 📋 Files

- `skeleton.html` - The minimal HTML to paste into Hivebrite (should load page-content.html via fetch)
- `page-content.html` - All actual content, logic, and i18n labels
- `labels/en.json`, `labels/fr.json`, `labels/de.json` - Language-specific text
- `athlete-info.json` - Extra athlete information for flip cards

## 🔗 How It Should Work (in Hivebrite)

1. Paste `skeleton.html` content into Hivebrite's HTML block
2. Skeleton fetches `page-content.html` from jsDelivr CDN
3. `page-content.html` auto-loads labels and populates all text

## ⚠️ Current Workaround for Hivebrite

Since Hivebrite doesn't execute `<script>` tags in custom HTML blocks, you need to either:

1. **Ask Hivebrite support** how to inject custom JavaScript (may require API or different field type)
2. **Use an embed/iframe approach** if Hivebrite allows it
3. **Paste the full page-content.html directly** into Hivebrite (not ideal, but works)
   - Then update it whenever you make changes
   - Changes won't auto-deploy from git

## 📝 To Deploy Changes

Once Hivebrite setup is resolved:
- Push changes to GitHub
- jsDelivr automatically picks up the latest main branch
- Hivebrite page refreshes and shows new content
