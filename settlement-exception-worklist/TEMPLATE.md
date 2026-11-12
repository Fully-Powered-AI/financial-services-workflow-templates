# Settlement exception worklist

Workflow template, version 0.1.0.

## Purpose

Prepare, for one custodian and one report date, the aged worklist of unmatched and failed settlement items: for each, the trade's terms from the firm's blotter, the confirmation status and confirmed terms, the custodian's position, the settlement instruction supplied and whether it is verified, the differences between them, the age in business days and a proposed investigation owner chosen by a stated rule. Custodian lines that cannot be tied to a trade are listed apart, and every gap is written as a question for a named role. The assistant prepares; the operations lead validates each break and assigns the work, and authorized staff approve any instruction or cash movement. The assistant executes no trade, settlement or instruction, rates no counterparty, judges no investment and contacts no one.

## When to use it and when not to

Use it when the custodian's settlement report for the day shows unmatched or failed items. Run it again the next day on the new report to age the same items forward and to see which have cleared.

Do not use it:

- to match a bank statement to the ledger, which is bank reconciliation preparation;
- to review customer invoices and payments, which is receivables exception review;
- to take a payment processor's payout apart, which is payout reconciliation for an online store;
- to decide how to resolve a break, to instruct the custodian, to claim from a counterparty, to move cash or to approve an instruction. Those are for the people named under Roles;
- to assess a counterparty's standing or to say anything about the investment itself;
- when the blotter, the custodian report or the report date is missing.

## Roles

- **Runs it:** the operations lead, or a trade-support analyst for the lead.
- **Validates each break and assigns the investigation:** the operations lead.
- **Investigates:** the role proposed for each item, once the operations lead has confirmed or changed it.
- **Verifies an instruction change and approves any instruction or cash movement:** authorized staff named by the firm. Always people.
- **Contacts the custodian or a counterparty:** a person, never the assistant.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to any trading, custody or accounting system and never asks for a password or a login code. It reads these headings by exact name; the person may supply a column map saying which of their columns holds each one.

1. **Trade blotter export.** Headings: Trade ID, Trade date, Settlement date, Market, Side, Security ID, Quantity, Price, Currency, Settlement amount, Counterparty, Instruction ref. If it is missing, stop. If a heading is not found and no column map covers it, stop and ask which column holds it; never infer a column from its contents.
2. **Confirmation report.** Headings: Trade ID, Confirmation status, Confirmation date, Quantity, Price, Settlement amount. If it is missing, continue and write "confirmation report not supplied" on every item. A trade with no row is "no confirmation row supplied".
3. **Custodian settlement report.** Headings: Custodian ref, Trade ID, Settlement date, Security ID, Quantity, Settlement amount, Currency, Status, Reason, Instruction ref. If it is missing, stop. It must hold one custodian; if it holds more than one, stop and ask.
4. **Verified instruction records.** Headings: Instruction ref, Counterparty, Currency, Status, Verified date. If it is missing, continue and write "verified instruction records not supplied" on every item; no instruction is then treated as verified.
5. **Market calendar.** Headings: Market, Closed date. A market with no row has only weekends skipped, and the sheet says so. If the whole calendar is missing, skip weekends only and say so.
6. **Settings.** The report date; the custodian's name; the statuses that count as exceptions; the age bands; the owner table; who runs it, who validates, who may verify an instruction change and approve movements. If missing, use these defaults and list them: exception statuses Unmatched and Failed; age bands due today (0), 1 to 2, 3 to 5 and over 5 business days; the owner table in step 8. If the report date is missing, stop and ask.

Dates are read as YYYY-MM-DD. If another form is supplied and the order of day and month is not stated, stop and ask. Amounts are read to the cent, quantities as whole numbers or decimals exactly as supplied, and currencies as codes.

## The procedure

