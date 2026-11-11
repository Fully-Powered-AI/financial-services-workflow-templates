# Client report check log: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs are the invented example in `public/example.md` (the firm, the four households, the custodians, the accounts and every figure are made up). No client data was used. This is the second run on this example: the first run, earlier the same day, found ambiguities in the instructions and in how the example's inputs were laid out, and the template and example were then revised. This record replaces the first and describes only this run.

## Inputs used

The batch period (1 July 2026 to 30 September 2026) and batch name (Q3 2026 batch), the account inventory (nine rows), the nine custodian statements, the nine billing records, the four draft reports (R-101 to R-104), the report checklist and the "to the cent, no tolerance" setting, all as written in "What the person supplies" in `public/example.md`, under the template's default headers.

Two honest limits. The same model worked on the revised template and ran it, and the example's published output was on screen while the log was worked out, so this is not a blind or independent comparison. The sums and differences were recomputed from the inputs and the template's steps rather than copied.

## What came out

```
CLIENT REPORT CHECK LOG: Q3 2026 batch, 1 July 2026 to 30 September 2026

Prepared for: the reporting lead. Checked 4 reports against 9 custodian statements, 9 billing records and the account inventory for 4 households.
Release is approved by the adviser and the designated reviewer. This log releases and sends nothing and comments on no performance.

Summary: 4 reports. Hold: 2 (R-101, R-103). Differences to correct: 1 (R-102). No differences found: 1 (R-104). Differences logged: 7.

REPORT LOG

R-101, Marlowe household. Status: HOLD (membership difference).
- Recipients: A. Marlowe, J. Marlowe. Match the inventory.
- Membership: 3 of 4 accounts open in the period are on the report. Account 9021 is not on it. See D-1.
- Period: 1 July 2026 to 30 September 2026. Matches the batch.
- Totals: 4410, 7782 and 3305 match their statements. Household total 697,036.65 equals the three accounts shown; the four statements total 948,366.90; difference -251,330.25, which is the value of account 9021 (see D-1).
- Fees: 4410 and 7782 match billing. 3305 does not. See D-2. Fee total 1,715.60 against 2,370.93 in billing; difference -655.33, which is 628.33 for account 9021 (D-1) and 27.00 on account 3305 (D-2).
- Sections: all six present.
- Differences: D-1, D-2.

R-102, Pendry household. Status: DIFFERENCES TO CORRECT.
- Recipients: R. Pendry, S. Pendry. Match the inventory.
- Membership: 2 of 2 accounts open in the period are on the report. 6643 opened on 12 August 2026.
- Period: 1 April 2026 to 30 June 2026. Does not match the batch. See D-3.
- Totals: 1156 and 6643 match their statements. Household total 330,068.40 equals the two accounts and the two statements.
- Fees: 762.80 and 31.19 match billing. Fee total 793.99 equals the billing records.
- Sections: Activity is missing. See D-4.
- Differences: D-3, D-4.

R-103, Quillon household. Status: HOLD (recipient difference; unexplained total difference).
- Recipients: T. Quillon and V. Quillon. V. Quillon is not on the inventory. See D-5.
- Membership: 2 of 2 accounts open in the period are on the report. 8814 closed on 5 September 2026 and shows 0.00 with the closing noted, as the statement does.
- Period: 1 July 2026 to 30 September 2026. Matches the batch.
- Totals: 5207 and 8814 match their statements. Household total 141,775.30 against 140,775.30 from both the accounts and the statements; difference +1,000.00. See D-6.
- Fees: 351.94 and 166.20 match billing. Fee total 518.14 equals the billing records.
- Sections: Disclosures is present but unfinished. See D-7.
- Differences: D-5, D-6, D-7.

R-104, Ashgrove household. Status: NO DIFFERENCES FOUND.
- Recipients: L. Ashgrove. Match the inventory.
- Membership: 1 of 1 account open in the period is on the report.
- Period: 1 July 2026 to 30 September 2026. Matches the batch.
- Totals: 2290 matches its statement at 78,420.75. Household total equals it.
- Fees: 196.05 matches billing. Fee total equals it.
- Sections: all six present.
- Differences: none.

DIFFERENCES FOR CORRECTION

D-1. R-101, membership. The report omits account 9021, Family trust, Custodian X, open all quarter. Statement ending value 251,330.25; billing fee 628.33. Difference: account missing, and both its value and its fee are missing from the household total and the fee total. Marked for correction. Resolved by the reporting lead: ______
D-2. R-101, fees. Account 3305. Report shows 214.13; billing shows 241.13. Difference -27.00. Marked for correction. Resolved by the reporting lead: ______
D-3. R-102, period. Report shows 1 April 2026 to 30 June 2026; the batch period is 1 July 2026 to 30 September 2026. Account 6643 was opened on 12 August 2026, after the period the report shows. Marked for correction. Resolved by the reporting lead: ______
D-4. R-102, sections. The firm's checklist requires Activity; the report has no Activity section. Marked for correction. Resolved by the reporting lead: ______
D-5. R-103, recipients. The report is addressed to T. Quillon and V. Quillon; the inventory lists T. Quillon only. Marked for correction. Resolved by the reporting lead: ______
D-6. R-103, totals. Household total on the report 141,775.30; accounts on the report and their statements total 140,775.30. Difference +1,000.00, not explained by any account. Marked for correction. Resolved by the reporting lead: ______
D-7. R-103, sections. Disclosures contains the placeholder "[to be added]". Marked for correction. Resolved by the reporting lead: ______

NOT CHECKED
Allocation percentages, activity figures, holdings, performance figures and wording were not checked, and no figure was recalculated from transactions. The draft reports show no period against each account and no fee periods, so account periods and fee periods were not checked on the reports; only the cover period was. The statements are taken as the correct source for values and the billing records for fees.

SIGN-OFF
Differences resolved by the reporting lead: ______ Date: ______
Release approved by the adviser: ______ Date: ______
Release approved by the designated reviewer: ______ Date: ______

Every figure traces to the draft reports, custodian statements, billing records and account inventory supplied for the Q3 2026 batch. The log changes no record, releases nothing and sends nothing.
```

