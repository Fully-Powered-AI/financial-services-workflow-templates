# Corporate action deadline brief: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Northgate Example Advisory, Issuer A, Custodian One and Custodian Two, notice CN-0417). No client data was used. The model that ran the trial did not write the template. It read the template and the example's inputs first, produced the brief, and only then compared it with the example's published output. This is the second run: after review the instructions, the output format and the example were changed (stop and deadline-passed rules added to the instructions, calendar days defined, a third ending for a stale instruction, the treatment of holdings at a custodian with no notice, and roles named for eligibility questions and for asking the custodian), so the earlier run's record was replaced by this one.

## Inputs used

The five inputs and the firm settings under "What the operations lead supplies" in `public/example.md`: the notice, the holdings export (six accounts), the standing instructions (three rows), no other correspondence, no prior records, brief date Monday 9 November 2026, one-business-day cut-off, 24-month limit, no closed days.

## What came out

```
CORPORATE ACTION DEADLINE BRIEF: Issuer A Ordinary Shares (XS-0001), optional dividend

Prepared for: Operations lead, Northgate Example Advisory. Brief date: Monday 9 November 2026.
Source: Custodian One notice CN-0417, dated Monday 2 November 2026.

Event as noticed: Optional dividend, cash or shares. Record date Friday 6 November 2026.

Dates and deadlines:
- Firm internal cut-off: Thursday 12 November 2026 (3 days from the brief date). Set by the firm's rule of one business day before the custodian deadline.
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
1. A-103: no instruction on file. Client service reaches the authorized client; the investment manager or the authorized client decides the election. The notice states that holders who make no election receive Option 1.
2. A-105: no instruction on file, and no notice or correspondence from Custodian Two is on file. Client service confirms the instruction with the authorized client; custody operations obtains Custodian Two's notice and deadlines.
3. A-102: instruction is past the 24-month limit. Client service confirms it still stands.
4. A-104: instruction is past the limit and "Voluntary events, No action" does not clearly cover an optional dividend. Client service confirms with the plan sponsor.
5. Payment date: not stated in the notice. Custody operations asks Custodian One.
6. Prior event records for this security: not supplied. The operations lead supplies them if they exist.

For specialists (not answered here): the tax treatment of Option 1 and Option 2 for each account (tax specialist); the entitlement for each account under each option (custody operations, from the custodian).

Decision and submission: the investment manager, or the authorized client for each account, decides. Custody operations or the operations lead verifies and submits only approved instructions before the firm cut-off. This brief recommends no election, values nothing, and has sent nothing.

Every date is quoted from notice CN-0417 or set by the firm's stated rule; every quantity is from the holdings export with position date 2026-11-06.
```

## What was observed

- Every required part of the output format was produced, and no stop condition was triggered: the security ID matched, every position date equalled the record date, the headers matched the defaults, and no deadline had passed.
- Dates, ages, subtotals and the total were worked out by hand from the inputs. The cut-off lands on Thursday 12 November, and the ages are 19, 29 and 57 months. The result agrees with the published example on all of them.
- The brief matches the published example in substance. The wording differs in a few places:
  - The missing confirmations are in a different order: this run listed A-103, A-105, A-102, A-104, where the example lists A-103, A-102, A-104, A-105. Content and roles agree.
  - This run kept the parenthetical roles on "authorized by" (trustee, director, plan sponsor) because they are in the input; the example shortens them to "Client".
  - The A-102 line reads the same as the example's wording, the third ending the format now provides.
- No fact was added that is not in the inputs, in either output. The payment date and the notice's silence on a time for the issuer deadline were not filled in.
- The points that needed a guess in the earlier run did not recur: calendar days, the Custodian Two holding in the total, the third ending for a stale instruction and the role asked about the payment date are now stated in the instructions. No eligibility question arose, so the new routing for those was not exercised.
- The rules for a passed deadline, a notice with no record date or no options, and counting the cut-off on open days were present in the instructions but not exercised, because this example triggers none of them. Counting the cut-off on open days was trivial here (no closed days).
- One judgment remains: A-104's "Voluntary events, No action" sits between "plainly includes" and "does not clearly cover". The template's acceptance test 5 points to "does not clearly cover", and both outputs agree.
- After this run, minor edits were made to the template following review: a same-day deadline rule ("deadline passed" or "due today"), blank quantities and prior records named under missing confirmations in the instruction block, the no-election outcome not called a firm default in the block, and the closing total line's clause made optional. This example triggers none of them, so the output above was not regenerated and is the record of the run on the earlier wording.
- This was one run by one model on one invented example. It shows the instructions can be followed to produce the output format. It does not show the template works in a firm's own environment, and the acceptance tests other than the first were not run.
