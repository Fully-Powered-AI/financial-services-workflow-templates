# Corporate action deadline brief

When a custodian notice announces an event on securities your firm holds, operations has one brief: the affected holdings, the options as the notice quotes them, every deadline, the instructions on file and what is still unconfirmed. It recommends nothing and submits nothing.

*Capability template · Finance and investment · Operations and process improvement · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/corporate-action-deadline-brief/)*

## The outcome

When a custodian announces an event on a security you hold, the operations lead has one brief instead of a notice, a spreadsheet and a search through old emails. It lists which accounts hold the security on the record date and how much, what the options are in the words of the official notice, and the two dates that matter: the custodian's deadline and the issuer's. It shows which accounts already have a standing instruction on file, whether that instruction clearly covers this kind of event, and which confirmations nobody has yet supplied.

The brief decides nothing. The investment manager or the authorized client chooses the election. Operations submits the instructions once they are approved.

## Who starts the work, and when

The operations lead starts it once a custodian notice about a held security has arrived and the holdings export as of the record date is available. The investment manager and client service read the brief; custody operations uses it to submit approved instructions, and tax specialists are pointed to the questions that belong to them.

## What they supply

- The official event notice, as text or a copy of it, with its reference and date.
- The holdings export as of the record date, with each account and its quantity.
- Standing instructions on file for the accounts concerned.
- Any custodian correspondence about the event.
- Earlier records of events on the same security, if there are any.
- The firm's own internal cut-off rule and the dates it is closed.

## What comes out

One brief in a fixed order. It carries the event as noticed, a dated deadline list with days remaining, the options quoted from the notice, the affected accounts and their quantities, the standing instructions on file, the confirmations still missing with the role that can supply each, the questions that go to specialists, and who decides and who submits. Where the notice says nothing on a point, the brief says so rather than filling it in.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), where a repeatable brief replaces rebuilding the same picture for every event.
- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), where the brief's dated record of notices, deadlines and instructions on file sits beside the election records the firm keeps.
- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), the firms that hold securities for clients and receive custodian notices.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), with regular events and a standing way of handling them.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more accounts and custodians make the manual picture harder to hold.

## What has to change for your company

Set how many business days before the custodian's deadline your firm wants instructions in. Decide how old a standing instruction may be before someone must confirm it again. Match the template's default column headers to your holdings export, or rename the headers in the export. Name the roles at your firm who decide, verify and submit.

It does not recommend an election, value an entitlement, give a tax view or submit anything. It is a separate piece of work from any reconciliation; the brief neither matches positions to the custodian's records nor explains breaks.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example, in Claude on 10 November 2026, and the record is published with it. It has not been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on past events your operations lead already knows, with cases written in advance: a notice that omits a deadline, a standing instruction that does not clearly cover the event, an export dated after the record date. The operations lead checks every date and quantity against the notice and the export before anyone relies on the brief.

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

- [Client document request tracker](https://fullypowered.ai/capabilities/client-document-request-tracker/)
- [Client-status update preparation](https://fullypowered.ai/capabilities/client-status-update-preparation/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
