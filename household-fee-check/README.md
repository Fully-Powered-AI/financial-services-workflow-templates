# Household fee check

On the fee review date, the billing owner gets a fee check by account and household that applies the firm's own agreed schedules and approved waivers to the valuation files, with draft invoice lines, differences against custodian debits and every doubtful account kept apart for review.

*Capability template · Finance and investment · Finance and accounting · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/household-fee-check/)*

## The outcome

The billing owner opens the fee run with the arithmetic already laid out. Each account that can be calculated has a draft invoice line with its value, its schedule, any waiver applied and the fee that results. Next to each line sits the amount the custodian actually debited and the difference.

The accounts that cannot be calculated safely are not guessed at. A fee that depends on an unclear proration, a valuation that is out of date, a negotiated rate nobody approved, or an account that has closed goes to a separate list, with the facts known and a question for a named person. The billing owner confirms the rules and the exceptions. An authorized approver decides on any charge or credit. The template debits, invoices and credits nothing.

## Who starts the work, and when

The billing owner starts it on the fee review date, once the period-end valuation files and the custodian debit records are in hand. The approver reviews the result before any invoice is released or any credit is raised.

## What they supply

- The valuation files for the fee period, one value and one date per account.
- The household links: which accounts belong to which household.
- The firm's agreed fee schedules and the fee terms that say which household or account uses which schedule.
- The approved waivers and discounts, with who approved each and when.
- The account open and close dates.
- The custodian debit records for the fee period.
- A short settings note: the period, the debit window, the proration rule and the tolerance.

## What comes out

One fee check in a fixed order: the settings used, draft invoice lines by household and account, differences against custodian debits, the review list, a tie-out of the totals and the decisions that belong to the billing owner and the approver. If a file does not have the headers the template expects, it stops and asks, rather than guessing which column is which.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), where advisory and investment firms bill on the value of the accounts they manage.
- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), which owns the invoice run and the reconciliation to what the custodian collected.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where fee terms have accumulated over years of client conversations.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when the client list outgrows a fee run done by eye.

It sits beside [Client billing summary](https://fullypowered.ai/capabilities/client-billing-summary/), which explains an invoice built from billed time, and [Subscription billing exception sheet](https://fullypowered.ai/capabilities/subscription-billing-exception-sheet/), which checks plans and seats. This one is for fees charged as a share of account value.

## What has to change for your company

Settle your own rules before the first run: how often you bill, whether a fee is worked out on the household or on each account, how long a valuation may be before it counts as out of date, and what you do when an account opens or closes in the middle of a period. Fix your tolerance for small differences. Decide who may approve a waiver, and who releases a charge or a credit. The template follows your schedules and waivers; it does not set them, and it takes no tax or regulatory position.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example, in Claude on 10 November 2026, and the record is published with it. It has not been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your firm means running it on a past period whose fees you already know, plus hard cases written in advance: a household that spans a tier boundary, a waiver that ended last year, an account that closed mid-period, a debit on an account nobody listed. The billing owner checks every figure against the valuation files before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) sets those cases up.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Client billing summary](https://fullypowered.ai/capabilities/client-billing-summary/)
- [Subscription billing exception sheet](https://fullypowered.ai/capabilities/subscription-billing-exception-sheet/)
- [Bank reconciliation preparation](https://fullypowered.ai/capabilities/bank-reconciliation-preparation/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
