# Settlement exception worklist: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs are the template's own invented example (Quillon Row Capital, Custodian X, report date 2026-11-05). No client data was used. The assistant did not write the template. It read the template and only the inputs section of `public/example.md` (settings, blotter, confirmation report, custodian report, verified instruction records, market calendar), followed the instruction block and the output format, and only afterwards read the published example's output to compare. It was run once, by hand, with no retries.

## Inputs used

The six inputs in `public/example.md` under "The inputs": settings, trade blotter (8 rows), confirmation report (7 rows), custodian settlement report (8 rows), verified instruction records (4 rows) and market calendar (1 closed date). No column map was given.

## What came out

```
SETTLEMENT EXCEPTION WORKLIST: Custodian X, report date 2026-11-05

For: operations lead. Prepared by: trade-support analyst on 2026-11-05.
Sources: trade blotter 8 rows; confirmation report 7 rows; custodian report 8 rows; verified instructions 4 rows; market calendar 1 closed date.
Settings used: exception statuses Unmatched, Failed; age bands due today, 1 to 2, 3 to 5, over 5 business days; owner roles Trade support, Custody operations, Finance; weekends skipped, plus MKT-2 closed 2026-11-02 (MKT-1 has no closed dates supplied, so only weekends are skipped for it). Defaults used: the default owner table (the settings name the roles but give no table).

SUMMARY
Exceptions: 8 (7 linked to a trade, 1 not linked).
By age: Due today 1. 1 to 2 business days 2. 3 to 5 business days 4. Over 5 business days 0. Not yet due 0. Not aged 1.
By proposed owner: Custody operations 4; Trade support 4; Finance 0.
Trade value by currency (blotter amounts, linked trades only, not converted): USD 166,150.00 (5 trades); EUR 50,000.00 (2 trades).
Left off: 1 custodian row with a status outside the exception list (Settled 1).

WORKLIST, oldest first
1. T-1001 | Buy 1,000 SEC-A1 at 25.40 USD | USD 25,400.00 | Counterparty A | MKT-1
   Due 2026-10-29. Age: 5 business days (3 to 5). Nothing skipped.
   Confirmation: Confirmed 2026-10-27. Agrees with the blotter.
   Custodian: C-9001, Failed, reason "Counterparty has not delivered". Agrees with the blotter.
   Instruction: INS-A-USD, Verified 2026-06-15. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: None.
   Proposed owner: Custody operations. Also involves: none. Because: rule 4, nothing in kinds 1 to 3 applies; the open question is the custodian's own reason.
   Operations lead: validate the break; confirm or change the owner.

2. T-1002 | Sell 500 SEC-B2 at 80.10 USD | USD 40,050.00 | Counterparty B | MKT-1
   Due 2026-10-30. Age: 4 business days (3 to 5). Nothing skipped.
   Confirmation: Confirmed 2026-10-28. Agrees with the blotter.
   Custodian: C-9002, Unmatched, reason "No matching instruction from counterparty". Agrees with the blotter.
   Instruction: INS-B-USD, Verified 2026-07-02. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: None.
   Proposed owner: Custody operations. Also involves: none. Because: rule 4, nothing in kinds 1 to 3 applies; the open question is the custodian's own reason.
   Operations lead: validate the break; confirm or change the owner.

3. T-1007 | Sell 1,500 SEC-G7 at 9.80 USD | USD 14,700.00 | Counterparty C | MKT-1
   Due 2026-10-30. Age: 4 business days (3 to 5). Nothing skipped.
   Confirmation: no confirmation row supplied.
   Custodian: no row on the custodian report.
   Instruction: INS-C-USD, not in the verified instruction records. (INS-C-EUR is a record for the same counterparty in another currency and is not used.)
   Flags: confirmation missing; no verified instruction record.
   Proposed owner: Custody operations. Also involves: Trade support. Because: rule 1, no verified instruction record; rule 2 also applies (confirmation missing).
   Operations lead: validate the break; confirm or change the owner.

4. T-1003 | Buy 2,000 SEC-C3 at 12.50 EUR | EUR 25,000.00 | Counterparty C | MKT-2
   Due 2026-10-30. Age: 3 business days (3 to 5). Closed day skipped: 2026-11-02 (MKT-2).
   Confirmation: Confirmed 2026-10-30. Agrees with the blotter.
   Custodian: C-9003, Unmatched, reason "Cash amount mismatch". Settlement amount EUR 25,250.00 against EUR 25,000.00 on the blotter: custodian higher by EUR 250.00. Security, quantity, currency and date agree.
   Instruction: INS-C-EUR, "Change received - not verified", no verified date supplied. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: instruction change not verified; cash difference EUR 250.00.
   Proposed owner: Custody operations. Also involves: Finance. Because: rule 1, instruction not verified; rule 3 also applies (amount difference with agreeing terms).
   Operations lead: validate the break; confirm or change the owner.

5. T-1004 | Buy 300 SEC-D4 at 150.00 USD | USD 45,000.00 | Counterparty A | MKT-1
   Due 2026-11-04. Age: 1 business day (1 to 2). Nothing skipped.
   Confirmation: Unconfirmed, date not supplied; quantity, price and amount not supplied.
   Custodian: C-9004, Unmatched, reason "Counterparty instruction not received". Agrees with the blotter.
   Instruction: INS-A-USD, Verified 2026-06-15. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: confirmation missing (status as supplied: Unconfirmed).
   Proposed owner: Trade support. Also involves: none. Because: rule 2, confirmation missing.
   Operations lead: validate the break; confirm or change the owner.

6. T-1005 | Sell 4,000 SEC-E5 at 6.25 EUR | EUR 25,000.00 | Counterparty D | MKT-2
   Due 2026-11-04 (blotter); the custodian shows 2026-11-05. Age: 1 business day (1 to 2), counted from the blotter date. Nothing skipped.
   Confirmation: Confirmed 2026-11-02. Agrees with the blotter.
   Custodian: C-9005, Unmatched, reason "Settlement date mismatch". Settlement date 2026-11-05 against 2026-11-04 on the blotter. Security, quantity, amount and currency agree.
   Instruction: INS-D-EUR, Verified 2026-05-20. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: conflicting dates (blotter 2026-11-04, custodian 2026-11-05).
   Proposed owner: Trade support. Also involves: none. Because: rule 2, conflicting dates.
   Operations lead: validate the break; confirm or change the owner.

7. T-1006 | Buy 100 SEC-F6 at 410.00 USD | USD 41,000.00 | Counterparty B | MKT-1
   Due 2026-11-05. Age: 0 business days (due today). Nothing skipped.
   Confirmation: Disputed 2026-11-03. Price 410.50 against 410.00 on the blotter (+0.50); amount USD 41,050.00 against USD 41,000.00 (+50.00). Quantity agrees.
   Custodian: C-9006, Unmatched, reason "Price mismatch". Agrees with the blotter.
   Instruction: INS-B-USD, Verified 2026-07-02. Counterparty and currency agree with the trade; the custodian holds the same reference.
   Flags: confirmation disputed.
   Proposed owner: Trade support. Also involves: none. Because: rule 2, confirmation disputed.
   Operations lead: validate the break; confirm or change the owner.

NOT LINKED TO A TRADE
C-9009 | Custodian X, Unmatched, reason "No trade reference" | 2026-11-02 | SEC-J9, 700, USD 18,900.00 | instruction ref INS-A-USD
   Age: not counted, because without a trade there is no market.
   Flags: missing identifier. Not matched to any trade by amount or security.
   Proposed owner: Trade support. Because: rule 2, no trade reference.

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
Prepared by: trade-support analyst, 2026-11-05.
Breaks validated and owners assigned by: ____________________  Date: ____________

Prepared for review. Nothing sent, changed or approved; no one contacted.
```

