# Service provider evidence matrix

When a material service provider needs approval or renewal, the vendor owner gets one matrix: the provider's evidence set against the firm's own review criteria, with self-attestations, dated reports and untested claims kept apart from independent evidence, and every unanswered question listed.

*Capability template · Finance and investment · Procurement and suppliers · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/service-provider-evidence-matrix/)*

## The outcome

The people who judge a provider start from one page instead of a folder. Every criterion your firm approved for the review sits in a row, and under it sits whatever the provider has supplied for it, quoted as supplied and labelled by what kind of evidence it is.

The labels are the point. A provider saying it encrypts data, a report from an outside assurance firm that is two years old, a recovery plan nobody has run, a promise written into the agreement and a recent independent test look alike in a long file. In the matrix they are different things, and a criterion that rests only on the provider's own word says so.

The gaps are on the page as well: criteria with nothing supplied, questions you asked that have not been answered, and earlier findings still open. Your reviewers assess the evidence. The committee decides on the relationship. The matrix does neither.

## Who starts the work, and when

The vendor owner starts it when a material service provider is coming up for approval or renewal and the provider's documents have arrived. It runs again each time the provider sends more, so the reviewers always see the current state of the file.

The vendor owner reads the matrix first and checks it against the source documents before it goes to the risk, security and legal reviewers.

## What they supply

- **Your review criteria,** as your firm approved them: an identifier, the area, the criterion and the evidence you want for it.
- **The provider's evidence,** listed one item at a time: which criteria it speaks to, the document and place, the statement, what kind of evidence it is, who issued it and the date it is stated as at.
- **The review facts:** the provider and service, whether this is an approval or a renewal, the date of the review, how old evidence may be before it counts as dated, and who reviews each area.
- **Earlier findings and questions already put to the provider,** if you have them.

## What comes out

A matrix in your criteria's order, grouped by area, with the reviewer for each area named. Each criterion shows whether independent, current evidence exists for it, then every item supplied, quoted word for word with its source, issuer, date and stated scope.

After the matrix: evidence that points at no criterion, the questions still unanswered, criteria with nothing supplied, and a plain statement of who assesses and who approves.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Procurement and suppliers](https://fullypowered.ai/functions/procurement-and-suppliers/), where the approval of a provider begins and the owner of the relationship sits.
- [Compliance, risk and privacy](https://fullypowered.ai/functions/compliance-risk-and-privacy/), whose reviewers weigh the evidence the matrix organizes.
- [Finance and investment](https://fullypowered.ai/industries/finance-and-investment/), where firms rely on outside providers for reporting, custody support and operations and must show how each was reviewed.
- [Insurance](https://fullypowered.ai/industries/insurance/), where claims, administration and data services are often outsourced.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where providers have accumulated over the years and renewals arrive faster than reviews.

## What has to change for your company

Use your own approved criteria; the capability adds none. Decide how old a report may be before you call it dated, and which kinds of evidence you accept as independent. Name the reviewer for each area, the committee that approves, and where the matrix is kept. Decide how you want evidence listed: one row per document statement is the default. It runs in ChatGPT, Claude, Copilot or Gemini from files and notes you supply; it needs no connection to any system and no access to the provider.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the record of the last run is published with it. It has not yet been tested in a client environment.

Testing in your environment means running it on one or two past reviews your team remembers well, plus cases written in advance with the expected result: a report older than your limit, an item marked independent that the provider itself issued, a criterion with no evidence, an evidence item pointing at a criterion that does not exist. Your reviewers check every label against the source document before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set.

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

- [Vendor renewal review](https://fullypowered.ai/capabilities/vendor-renewal-review/)
- [Vendor quote comparison](https://fullypowered.ai/capabilities/vendor-quote-comparison/)
- [Teaching tool vendor data questions](https://fullypowered.ai/capabilities/education-vendor-data-questions/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
