# Client report check log: an invented example

*Illustrative example with invented data.* The firm, households, custodians, accounts and every figure below are made up. The firm is "the firm" throughout; custodians are Custodian X, Y and Z.

The reporting lead at an invented advisory firm is checking a batch of four quarterly reports for the period 1 July 2026 to 30 September 2026. Batch name: Q3 2026 batch. Report checklist: Cover and recipients; Account summary; Allocation; Activity; Fees; Disclosures. Accepted difference on an account value: none, exact to the cent.

## What the person supplies

The three record lists use the template's default headers, in the order shown. Each line below is one row.

**Account inventory** (Household; Account (last four); Account name; Custodian; Status; Opened; Closed; Report recipients)

- Marlowe; 4410; Joint brokerage; Custodian X; open; blank; blank; A. Marlowe, J. Marlowe.
- Marlowe; 7782; IRA (A. Marlowe); Custodian X; open; blank; blank; A. Marlowe, J. Marlowe.
- Marlowe; 3305; IRA (J. Marlowe); Custodian Y; open; blank; blank; A. Marlowe, J. Marlowe.
- Marlowe; 9021; Family trust; Custodian X; open; blank; blank; A. Marlowe, J. Marlowe.
- Pendry; 1156; Joint brokerage; Custodian Y; open; blank; blank; R. Pendry, S. Pendry.
- Pendry; 6643; Education account; Custodian Z; new; 12 August 2026; blank; R. Pendry, S. Pendry.
- Quillon; 5207; Individual brokerage; Custodian X; open; blank; blank; T. Quillon.
- Quillon; 8814; IRA; Custodian X; closed; blank; 5 September 2026; T. Quillon.
- Ashgrove; 2290; Individual brokerage; Custodian Y; open; blank; blank; L. Ashgrove.

**Custodian statements** (Custodian; Account (last four); Account name; Period start; Period end; Ending value)

- Custodian X; 4410; Joint brokerage; 1 July 2026; 30 September 2026; 412,380.55.
- Custodian X; 7782; IRA (A. Marlowe); 1 July 2026; 30 September 2026; 188,206.10.
- Custodian Y; 3305; IRA (J. Marlowe); 1 July 2026; 30 September 2026; 96,450.00.
- Custodian X; 9021; Family trust; 1 July 2026; 30 September 2026; 251,330.25.
- Custodian Y; 1156; Joint brokerage; 1 July 2026; 30 September 2026; 305,118.40.
- Custodian Z; 6643; Education account; 12 August 2026; 30 September 2026; 24,950.00.
- Custodian X; 5207; Individual brokerage; 1 July 2026; 30 September 2026; 140,775.30.
- Custodian X; 8814; IRA; 1 July 2026; 5 September 2026; 0.00.
- Custodian Y; 2290; Individual brokerage; 1 July 2026; 30 September 2026; 78,420.75.

**Billing records** (Account (last four); Fee period start; Fee period end; Fee amount)

- 4410; 1 July 2026; 30 September 2026; 1,030.95.
- 7782; 1 July 2026; 30 September 2026; 470.52.
- 3305; 1 July 2026; 30 September 2026; 241.13.
- 9021; 1 July 2026; 30 September 2026; 628.33.
- 1156; 1 July 2026; 30 September 2026; 762.80.
- 6643; 12 August 2026; 30 September 2026; 31.19.
- 5207; 1 July 2026; 30 September 2026; 351.94.
- 8814; 1 July 2026; 5 September 2026; 166.20.
- 2290; 1 July 2026; 30 September 2026; 196.05.

**Draft reports** (what each draft shows)

