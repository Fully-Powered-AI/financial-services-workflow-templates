# Settlement exception worklist: an invented example

*Illustrative example with invented data.* The firm, the custodian, the counterparties, the securities, every row and every figure below are invented. Quillon Row Capital is an invented investment firm. Its operations lead runs the worklist on Thursday 5 November 2026, after Custodian X's settlement report arrives. People are referred to by role, counterparties by letter and securities by code.

The inputs come first, in full, so the template can be run on them. The worklist follows.

## The inputs

### 1. Settings

```
Custodian: Custodian X.
Report date: 2026-11-05 (Thursday). Prepared: Thursday 5 November 2026.
Runs it: trade-support analyst. Validates and assigns: operations lead.
Exception statuses: Unmatched, Failed.
Age bands: due today (0), 1 to 2, 3 to 5, over 5 business days.
Owner roles: Trade support, Custody operations, Finance.
Authorized to verify an instruction change and to approve any instruction
or cash movement: authorized staff named by the operations lead.
(No column map given.)
```

### 2. Trade blotter export

```
Trade ID,Trade date,Settlement date,Market,Side,Security ID,Quantity,Price,Currency,Settlement amount,Counterparty,Instruction ref
T-1001,2026-10-27,2026-10-29,MKT-1,Buy,SEC-A1,1000,25.40,USD,25400.00,Counterparty A,INS-A-USD
T-1002,2026-10-28,2026-10-30,MKT-1,Sell,SEC-B2,500,80.10,USD,40050.00,Counterparty B,INS-B-USD
T-1003,2026-10-28,2026-10-30,MKT-2,Buy,SEC-C3,2000,12.50,EUR,25000.00,Counterparty C,INS-C-EUR
T-1004,2026-11-02,2026-11-04,MKT-1,Buy,SEC-D4,300,150.00,USD,45000.00,Counterparty A,INS-A-USD
T-1005,2026-11-02,2026-11-04,MKT-2,Sell,SEC-E5,4000,6.25,EUR,25000.00,Counterparty D,INS-D-EUR
T-1006,2026-11-03,2026-11-05,MKT-1,Buy,SEC-F6,100,410.00,USD,41000.00,Counterparty B,INS-B-USD
T-1007,2026-10-28,2026-10-30,MKT-1,Sell,SEC-G7,1500,9.80,USD,14700.00,Counterparty C,INS-C-USD
T-1008,2026-11-03,2026-11-05,MKT-1,Buy,SEC-H8,50,220.00,USD,11000.00,Counterparty A,INS-A-USD
```

### 3. Confirmation report

```
Trade ID,Confirmation status,Confirmation date,Quantity,Price,Settlement amount
T-1001,Confirmed,2026-10-27,1000,25.40,25400.00
T-1002,Confirmed,2026-10-28,500,80.10,40050.00
T-1003,Confirmed,2026-10-30,2000,12.50,25000.00
T-1004,Unconfirmed,,,,
T-1005,Confirmed,2026-11-02,4000,6.25,25000.00
T-1006,Disputed,2026-11-03,100,410.50,41050.00
T-1008,Confirmed,2026-11-03,50,220.00,11000.00
```

### 4. Custodian settlement report, Custodian X

```
Custodian ref,Trade ID,Settlement date,Security ID,Quantity,Settlement amount,Currency,Status,Reason,Instruction ref
C-9001,T-1001,2026-10-29,SEC-A1,1000,25400.00,USD,Failed,Counterparty has not delivered,INS-A-USD
C-9002,T-1002,2026-10-30,SEC-B2,500,40050.00,USD,Unmatched,No matching instruction from counterparty,INS-B-USD
C-9003,T-1003,2026-10-30,SEC-C3,2000,25250.00,EUR,Unmatched,Cash amount mismatch,INS-C-EUR
C-9004,T-1004,2026-11-04,SEC-D4,300,45000.00,USD,Unmatched,Counterparty instruction not received,INS-A-USD
C-9005,T-1005,2026-11-05,SEC-E5,4000,25000.00,EUR,Unmatched,Settlement date mismatch,INS-D-EUR
C-9006,T-1006,2026-11-05,SEC-F6,100,41000.00,USD,Unmatched,Price mismatch,INS-B-USD
C-9008,T-1008,2026-11-05,SEC-H8,50,11000.00,USD,Settled,,INS-A-USD
C-9009,,2026-11-02,SEC-J9,700,18900.00,USD,Unmatched,No trade reference,INS-A-USD
```

### 5. Verified instruction records

```
Instruction ref,Counterparty,Currency,Status,Verified date
INS-A-USD,Counterparty A,USD,Verified,2026-06-15
INS-B-USD,Counterparty B,USD,Verified,2026-07-02
INS-C-EUR,Counterparty C,EUR,Change received - not verified,
INS-D-EUR,Counterparty D,EUR,Verified,2026-05-20
```

### 6. Market calendar (closed days)

```
Market,Closed date
MKT-2,2026-11-02
```

(MKT-1 has no closed days supplied, so only weekends are skipped for it.)

