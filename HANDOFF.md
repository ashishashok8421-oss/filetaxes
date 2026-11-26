# Design handoff: Tax Prototype concept

A clickable design prototype of a free tax return service filed by a software tax agent. Concept only, with sample data. Not an available service. Nothing entered is saved or sent.

## Run it
- Open this folder in Visual Studio Code (File, Open Folder).
- Install the recommended "Live Server" extension when prompted, then right-click `index.html` and choose "Open with Live Server".
- No build step and no packages. Plain HTML, CSS and a little JavaScript.

## Pages, in journey order
| File | Step | What it is |
|---|---|---|
| `index.html` | Landing | Marketing page. "Start my return" leads to `start.html`. |
| `start.html` | 1 | Welcome. Says the tax agent is software, not a person. Clears saved answers. |
| `income.html` | 1 | Four income options. Summary chips update as options are ticked. Ticking self-employment routes to `self-employed.html`. |
| `self-employed.html` | 1 | Follow-up, shown only if self-employment was ticked. |
| `more.html` | 1 | Three checks: pension, Child Benefit, unpaid or late tax. |
| `connect.html` | 2 | Connect HMRC and three sample accounts (Example Bank, Example Invest, Example Pension). |
| `authorise.html` | 2 | Authorise Tax Prototype as the customer's tax agent with HMRC, with a clearly labelled mock HMRC sign-in. |
| `dashboard.html` | 3 | Your return: the tax figure recalculated as sections fill in, sections with sources, two questions, and a chat with the tax agent. |
| `approve.html` | 4 | Check the figures, see how the result is worked out, and approve. |
| `filed.html` | 5 | Filed, with receipt, messages with the tax agent, next year and payments on account. |

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
| Tax agent mark | Rounded square in the accent colour with a spark (`.ag`) |

## How the code is organised
- Each page is self-contained: its styles are in a `<style>` block in the head, its behaviour in one `<script>` at the end.
- The script holds small shared helpers (`STORE` for saved answers, `wire` for `[button text, destination]` rules, `toast`).
- Links with no screen behind them show "Not part of this prototype."
- The dark bar fixed to the bottom (`.pt-bar`) is the concept notice plus Back, Next and Home links. Keep the notice if the site is public.
- Flow pages are designed at a fixed 1280px width (desktop only). The landing page is fluid.
- `dashboard.html` works the estimate out from 2025 to 2026 rates for the sample customer (`calc()`), so it changes with what is connected.

## Known gaps, in priority order
1. Styles and helpers are repeated in every flow page. First refactor: move shared rules into one `styles.css` and one script.
2. Connections and the return always show the sample customer (employment plus savings, investments and a pension), whatever is ticked on `income.html`.
3. No mobile layout for the flow pages.
4. Company directors are not covered; `income.html` says so.
5. The tax agent's replies are canned, chosen by keyword.
6. The landing page reviews are samples and say so.

## Sample data used throughout
Customer Maya. Salary £68,000, tax already paid £14,632, interest £1,550, dividends £820, investment profit £5,400, pension £7,500 (paid £6,000 plus £1,500 basic relief). Income Tax due £13,660, Capital Gains Tax £576, total £14,236, so HMRC owes £396. Authorised with HMRC 17 November 2026, filed 24 November 2026, receipt SAMPLE-0000-0000, deadline 31 January 2027.

## Hosting
See `README.md` for Render steps. `render.yaml` describes a static site published from the folder root.