## What was observed

- Every required part was produced: read-back with counts, a block per report, seven numbered differences each with the blank resolution line, the not-checked section, blank sign-off lines and the closing line. Nothing was approved, no performance was discussed, no instruction needed refusing, and nothing required stopping: the batch period, statements and inventory were present and every header matched the template's defaults.
- The sums were recomputed and agree: R-101 accounts 697,036.65 against 948,366.90 in statements, fee gap -655.33 = -628.33 - 27.00; R-103 total +1,000.00; 7 differences; 9 accounts, 9 statements, 9 billing records.
- The log was written from the revised steps. The batch name came from the inputs this time. HOLD reasons used the fixed phrases ("membership difference"; "recipient difference; unexplained total difference"). Differences were numbered in report order and step order. The draft reports show no per-account periods and no fee periods, so nothing was logged for them and the NOT CHECKED section says so.
- Where the revised template still left a choice: how to treat the cover period error on R-102 for account 6643's statement period. It was folded into D-3 and not logged separately. Nothing else needed a guess.
- No figure, status or difference number differs from the published example. The four Membership lines word the count differently ("accounts open in the period" here, "open at any time in the period" in the example and the output format). Otherwise the log matches the example's published output, which is expected given the limit above, so this run shows the revised instructions can be followed to that result on this example and little more.
- The template's "Acceptance tests" were not run; only this example was. Tests 10 and 11, added after the first run, have not been run.
- After this run, the instruction block and step 3 were amended with clarifications (the default checklist, billing records not supplied, a fee or billing record with no counterpart, what each difference states, how a closed account without a note or an account closed before the period is treated, and where the output format sits). The example's outputs are unaffected by them, but the amended wording was not re-run.
- One trial is a single data point. It says nothing about real client records, other models or other exports, and the template has not been tested in a client environment.