## The worklist

```
SETTLEMENT EXCEPTION WORKLIST: Custodian X, report date 2026-11-05

For: operations lead. Prepared by: trade-support analyst on 5 November 2026.
Sources: trade blotter 8 rows; confirmation report 7 rows; custodian report 8 rows; verified instructions 4 rows; market calendar 1 closed date.
Settings used: exception statuses Unmatched, Failed; age bands due today, 1 to 2, 3 to 5, over 5 business days; owner roles Trade support, Custody operations, Finance; weekends skipped, plus the closed dates supplied. Defaults used: the default owner table (the settings name the owner roles but give no table).

SUMMARY
Exceptions: 8 (7 linked to a trade, 1 not linked).
By age: Due today 1. 1 to 2 business days 2. 3 to 5 business days 4. Over 5 business days 0. Not yet due 0. Not aged 1.
By proposed owner: Custody operations 4; Trade support 4; Finance 0.
Trade value by currency (blotter amounts, linked trades only, not converted): USD 166,150.00 (5 trades); EUR 50,000.00 (2 trades).
Left off: 1 custodian row with a status outside the exception list (Settled 1).

WORKLIST, oldest first
1. T-1001 | Buy 1,000 SEC-A1 at 25.40 USD | USD 25,400.00 | Counterparty A | MKT-1
   Due 2026-10-29. Age: 5 business days (3 to 5).
   Confirmation: Confirmed 2026-10-27. Agrees with the blotter.
   Custodian: C-9001, Failed, reason "Counterparty has not delivered". Agrees with the blotter.
   Instruction: INS-A-USD, Verified 2026-06-15. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: None.
   Proposed owner: Custody operations. Also involves: none. Because: rule 4, terms agree, the trade is confirmed and the instruction is verified, so the open question is the custodian's reason.
   Operations lead: validate the break; confirm or change the owner.

2. T-1002 | Sell 500 SEC-B2 at 80.10 USD | USD 40,050.00 | Counterparty B | MKT-1
   Due 2026-10-30. Age: 4 business days (3 to 5).
   Confirmation: Confirmed 2026-10-28. Agrees with the blotter.
   Custodian: C-9002, Unmatched, reason "No matching instruction from counterparty". Agrees with the blotter.
   Instruction: INS-B-USD, Verified 2026-07-02. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: None.
   Proposed owner: Custody operations. Also involves: none. Because: rule 4, terms agree, the trade is confirmed and the instruction is verified, so the open question is the custodian's reason.
   Operations lead: validate the break; confirm or change the owner.

3. T-1007 | Sell 1,500 SEC-G7 at 9.80 USD | USD 14,700.00 | Counterparty C | MKT-1
   Due 2026-10-30. Age: 4 business days (3 to 5).
   Confirmation: no confirmation row supplied.
   Custodian: no row on the custodian report.
   Instruction: INS-C-USD, not in the verified instruction records.
   Flags: confirmation missing; no verified instruction record.
   Proposed owner: Custody operations. Also involves: Trade support. Because: rule 1, the instruction on the trade has no verified record; rule 2 also applies, because the trade has no confirmation row.
   Operations lead: validate the break; confirm or change the owner.

4. T-1003 | Buy 2,000 SEC-C3 at 12.50 EUR | EUR 25,000.00 | Counterparty C | MKT-2
   Due 2026-10-30. Age: 3 business days (3 to 5). 2026-11-02 is a closed day for MKT-2 and is not counted.
   Confirmation: Confirmed 2026-10-30. Agrees with the blotter.
   Custodian: C-9003, Unmatched, reason "Cash amount mismatch". Settlement amount EUR 25,250.00 against EUR 25,000.00 on the blotter: custodian higher by EUR 250.00. Security, quantity and date agree.
   Instruction: INS-C-EUR, "Change received - not verified", no verified date supplied. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: instruction change not verified; cash difference EUR 250.00.
   Proposed owner: Custody operations. Also involves: Finance. Because: rule 1, the instruction is not verified, which comes before every other kind. Rule 3 also applies: the cash difference is Finance's. Authorized staff verify the change; this worklist does not act on it.
   Operations lead: validate the break; confirm or change the owner.

5. T-1004 | Buy 300 SEC-D4 at 150.00 USD | USD 45,000.00 | Counterparty A | MKT-1
   Due 2026-11-04. Age: 1 business day (1 to 2).
   Confirmation: Unconfirmed, no date and no terms supplied.
   Custodian: C-9004, Unmatched, reason "Counterparty instruction not received". Agrees with the blotter.
   Instruction: INS-A-USD, Verified 2026-06-15. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: confirmation missing.
   Proposed owner: Trade support. Also involves: none. Because: rule 2, the trade is not confirmed.
   Operations lead: validate the break; confirm or change the owner.

6. T-1005 | Sell 4,000 SEC-E5 at 6.25 EUR | EUR 25,000.00 | Counterparty D | MKT-2
   Due 2026-11-04. Age: 1 business day (1 to 2), counted from the blotter date.
   Confirmation: Confirmed 2026-11-02. Agrees with the blotter.
   Custodian: C-9005, Unmatched, reason "Settlement date mismatch". Settlement date 2026-11-05 against 2026-11-04 on the blotter. Security, quantity and amount agree.
   Instruction: INS-D-EUR, Verified 2026-05-20. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: conflicting dates (blotter 2026-11-04, custodian 2026-11-05).
   Proposed owner: Trade support. Also involves: none. Because: rule 2, the two records disagree on the settlement date.
   Operations lead: validate the break; confirm or change the owner.

7. T-1006 | Buy 100 SEC-F6 at 410.00 USD | USD 41,000.00 | Counterparty B | MKT-1
   Due 2026-11-05. Age: 0 business days (due today).
   Confirmation: Disputed 2026-11-03. Confirmed price 410.50 against 410.00 on the blotter (+0.50); confirmed amount USD 41,050.00 against USD 41,000.00 (+50.00). Quantity agrees.
   Custodian: C-9006, Unmatched, reason "Price mismatch". Agrees with the blotter.
   Instruction: INS-B-USD, Verified 2026-07-02. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: confirmation disputed.
   Proposed owner: Trade support. Also involves: none. Because: rule 2, the confirmation is disputed and its price differs from the firm's record.
   Operations lead: validate the break; confirm or change the owner.

NOT LINKED TO A TRADE
C-9009 | Custodian X, Unmatched, reason "No trade reference" | 2026-11-02 | SEC-J9, 700, USD 18,900.00 | instruction ref INS-A-USD
   Age: not counted, because without a trade there is no market.
   Flags: missing identifier. Not matched to any trade by amount or security.
   Proposed owner: Trade support. Because: rule 2, the custodian line carries no trade reference.

QUESTIONS
For Custody operations: T-1003 (Buy 2,000 SEC-C3, due 2026-10-30): instruction INS-C-EUR for Counterparty C reads "Change received - not verified" with no verified date. Have authorized staff verified this change, and on what date?
For Finance: T-1003: Custodian X shows EUR 25,250.00 against EUR 25,000.00 on the blotter and the confirmation, a gap of EUR 250.00. What is the EUR 250.00?
For Custody operations: T-1007 (Sell 1,500 SEC-G7, USD 14,700.00, due 2026-10-30): the blotter's instruction ref INS-C-USD is not in the verified instruction records. Is there a verified record under that reference, and what are its status and date?
For Custody operations: T-1007 has no row on the Custodian X report of 2026-11-05. Does Custodian X hold any record of this trade?
For Trade support: T-1007 has no confirmation row. Is there a confirmation for this trade, and what are its status, date and terms?
For Trade support: T-1004 (Buy 300 SEC-D4, USD 45,000.00, due 2026-11-04) shows status Unconfirmed with no terms. Has a confirmation been received, and with what terms?
For Trade support: T-1005 (Sell 4,000 SEC-E5): the blotter settlement date is 2026-11-04 and Custodian X shows 2026-11-05. Which settlement date was agreed with Counterparty D?
For Trade support: T-1006 (Buy 100 SEC-F6): the confirmation, status Disputed, shows price 410.50 and amount USD 41,050.00; the blotter shows 410.00 and USD 41,000.00. Which price was agreed?
For Trade support: custodian line C-9009 (SEC-J9, 700, USD 18,900.00, 2026-11-02, instruction ref INS-A-USD) has no Trade ID. Which trade, if any, does it belong to?

SIGN-OFF
Prepared by: trade-support analyst, 5 November 2026.
Breaks validated and owners assigned by: ____________________  Date: ____________

Prepared for review. Nothing sent, changed or approved; no one contacted.
```

