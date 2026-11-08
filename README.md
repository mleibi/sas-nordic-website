# SAS Nordic Team — Website Code

Source files for the SAS Nordic Team website, served in production via [jsDelivr](https://www.jsdelivr.com/) directly from this GitHub repo.

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
