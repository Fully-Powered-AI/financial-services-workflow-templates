# Service provider evidence matrix: tried on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in [example.md](example.md): the review facts, ten criteria, thirteen evidence items, three earlier findings and three asked questions for an invented wealth advisory firm and its invented Provider A. No client data was used.

This is the third run on that date and the one recorded. The first run, made before review, gave the same labels, quotations, statuses, counts and lists as the published example but differed from it in presentation. The second was made after the template was revised to settle the points that run exposed. After the independent review, the template was revised again: the "figure or period" test now rests on named words in `evidence_wanted`, the output format prints the title line in bold and a blank line after each bold heading, a fixed line in the header says that "Independently supported" describes the kind of evidence and not its sufficiency, and the instruction block now spells out the counting of inputs and the "criterion not found" rule. This run was made on that revised block.

How this run was made, and its limit. It was not a cold run. The assistant that made the revision also followed the revised instruction block and output format on the inputs, and had already read the published example and the earlier records, so this is a check that the revised wording produces the intended form, not an independent run. A run by an assistant that has seen none of this would be stronger evidence and has not been made. The draft was composed from the inputs under the revised rules, then compared with the published output; the comparison is below.

## What came out

```
**SERVICE PROVIDER EVIDENCE MATRIX: Provider A, hosted client reporting portal and monthly statement production**

For: Head of operations. Reason: renewal. Review date: Tuesday 10 November 2026.
Age limit: 12 months; evidence stated as at 10 November 2025 or later counts as current.
Prepared from: 10 criteria, 13 evidence items, 3 earlier findings, 3 asked questions.
Criteria: 10. Independently supported: 1. Dated independent evidence only: 1. Not independently supported (status No only): 7. No evidence supplied: 1.
Evidence items: 13. Independent and current: 1. Independent, dated: 1. Provider's own statement: 7. Provider's plan, no test recorded: 1. Contract text: 3. Of these, not tied to a criterion: 1.
Independently supported names the kind of evidence, not whether it is enough.

**Service scope** (reviewer: Head of operations)

SC1 The service is described in writing and matches what the firm uses it for. Evidence wanted: A service description in the agreement or its schedules. Independently supported: No.

- E01, Provider's own statement: "Provider A supplies a hosted client reporting portal and monthly statement production for the firm's advisory clients." Renewal proposal, Section 2. Issued by Provider A. As of 14 September 2026. Scope stated: not stated.
- E02, Contract text: "The Services are the hosted reporting portal and the monthly production of client statements described in Annex 1." Proposed renewal agreement (unsigned), Services schedule 1.1. Issued by Provider A. As of 14 September 2026. Scope stated: not stated.

SC2 Any subcontracted part of the service is named. Evidence wanted: A named list of subcontractors and the part each performs. Independently supported: No.

- E03, Provider's own statement: "Statement printing is carried out by a partner print company; no other part of the service is subcontracted." Renewal proposal, Section 2.4. Issued by Provider A. As of 14 September 2026. Scope stated: not stated.

Earlier findings, Service scope: None.

**Data handling** (reviewer: Security reviewer)

DH1 Where client data is stored and processed is stated. Evidence wanted: A statement of countries and sites for storage and processing. Independently supported: No.

- E04, Provider's own statement: "Client data is stored and processed in the United States only." Security questionnaire, Answer 14. Issued by Provider A. As of 30 August 2026. Scope stated: not stated.

DH2 Client data is encrypted in transit and at rest. Evidence wanted: An independent report or test covering encryption. Independently supported: Yes.

- E05, Independent, dated: "Client data is encrypted in transit and at rest. No exceptions noted." Independent controls report, Control 4.2. Issued by Assurance firm X. As of 30 June 2025 (older than the limit). Scope stated: Period 1 July 2024 to 30 June 2025; reporting portal only; statement production not included.
- E06, Provider's own statement: "All client data is encrypted at rest and in transit." Security questionnaire, Answer 21. Issued by Provider A. As of 30 August 2026. Scope stated: not stated.
- E13, Independent and current: "Encryption settings on the portal's transport and databases were inspected at retest; no weaknesses were found." Penetration test summary, Section 3. Issued by Testing firm Y. As of 15 May 2026. Scope stated: Portal and its databases; statement production not included.

DH3 Client data is returned or deleted when the service ends. Evidence wanted: Agreement text stating the periods for return and deletion. Independently supported: No.

- E07, Contract text: "On termination the Provider shall return the Customer's data within 30 days and delete remaining copies within 90 days." Proposed renewal agreement (unsigned), Clause 12.3. Issued by Provider A. As of 14 September 2026. Scope stated: not stated.

Earlier findings, Data handling: None.

**Continuity** (reviewer: Risk reviewer)

CO1 A continuity plan states a recovery time for the service. Evidence wanted: The plan or its summary with the recovery time. Independently supported: No.

- E08, Provider's plan, no test recorded: "The recovery time target for the reporting portal is 8 hours." Continuity plan summary, Page 2. Issued by Provider A. As of 31 March 2026. Scope stated: not stated.

CO2 The plan has been tested within the last 12 months. Evidence wanted: A test record that shows the date and the result. Independently supported: No.

- E09, Provider's own statement: "A failover test of the reporting portal was completed on 20 February 2026 and service was restored in 6 hours." Annual continuity test summary, Page 1. Issued by Provider A. As of 20 February 2026. Tested on 20 February 2026, by the provider. Scope stated: not stated.

Earlier findings, Continuity: F1, 14 November 2025, "Last failover test was more than a year old", status as supplied: closed.

**Contract commitments** (reviewer: Legal reviewer)

CT1 The provider must report a security incident within a stated period. Evidence wanted: Agreement text stating the period in hours or days. Independently supported: No.

- E10, Contract text: "The Provider shall notify the Customer of a security incident affecting Customer data without undue delay." Proposed renewal agreement (unsigned), Clause 9.1. Issued by Provider A. As of 14 September 2026. Scope stated: not stated. No figure in the quoted text.

CT2 The firm may receive the provider's audit reports each year. Evidence wanted: Agreement text giving the firm that right. Independently supported: No evidence supplied.

- No evidence supplied.

Earlier findings, Contract commitments: None.

**Audit reports** (reviewer: Risk reviewer)

AR1 An independent report on the provider's controls covers the service and is current. Evidence wanted: A report stated as at a date within the age limit that covers the service. Independently supported: Dated only.

- E05, Independent, dated: "Client data is encrypted in transit and at rest. No exceptions noted." Independent controls report, Control 4.2. Issued by Assurance firm X. As of 30 June 2025 (older than the limit). Scope stated: Period 1 July 2024 to 30 June 2025; reporting portal only; statement production not included.
- E11, Provider's own statement: "There have been no material changes to the controls since 30 June 2025." Bridge letter, Paragraph 2. Issued by Provider A. As of 1 September 2026. Scope stated: not stated.

Earlier findings, Audit reports: F2, 14 November 2025, "The report did not cover statement production", status as supplied: open. Open at the last review.

**Earlier findings not matched to an area**

- F3, Billing, 14 November 2025, "Invoices were issued late twice", status as supplied: closed.

**Evidence not tied to a criterion**

- E12, Provider's own statement: "Provider A carries professional indemnity insurance." Renewal proposal, Section 6. Issued by Provider A. As of 14 September 2026. Scope stated: not stated. No criterion named.

**Unanswered questions**

Asked and not answered: 2 (1 answered).
- Q1, SC2, asked 22 September 2026: "Name the print partner and the sites where statements are produced."
- Q2, CT2, asked 6 October 2026: "Confirm whether the firm may receive the provider's audit reports each year."

Criteria with no evidence supplied: CT2. Evidence wanted: Agreement text giving the firm that right. (Request wording only; nothing has been sent.)
Not independently supported: SC1, SC2, DH1, DH3, CO1, CO2, CT1.
Dated independent evidence only: AR1.

**Who decides**

Assessed by the reviewers named above. Approved by the Vendor oversight committee. This matrix assesses no control, reads no contract for its legal effect and approves no relationship.

Draft for the Head of operations. Nothing has been sent, changed or approved.
```

