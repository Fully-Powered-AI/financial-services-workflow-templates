# Corporate action deadline brief

Capability template, version 0.1.0.

## Purpose

Prepare, for an operations lead at an asset manager or advisory firm, one brief for one corporate action announced in a custodian notice. The brief lists the affected holdings from the record-date export, the options exactly as the official notice quotes them, the custodian and issuer deadlines with days remaining, the standing instructions on file and whether each clearly covers the event, and the confirmations still missing, each with the role that can supply it. The assistant prepares and checks. It recommends no election, values no entitlement, gives no tax view and submits nothing. The investment manager or authorized client decides each election; operations verifies and submits approved instructions.

## When to use it and when not to

Use it when a custodian notice announces an event, voluntary or mandatory, affecting a security the firm holds for clients or for itself, and an election, a deadline or a confirmation could depend on it. Run it once per event, once the holdings export as of the record date is available, which can be after the notice arrives; run it again if a corrected notice arrives.

Do not use it to match the firm's positions to the custodian's records or to explain differences between them; that is reconciliation work and a separate piece of work. Do not use it to value a position or an entitlement, to advise on tax, to pick an election, or to send anything to a custodian, issuer or client. Do not use it when no official notice is available: a summary, an email forward or a message from a colleague is not the notice.

## Roles

- **Runs it:** the operations lead.
- **Decides each election:** the investment manager, or the authorized client for the account.
- **Verifies and submits approved instructions:** custody operations or the operations lead, acting only on a recorded approval.
- **Confirms standing instructions and reaches clients:** client service.
- **Answers tax questions:** the tax specialist.
- **Assigns eligibility and legal-status questions:** the operations lead names the specialist at the firm who takes each one; the template names none.
- **Asks the custodian about a point the notice leaves out,** such as the payment date: custody operations.

## Inputs

1. **The official notice,** as text or a copy, with its reference and date. If missing, stop. If more than one notice on the same event is supplied and they disagree, see the stop conditions.
2. **The holdings export as of the record date,** with these default headers: Account ID, Account name, Security ID, Security name, Quantity (record date), Position date, Custodian. If a header differs or a column is missing, stop and ask which of the supplied headers stands for each missing one; never guess.
3. **Standing instructions on file,** with these default headers: Account ID, Event type, Instruction, Date on file, Authorized by. If the headers differ, stop and ask. An account with no row has no instruction on file.
4. **Custodian correspondence** about the event. If none, say none was supplied.
5. **Prior event records** for the same security, if any. If none, print "not supplied".
6. **The firm's settings:** the internal cut-off, [your internal cut-off in business days before the custodian deadline] (default one); the age after which a standing instruction must be confirmed again, [your instruction age limit in months] (default 24); the dates the firm is closed; the brief date (default today); and, only when a deadline falls on the brief date, the time now in the notice's time zone.

## The procedure

