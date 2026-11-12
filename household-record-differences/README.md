# Household record differences

When the CRM and the custodian's account export disagree about a household, the operations owner gets one comparison: accounts with no household, possible duplicates and field-by-field differences, each with its source row and a proposed correction left as a question. No record is changed.

*Workflow template · Finance and investment · Business systems and integrations · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflow templates/household-record-differences/)*

## The outcome

The question "which of our systems has it right?" becomes a list with rows attached. The operations owner opens one page and sees every account the custodian reports that no household in the CRM claims, every account the CRM links that the custodian does not show, every account linked to two households, and every household link where the owner on the account looks like someone in a different household.

The page also lists contacts that may be one person recorded twice, and similar names kept apart from exact repeats, so a near match is never treated as a certain one. For accounts that match, it compares account number (including one written differently), title, primary owner, email and postal code field by field. Each finding names the file and line it came from and ends in a question, such as "Should the CRM link this account to this household?" The answer, and every change that follows, belongs to the operations owner.

The workflow template does not merge, relink or correct anything, contacts no client, and says nothing about whether an account is suitable, how an investment is doing or whether a client is who the record says.

## Who starts the work, and when

An operations owner at an advisory firm starts it, usually when a billing run, a client report or an adviser review turns up an account that is missing from a household, or after a period of change such as a migration, a merger of two books of clients or a custodian switch. It is also worth running regularly, each run started by the operations owner, so differences are found before a client notices them. The operations owner supplies the exports and the firm's own matching rules, reads the comparison and decides each correction.

## What they supply

- **The CRM household register:** one row per contact, with household, name, role, email and postal code.
- **The CRM account links:** which account numbers the CRM places in which household.
- **The custodian's account export:** one row per account, with title, registration, owner names, mailing email, postal code and status.
- **The firm's matching rules,** in plain sentences, such as how trust accounts name their primary owner. The comparison applies what is written and nothing more.
- **Optional settings:** the date, who the comparison is for, and whether account numbers are shown in full or masked.

## What comes out

One comparison in a fixed order: the files and the header check, the account match, accounts with no household, accounts the CRM links that the custodian does not show, household links in question, possible duplicates, field-by-field differences, numbered questions for the operations owner, the decisions that remain, and what was not checked. A section with nothing to report says what was checked and found nothing.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Business systems and integrations](https://fullypowered.ai/functions/business-systems-and-integrations/), where two systems that should describe the same client drift apart and someone has to say where.
- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), where a repeatable check replaces a manual search for the missing account.
- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), where the CRM and the custodian each hold part of the picture of a client household.
- [Acquisitions and integration](https://fullypowered.ai/situations/acquisitions-and-integration/), when another firm's client records are brought in beside your own.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when accounts are opened faster than the records are tidied.

It compares two sets of client records. To understand one unfamiliar export before using it, use [dataset profile](https://fullypowered.ai/workflows/dataset-profile/). When two reports give different totals for one measure, use [metric definition reconciliation](https://fullypowered.ai/workflows/metric-definition-reconciliation/). For matching an asset list to invoices, see [asset register to invoice reconciliation](https://fullypowered.ai/workflows/asset-register-to-invoice-reconciliation/).

## What has to change for your company

Write down your matching rules once: which field links an account to a household, how joint accounts, trusts and custodial accounts name their primary owner, and which differences matter to you. Check that your exports use the default column headers, or rename the headers before you run it; a mismatch stops the comparison on purpose. Decide who verifies identities and authorizes corrections, and how a correction is recorded. Names, emails and postal codes are personal data about your clients: decide what your firm's rules allow you to give an AI product, use the masking setting for account numbers if you want it, and leave out birth dates, tax numbers, balances and holdings, which the comparison does not need. It runs in ChatGPT, Claude, Copilot or Gemini from files you supply; it needs no connection to your systems, and it never asks for a login.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026; the record of that run is published with it, and it names the small wording edits made afterward that have not been run again, including a last pass of clauses added to the instruction block. That run produced every section, including accounts with no household, an account linked to two households, a link conflict, two possible duplicates and four field differences; it did not exercise the stop conditions or the requests the template declines. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on an extract from each system for a few households your team already knows well, with differences planted in copies and written down in advance: an account the CRM does not hold, an account linked to two households, a postal code that disagrees, a name spelled two ways. The operations owner confirms each finding against the rows before anyone relies on the comparison. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

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

- [Dataset profile](https://fullypowered.ai/workflow templates/dataset-profile/)
- [Metric definition reconciliation](https://fullypowered.ai/workflow templates/metric-definition-reconciliation/)
- [Asset register to invoice reconciliation](https://fullypowered.ai/workflow templates/asset-register-to-invoice-reconciliation/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