## What was observed

- Every required part was produced. No stop condition applied: headers matched, ids were unique, all evidence types were valid, no password or personal data appeared, no provider text carried an instruction, no items contradicted each other, no statement was missing, no reviewer was missing and no `as_of` date was after the review date. The cut-off, 10 November 2025, needed no fallback: the 10th exists in every month.
- The counts agree with the lists: ten criteria (1 Yes, 1 Dated only, 7 No, 1 No evidence supplied) and thirteen evidence items (1 + 1 + 7 + 1 + 3), with one item tied to no criterion. "Not independently supported" counts only the seven criteria with status No.
- Nothing was judged. The draft quotes the encryption report as supplied without saying whether its scope fits, and quotes clause 9.1 without saying what "without undue delay" means. "No figure in the quoted text." was added only to clause 9.1, the one criterion whose `evidence_wanted` ("Agreement text stating the period in hours or days") contains one of the named words and whose quote states no number. It was not added to DH3, whose `evidence_wanted` contains "periods" but whose quote states 30 and 90 days, or to any other criterion.
- The fixed header line was printed as written. DH2 still shows "Independently supported: Yes" although both independent items state that statement production is not included; the header line now says the word describes the kind of evidence, and the scope stays printed for the reviewers.
- Compared with the published example, the content and the form are the same, including bold title, bold headings with a blank line after each, and the earlier-findings line printed for every area after its last criterion. The comparison is close to circular, because the example was updated to the same revised format before this run.
- This run did not exercise these rules, because the inputs do not reach them: the cut-off fallback for a review date on the 29th to 31st, a missing reviewer, a missing statement, an `as_of` date after the review date, a question naming an unlisted criterion ("criterion not found"), and the "Tested on" and "(older than the limit)" slots on the line for evidence not tied to a criterion. They are written into the instruction block and the format but have not been run.
- No fact appears in the output that is not in the inputs, apart from the fixed header line. The weekday for the review date is given in the inputs.
- Not settled by this run: a plan exercised or witnessed by an outside party has no label (see What to customize in the template).
- No defect in the rules was found in this run.
