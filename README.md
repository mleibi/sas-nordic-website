# SAS Nordic Team — Website Code

Source files for the SAS Nordic Team website, served in production via [jsDelivr](https://www.jsdelivr.com/) directly from this GitHub repo.

The website itself is a page on [Hivebrite](https://hivebrite.io/), a hosted community platform (not a standalone static site). Hivebrite controls the page URL and layout; this repo supplies assets (images, CSS, JS) that are referenced from custom HTML/CSS blocks pasted into the Hivebrite page editor.

- Live page: https://sas-ski.ch/page/nordic-team-3

## How it works

- Push changes to the `main` branch on GitHub.
- jsDelivr serves any file in this repo at:
  `https://cdn.jsdelivr.net/gh/<github-user>/<repo-name>@main/<path-to-file>`
  For this repo, that's: `https://cdn.jsdelivr.net/gh/mleibi/sas-nordic-website@main/<path-to-file>`
  e.g. `https://cdn.jsdelivr.net/gh/mleibi/sas-nordic-website@main/pages/nordic-team/labels/en.json`
- jsDelivr caches files for up to 7 days. A GitHub Actions workflow (`.github/workflows/purge-jsdelivr.yml`) automatically purges the cache for every file changed on each push to `main`, so updates normally show up within a minute or two without any manual step.
- If you ever need to purge a file manually (e.g. re-running after a failed workflow), hit:
  `https://purge.jsdelivr.net/gh/<github-user>/<repo-name>@main/<path-to-file>`
- For instant updates without caching delay, reference a specific commit hash in the URL instead of `@main`.

## Folder scope

Only this `Code` folder is a git repository. The rest of the `Nordisch` Google Drive workspace is not version controlled.

## Files

- `website.md` — code snippets for the website.
- `pages/nordic-team/skeleton.html` — the one custom HTML block pasted into all 3 Hivebrite "Nordic Team" pages (EN/FR/DE). Identical everywhere except the `LANG` value in its `<script>`, which picks which JSON file of text to load.
- `pages/nordic-team/labels/en.json`, `fr.json`, `de.json` — the actual page text per language. Edit these to change wording; never edit text directly in `skeleton.html`.
- `pages/nordic-team/icons/` — SVG icons for the Disciplines section, loaded via `<img>` from jsDelivr (not inlined).
- The hero photo carousel above the title uses Hivebrite-hosted images (`https://sas-ski.ch/storage/<id>`), not files in this repo — see "Images" below.
- `footer/sponsors.html` — site-wide sponsors footer markup (`#sponsors` container + styles). Paste into any Hivebrite page's custom HTML block.
- `footer/sponsors-script.html` — companion script that loads the sponsor logos into `#sponsors`. Requires jQuery (already on Hivebrite). Paste alongside `sponsors.html`.

Changing the page structure (adding/removing a section) means editing `skeleton.html` once and adding the matching key to all 3 JSON files. The push to `main` automatically purges the jsDelivr cache for changed files.

## Images

- **Content photos** (team/event photos, hero carousel): upload directly through the Hivebrite page editor's image/media block, not into this repo. Hivebrite then hosts it at a stable `https://sas-ski.ch/storage/<id>/download` URL (no `Expires`/`Signature` params) — use that URL directly in `skeleton.html`. Never use a signed "download" link copied straight from a file browser; those expire after a few hours.
- **Template assets** (the Discipline icons, anything tied to the page's own markup/CSS): keep in this repo under `pages/nordic-team/icons/`, versioned alongside the structural changes that use them.
