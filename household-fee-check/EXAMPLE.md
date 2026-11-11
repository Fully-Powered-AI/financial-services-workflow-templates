# Household fee check: an invented example

*Illustrative example with invented data.* The firm, the households, the accounts, the approvers, every rate and every figure below are invented. The firm is an invented advisory business, Advisory Firm A. Its billing owner runs the fee check for the third quarter of 2026 on 6 October 2026, and an approver, Approver A, releases any charge or credit. Households and accounts are referred to by letter and code.

The inputs come first, in full, so the template can be run on them. The fee check follows.

## The inputs

### 1. Settings (typed by the billing owner)

```
Firm: Advisory Firm A
Fee review date: 2026-10-06
Fee period: 2026-07-01 to 2026-09-30 (92 days)
Currency: USD
Debit window: 2026-10-01 to 2026-10-05
Stale valuation limit: 5 days before period end
Proration rule: none
Tolerance: 0.00
Billing owner: Billing owner A
Approver: Approver A
```

### 2. Valuation file

```
account_id,valuation_date,market_value,currency
A-101,2026-09-30,640000.00,USD
A-102,2026-09-30,410000.00,USD
A-103,2026-09-30,150100.00,USD
B-201,2026-09-30,820000.00,USD
B-202,2026-09-30,95000.00,USD
C-301,2026-09-18,300000.00,USD
D-401,2026-09-30,500000.00,USD
E-502,2026-09-30,260000.00,USD
F-601,2026-09-30,410000.00,USD
```

### 3. Household links

```
household_id,household_name,account_id
H-1,Household A,A-101
H-1,Household A,A-102
H-1,Household A,A-103
H-2,Household B,B-201
H-2,Household B,B-202
H-3,Household C,C-301
H-4,Household D,D-401
H-5,Household E,E-501
H-5,Household E,E-502
H-6,Household F,F-601
```

### 4. Fee terms

```
household_id,schedule_id,basis,periods_per_year,effective_from,effective_to
H-1,S-1,household,4,2024-01-01,
H-2,S-3,account,4,2023-01-01,
H-3,S-2,account,4,2022-01-01,
H-4,S-2,account,4,2026-08-15,
H-5,S-2,account,4,2022-01-01,
H-6,S-2,account,4,2023-01-01,
```

### 5. Fee schedules

```
schedule_id,tier_floor,tier_ceiling,annual_rate_pct
S-1,0,1000000,1.00
S-1,1000000,,0.80
S-2,0,,0.90
S-3,0,500000,1.20
S-3,500000,,0.90
```

### 6. Waivers and discounts

```
waiver_id,household_id,account_id,type,value,valid_from,valid_to,approved_by,approved_on
W-1,H-2,B-202,waive,,2025-01-01,,Approver A,2025-01-10
W-2,H-6,F-601,rate_override_pct,0.75,2026-07-01,,,
W-3,H-1,,discount_pct,10,2025-01-01,2025-12-31,Approver A,2024-12-18
```

### 7. Account dates

```
account_id,open_date,close_date
A-101,2019-03-04,
A-102,2021-06-14,
A-103,2023-02-20,
B-201,2020-01-09,
B-202,2022-05-16,
C-301,2018-11-02,
D-401,2026-08-15,
E-501,2017-04-03,2026-08-20
E-502,2024-09-12,
F-601,2021-10-25,
```

### 8. Custodian debits

```
debit_id,account_id,debit_date,amount,currency
D-1,A-101,2026-10-01,1546.64,USD
D-2,A-102,2026-10-01,990.28,USD
D-3,A-103,2026-10-01,362.74,USD
D-4,B-201,2026-10-01,2220.00,USD
D-5,B-202,2026-10-01,285.00,USD
D-6,C-301,2026-10-02,675.00,USD
D-7,D-401,2026-10-02,1125.00,USD
D-8,E-501,2026-10-02,640.00,USD
D-9,E-502,2026-10-02,585.00,USD
D-10,F-601,2026-10-02,768.75,USD
D-11,Z-999,2026-10-02,50.00,USD
D-0,A-101,2026-07-03,2800.00,USD
```

## The fee check

