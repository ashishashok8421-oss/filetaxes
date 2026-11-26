# Tax Prototype: concept prototype

A clickable design prototype of a tax return service. Concept only, with sample data: names, reviews and figures are made up.
Tax Prototype is not an available service. Nothing entered is saved or sent.

## Run locally
Open the folder in VS Code, install the recommended Live Server extension, then right-click
`index.html` and choose "Open with Live Server". Or run `npx serve .` from this folder.

## Pages
`index.html` (landing) → `start.html` → `income.html` → `self-employed.html` (only if self-employment is ticked)
→ `more.html` → `accountant.html` → `plan.html` → `dashboard.html` (its "Authorise Priya" button opens `authorise.html`)
→ `approve.html` → `filed.html`.

Answers are kept in `sessionStorage` for the tab, so the summary chips, the plan choice, the dashboard counts and the Back links follow what was picked.
Anything that leads nowhere shows "Not part of this prototype."
See `HANDOFF.md` for design tokens, sample data, wording rules and known gaps.

## Deploy on Render
1. Push this folder to a GitHub repository.
2. In Render: New → Blueprint, pick the repository. `render.yaml` creates a static site called
   `tax-prototype` with no build step, published from the repository root.
3. Every push to `main` redeploys.

The site sends `X-Robots-Tag: noindex` and has a `robots.txt` that blocks crawlers, so the concept stays out of search results.
