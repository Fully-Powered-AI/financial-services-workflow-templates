# AI workflow templates for advisory and investment firm operations

FullyPowered Workflow Templates for advisory and investment firms turn the AI your firm already pays for into a team that knows how the work is done: a reporting lead with every client report checked against custodian statements before release, an operations lead with the unmatched settlement items aged and listed for assignment, a billing owner with household fees checked against the firm's agreed schedules and drafted. 6 workflow templates, made to be customized and deployed. All plain Markdown, all free, MIT license.

We are FullyPowered AI. We build AI workflows for companies, and these are the templates we start from. We publish them because a good starting point should be open to everyone. Copy one. Change it. Make it yours.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** These are templates, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See more examples for advisory and investment firms](https://fullypowered.ai/industries/finance-and-investment/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme) · [Have one built for your team](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme) Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Who this is for**

- Firm owners and managing partners who have paid for AI and want it doing real operations work.
- Operations and client-service leads who want a careful, repeatable process their team can run this week.
- The person who does the work, who gets a precise first pass and still makes every call.

**What these are for**

- **Your best way of doing it, for the whole team.** One piece of work, written down precisely enough that an assistant prepares it the same way every time.
- **Work you can check.** Every template says what it needs, what it produces, what it checked and what it could not.
- **A person decides.** Anything that sends, posts, pays or changes a record waits for someone to approve it.
- **Tied into your business systems.** A workflow can be designed to pull from the systems your company already runs, and even push data back into them, with guardrails and a person approving. [Browse the Connectors Directory](https://fullypowered.ai/connectors/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme).
- **Free, open and portable.** MIT-licensed plain instructions that run in the assistant or agent your team already uses: ChatGPT, Claude, Claude Code, Claude Cowork, Codex, Copilot, Gemini, Grok, Perplexity.

**Quick start**

1. **Compare your client records with the custodian's list.** Open ChatGPT, Claude, Copilot or Gemini. Copy the text below into a new chat, replace the square-bracket parts with your own, and attach your three exports. Remove birth dates, tax numbers and balances first, and check what your firm allows you to share with an AI assistant.

   ```text
   You are helping the operations owner at [firm name] compare our CRM household records with the custodian's account export. I have attached three files: the CRM household register, the CRM account links and the custodian's account export. Our matching rules are: [write your rules in plain sentences, for example how trust accounts name their primary owner]. Check that the column headers look right and stop to tell me if anything is off. Then list accounts with no household, CRM accounts the custodian does not show, accounts linked to two households, possible duplicate contacts and field-by-field differences. Give the source row for each finding and end each with a question for me. Do not change, merge or correct anything, contact anyone or judge any account. I decide every correction. Say what you did not check.
   ```

2. Read what comes back. It marks what it checked and what is left for you. What comes back, with invented data:

   ```text
   HOUSEHOLD RECORD DIFFERENCES: Firm F

   For: the operations owner. Prepared Tuesday 10 November 2026 from crm_households.csv and crm_accounts.csv (CRM, exported 2026-11-09) and custodian_accounts.csv (custodian, exported 2026-11-09). Nothing in any record has been changed.

   1. THE FILES
   Header check: all three files match the defaults in name and order. crm_households.csv: 14 rows, 12 households. crm_accounts.csv: 14 rows, 13 distinct account numbers. custodian_accounts.csv: 14 rows, 14 distinct account numbers. Full exports, as stated; the figures describe the rows supplied. Rules applied: typed rule 1 (Trust registrations); defaults for the rest.

   2. ACCOUNT MATCH
   Custodian accounts: 14. Matched exactly: 11. Matched after leading zeros: 1. In the custodian export only: 2. In the CRM only: 1. CRM distinct account numbers: 13 (11 + 1 + 1).

   3. ACCOUNTS WITH NO HOUSEHOLD (in the custodian export, not in the CRM)
   ```

3. Stop there. You will know if this is for you. When you want it fitted to your company, or built into your agents, [that is what we do](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme).

In every workflow a person on your team starts the work, supplies the files and decides; the template prepares and checks, and nothing is sent, changed or submitted for you.

These are examples and a starting point, made to be changed to fit how your firm works. Work that is not listed here can still be built for your firm, as one step or as many.

## The workflow templates here today

- **[Client report check log](client-report-check-log/)**: Before a batch of client reports is released, the reporting lead gets a log, report by report, of household membership, periods, totals against the custodian statements, fee figures and missing sections, with every difference marked for correction. Nothing is released or sent.
- **[Corporate action deadline brief](corporate-action-deadline-brief/)**: When a custodian notice announces an event on securities your firm holds, operations has one brief: the affected holdings, the options as the notice quotes them, every deadline, the instructions on file and what is still unconfirmed. It recommends nothing and submits nothing.
- **[Household fee check](household-fee-check/)**: On the fee review date, the billing owner gets a fee check by account and household that applies the firm's own agreed schedules and approved waivers to the valuation files, with draft invoice lines, differences against custodian debits and every doubtful account kept apart for review.
- **[Household record differences](household-record-differences/)**: When the CRM and the custodian's account export disagree about a household, the operations owner gets one comparison: accounts with no household, possible duplicates and field-by-field differences, each with its source row and a proposed correction left as a question. No record is changed.
- **[Service provider evidence matrix](service-provider-evidence-matrix/)**: When a material service provider needs approval or renewal, the vendor owner gets one matrix: the provider's evidence set against the firm's own review criteria, with self-attestations, dated reports and untested claims kept apart from independent evidence, and every unanswered question listed.
- **[Settlement exception worklist](settlement-exception-worklist/)**: When the settlement report shows unmatched or failed items, your operations lead gets one aged worklist: each trade's terms, confirmation status, supplied instruction and custodian differences side by side, with a proposed owner. The lead validates and assigns; nothing is sent or moved.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

To take the whole collection, press **Use this template** at the top of this page: it copies every folder into a repository in your own account, yours to change.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The workflow template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More workflow templates

The [FullyPowered Workflows Directory](https://fullypowered.ai/workflows/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

For the work these templates come from, by area of the business and by task, see [AI workflow examples for finance and investment firms](https://fullypowered.ai/industries/finance-and-investment/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [FullyPowered AI](https://fullypowered.ai/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=financial-services-readme&from=gh-financial-services-readme).
