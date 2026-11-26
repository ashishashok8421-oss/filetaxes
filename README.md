# Tax Prototype: concept prototype

A clickable design prototype of a free tax return service. A software tax agent fills in a Self Assessment
return from HMRC and connected accounts, the customer approves it, and it is filed. Concept only, with sample data.
Tax Prototype is not an available service. Nothing entered is saved or sent, and nothing contacts HMRC.

## Run locally
Open the folder in VS Code, install the recommended Live Server extension, then right-click
`index.html` and choose "Open with Live Server". Or run `npx serve .` from this folder.

## Pages
`index.html` (landing) → `start.html` → `income.html` → `self-employed.html` (only if self-employment is ticked)
→ `more.html` → `connect.html` (its "Authorise" button opens `authorise.html`) → `dashboard.html` (your return)
→ `approve.html` → `filed.html`.

Answers are kept in `sessionStorage` for the tab, so summaries, connections, the tax estimate and Back links follow
what was picked. The welcome screen clears them, so each run starts fresh.
See `HANDOFF.md` for design tokens, sample data and known gaps.

## Deploy on Render
Create a Static Site from the repository with an empty build command and `.` as the publish directory,
or use New → Blueprint, which reads `render.yaml`. Every push to `main` redeploys.

The site has a `robots.txt` that blocks crawlers, and each page carries a `noindex` tag.
