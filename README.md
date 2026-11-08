# SAS Nordic Team — Website Code

Source files for the SAS Nordic Team website, served in production via [jsDelivr](https://www.jsdelivr.com/) directly from this GitHub repo.

The website itself is a page on [Hivebrite](https://hivebrite.io/), a hosted community platform (not a standalone static site). Hivebrite controls the page URL and layout; this repo supplies assets (images, CSS, JS) that are referenced from custom HTML/CSS blocks pasted into the Hivebrite page editor.

- Live page: https://sas-ski.ch/page/nordic-team-3

## How it works

- Push changes to the `main` branch on GitHub.
- jsDelivr serves any file in this repo at:
  `https://cdn.jsdelivr.net/gh/<github-user>/<repo-name>@main/<path-to-file>`
- jsDelivr caches files for up to 7 days. To force an immediate update after a push, purge the cache for the changed file(s):
  `https://purge.jsdelivr.net/gh/<github-user>/<repo-name>@main/<path-to-file>`
- For instant updates without caching delay, reference a specific commit hash in the URL instead of `@main`.

## Folder scope

Only this `Code` folder is a git repository. The rest of the `Nordisch` Google Drive workspace is not version controlled.

## Files

- `website.md` — code snippets for the website.
- `pages/nordic-team/skeleton.html` — the one custom HTML block pasted into all 3 Hivebrite "Nordic Team" pages (EN/FR/DE). Identical everywhere except the `LANG` value in its `<script>`, which picks which JSON file of text to load.
- `pages/nordic-team/labels/en.json`, `fr.json`, `de.json` — the actual page text per language. Edit these to change wording; never edit text directly in `skeleton.html`.

Changing the page structure (adding/removing a section) means editing `skeleton.html` once and adding the matching key to all 3 JSON files. Remember to purge the jsDelivr cache for the JSON file(s) you changed (see above) so edits show up without waiting up to 7 days.
