# Fully Powered Capability Templates: Financial Services

Operations a client never has to think about. These capability templates are written for the operations and client-service staff of advisory and investment firms. They prepare the checking around records, reports, fees and settlements from the firm's own data. They recommend, value and rate nothing, assess no client and submit nothing.

This repository holds 6 capability templates for operations and client-service staff at an advisory or investment firm. Each one is a single piece of work with its own folder: what it is for and who starts it, the complete template an AI assistant follows, a worked example with invented data, what to change for your company, what has been checked, and its sources.

## The capabilities

- **[Client report check log](client-report-check-log/)**: Before a batch of client reports is released, the reporting lead gets a log, report by report, of household membership, periods, totals against the custodian statements, fee figures and missing sections, with every difference marked for correction. Nothing is released or sent.
- **[Corporate action deadline brief](corporate-action-deadline-brief/)**: When a custodian notice announces an event on securities your firm holds, operations has one brief: the affected holdings, the options as the notice quotes them, every deadline, the instructions on file and what is still unconfirmed. It recommends nothing and submits nothing.
- **[Household fee check](household-fee-check/)**: On the fee review date, the billing owner gets a fee check by account and household that applies the firm's own agreed schedules and approved waivers to the valuation files, with draft invoice lines, differences against custodian debits and every doubtful account kept apart for review.
- **[Household record differences](household-record-differences/)**: When the CRM and the custodian's account export disagree about a household, the operations owner gets one comparison: accounts with no household, possible duplicates and field-by-field differences, each with its source row and a proposed correction left as a question. No record is changed.
- **[Service provider evidence matrix](service-provider-evidence-matrix/)**: When a material service provider needs approval or renewal, the vendor owner gets one matrix: the provider's evidence set against the firm's own review criteria, with self-attestations, dated reports and untested claims kept apart from independent evidence, and every unanswered question listed.
- **[Settlement exception worklist](settlement-exception-worklist/)**: When the settlement report shows unmatched or failed items, your operations lead gets one aged worklist: each trade's terms, confirmation status, supplied instruction and custodian differences side by side, with a proposed owner. The lead validates and assigns; nothing is sent or moved.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The capability template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More capabilities

The [Fully Powered Capabilities Directory](https://fullypowered.ai/capabilities/) lists every capability across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the capability drew on. Published by [Fully Powered AI](https://fullypowered.ai/).