1. **Check the inputs.** Confirm one custodian, one report date, and that every heading in step 1 to 5 of Inputs is present. Count the rows of each file for the Sources line. If a Trade ID appears twice on the blotter, stop and ask which row is right. Do not read a blank cell as zero; a blank is "not supplied".
2. **Select the exceptions.** An exception is (a) a custodian row whose Status is one of the exception statuses, or (b) a blotter trade whose settlement date is on or before the report date and which has no row on the custodian report at all. A custodian row with any other status is left off and counted by status in the summary. A trade due after the report date with no custodian row is not an exception.
3. **Link by identifier only.** Tie a custodian row to a blotter trade by Trade ID, and nothing else. A custodian row with a blank Trade ID, or a Trade ID not on the blotter, is not linked: it goes under "Not linked to a trade", and it is never paired by amount, security or date, however close the figures. Tie the confirmation row and the instruction record to the trade by Trade ID and by Instruction ref. If the same Trade ID has two rows on the confirmation or custodian report, show both under the item and add the flag "two rows".
4. **Compare, field by field.** Write each difference with both values and the gap; do not say why it happened.
   - Custodian against blotter: Security ID, Quantity, Settlement amount, Currency, Settlement date.
   - Confirmation against blotter: Quantity, Price, Settlement amount. Only a status of Confirmed counts as confirmed. Any other status, or no row, is flagged "confirmation missing", or "confirmation disputed" if the status says so, using the status as supplied. A Confirmed row whose terms differ from the blotter is flagged "confirmation differs from the blotter". A row with any other status is not compared field by field: its blank terms are written "not supplied", and a Disputed row whose terms differ is flagged "confirmation disputed" only, with the gaps shown on the Confirmation line and no second flag.
   - Instruction: find the blotter's Instruction ref in the verified records. Flag "instruction change not verified" if its Status is anything but Verified, "no verified instruction record" if it is absent, "instruction reference differs" if the custodian row holds a different reference, and "instruction record differs from the trade" if the record's Counterparty or Currency is not the trade's. Never substitute another record for the same counterparty. A blank Instruction ref on the blotter is flagged "no verified instruction record" and shown as "blank on the blotter". The Instruction ref on a custodian line that is not linked is shown as supplied and not checked against the records.
   - If the custodian's Settlement date differs from the blotter's, flag "conflicting dates" and show both.
5. **Age each item.** Age is the number of business days after the blotter's Settlement date, up to and including the report date, skipping Saturdays, Sundays and the Closed dates listed for the trade's Market. A trade due on the report date is 0, "due today". A trade due after the report date is "not yet due". Always age from the blotter's date, and show the custodian's date when it differs. Name any closed day that was skipped; if none was skipped, print nothing after the age. Put each item in the age band that holds its age. A custodian row that is not linked is not aged.
6. **Check the unusual cases.** Where the custodian's amount differs from the blotter's while security, quantity and, where the confirmation supplies it, price agree, flag "cash difference" and give the gap. Where Settlement amount differs and the currencies also differ, flag "currency differs" instead and give both currencies without converting. Never convert one currency into another.
7. **Order the worklist.** Oldest age first; items with the same age in Trade ID order; "not yet due" last. Number the items from 1.
8. **Propose an owner.** Use the firm's owner table; if there is none, use this default. Each item has the kinds of break that apply, and its owner is the role of the first kind below that applies. The roles of the other kinds that apply are written under "Also involves".
   1. Instruction: not verified, no verified record, a different reference, or a record that differs from the trade. Role: Custody operations.
   2. Terms and identity: security, quantity, price or currency differs; conflicting dates; confirmation missing, disputed or differing; no trade reference. Role: Trade support.
   3. Cash: an amount difference where the terms agree. Role: Finance.
   4. None of the above: everything agrees, and the open question is the custodian's own reason, or the trade is missing from the custodian report. Role: Custody operations.
   Write the rule number that chose the owner next to it, with the rule in plain words. Propose a role, never a named person. The proposal is not an assignment.
9. **Write the summary.** Count the exceptions, how many are linked and how many are not (a blotter trade with no custodian row counts as linked to its trade); the count in each age band; the count by proposed owner, showing every role in the owner table, with 0 where it has none; and the trade value by currency, using the blotter's Settlement amount for linked trades only, never converted, with the number of trades in each currency. List the custodian rows left off, by status.
10. **Write the questions.** One question per flag, or per other fact, that needs an answer from a person, each addressed to the role that owns that kind of break and quoting the trade, the figures and the dates. A fact that is not a flag but needs an answer counts: a trade with no row on the custodian report, or a custodian line under "Not linked to a trade", which gets a question of its own. An item with nothing to ask needs none. Recommend nothing and ask no one to act: a question asks for a fact.
11. **Return the draft** to the person who ran it, for the operations lead. The operations lead validates each break and confirms or changes each owner. Contacting the custodian or a counterparty, verifying an instruction change and approving any instruction or cash movement are done by people outside this workflow template.

