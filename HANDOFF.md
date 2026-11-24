# Design handoff: Tax Prototype concept prototype

A clickable design prototype of a tax return service. Concept only, with sample data. Not an available service. Nothing entered is saved or sent.

## Run it
- Open this folder in Visual Studio Code (File, Open Folder).
- Install the recommended "Live Server" extension when prompted, then right-click `index.html` and choose "Open with Live Server".
- No build step and no packages. Plain HTML, CSS and a little JavaScript.

## Pages, in journey order
| File | Step | What it is |
|---|---|---|
| `index.html` | Landing | Marketing page. "Start my return" leads to `start.html`. |
| `start.html` | 1a | Welcome. |
| `income.html` | 1b | Four income options. Summary panel updates as options are ticked. Ticking self-employment routes to `self-employed.html`. |
| `self-employed.html` | 1c | Follow-up, shown only if self-employment was ticked. |
| `more.html` | 1d | Three yes or no questions: pension, Child Benefit, unpaid or late tax. |
| `accountant.html` | 2 | The matched accountant. |
| `plan.html` | 3 | Three plans compared row by row. Prices are `[PRICE]` on purpose. |
| `dashboard.html` | 4 | After payment: what we need from you, talk to the accountant, call credits. |
| `approve.html` | 5 | Check the figures and approve. |
| `filed.html` | 6 | Filed, with messaging open. |

## Design tokens (theme "Ledger")
| Token | Value |
|---|---|
| Page background | `#F3F5F8` |
| Surface | `#FFFFFF` |
| Text | `#10243A` |
| Muted text | `#4A5B70` |
| Hairline | `#D5DBE3` |
| Accent | `#1B56B0` |
| Accent tint | `#E3ECF9` |
| Dark panel | `#10243A` |
| Success / success tint | `#0E6B4F` / `#DDF2EA` |
| Needs attention / tint | `#8A4B00` / `#FBEBD2` |
| Headings | Newsreader 600 |
| Body | IBM Plex Sans 400 to 700 |
| Radius | 8px buttons, 10 to 14px cards |

## How the code is organised
- Each page is self-contained: its styles are in a `<style>` block in the head, its behaviour in one `<script>` at the end.
- The script near the end of each page holds a short list of rules, `[button text, destination]`, which wires buttons to the next page.
- The dark bar fixed to the bottom (`.pt-bar`) is the concept notice plus Back, Next and Home links. Keep the notice if the site is public.
- Flow pages are designed at a fixed 1280px width (desktop only). The landing page is fluid.

## Known gaps, in priority order
1. Styles are repeated in every page. First refactor: move shared rules into one `styles.css`.
2. `plan.html` and `dashboard.html` use different class names from the other flow pages (they came from a different design pass). The header classes there are prefixed `h5-`.
3. Accountant, plan and dashboard pages always show the sample customer (employment plus savings and investments), whatever is ticked on `income.html`.
4. No mobile layout for the flow pages.
5. Company directors are not covered; `income.html` says so.
6. Landing page: the 4.9 rating is an assumption and the reviews are placeholders.

## Sample data used throughout
Customer Maya. Accountant Priya Shah, ACCA qualified (a UK accounting qualification), 8 years. Two 15-minute calls included, extra calls £25 per 15 minutes. Salary £68,000, interest £1,550, dividends £820, investment profit £5,400, pension £7,500, HMRC owes £396. Filed 24 November 2026, receipt SAMPLE-0000-0000.

## Hosting
See `README.md` for Render steps. `render.yaml` describes a static site published from the folder root.
