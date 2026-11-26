# Design handoff: Tax Prototype concept

A clickable design prototype of a tax return service. Concept only, with sample data. Not an available service. Nothing entered is saved or sent.

## Run it
- Open this folder in Visual Studio Code (File, Open Folder).
- Install the recommended "Live Server" extension when prompted, then right-click `index.html` and choose "Open with Live Server".
- No build step and no packages. Plain HTML, CSS and a little JavaScript.

## Pages, in journey order
| File | Step | What it is |
|---|---|---|
| `index.html` | Landing | Marketing page with pricing, sample reviews and FAQ. "Start my return" leads to `start.html`. |
| `start.html` | 1 | Welcome. |
| `income.html` | 1 | Part 1 of 2: four income options. The summary chips update as options are ticked. Ticking self-employment routes to `self-employed.html`. |
| `self-employed.html` | 1 | Shown only if self-employment was ticked. Continue is disabled until one option is picked. |
| `more.html` | 1 | Part 2 of 2: pension, Child Benefit, unpaid or late tax. Each has Yes, No and Not sure. |
| `accountant.html` | 2 | The matched accountant. |
| `plan.html` | 3 | Three plans: Check £99, Done for you £149, Year-round £199 (one-off, inc. VAT). |
| `dashboard.html` | 4 | After payment: what we need from you, talk to the accountant, call credits, what happens next. |
| `authorise.html` | 4 | Opened from the dashboard. Tax details, a mock HMRC sign-in panel, then the confirmation. |
| `approve.html` | 5 | The figures, how the result is reached, and the approval. |
| `filed.html` | 6 | Filed, with the message thread. |

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
- All flow pages share the same base styles, header, "Where your return is" bar and helper script (`STORE`, `wire`, `toast`), repeated in each file.
- `wire([[button text, destination]])` connects buttons to the next page. A link with `href="#"` or a button with `data-dead` shows "Not part of this prototype."
- Answers are kept in `sessionStorage` under `taxproto:` keys: `income`, `work`, `more`, `plan`, `auth`, `r5`, `r6`, `call`, `msg`.
- The dashboard derives every count, the progress bar and the highlighted row from that state in one `render()` function.
- The dark bar fixed to the bottom (`.pt-bar`) is the concept notice plus Back, Next and Home links. Keep the notice while the site is public.
- Flow pages are designed at a fixed 1280px width (desktop only). The landing page is fluid.

## Wording to keep consistent
- "Money-back guarantee" for the service promise. "Refund" is only used for money HMRC pays the customer.
- "Priya Shah, ACCA qualified accountant".
- "Connected accounts" for the sample savings, investment and pension accounts (Example Bank, Example Invest, Example Pension).

## Known gaps, in priority order
1. Styles and helper script are repeated in every flow page. First refactor: move them into one `styles.css` and one `app.js`.
2. Accountant, plan, dashboard and approve pages always show the sample customer (employment plus savings and investments), whatever is ticked on `income.html`.
3. No mobile layout for the flow pages.
4. Company directors are not covered; `income.html` and the landing page say so.
5. No payment screen: "Pay" on `plan.html` goes straight to the dashboard.
6. Landing page reviews are samples and are labelled as such.

## Sample data used throughout
Customer Maya. Accountant Priya Shah, ACCA qualified, 8 years. Two 15-minute calls included, extra calls £25 per 15 minutes.
Salary £68,000, interest £1,550, dividends £820, investment profit £5,400, pension £7,500 gross (£6,000 paid plus £1,500 basic relief).
Tax already paid £14,632. Income Tax due £13,660. Capital Gains Tax £576. Total due £14,236. HMRC owes £396.
Authorised 17 November 2026. Filed 24 November 2026, receipt SAMPLE-0000-0000. Tax year 6 April 2025 to 5 April 2026, deadline 31 January 2027.

## Hosting
See `README.md` for Render steps. `render.yaml` describes a static site published from the folder root.