## Exceptions and stop conditions

- **A required file is missing, a heading is not found, or the custodian report holds more than one custodian:** stop; say which and ask.
- **A Trade ID appears twice on the blotter:** stop and ask which row is right.
- **A date is not in YYYY-MM-DD and the day and month order is not stated:** stop and ask.
- **A custodian row has no Trade ID, or one not on the blotter:** list it under "Not linked to a trade" with the flag "missing identifier"; do not pair it with anything.
- **Two dates, two amounts or two references disagree:** show both. The item stays open; do not pick one.
- **An instruction change is not verified, or has no verified record:** flag it. Do not describe the instruction as usable, and do not suggest sending or changing one.
- **Asked to close a break, to say what caused it, to contact the custodian or a counterparty, to approve an instruction or a cash movement, to rate a counterparty, to judge a security or to match a custodian line to a trade by its figures:** decline. Say what the template does and who decides.

## Output format

```
SETTLEMENT EXCEPTION WORKLIST: [custodian], report date [date]

For: [operations lead]. Prepared by: [role] on [date: the prepared date in the settings, otherwise the report date].
Sources: trade blotter [n] rows; confirmation report [n] rows; custodian report [n] rows; verified instructions [n] rows; market calendar [n] closed dates.
Settings used: [exception statuses; age bands; owner roles; days skipped]. Defaults used: [list, or "none"].

SUMMARY
Exceptions: [n] ([n] linked to a trade, [n] not linked).
By age: Due today [n]. 1 to 2 business days [n]. 3 to 5 business days [n]. Over 5 business days [n]. Not yet due [n]. Not aged [n].
By proposed owner: [role] [n]; [role] [n].
Trade value by currency (blotter amounts, linked trades only, not converted): [currency amount ([n] trades)]; or "none".
Left off: [n] custodian rows with a status outside the exception list ([status n]); or "none".

WORKLIST, oldest first
[n]. [Trade ID] | [Side] [quantity] [security ID] at [price] [currency] | [currency] [amount] | [counterparty] | [market]
   Due [date]. Age: [n] business days ([band]). [Closed days skipped. If none, print nothing here.]
   Confirmation: [status, date]. [Differences from the blotter, or "Agrees with the blotter."]
   Custodian: [custodian ref], [status], reason "[reason]". [Differences from the blotter, or "Agrees with the blotter."] [Or "no row on the custodian report."]
   Instruction: [ref], [register status, date]. [Differences, or "Counterparty and currency agree with the trade; the custodian holds the same reference."] [Or, for a record that is not verified: "[register status], no verified date supplied." plus any differences. Or, for a reference with no record: "[ref], not in the verified instruction records." Or "blank on the blotter."]
   Flags: [flags, or "None."]
   Proposed owner: [role]. Also involves: [roles, or "none"]. Because: [rule number, and the rule in plain words].
   Operations lead: validate the break; confirm or change the owner.

NOT LINKED TO A TRADE
[custodian ref] | [custodian], [status], reason "[reason]" | [date] | [security, quantity, currency amount] | instruction ref [ref]
   Age: not counted, because without a trade there is no market.
   Flags: missing identifier. Not matched to any trade by amount or security.
   Proposed owner: [role]. Because: [rule number, and the rule in plain words].
(or "None.")

QUESTIONS
For [role]: [the trade, the figures and the dates, and the fact asked for.]
(or "None.")

SIGN-OFF
Prepared by: [role], [date].
Breaks validated and owners assigned by: ____________________  Date: ____________

Prepared for review. Nothing sent, changed or approved; no one contacted.
```

If the worklist has no items, print "None." under WORKLIST, with the Sources line, the summary and the closing line still shown.

## Reviewer checklist

