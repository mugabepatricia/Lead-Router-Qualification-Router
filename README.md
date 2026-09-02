# Lead Intake & Qualification Router (Make.com Automation)

A simulated business-ops automation that captures inbound leads, routes them by budget tier, and creates the right follow-up task automatically — built as a hands-on demonstration of workflow automation and process design.

## The Problem It Solves

Manually triaging inbound leads (checking a form, guessing priority, messaging the right person, remembering to follow up) doesn't scale and is easy to get wrong under a busy week. This automation removes the manual triage step entirely.

## How It Works

**Trigger → Router → Filtered Branches → Task Creation**

1. **Trigger:** A new submission on a Google Form (name, email, company, budget/interest level, message) lands in a connected Google Sheet.
2. **Watch:** Make watches the sheet for new rows in real time.
3. **Router:** The lead is split into one of two paths based on stated budget/interest level.
4. **Path A — High-Value Lead** (`Over $5,000` or `$1,000–$5,000`): creates a high-priority ClickUp task in a dedicated list, due same-day.
5. **Path B — Standard Lead** (`Under $1,000`): creates a task in a separate nurture list, due 3 days out.

The two filter conditions are mutually exclusive and together cover every possible submission — no lead falls through a gap, and no lead gets duplicate action.

## Tools Used

- **Make.com** — trigger, router, and conditional filter logic
- **Google Forms + Sheets** — lead capture and lightweight data store
- **ClickUp** — task management / follow-up destination

## Design Notes

- Originally planned to route high-value leads to an email alert. Hit a hard platform limitation: Make's Gmail module requires Google Workspace (business) accounts for restricted-scope OAuth — personal @gmail.com accounts are blocked from that connection type. Rather than burn time on a workaround unrelated to the core skill being demonstrated, I redesigned Path A to use a second ClickUp list instead. Same branching logic, same urgency differentiation, no platform dependency issue.
- Filters use OR logic to group two budget tiers into one "high-value" path, showing conditional logic beyond a simple if/else.

## Screenshots

- <a href="https://github.com/mugabepatricia/Lead-Router-Qualification-Router/commit/e99585a03dd30cba170b67934fde3b7bf5e42835">Project screenshot</a>

## What I'd Build Next

- Add a dashboard (Google Sheets or Looker Studio) summarizing lead volume by tier
- Swap the hardcoded due-date with a dynamic formula once on a plan/setup that supports it cleanly
- Add a Slack notification as a third parallel action for the high-value path