1. **Read the notice.** Pull out the issuer, security name and identifier, event type, record date, each option, what the notice says happens with no election, whether elections can be changed, the custodian deadline with its time and time zone, the issuer deadline, the payment date and the notice reference and date. Quote each option and the no-election sentence exactly. Where the notice does not state a point, write "not stated in the notice"; never fill a gap from general knowledge of how such events usually run.
2. **Check the export against the notice.** The security identifier must match. Every row's position date must equal the record date. If it does not, stop and tell the operations lead; do not use a later or earlier position.
3. **List the affected holdings.** Keep rows with a quantity above zero. Group by custodian, give each group a subtotal and give a grand total and an account count. Holdings at a custodian that sent no notice count in the total and are marked as awaiting that custodian's own notice. List zero-quantity accounts as not affected. Recompute every subtotal and total from the rows; a quantity that is blank is unknown, not zero, and goes to the missing confirmations.
4. **Name the deadlines.** List, in date order: the firm cut-off (the custodian deadline less the firm's business days, counted on the firm's open days), the custodian deadline and the issuer deadline. Give the weekday and the days remaining from the brief date, counted as calendar days (only the cut-off is counted on the firm's open days). Mark each as quoted from the notice or set by the firm's rule. A deadline on the brief date reads "deadline passed" if its stated time has gone and "due today" otherwise. A holding at a custodian other than the notice's sender has no deadline until that custodian's own notice is on file.
5. **Match standing instructions.** For each affected account, show the instruction, its date, its age in whole months from the brief date, and who authorized it. Say "covers this event type" only if the instruction's event type names this kind of event or a group that plainly includes it. If the wording is wider, narrower or vaguer than the event, write "does not clearly cover" and put it under missing confirmations. Mark any instruction older than the age limit; one that covers the event but is past the limit ends "Covers this event type; past the age limit, needs confirming." An account with no row reads "none on file". Never apply an instruction as an election.
6. **List the confirmations still missing.** Number each one: accounts with no instruction, instructions past the age limit or not clearly covering the event, holdings at a custodian whose notice is missing, points the notice does not state, any blank quantity and any unavailable prior record. Name the role that can supply each. Say what the notice states happens without an election, quoted, but do not call it a default the firm has chosen.
7. **Route the questions that are not for operations.** Tax treatment, entitlement amounts and anything about eligibility or legal status go to a specialist, as a question: the tax specialist for tax, and for eligibility and legal status whoever the operations lead assigns. Points the notice leaves out go to custody operations to ask the custodian. Write no answer to them.
8. **State who decides and who submits,** using the roles above. Print that the brief recommends no election, values nothing and has sent nothing.
9. **Close with the trace line,** naming the notice reference and date and the export's position date.

## Exceptions and stop conditions

- **No official notice, or the notice has no record date or no options:** stop and say which.
- **Two notices disagree on a date, an option or a rate:** stop on that field, show both quotes with their references, and ask the operations lead which governs. Do not choose.
- **The export's position date is not the record date, or the security identifier differs from the notice:** stop.
- **Headers do not match the defaults:** stop and ask.
- **A deadline falls before the brief date, or on the brief date with its stated time already gone:** write "deadline passed" beside it and tell the operations lead first, before the rest of the brief. If a deadline falls on the brief date and its time has not come, or the notice states no time, write "due today"; if the time now is not supplied, ask for it.
- **The notice is for a custodian that does not hold some of the accounts:** list those accounts as awaiting their own custodian's notice.
- **Asked to recommend or choose an election, apply a standing instruction as the election, compute an entitlement or value, give a tax view, reconcile positions to the custodian, or submit or send anything:** decline; those belong to the people named under Roles.

## Output format

```
CORPORATE ACTION DEADLINE BRIEF: [security name] ([security ID]), [event type]

Prepared for: [Operations lead, firm]. Brief date: [weekday date].
Source: [custodian] notice [reference], dated [weekday date].

Event as noticed: [event type]. Record date [weekday date].

Dates and deadlines:
- Firm internal cut-off: [weekday date] ([n] days from the brief date). Set by [the firm's rule].
- Custodian deadline: [time and zone], [weekday date] ([n] days). Quoted from the notice.
- Issuer deadline: [weekday date] ([n] days). Quoted from the notice.
- Payment date: [date, or "not stated in the notice"].

Options as quoted in the notice:
- Option [n], [name]: "[exact words]"
- No election: "[exact words, or not stated in the notice]"
- Changes: "[exact words, or not stated in the notice]"
- Entitlements are not calculated here.

Affected holdings (export position date [date], [matches / does not match] the record date):
- [Custodian]: [account ID name, quantity] ... Subtotal [n]. [If it sent no notice: Awaiting its own notice; no deadline yet.]
- Total [n] across [n] accounts[, optionally followed by "including any at a custodian awaiting its own notice"].
- Not affected (zero at the record date): [accounts, or "none"].

Standing instructions on file:
- [Account ID]: [event type], [instruction], [date] ([n] months old[, over the limit]), authorized by [role]. [Covers this event type. / Covers this event type; past the age limit, needs confirming. / Does not clearly cover this event; needs confirming.]
- [Account ID]: none on file.

Confirmations still missing:
1. [What is missing]. [Role] [supplies or confirms it].
[Or "None."]

For specialists (not answered here): [question] ([role]).
[Or "None raised."]

Decision and submission: [who decides]. [Who submits] verifies and submits only approved instructions before [the firm cut-off]. This brief recommends no election, values nothing, and has sent nothing.

Every date is quoted from notice [reference] or set by the firm's stated rule; every quantity is from the holdings export with position date [date].
```

## Reviewer checklist

1. Every option, the no-election sentence and each deadline match the notice word for word. (Operations lead)
2. Every quantity and subtotal matches the export, and the total adds up. (Operations lead)
3. The firm cut-off is correctly counted on the firm's open days. (Operations lead)
4. Each "covers this event type" or "does not clearly cover" judgment is right for the instruction's wording. (Client service)
5. Every account with an affected holding appears under standing instructions and, where needed, under missing confirmations. (Client service)
6. Nothing in the brief recommends an election, states a value or tax view, or treats a standing instruction as an election. (Investment manager)
7. Where the notice was silent, the brief says so. (Operations lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Normal event.** The example in the public folder. Expected: dates with days remaining, quoted options, holdings by custodian with correct totals, and the missing confirmations listed.
2. **Position date wrong.** The export is dated the day after the record date. Expected: stop; no holdings listed.
3. **Two notices disagree.** One gives a custodian deadline of the 13th, the other the 12th. Expected: stop on that field and show both quotes.
4. **Header mismatch.** "Qty" in place of "Quantity (record date)". Expected: stop and ask.
5. **Vague instruction.** "Voluntary events: no action" on an optional dividend. Expected: "does not clearly cover" and a missing confirmation.
6. **Deadline passed.** Brief date after the custodian deadline. Expected: "deadline passed" first.
7. **Other custodian.** An account at a custodian that sent no notice. Expected: listed as awaiting that custodian's notice; no deadline invented.
8. **Asked to choose.** "Which option should we take?" Expected: declined, with the decision left to the investment manager or authorized client.
9. **Asked for an amount.** "How much cash will account A get?" Expected: declined; routed to the custodian and custody operations.

## Instructions for the AI assistant

```
You prepare a corporate action deadline brief for an operations lead at an
asset manager or advisory firm. You never choose or recommend an election,
never value an entitlement or a holding, never give a tax view, never
reconcile positions, and never send, submit, post or change anything. The
investment manager or the authorized client decides each election; a person
in operations submits approved instructions. Never ask for a password or a
login code.

The user will supply: the official custodian notice with its reference and
date; the holdings export as of the record date (headers: Account ID,
Account name, Security ID, Security name, Quantity (record date), Position
date, Custodian); standing instructions (headers: Account ID, Event type,
Instruction, Date on file, Authorized by); any custodian correspondence;
earlier records of the event, if any; and the firm's settings (internal
cut-off in business days before the custodian deadline, default 1;
instruction age limit in months, default 24; closed dates; brief date; and,
only if a deadline falls on the brief date, the time now in the notice's
time zone). If
the notice is missing, or a header does not match, stop and ask. If another
input is missing, say so in the section it feeds and continue.

1. Read the notice. Extract the issuer, security, identifier, event type,
   record date, each option, the no-election consequence, whether elections
   can change, the custodian and issuer deadlines, the payment date and the
   notice reference. Quote options and the no-election sentence exactly.
   Where the notice is silent, write "not stated in the notice". If the
   notice has no record date or no options, stop and say which.
2. Check that the export's security ID matches the notice and every
   position date equals the record date. If not, stop.
3. List affected holdings (quantity above zero) by custodian, with
   subtotals, a total and an account count, recomputed from the rows. List
   zero holdings as not affected. A blank quantity is unknown, not zero, and
   goes to the missing confirmations.
   Holdings at a custodian that sent no notice count in the total and are
   marked as awaiting that custodian's own notice.
4. Give the deadlines in date order with weekday and days from the brief
   date, counted as calendar days: the firm cut-off (custodian deadline
   less the firm's business days, counted on the firm's open days using its
   closed dates), the custodian deadline, the issuer deadline. Write
   "deadline passed" beside any date before the brief date, or on the brief
   date with its stated time already gone, and tell the operations lead
   first, before the rest of the brief. A deadline on the brief date whose
   time has not come, or has no stated time, reads "due today"; if the
   time now is needed and not supplied, ask for it. A custodian other
   than the notice's sender has no deadline until its own notice is on file.
   If two notices disagree, stop on that field and show both.
5. For each affected account show its standing instruction, date, age in
   whole months and who authorized it. Say it covers the event only if its
   event type plainly includes this event; otherwise say it does not
   clearly cover it. Flag instructions past the age limit; one that covers
   the event but is past the limit ends "Covers this event type; past the
   age limit, needs confirming." "None on file" where there is no row.
   Never treat an instruction as an election.
6. Number the confirmations still missing, each with the role that
   supplies it: accounts with no instruction, instructions past the limit or
   not clearly covering the event, holdings at a custodian with no notice
   on file, points the notice does not state, blank quantities and missing
   prior records. Quote what the notice says happens without an election,
   but do not call it a default the firm has chosen. Route tax, entitlement
   and eligibility questions to specialists as questions, unanswered: tax to the tax specialist,
   eligibility and legal status to whoever the operations lead assigns,
   entitlements to custody operations. Points the notice leaves out go to
   custody operations to ask the custodian.
7. State who decides and who submits. Use the output format exactly and end
   with the trace line.

If asked to recommend or choose an election, compute an entitlement or a
value, give a tax view, reconcile positions, or submit anything, decline and
name who does it. Never adjust a date or quantity to resolve a conflict.
```

## What to customize

- Your internal cut-off, as business days before the custodian deadline.
- Your instruction age limit.
- The column headers of your holdings and standing-instruction exports.
- The roles at your firm that decide, verify, submit, confirm instructions and answer tax questions.
- Your closed dates, and where the approved brief is stored.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.
