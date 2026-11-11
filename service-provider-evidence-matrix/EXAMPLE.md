# Service provider evidence matrix: an invented example

*Illustrative example with invented data.* The firm, the providers, the documents, the quotations and every date below are invented. The firm is an invented wealth advisory firm renewing its hosted client reporting service. Its head of operations is the vendor owner; named reviewers read each area and a vendor oversight committee approves. The provider is called Provider A and the outside firms Assurance firm X and Testing firm Y.

The inputs come first, in full, so the template can be run on them. The matrix follows.

## The inputs

### 1. Review facts

```
Provider: Provider A
Service: hosted client reporting portal and monthly statement production
Reason for review: renewal
Review date: Tuesday 10 November 2026
Age limit: 12 months
Vendor owner: Head of operations
Reviewers by area: Service scope - Head of operations; Data handling -
  Security reviewer; Continuity - Risk reviewer; Contract commitments -
  Legal reviewer; Audit reports - Risk reviewer
Approving body: Vendor oversight committee
```

### 2. Review criteria (approved by the firm's vendor oversight committee)

```
criterion_id,area,criterion,evidence_wanted
SC1,Service scope,The service is described in writing and matches what the firm uses it for,A service description in the agreement or its schedules
SC2,Service scope,Any subcontracted part of the service is named,A named list of subcontractors and the part each performs
DH1,Data handling,Where client data is stored and processed is stated,A statement of countries and sites for storage and processing
DH2,Data handling,Client data is encrypted in transit and at rest,An independent report or test covering encryption
DH3,Data handling,Client data is returned or deleted when the service ends,Agreement text stating the periods for return and deletion
CO1,Continuity,A continuity plan states a recovery time for the service,The plan or its summary with the recovery time
CO2,Continuity,The plan has been tested within the last 12 months,A test record that shows the date and the result
CT1,Contract commitments,The provider must report a security incident within a stated period,Agreement text stating the period in hours or days
CT2,Contract commitments,The firm may receive the provider's audit reports each year,Agreement text giving the firm that right
AR1,Audit reports,An independent report on the provider's controls covers the service and is current,A report stated as at a date within the age limit that covers the service
```

### 3. The provider's evidence (typed by the vendor owner from the supplied documents)

```
evidence_id,criterion_ids,document,location,statement,evidence_type,issued_by,as_of,tested_on,scope_stated
E01,SC1,Renewal proposal,Section 2,"Provider A supplies a hosted client reporting portal and monthly statement production for the firm's advisory clients.",self-attestation,Provider A,2026-09-14,,
E02,SC1,Proposed renewal agreement (unsigned),Services schedule 1.1,"The Services are the hosted reporting portal and the monthly production of client statements described in Annex 1.",contract-text,Provider A,2026-09-14,,
E03,SC2,Renewal proposal,Section 2.4,"Statement printing is carried out by a partner print company; no other part of the service is subcontracted.",self-attestation,Provider A,2026-09-14,,
E04,DH1,Security questionnaire,Answer 14,"Client data is stored and processed in the United States only.",self-attestation,Provider A,2026-08-30,,
E05,DH2;AR1,Independent controls report,Control 4.2,"Client data is encrypted in transit and at rest. No exceptions noted.",independent-report,Assurance firm X,2025-06-30,,"Period 1 July 2024 to 30 June 2025; reporting portal only; statement production not included"
E06,DH2,Security questionnaire,Answer 21,"All client data is encrypted at rest and in transit.",self-attestation,Provider A,2026-08-30,,
E07,DH3,Proposed renewal agreement (unsigned),Clause 12.3,"On termination the Provider shall return the Customer's data within 30 days and delete remaining copies within 90 days.",contract-text,Provider A,2026-09-14,,
E08,CO1,Continuity plan summary,Page 2,"The recovery time target for the reporting portal is 8 hours.",plan,Provider A,2026-03-31,,
E09,CO2,Annual continuity test summary,Page 1,"A failover test of the reporting portal was completed on 20 February 2026 and service was restored in 6 hours.",plan,Provider A,2026-02-20,2026-02-20,
E10,CT1,Proposed renewal agreement (unsigned),Clause 9.1,"The Provider shall notify the Customer of a security incident affecting Customer data without undue delay.",contract-text,Provider A,2026-09-14,,
E11,AR1,Bridge letter,Paragraph 2,"There have been no material changes to the controls since 30 June 2025.",self-attestation,Provider A,2026-09-01,,
E12,,Renewal proposal,Section 6,"Provider A carries professional indemnity insurance.",self-attestation,Provider A,2026-09-14,,
E13,DH2,Penetration test summary,Section 3,"Encryption settings on the portal's transport and databases were inspected at retest; no weaknesses were found.",independent-report,Testing firm Y,2026-05-15,,"Portal and its databases; statement production not included"
```

### 4. Earlier findings

```
finding_id,area,date,finding,status
F1,Continuity,2025-11-14,Last failover test was more than a year old,closed
F2,Audit reports,2025-11-14,The report did not cover statement production,open
F3,Billing,2025-11-14,Invoices were issued late twice,closed
```

### 5. Questions already put to the provider

```
question_id,criterion_id,question,asked_on,answered
Q1,SC2,Name the print partner and the sites where statements are produced.,2026-09-22,no
Q2,CT2,Confirm whether the firm may receive the provider's audit reports each year.,2026-10-06,no
Q3,DH1,List the countries where backup copies are held.,2026-10-06,yes
```

## The output

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