- R-101, Marlowe. Recipients: A. Marlowe, J. Marlowe. Period: 1 July 2026 to 30 September 2026. Accounts: 4410 412,380.55; 7782 188,206.10; 3305 96,450.00. Household total 697,036.65. Fees: 4410 1,030.95; 7782 470.52; 3305 214.13; fee total 1,715.60. Sections present: all six.
- R-102, Pendry. Recipients: R. Pendry, S. Pendry. Period: 1 April 2026 to 30 June 2026. Accounts: 1156 305,118.40; 6643 24,950.00. Household total 330,068.40. Fees: 1156 762.80; 6643 31.19; fee total 793.99. Sections present: Cover and recipients; Account summary; Allocation; Fees; Disclosures.
- R-103, Quillon. Recipients: T. Quillon and V. Quillon. Period: 1 July 2026 to 30 September 2026. Accounts: 5207 140,775.30; 8814 0.00 (noted as closed 5 September 2026). Household total 141,775.30. Fees: 5207 351.94; 8814 166.20; fee total 518.14. Sections present: all six, but the Disclosures page reads "[to be added]".
- R-104, Ashgrove. Recipients: L. Ashgrove. Period: 1 July 2026 to 30 September 2026. Accounts: 2290 78,420.75. Household total 78,420.75. Fees: 2290 196.05; fee total 196.05. Sections present: all six.

## What comes out

```
CLIENT REPORT CHECK LOG: Q3 2026 batch, 1 July 2026 to 30 September 2026

Prepared for: the reporting lead. Checked 4 reports against 9 custodian statements, 9 billing records and the account inventory for 4 households.
Release is approved by the adviser and the designated reviewer. This log releases and sends nothing and comments on no performance.

Summary: 4 reports. Hold: 2 (R-101, R-103). Differences to correct: 1 (R-102). No differences found: 1 (R-104). Differences logged: 7.

REPORT LOG

R-101, Marlowe household. Status: HOLD (membership difference).
- Recipients: A. Marlowe, J. Marlowe. Match the inventory.
- Membership: 3 of 4 accounts open at any time in the period are on the report. Account 9021 is not on it. See D-1.
- Period: 1 July 2026 to 30 September 2026. Matches the batch.
- Totals: 4410, 7782 and 3305 match their statements. Household total 697,036.65 equals the three accounts shown; the four statements total 948,366.90; difference -251,330.25, which is the value of account 9021 (see D-1).
- Fees: 4410 and 7782 match billing. 3305 does not. See D-2. Fee total 1,715.60 against 2,370.93 in billing; difference -655.33, which is 628.33 for account 9021 (D-1) and 27.00 on account 3305 (D-2).
- Sections: all six present.
- Differences: D-1, D-2.

R-102, Pendry household. Status: DIFFERENCES TO CORRECT.
- Recipients: R. Pendry, S. Pendry. Match the inventory.
- Membership: 2 of 2 accounts open at any time in the period are on the report. 6643 opened on 12 August 2026.
- Period: 1 April 2026 to 30 June 2026. Does not match the batch. See D-3.
- Totals: 1156 and 6643 match their statements. Household total 330,068.40 equals the two accounts and the two statements.
- Fees: 762.80 and 31.19 match billing. Fee total 793.99 equals the billing records.
- Sections: Activity is missing. See D-4.
- Differences: D-3, D-4.

R-103, Quillon household. Status: HOLD (recipient difference; unexplained total difference).
- Recipients: T. Quillon and V. Quillon. V. Quillon is not on the inventory. See D-5.
- Membership: 2 of 2 accounts open at any time in the period are on the report. 8814 closed on 5 September 2026 and shows 0.00 with the closing noted, as the statement does.
- Period: 1 July 2026 to 30 September 2026. Matches the batch.
- Totals: 5207 and 8814 match their statements. Household total 141,775.30 against 140,775.30 from both the accounts and the statements; difference +1,000.00. See D-6.
- Fees: 351.94 and 166.20 match billing. Fee total 518.14 equals the billing records.
- Sections: Disclosures is present but unfinished. See D-7.
- Differences: D-5, D-6, D-7.

R-104, Ashgrove household. Status: NO DIFFERENCES FOUND.
- Recipients: L. Ashgrove. Match the inventory.
- Membership: 1 of 1 account open at any time in the period is on the report.
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

Counts: 9 accounts in the inventory and 9 statements and 9 billing records; 4 reports; 7 differences.