How the figures trace: the blotter has 8 trades, and 7 of them are exceptions (T-1008 is Settled at the custodian, so it is left off). The custodian report has 8 rows: 6 linked exceptions, 1 Settled and 1 not linked. T-1007 is the seventh linked exception, found only on the blotter. Ages count business days after the due date up to and including 2026-11-05. T-1001, due Thursday 29 October: 30 Oct, 2, 3, 4 and 5 Nov, which is 5. T-1002 and T-1007, due Friday 30 October: 2, 3, 4 and 5 Nov, which is 4. T-1003, due Friday 30 October in MKT-2: 2 Nov is closed, so 3, 4 and 5 Nov, which is 3. T-1004 and T-1005, due 4 November: 5 Nov, which is 1. T-1006 is due on the report date, so 0. Sorting is by age, then Trade ID. The USD total is 25,400.00 + 40,050.00 + 45,000.00 + 41,000.00 + 14,700.00 = 166,150.00 (T-1001, T-1002, T-1004, T-1006, T-1007); the EUR total is 25,000.00 + 25,000.00 = 50,000.00 (T-1003, T-1005). The USD 18,900.00 on C-9009 is left out of the totals because it has no trade. Owners: Custody operations has T-1001, T-1002, T-1003 and T-1007; Trade support has T-1004, T-1005, T-1006 and C-9009. The defaults used are the owner table of step 8, because the settings give roles but no table.
