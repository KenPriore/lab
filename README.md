# kenpriore.ai — The Lab

Static site. No build step, no dependencies beyond the Archivo webfont.
Source of truth for design decisions: `Monito/signal-v2-design-language/DESIGN-SYSTEM.md`.
Project status and open decisions: `Monito/site-home-kenpriore-ai/STATUS.md`.

## Deploy

GitHub Pages, served from the default branch root.

⛔ **CNAME is intentionally absent.** `kenpriore.github.io` still holds a stale
`CNAME` claiming `kenpriore.ai`, and a custom domain can only be claimed by one
repo at a time. Clear that claim BEFORE adding a `CNAME` file here.

⚠ The apex `kenpriore.ai` currently resolves to an Express app on Google, not to
GitHub Pages. Moving it is a DNS change, not a repo change. Recommended order:
map `lab.kenpriore.ai` to the existing Google service and confirm it answers,
then repoint the apex here. That way the front door is never dark.

⚠ Pages builds fail transiently roughly half the time. Recovery is `POST` to
`/repos/:owner/:repo/pages/builds` followed by an empty commit. Never `gh run rerun`.

## ⛔ login.html is not authentication

The gate on that page is a review scaffold: the script opens the signed-in view
on any input. It exists so the layout can be reviewed. Before this site serves a
real domain, either wire a server-side hashed check (static hosting cannot do
this) or replace the page with a link to the real gated app.