## What was observed

Whether every required part was produced. Yes: Sources line, settings and defaults line, summary, an ordered worklist of seven items, the "Not linked to a trade" section, questions, sign-off and the closing line. Nothing in the inputs triggered a stop condition: no required file was missing, every heading matched, there was one custodian, no duplicate Trade ID and all dates were YYYY-MM-DD.

Checks against the reviewer checklist. All ten pass on this output. The custodian report's eight rows are accounted for exactly once (six linked exceptions, one not linked, one Settled and left off); the one blotter trade with no custodian row and due before the report date (T-1007) is on the worklist; the one blotter trade not on the worklist (T-1008) is Settled at the custodian. Ages were counted by hand, with 2026-11-02 skipped for MKT-2 on T-1003 only. The totals add up (USD 25,400.00 + 40,050.00 + 45,000.00 + 41,000.00 + 14,700.00 = 166,150.00; EUR 25,000.00 + 25,000.00 = 50,000.00) and nothing was converted. No cause is stated for any break and no questions recommend an action.

Differences from the published example output.
- Numbers, counts, order, ages, owners, "Also involves" roles and summary are the same as the example's. The differences are in wording and detail only.
- Defaults line: the example says "Defaults used: none". The settings name three owner roles but give no owner table, so this run listed the default owner table as a default used.
- T-1006 flag: this run wrote "confirmation disputed", as the template says to when the status says so. The example wrote "confirmation differs from the blotter on price", which the template reserves for a Confirmed row.
- T-1007 flags: the example lists "not on the custodian report" as a flag. The template defines no such flag, and this run left it to the "Custodian:" line.
- Rule text: the example gives a plain-words reason for each owner; this run named the rule number from step 8.
- Questions: the example has six, merging several facts into one question and sending two to Custody operations. This run has nine, one per fact and role, and sends the cash gap to Finance and the missing confirmation on T-1007 to Trade support. The example asks "was the trade sent to the custodian?" and "has a confirmation been requested?", which ask about actions taken rather than a recorded fact; this run asked for records instead.
- Instruction line detail: this run also stated "no verified date supplied" for INS-C-EUR and that counterparty and currency agree with the trade.
- Prepared date: the example prints "5 November 2026"; this run printed 2026-11-05, the form the template reads dates in. The settings give 5 November as the prepared date, so it is the report date and not the day this trial was run.

