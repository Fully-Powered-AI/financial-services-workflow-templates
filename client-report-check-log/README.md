# Client report check log

Before a batch of client reports is released, the reporting lead gets a log, report by report, of household membership, periods, totals against the custodian statements, fee figures and missing sections, with every difference marked for correction. Nothing is released or sent.

*Capability template · Finance and investment · Analytics and reporting · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/client-report-check-log/)*

## The outcome

The batch is checked against the firm's own records before any client sees it. For each report the reporting lead can see which accounts belong to the household and whether each one is on the page, whether the dates are the right dates, whether every account value matches its custodian statement, whether the fee figures match the billing records, and whether every section the firm requires is there and finished.

Each difference arrives in one place, with the report's figure beside the record's figure and the gap between them, marked for correction. Reports with a wrong recipient, a missing account or a total nobody can explain are marked to hold. The reporting lead resolves the differences. The adviser and the designated reviewer approve release. The log does neither, and it says nothing about performance.

## Who starts the work, and when

The reporting lead starts it when a batch of draft reports is ready for release review, usually at the end of a quarter, and again after corrections are made to confirm the differences are closed. Reporting operations staff can prepare the inputs.

## What they supply

- The draft reports in the batch, with the batch period and, if there is one, a batch name.
- The custodian statements for the same period, as exported lists or pasted rows.
- The account inventory: which accounts belong to which household, their status and who receives the report.
- The billing records: the fee for each account and fee period.
- The firm's report checklist: the sections every report must carry.

## What comes out

One log in a fixed order: a count of reports by status, then each report with its recipient, membership, period, totals, fees and section checks, then a numbered list of differences, each marked for correction with a blank for the reporting lead's resolution. The log ends with what was not checked and blank sign-off lines for the reporting lead, the adviser and the designated reviewer.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), where an advisory firm sends the same kind of report to many households on the same day.
- [Professional services](https://fullypowered.ai/industries/professional-services/), for firms whose client deliverables are checked by a second person before they go out.
- [Analytics and reporting](https://fullypowered.ai/functions/analytics-and-reporting/), which owns how recurring reports are assembled and trusted.
- [Quality management](https://fullypowered.ai/functions/quality-management/), for the release check that sits between drafting and the client.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where the reporting routine already exists and the check is the gap.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more households make a manual line-by-line check slower each quarter.

## What has to change for your company

Set the sections your reports must carry. Decide how many cents of difference you accept on an account value, if any. Name the roles that resolve differences and approve release. Say which records are the source for membership, values and fees; the template logs both facts when two records disagree and leaves the choice to the reporting lead. Decide which differences hold a report, if you want more or fewer than it does. Match the default column headers in the template to your exports, or tell the assistant which headers you use.

## What has been checked

Fully Powered AI wrote this capability template from its own map of the work. It was editorially reviewed on 10 November 2026. It was tried once on its invented example, in Claude on 10 November 2026, and the record is published with it. It has not been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past batch whose differences the reporting lead already knows, and checking that each one is found and each clean report is left clean. The reporting lead checks every figure in the log against the source records before anyone relies on it.

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

- [Spreadsheet check before sharing](https://fullypowered.ai/capabilities/spreadsheet-check-before-sharing/)
- [Weekly receivables summary](https://fullypowered.ai/capabilities/weekly-receivables-summary/)
- [Household fee check](../household-fee-check/)
- [Household record differences](../household-record-differences/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
