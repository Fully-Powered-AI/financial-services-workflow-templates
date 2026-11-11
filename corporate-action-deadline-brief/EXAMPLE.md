# Corporate action deadline brief: an invented example

*Illustrative example with invented data.* Everything below is made up: the advisory firm (Northgate Example Advisory), the issuer (Issuer A), the custodians (Custodian One and Custodian Two), the accounts, the security identifier and the notice. None of it is a real organization, holding or event.

## What the operations lead supplies

**Brief date:** Monday 9 November 2026. **Firm settings:** internal cut-off is one business day before the custodian deadline; a standing instruction older than 24 months must be confirmed again; the firm has no closed days in the period.

**1. The official notice** (Custodian One notice reference CN-0417, dated Monday 2 November 2026), typed in by the operations lead:

> Issuer A Ordinary Shares, security ID XS-0001. Event: optional dividend, cash or shares. Record date: Friday 6 November 2026. Option 1, cash: 0.40 per share held. Option 2, shares: 1 new share for every 40 shares held; fractions are paid in cash. Holders who make no election receive Option 1. Elections must reach Custodian One by 5:00 p.m. Eastern on Friday 13 November 2026. The issuer's election deadline is Tuesday 17 November 2026. Elections cannot be changed after submission.

**2. Holdings export** (columns as the template expects; position date 6 November 2026):

- Account ID, Account name, Security ID, Security name, Quantity (record date), Position date, Custodian
- A-101, Rowan Family Trust, XS-0001, Issuer A Ordinary Shares, 12000, 2026-11-06, Custodian One
- A-102, Example Foundation, XS-0001, Issuer A Ordinary Shares, 8500, 2026-11-06, Custodian One
- A-103, Individual Account 103, XS-0001, Issuer A Ordinary Shares, 400, 2026-11-06, Custodian One
- A-104, Staff Pension Plan, XS-0001, Issuer A Ordinary Shares, 25000, 2026-11-06, Custodian One
- A-105, Account 105, XS-0001, Issuer A Ordinary Shares, 1500, 2026-11-06, Custodian Two
- A-106, Account 106, XS-0001, Issuer A Ordinary Shares, 0, 2026-11-06, Custodian One

**3. Standing instructions on file:**

- Account ID, Event type, Instruction, Date on file, Authorized by
- A-101, Optional dividend, Take cash, 2025-03-12, Client (Rowan Family Trust trustee)
- A-102, Optional dividend, Take shares, 2024-06-03, Client (Example Foundation director)
- A-104, Voluntary events, No action, 2022-01-20, Client (plan sponsor)
- No instruction is on file for A-103, A-105 or A-106.

**4. Custodian correspondence:** none beyond the notice. **5. Prior event records:** not supplied.

## The brief

```
CORPORATE ACTION DEADLINE BRIEF: Issuer A Ordinary Shares (XS-0001), optional dividend

Prepared for: Operations lead, Northgate Example Advisory. Brief date: Monday 9 November 2026.
Source: Custodian One notice CN-0417, dated Monday 2 November 2026.

Event as noticed: Optional dividend, cash or shares. Record date Friday 6 November 2026.

Dates and deadlines:
- Firm internal cut-off: Thursday 12 November 2026 (3 days from the brief date). Set by the firm's rule, one business day before the custodian deadline.
- Custodian deadline: 5:00 p.m. Eastern, Friday 13 November 2026 (4 days). Quoted from the notice.
- Issuer deadline: Tuesday 17 November 2026 (8 days). Quoted from the notice.
- Payment date: not stated in the notice.

Options as quoted in the notice:
- Option 1, cash: "0.40 per share held."
- Option 2, shares: "1 new share for every 40 shares held; fractions are paid in cash."
- No election: "Holders who make no election receive Option 1."
- Changes: "Elections cannot be changed after submission."
- Entitlements are not calculated here.

Affected holdings (export position date 2026-11-06, matches the record date):
- Custodian One: A-101 Rowan Family Trust, 12,000. A-102 Example Foundation, 8,500. A-103 Individual Account 103, 400. A-104 Staff Pension Plan, 25,000. Subtotal 45,900.
- Custodian Two: A-105 Account 105, 1,500. Subtotal 1,500. Awaiting its own notice; no deadline yet.
- Total 47,400 across 5 accounts.
- Not affected (zero at the record date): A-106.

Standing instructions on file:
- A-101: Optional dividend, Take cash, 2025-03-12 (19 months old), authorized by Client (Rowan Family Trust trustee). Covers this event type.
- A-102: Optional dividend, Take shares, 2024-06-03 (29 months old, over the limit), authorized by Client (Example Foundation director). Covers this event type; past the age limit, needs confirming.
- A-103: none on file.
- A-104: Voluntary events, No action, 2022-01-20 (57 months old, over the limit), authorized by Client (plan sponsor). Does not clearly cover this event; needs confirming.
- A-105: none on file.

Confirmations still missing:
1. A-103: no instruction on file. Client service reaches the authorized client; the investment manager or the authorized client decides the election. If none is made, the notice says Option 1 applies.
2. A-102: the instruction is older than the limit. Client service confirms it still stands.
3. A-104: the instruction is older than the limit, and "No action" may or may not cover an optional dividend. Client service asks the plan sponsor; whether the instruction applies is not decided here.
4. A-105: no instruction on file, and no notice or correspondence from Custodian Two is on file. Client service confirms the instruction with the authorized client; custody operations obtains Custodian Two's own notice and deadlines.
5. Payment date: not in the notice. Custody operations asks Custodian One.
6. Earlier records of events on this security: not supplied. The operations lead supplies them if they exist.

For specialists (not answered here): the tax treatment of Option 1 and Option 2 for each account (tax specialist); the entitlement for each account under each option (custody operations, from the custodian).

Decision and submission: the investment manager or the authorized client decides each account's election. Operations verifies and submits only approved instructions to Custodian One before the firm cut-off. This brief recommends no election, values nothing, and has sent nothing.

Every date is quoted from notice CN-0417 or set by the firm's stated rule; every quantity is from the holdings export with position date 2026-11-06.
```