```
FEE CHECK: Advisory Firm A, fee period 2026-07-01 to 2026-09-30
Fee review date 2026-10-06. Debits compared: 2026-10-01 to 2026-10-05. Prepared for Billing owner A; approver Approver A.
Status: DRAFT. Not ready to release: 4 accounts held for review, 2 differences over tolerance and 1 debit on an unlisted account.
Inputs not supplied: none.

1. SETTINGS USED
Currency USD. Period 92 days. Stale valuation limit 5 days, so a valuation dated before 2026-09-25 is stale. Proration rule: none. Tolerance 0.00. Rounding: to the cent, half up.
Accounts: 10 linked to a household; 9 valued; 6 with a draft line; 4 held for review; 0 excluded (closed before the period).
Debits: 11 inside the window; 1 outside it (D-0, A-101, 2026-07-03, 2,800.00), not compared.
Waivers not applied because they were not in force on 2026-09-30: W-2 (Household F, rate_override_pct, unknown type, no approver or approval date); W-3 (Household A, 10 percent discount, ended 2025-12-31).

2. DRAFT INVOICE LINES
Household A (H-1), schedule S-1, basis household, 4 periods a year.
Household value 1,200,100.00. Fee: (1,000,000.00 at 1.00% + 200,100.00 at 0.80%) / 4 = 2,900.20.
Line 1: A-101, value 640,000.00 on 2026-09-30; share of fee 1,546.64; waiver none; draft fee 1,546.64.
Line 2: A-102, value 410,000.00 on 2026-09-30; share of fee 990.82; waiver none; draft fee 990.82.
Line 3: A-103, value 150,100.00 on 2026-09-30; share of fee 362.74; waiver none; draft fee 362.74.
Household total 2,900.20.

Household B (H-2), schedule S-3, basis account, 4 periods a year.
Line 4: B-201, value 820,000.00 on 2026-09-30; fee before waiver (500,000.00 at 1.20% + 320,000.00 at 0.90%) / 4 = 2,220.00; waiver none; draft fee 2,220.00.
Line 5: B-202, value 95,000.00 on 2026-09-30; fee before waiver (95,000.00 at 1.20%) / 4 = 285.00; waiver W-1 (waive, approved by Approver A on 2025-01-10) -285.00; draft fee 0.00.
Household total 2,220.00.

Household E (H-5), schedule S-2, basis account, 4 periods a year.
Line 6: E-502, value 260,000.00 on 2026-09-30; fee before waiver (260,000.00 at 0.90%) / 4 = 585.00; waiver none; draft fee 585.00.
Household total for drafted lines 585.00. E-501 is held (review item 1).

Draft invoice lines: 6. Total 5,705.20. Waived: 285.00.

3. DIFFERENCES AGAINST CUSTODIAN DEBITS
Difference is the debit minus the draft fee.
- A-101: draft 1,546.64; debit 1,546.64 (D-1); difference 0.00. Matches.
- A-102: draft 990.82; debit 990.28 (D-2); difference -0.54. Debit is lower than the draft.
- A-103: draft 362.74; debit 362.74 (D-3); difference 0.00. Matches.
- B-201: draft 2,220.00; debit 2,220.00 (D-4); difference 0.00. Matches.
- B-202: draft 0.00; debit 285.00 (D-5); difference 285.00. Debit is higher than the draft; it equals the fee before the waiver.
- E-502: draft 585.00; debit 585.00 (D-9); difference 0.00. Matches.
Held accounts, debit recorded and no draft figure to compare: C-301 675.00 (D-6); D-401 1,125.00 (D-7); E-501 640.00 (D-8); F-601 768.75 (D-10).
Debit on an account in no household link: Z-999 50.00 (D-11).
Accounts with a draft line and no debit in the window: none.

4. FOR REVIEW
Review 1. Closed account: E-501 (Household E). Closed 2026-08-20, so it was open for part of the period. No valuation is in the valuation file, so no fee can be worked out. The custodian debited 640.00 (D-8) on 2026-10-02. Question for Billing owner A: was a final fee due for 2026-07-01 to 2026-08-20, and on what value? Approver A decides any charge or credit.
Review 2. Unclear proration: D-401 (Household D). Opened 2026-08-15, which is 47 of the period's 92 days, and the proration rule is none. Reference only, not a draft line: a full-period fee would be (500,000.00 at 0.90%) / 4 = 1,125.00, and the custodian debited 1,125.00 (D-7). Question for Billing owner A: which proration rule applies to an account opened inside the period? Approver A decides any credit.
Review 3. Stale valuation: C-301 (Household C). Valued 2026-09-18, which is 12 days before period end, beyond the 5-day limit. Reference only, not a draft line: at the supplied value the fee would be (300,000.00 at 0.90%) / 4 = 675.00, and the custodian debited 675.00 (D-6). Question for Billing owner A: is a period-end valuation available for C-301, or is the 2026-09-18 value to be used? Approver A decides any charge or credit.
Review 4. Negotiated override: F-601 (Household F). W-2 asks for 0.75, read as an annual rate in percent because its type is unknown, and has no approver and no approval date, so it is not applied. Reference only, not a draft line: at schedule S-2 the fee would be (410,000.00 at 0.90%) / 4 = 922.50; at 0.75 percent it would be 768.75, and the custodian debited 768.75 (D-10). Question for Billing owner A: was the override approved, and by whom? Approver A decides whether it is approved and whether any charge or credit follows.
Differences over tolerance on drafted lines: 2 (A-102 and B-202, section 3).

5. TIE-OUT
Debits inside the window: 9,248.41 = 5,989.66 on accounts with draft lines + 3,208.75 on held accounts + 50.00 on an unlisted account.
Draft fees on drafted lines 5,705.20; debits on the same accounts 5,989.66; net difference 284.46 = -0.54 + 285.00.
Accounts: 6 with draft lines + 4 held + 0 excluded = 10 linked to a household.

6. DECISIONS
For Billing owner A: confirm the rules used in section 1; answer the questions in review items 1 to 4; say whose account Z-999 is (the debit D-11 in section 3); confirm that A-102 and B-202 are real differences.
For Approver A: decide whether any charge or credit follows from the held accounts and from the two differences. Nothing has been debited, invoiced or credited.

Every figure traces to the files supplied. Nothing is debited, invoiced or credited.
```
