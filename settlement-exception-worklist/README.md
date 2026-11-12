# Settlement exception worklist

When the settlement report shows unmatched or failed items, your operations lead gets one aged worklist: each trade's terms, confirmation status, supplied instruction and custodian differences side by side, with a proposed owner. The lead validates and assigns; nothing is sent or moved.

*Workflow template · Finance and investment · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/settlement-exception-worklist/)*

## The outcome

A settlement report tells you that something did not settle. It rarely tells you why, and the answer is spread over four places: the trade blotter, the confirmation report, the custodian's own report and the record of verified settlement instructions. Your operations lead normally rebuilds that picture by hand, trade by trade, before anyone can be asked to look.

This workflow template does the rebuilding. Every unmatched or failed item arrives with what the firm recorded, what the counterparty confirmed, what the custodian holds and which instruction applies, and each difference is written out next to the figures it comes from. Items are aged in business days against the market's own calendar, oldest first, so the trade that has been open for a week is not buried under the one that fell due this morning.

Each item carries a proposed owner, a role chosen by a stated rule, with the reason beside it. Anything the evidence cannot settle stays open and is written as a question for a named role: a custodian line with no trade reference, two dates that disagree, an instruction change nobody has verified. The operations lead decides what is a real break and who investigates it.

## Who starts the work, and when

The operations lead, or a trade-support analyst for the lead, starts it when the custodian's settlement report for the day arrives with unmatched or failed items on it. It can be run again the next morning on the new report to age the same items forward and show which ones have cleared.

The operations lead reviews the worklist before anyone else sees it.

## What they supply

- **The trade blotter export:** the firm's own record of each trade, with its intended settlement date, market and the instruction it was booked against.
- **The confirmation report:** the status of each trade's confirmation and the terms the counterparty confirmed.
- **The custodian's settlement report** for the report date.
- **The verified instruction records:** the firm's list of settlement instructions and whether each has been verified.
- **The market calendar:** the days each market is closed.
- **The settings:** the report date, the age bands, which custodian statuses count as exceptions and the owner roles to propose.

## What comes out

One worklist, oldest first. Each item shows the trade's terms, the confirmation, the custodian's position and the instruction, the differences between them, the age, any flags and the proposed owner with the rule behind it. A summary on top counts items by age and by proposed owner, with trade value by currency and never converted. Custodian lines that cannot be tied to a trade are listed apart, and open questions are written for named roles.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), where unsettled trades become cash breaks and the cash questions are asked.
- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), which owns the daily routine of looking at breaks, assigning them and following them to the end.
- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), where trade and custody operations sit between the investment team, the custodian and the firm's counterparties.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where the daily break review has always lived in one experienced person's head.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when trade volume rises faster than the operations team and the old way of walking through breaks stops keeping up.

It sits beside, and is distinct from, [bank reconciliation preparation](https://fullypowered.ai/workflows/bank-reconciliation-preparation/), which is about a bank statement checked against the firm's ledger; [receivables exception review](https://fullypowered.ai/workflows/receivables-exception-review/), which deals with customer invoices and payments; and [payout reconciliation for an online store](https://fullypowered.ai/workflows/payout-reconciliation-for-an-online-store/), which reconciles an online store's payment-processor payouts.

## What has to change for your company

Map your export headings to the ones the template expects. Set your age bands and the custodian statuses that count as exceptions. Write your owner table: which role takes a terms difference, a confirmation that is missing, an instruction that is not verified, a cash difference or a custodian line with no reference. Decide who may verify an instruction change and who approves any instruction or cash movement, and keep that outside this workflow template. Add the markets you trade in, with their closed days. Run it first on a day your operations lead has already worked by hand.

This workflow template executes no trade, settlement or instruction. It rates no counterparty and judges no investment. It does not contact the custodian or a counterparty.

## What has been checked

Fully Powered AI wrote this workflow template and it was editorially reviewed on 10 November 2026. Every figure in its invented example was recomputed by hand from the inputs shown with it. It was tried once on its invented example in Claude on 10 November 2026, and the record is published with it. Any edits made after the trial have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on past days your operations lead has already worked, with cases written in advance: a custodian line with no trade reference, a trade missing from the custodian report, two settlement dates that disagree, an instruction change not yet verified, a closed market day inside the ageing, and a column heading it does not recognize. The operations lead compares every item with the notes already made before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Bank reconciliation preparation](https://fullypowered.ai/workflows/bank-reconciliation-preparation/)
- [Receivables exception review](https://fullypowered.ai/workflows/receivables-exception-review/)
- [Month-end close checklist](https://fullypowered.ai/workflows/month-end-close-checklist/)
- [Payout reconciliation for an online store](https://fullypowered.ai/workflows/payout-reconciliation-for-an-online-store/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