Facts in either output that are not in the inputs.
- The example's question about T-1004 says the trade is "unconfirmed by Counterparty A". The inputs say only "Unconfirmed"; they do not say who has not confirmed.
- The example's "was the trade sent to the custodian?" supposes something the inputs do not say.
- This run's output adds nothing beyond the inputs. Its one inference is that T-1007 counts as "linked to a trade" in the summary although it has no custodian row (see below).

Where the template was ambiguous or needed a guess.
1. "Linked" is defined for custodian rows. T-1007 has no custodian row, yet the summary says "linked to a trade" and the trade value uses "linked trades only". This run counted T-1007 as linked because it is a blotter trade (7 linked, 1 not linked, USD total includes it). The template never says so.
2. Blank cells on the confirmation row for T-1004. The template says a blank is "not supplied", never zero, but does not say whether a non-Confirmed row's blank terms are to be compared with the blotter. This run did not compare and wrote "not supplied".
3. The status "Disputed" and flags. Step 4 names "confirmation disputed" for that status and "confirmation differs from the blotter" for a Confirmed row. T-1006 is Disputed with a different price, so only the first applies, but the template does not say whether to also flag the price difference. This run showed the gap on the Confirmation line.
4. Defaults. The settings listed owner roles but no owner table. The template says to use the step 8 table if none, and to list defaults used; whether naming roles counts as supplying a table is a judgement call.
5. Questions for the unlinked line. Step 10 says one per "item whose flags need an answer". It is unclear whether the line under "Not linked to a trade" is an item. This run asked one question for C-9009; the example did too.
6. Ties in the owner rule. Step 8 says the owner is the first kind that applies. For T-1003 the cash difference (rule 3) and the unverified instruction (rule 1) both apply, and the template resolves this clearly. For C-9009 there is no trade, so the instruction on the line cannot be compared with anything; the template does not say whether the line's own instruction ref should be checked against the records. This run did not.
7. Format placeholders. The output format shows "[Closed days skipped, or nothing.]". This run wrote "Nothing skipped." The wording is left to the reader.
8. Summary placeholders do not say whether a role with no items (Finance 0) is listed. This run listed it.
9. Date of preparation. The format has "Prepared by: [role] on [date]". It is not stated whether the date is the report date or the day the assistant runs. This run used the date in the settings.
10. The "Instruction" line format in the worklist has a fixed sentence for the clean case but no wording for a record that exists with no verified date (INS-C-EUR) or for a reference with no record at all. This run improvised.

Nothing in the instructions told the assistant to stop on this input. Nothing asked for an action outside the template's limits.

Shortcomings of this trial. One run, by one model, hand-computed, on a small invented set of eight trades. It shows the instructions can be followed to a complete output on these inputs. It does not show they hold on a real blotter, with unusual column names, large volumes or other markets. It was run in Claude Code, not in a chat product with a pasted instruction block. Nothing here tests the template in a client environment.

- After the trial, the findings were answered in the template and the example, and the changes were not run again: the published example now matches this run's wording for the T-1006 flag ("confirmation disputed"), the T-1007 flags, the defaults line (the default owner table) and the questions (one fact per question, each to the role that owns that kind of break); the template now says that a blotter-only exception counts as linked, how a non-Confirmed row with blank terms and a Disputed row with different terms are written, what to print for an instruction that is not verified or has no record, how to treat a blank or unlinked instruction ref, that every role is shown in the owner counts, that the prepared date is the date in the settings, and that each owner reason carries the rule number. The recorded output above is unchanged.
- After the independent review, further small edits were made and not run again: the instruction block gained one line each for the "two rows", "conflicting dates", "instruction reference differs" and "currency differs" flags and for an unlinked line not being aged; questions are now one per flag or fact, to the role that owns that kind of break, and a trade with no custodian row or an unlinked custodian line gets one; and the format now says to print nothing after the age when no closed day is skipped (this run wrote "Nothing skipped." and that recorded output is unchanged). The published example's T-1003 and T-1007 instruction lines were aligned with the output format; the T-1003 line now matches this run's wording.
