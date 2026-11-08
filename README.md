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
- `pages/nordic-team/en.html`, `fr.html`, `de.html` — custom HTML block for each language version of the Nordic Team page. Hivebrite hosts a separate page per language; paste the matching file's contents into that page's custom HTML block.