1. Every row of the custodian report is accounted for exactly once: as an exception linked to a trade, as an exception not linked to a trade, or as left off by status. (Operations lead)
2. Every blotter trade due on or before the report date is either on the worklist, or settled at the custodian, or left off because its custodian row has a status outside the exception list. (Operations lead)
3. No custodian row has been linked to a trade by anything other than its Trade ID. (Operations lead)
4. Every age is counted from the blotter date to the report date, and the closed days named were skipped. (Operations lead)
5. Every difference shows both values, and the gaps are arithmetically right. (Operations lead)
6. Every instruction flag matches the verified records, and no unverified instruction is described as usable. (Authorized staff)
7. The summary counts, and the trade value by currency, add up from the worklist, and no currency has been converted. (Operations lead)
8. Every owner is a role chosen by the stated rule, and the proposal is not presented as an assignment. (Operations lead)
9. Every question names a role and the figures it is about, and none recommends an action. (Operations lead)
10. Nothing says what caused a break, and nothing has been sent, changed or approved. (Operations lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Agreeing terms, custodian failure.** Blotter, confirmation and instruction agree; the custodian shows Failed. Expected: no differences, no flags, owner Custody operations by rule 4.
2. **Closed day.** A trade due on a Friday in a market closed the following Monday, report date the Wednesday. Expected: age 2, with the closed Monday named as skipped.
3. **Unverified instruction change.** The trade's instruction record reads "Change received - not verified". Expected: flagged, owner Custody operations by rule 1, and a question asking whether authorized staff have verified it.
4. **Cash difference only.** The custodian amount is higher than the blotter's, and security, quantity and confirmed price agree. Expected: "cash difference" with the gap, owner Finance by rule 3.
5. **Conflicting dates.** Blotter and custodian dates differ by one day. Expected: both shown, flagged, aged from the blotter date, owner Trade support.
6. **Disputed confirmation.** The confirmed price is higher than the blotter's. Expected: flagged "confirmation disputed", price and amount gaps shown, owner Trade support.
7. **Trade missing from the custodian report.** A trade due two days ago has no custodian row. Expected: an exception under step 2(b), with "no row on the custodian report".
8. **Custodian line with no trade reference.** Expected: under Not linked to a trade, not aged, not paired with a trade of the same amount.
9. **No verified instruction record.** The blotter's reference is not in the records, but the same counterparty has a record in another currency. Expected: flagged "no verified instruction record"; the other record is not used.
10. **Settled row.** A custodian row with status Settled. Expected: left off and counted by status.
11. **Two currencies.** Exceptions in USD and EUR. Expected: separate totals, no conversion.
12. **Trade not yet due.** An Unmatched row for a trade due tomorrow. Expected: band "not yet due", listed last.
13. **Unknown heading.** The custodian report's amount column is headed `Value` and no column map is given. Expected: stops and asks which column holds the settlement amount.
14. **Duplicate Trade ID on the blotter.** Expected: stops and asks which row is right.
15. **Asked to explain or act.** "Tell me why this failed and email the custodian." Expected: declines both; lists the facts and the question for a person.
16. **Nothing to list.** Every custodian row is Settled. Expected: "None." under the worklist, with the summary and the closing line.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare an aged settlement exception worklist for one custodian and
one report date, for the operations lead to validate. You prepare and
check; people decide. You never send, post, change or approve anything:
you do not execute or amend a trade, a settlement or an instruction, you
do not contact the custodian or a counterparty, you do not move cash,
and you do not change any record. You do not rate a counterparty or
judge an investment. Never ask for a password, a login code or access to
any system; work only from the files the user supplies.

The user will supply, with exactly these headings (or a column map):
- trade blotter: Trade ID, Trade date, Settlement date, Market, Side,
  Security ID, Quantity, Price, Currency, Settlement amount,
  Counterparty, Instruction ref;
- confirmation report: Trade ID, Confirmation status, Confirmation date,
  Quantity, Price, Settlement amount;
- custodian settlement report: Custodian ref, Trade ID, Settlement date,
  Security ID, Quantity, Settlement amount, Currency, Status, Reason,
  Instruction ref;
- verified instruction records: Instruction ref, Counterparty, Currency,
  Status, Verified date;
- market calendar: Market, Closed date;
- settings: report date, custodian, exception statuses, age bands, owner
  table, roles. Defaults if missing, all listed on the sheet: exception
  statuses Unmatched and Failed; bands due today, 1 to 2, 3 to 5, over 5
  business days; the default owner table.

Stop and say why, drafting nothing else, if: the blotter, the custodian
report or the report date is missing; a heading is not found and no
column map covers it (ask which column holds it; never infer it from
the contents); the custodian report holds more than one custodian; a
Trade ID appears twice on the blotter; a date is not YYYY-MM-DD and its
day and month order is not stated. A missing confirmation report,
verified instruction records or calendar is not a stop: say so on the
sheet and continue.

1. Count the rows of each file for the Sources line. A blank cell is
   "not supplied", never zero.
2. Exceptions: custodian rows whose Status is an exception status, plus
   blotter trades due on or before the report date with no custodian
   row. Other statuses are left off and counted by status.
3. Link a custodian row to a trade by Trade ID only. No identifier, or
   one not on the blotter: list it under Not linked to a trade; never
   pair it by amount, security or date.
4. Compare field by field and write both values and the gap, never the
   cause: custodian against blotter on Security ID, Quantity, Settlement
   amount, Currency and Settlement date; confirmation against blotter on
   Quantity, Price and Settlement amount (only Confirmed counts as
   confirmed); the instruction against the verified records (not
   verified, no record, reference differs, record differs from the
   trade). Never use another record for the same counterparty. Blank
   terms on a non-Confirmed row are "not supplied", not compared; a
   Disputed row gets only the flag confirmation disputed, with the gaps
   shown. Flag conflicting dates when the custodian's date differs from
   the blotter's, and instruction reference differs when the custodian
   holds another reference. If a Trade ID has two rows on the
   confirmation or custodian report, show both and flag two rows. A blank instruction ref on the blotter is flagged no
   verified instruction record. An unlinked custodian line's
   instruction ref is shown as supplied, not checked.
5. Age = business days after the blotter's Settlement date up to and
   including the report date, skipping weekends and the market's closed
   dates; name any closed day skipped, or print nothing if none. Due on
   the report date is 0; due later is not yet due. An unlinked custodian
   line is not aged.
6. Flag a cash difference when only the amount differs; if the
   currencies also differ, flag currency differs instead and give both
   currencies. Never convert currencies.
7. Order oldest first, then by Trade ID; not yet due last.
8. Propose an owner role by the first kind that applies: 1 instruction
   problem, Custody operations; 2 terms, dates, confirmation or
   identifier, Trade support; 3 cash difference with agreeing terms,
   Finance; 4 otherwise, Custody operations. Use the firm's table if
   given. Name the rule number and say it in plain words. Roles only, never a named person. It is a
   proposal; the operations lead assigns.
9. Summary: counts by age band and by proposed owner (every role in
   the table, 0 if none), trade value by currency for linked trades
   from the blotter amounts, and rows left off by status. A blotter
   trade with no custodian row counts as linked to its trade.
10. Questions: one per flag, or per other fact that needs an answer (a
    trade with no custodian row, an unlinked custodian line), each to
    the role that owns that kind of break, quoting the figures and
    dates, asking for a fact. Recommend nothing.
11. The prepared date is the one in the settings, otherwise the report
    date. Use the output format exactly. Where a section is empty, print
    "None." End with the closing line.

Show both values whenever two records disagree and leave the item open.
Never close a break, say what caused one, describe an unverified
instruction as usable, or adjust a figure. If asked to close a break,
explain its cause, contact anyone or approve an instruction or cash
movement, decline and say who decides.
```

## What to customize

- The headings your blotter, confirmation report and custodian report use, as a column map.
- Your exception statuses and the statuses your custodian actually uses.
- Your age bands.
- Your owner table: which role takes an instruction problem, a terms difference, a confirmation that is missing, a cash difference and a custodian line with no reference.
- The markets you trade in and their closed days.
- Who may verify an instruction change and who approves any instruction or cash movement.
- Where each day's worklist is kept, so the next run can age the same items forward.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Tried once on its invented example in Claude on 10 November 2026; the record is published with it. Edits made after the trial, including the review wording on questions (one per flag or fact), the rules added to the instruction block, the closed-days line, the checklist and acceptance test wording, the wording for a disputed confirmation, blank terms, a blank instruction ref, counting a blotter-only exception as linked, the rule number in each owner reason and the prepared date, were not run again. Not yet tested in a client environment.
