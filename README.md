# Portfolio News Monitor

An automated M&A signal monitoring system for tracking a company watchlist, built on [Claude Cowork](https://claude.ai). Delivers a **daily alert** (weekday mornings) and a **weekly digest** (Monday) via email.

Designed for Corp Dev / M&A professionals who need a fast, structured signal feed — not a news aggregator.

---

## What it does

- **Daily Alert** — scans the last 24h for HIGH and MEDIUM M&A signals across all tracked companies. Skips noise. In your inbox by 8am.
- **Weekly Digest** — every Monday at 7:30am, a full 7-day sweep with ranked signals, per-company breakdown, executive activity, sector macro themes, and a "Watch List for Next Week."

Each item includes a **"Why It Matters"** section framed specifically for corp dev: valuation signals, deal probability shifts, competitive positioning, acquisition window timing.

---

## Signal types monitored

Press releases · Product launches · Funding rounds · M&A activity · Security incidents · Leadership changes · Executive speeches / podcasts / interviews · SEC / regulatory filings · Strategic partnerships · Earnings surprises

---

## Files

| File | Purpose |
|---|---|
| `portfolio_config.json` | Master watchlist — companies, aliases, sector, AI angle, key people |
| `tasks/daily_alert_prompt.md` | Prompt template for the daily alert scheduled task |
| `tasks/weekly_digest_prompt.md` | Prompt template for the weekly digest scheduled task |

---

## Setup

### 1. Configure your watchlist

Edit `portfolio_config.json`:
- Add your portfolio companies under `portfolio_companies`
- Add competitors under `competitor_watchlist`
- Add key executives under `key_people`
- Set `owner_email` to your email address

### 2. Create the scheduled tasks in Claude Cowork

Open Claude Cowork and paste this prompt:

```
Set up two scheduled tasks for my Portfolio News Monitor:

1. Daily alert — runs weekdays at 8am, uses the prompt in tasks/daily_alert_prompt.md
2. Weekly digest — runs Mondays at 7:30am, uses the prompt in tasks/weekly_digest_prompt.md

My email is [YOUR EMAIL]. My company watch list is in portfolio_config.json.
```

Or create them manually in the Claude Cowork "Scheduled" sidebar using the prompts in the `tasks/` folder.

### 3. Run once to approve tool permissions

Click "Run now" on each task to pre-approve web search and browser (Outlook) permissions — this prevents future runs from pausing for approval.

---

## Customization

**Change the companies:** Edit `portfolio_config.json` and update the task prompts accordingly.

**Change delivery:** Swap the Outlook send step for Slack (`slack_send_message` tool) or a file save.

**Change frequency:** Edit the cron expression in the task settings. `0 8 * * 1-5` = weekdays at 8am.

**Add sources:** The prompts include site-specific search queries. Add `site:yoursite.com` to any search step.

---

## Example watch list (data center supply chain / AI infrastructure)

| Company | Ticker | Segment | Why Watch |
|---|---|---|---|
| Vertiv Holdings | VRT | Power & Thermal | Most AI-direct hardware play; NVIDIA co-dev partner |
| Equinix | EQIX | Colocation | 250+ DCs; AI interconnection platform |
| Eaton Corporation | ETN | Power Management | Acquired Boyd Thermal $9.5B; liquid cooling bet |
| nVent Electric | NVT | Enclosures & Cooling | NVIDIA partner; orders +65% YoY |
| Celestica | CLS | Contract Manufacturing | Google TPU partner; $16B 2026 guidance |
| Arista Networks | ANET | DC Networking | AI cluster ethernet backbone |
| Modine Manufacturing | MOD | Thermal Management | Small cap; potential acquisition target |
| Digital Realty | DLR | Data Center REIT | Hyperscale pre-leasing signal |
| Accelsius | — | Liquid Cooling (Private) | Two-phase direct-to-chip; Series B; JCI-backed |
| Zayo Group | — | Fiber Infrastructure (Private) | PE-owned; watch for exit signal |

---

## License

MIT
