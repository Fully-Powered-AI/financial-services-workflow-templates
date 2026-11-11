# Household fee check

Capability template, version 0.1.0.

## Purpose

Prepare the fee check a billing owner works from on the fee review date. It applies the firm's own agreed fee schedules and approved waivers to the period-end valuation files, account by account and household by household, and produces draft invoice lines with the working shown. It compares each line with what the custodian debited and states the difference. Accounts it cannot calculate safely, because of an unclear proration, a stale valuation, a negotiated override nobody approved or a closed account, are kept apart on a review list, each with a question for a named role. The assistant prepares and checks. It debits, invoices and credits nothing, changes no record, and takes no tax or regulatory position. The billing owner confirms the rules and the exceptions, and an authorized approver releases any charge or credit.

## When to use it and when not to

Use it on the fee review date for one fee period, once the period-end valuation files and the custodian debit records for that period are in hand.

Do not use it to check fees billed on time or subscriptions (use the client billing summary or the subscription billing exception sheet), to tie cash to the bank (use the bank reconciliation preparation), to decide what the firm should charge, or to work out tax. Do not use it when the firm has no written fee schedule: without one there is nothing to apply. A schedule that depends on cash flows, minimum fees or caps is outside these rules; see the stop conditions.

## Roles

- **Runs it and confirms the rules and exceptions:** the billing owner.
- **Answers questions about an account's valuation, dates or terms:** the person named in the question, usually the adviser or the operations lead. If the settings name no such contact, every question goes to the billing owner.
- **Releases any charge or credit:** the authorized approver. The template never does.

## Inputs

Read each file as supplied. Default column headers are listed. If a header does not match, do not guess which column is meant: stop, list the headers found against the headers expected, and ask the billing owner which is which. If a file holds a column these rules do not use (such as a minimum fee, a cap or a flow adjustment), stop and ask whether it changes the calculation.

1. **Settings,** typed by the billing owner: firm name, fee review date, fee period (start and end, both included), currency, debit window (first and last date), stale valuation limit in days before period end (default 5), proration rule (`none` or `daily`; default `none`), tolerance for differences (default 0.00), who the billing owner and approver are, and, optionally, the adviser or operations contact for questions about an account (default: the billing owner). If the period, currency or debit window is missing, stop and ask. Rounding is to the cent, half up.
2. **Valuation file.** Default headers: `account_id, valuation_date, market_value, currency`. One row per account. If missing, stop.
3. **Household links.** Default headers: `household_id, household_name, account_id`. If missing, stop.
4. **Fee terms.** Default headers: `household_id, schedule_id, basis, periods_per_year, effective_from, effective_to`. `basis` is `household` or `account`. A blank `effective_to` means still in force. If missing, stop.
5. **Fee schedules.** Default headers: `schedule_id, tier_floor, tier_ceiling, annual_rate_pct`. Tiers are marginal: each rate applies only to the slice of value between its floor and its ceiling. A blank ceiling means no upper limit. If missing, stop.
6. **Waivers and discounts.** Default headers: `waiver_id, household_id, account_id, type, value, valid_from, valid_to, approved_by, approved_on`. A blank `account_id` means the whole household. Known types: `waive` (no value) and `discount_pct` (value is a percentage). If the file is missing, say "waivers not supplied", apply none, and put that in the status line.
7. **Account dates.** Default headers: `account_id, open_date, close_date`. A blank `close_date` means open. If missing, stop: proration and closures cannot be judged.
8. **Custodian debits.** Default headers: `debit_id, account_id, debit_date, amount, currency`. If missing, stop.

## The procedure

1. **Check the files.** Confirm the headers. Confirm every account appears once in the valuation file; if one appears twice, stop and ask. Confirm each schedule's first floor is 0, each floor equals the previous ceiling and only the last ceiling is blank; if not, stop and ask.
2. **Link and classify each account.** Take the accounts from the household links and the account dates. An account that closed before the period start is excluded and listed. Every other account is either calculated or held, and a held account gets the first reason that applies, in this order: closed (it closed inside the period, or it has no valuation row); unclear proration (it opened inside the period and the proration rule is `none`, or the rule is `daily` but its household is calculated on the household basis); stale valuation (the valuation is dated more than the stale limit before the period end, or after the period end); negotiated override (a waiver row for the account or its household has no approver or no approval date, or has an unknown type); other (no household link, no fee terms in force on the period end, two fee terms in force, no schedule, a currency that differs from the settings, a waiver that ends inside the period, or two waivers in force on the same account). Note every further reason on the same review item.
3. **Waivers in force.** A waiver is in force when it has an approver and an approval date, a known type, its `valid_from` is on or before the period end and its `valid_to` is blank or on or after the period end. Every other waiver is not in force: it is not applied and is listed with its reason (ended before the period start, starts after the period end, no approver or approval date, or unknown type). Apply only waivers in force.
4. **Calculate the fee.** For an account on the account basis, apply the schedule's tiers to its value: for each tier, the slice of value inside it times the annual rate, added together, divided by `periods_per_year`, rounded to the cent. For a household on the household basis, add every account's value in the household, apply the tiers to the total in the same way, and round once. If any account in a household calculated on the household basis is held, hold the whole household and say which account blocks it. Allocate a household fee to its accounts in proportion to their values, rounded to the cent; put any rounding remainder on the account with the largest value (the lowest account number if tied).
5. **Proration.** If the proration rule is `daily` and an account on the account basis opened inside the period, multiply its fee by the days it was open in the period divided by the days in the period, counting the open date and the period end, then round. Otherwise an account that opened inside the period is held.
6. **Apply the waivers in force.** `waive` takes the account's fee to 0.00. `discount_pct` takes that percentage off the account's fee, rounded to the cent. A waiver with a blank `account_id` applies to every account in the household, after any allocation. Show the fee before the waiver, the waiver and the draft fee.
7. **Draft the invoice lines.** One line per calculated account, grouped by household, each with its value and valuation date, the fee before waiver with the working, the waiver and the draft fee. Show the household's working and total above its lines. Total all the lines and the amount waived.
8. **Compare with the debits.** Count debits dated inside the debit window; list the others as outside the window and compare nothing. For each drafted account, the difference is the debit minus the draft fee (the sum of its debits if there are several). A difference is flagged when its size is greater than the tolerance. Say whether the debit is higher or lower. If the debit equals the fee before a waiver, say so. For held accounts, show the debit with no draft figure. List debits on accounts in no household link; they get no review item, and the question about each goes to the billing owner in section 6. List drafted accounts with no debit.
9. **Write the review list.** One item per held account or household, in this order: closed, unclear proration, stale valuation, negotiated override, other. Each item gives the account, the facts from the files, a reference figure only if every input to it is present (marked "Reference only, not a draft line") and a question for a named role. The reference figure for an override is the schedule fee and, where the request gives a number, the fee at that number. The reference figure for a stale valuation is the fee at the supplied value. For an account opened inside the period, give the days open and the days in the period, and the full-period fee as the reference. Never put a reference figure into the draft lines or the totals.
10. **Tie out and hand over.** Debits in the window must equal debits on drafted accounts plus debits on held accounts plus debits on unlisted accounts. Net difference must equal the sum of the listed differences. Accounts with a draft line plus held accounts plus excluded accounts must equal the accounts linked to a household. If anything does not tie, stop and report the figures. Return the fee check to the billing owner only.

## Exceptions and stop conditions

- **A required file is missing, a header does not match or a file holds a column the rules do not use:** stop; list what was found and what was expected.
- **An account appears twice in the valuation file, or a schedule's tiers have a gap, an overlap or a first floor that is not 0:** stop; ask the billing owner.
- **The tie-out fails:** stop; report the figures and the difference. Never adjust a figure to make it tie.
- **A schedule or term the rules cannot express (a fee on cash flows, a minimum or a cap):** stop; ask whether to hold those accounts or have the rules extended.
- **An account cannot be calculated:** keep it on the review list; never fill a gap with an assumed value, date, rate or waiver.
- **Asked to debit, invoice, credit, release, post, send anything or change a record, to decide an override is approved, to choose a proration rule, or to give a tax or regulatory view:** decline; the billing owner and the approver decide.

## Output format

```
FEE CHECK: [firm], fee period [start] to [end]
Fee review date [date]. Debits compared: [first] to [last]. Prepared for [billing owner]; approver [approver].
Status: DRAFT. Not ready to release: [n] accounts held for review, [n] differences over tolerance and [n] debits on unlisted accounts. / DRAFT. Nothing held and no difference over tolerance; ready for the billing owner's confirmation.
Inputs not supplied: [list / none].

1. SETTINGS USED
Currency [x]. Period [n] days. Stale valuation limit [n] days, so a valuation dated before [date] is stale. Proration rule: [rule]. Tolerance [amount]. Rounding: to the cent, half up.
Accounts: [n] linked to a household; [n] valued; [n] with a draft line; [n] held for review; [n] excluded (closed before the period).
Debits: [n] inside the window; [n] outside it ([each: id, account, date, amount]), not compared. / none outside.
Waivers not applied because they were not in force on [period end]: [id, household, type, reason (ended / not yet started / no approval / unknown type)]. / none.

2. DRAFT INVOICE LINES
[Household name] ([id]), schedule [id], basis [household/account], [n] periods a year.
[Household basis only: Household value [amount]. Fee: ([working]) / [n] = [amount].]
Line [n]: [account], value [amount] on [date]; [household basis: share of fee [amount]] [account basis: fee before waiver ([working]) / [n] = [amount]]; waiver [none / id, type, approved by, approved on: -[amount]]; draft fee [amount].
Household total [amount].
Draft invoice lines: [n]. Total [amount]. Waived: [amount]. / No draft lines.

3. DIFFERENCES AGAINST CUSTODIAN DEBITS
Difference is the debit minus the draft fee.
- [Account]: draft [amount]; debit [amount] ([debit id]); difference [amount]. [Matches. / Debit is higher than the draft. / Debit is lower than the draft.]
Held accounts, debit recorded and no draft figure to compare: [account amount (id)]. / none.
Debit on an account in no household link: [account amount (id)]. / none.
Accounts with a draft line and no debit in the window: [list / none].

4. FOR REVIEW
Review [n]. [Closed account / Unclear proration / Stale valuation / Negotiated override / Other]: [account] ([household]). [Facts from the files.] [Reference only, not a draft line: ...] Question for [role]: [question]. [Approver] decides any charge or credit.
Differences over tolerance on drafted lines: [n] ([accounts]). / none.
/ Nothing held for review.

5. TIE-OUT
Debits inside the window: [total] = [amount] on accounts with draft lines + [amount] on held accounts + [amount] on unlisted accounts.
Draft fees on drafted lines [amount]; debits on the same accounts [amount]; net difference [amount] = [the listed differences].
Accounts: [n] with draft lines + [n] held + [n] excluded = [n] linked to a household.

6. DECISIONS
For [billing owner]: [confirm the rules in section 1; answer the questions in the review items and any question about a debit on an unlisted account; confirm the differences].
For [approver]: [decide whether any charge or credit follows]. Nothing has been debited, invoiced or credited.

Every figure traces to the files supplied. Nothing is debited, invoiced or credited.
```

## Reviewer checklist

1. Each draft fee recomputes from the value, the schedule's tiers and the periods a year. (Billing owner)
2. Household fees use the total household value, and the allocated shares add back to the household fee. (Billing owner)
3. Every waiver applied has an approver and an approval date and was in force on the period end. (Billing owner)
4. Every account is either on a draft line, on the review list or excluded, and the counts tie. (Billing owner)
5. No reference figure appears in the draft lines or totals. (Billing owner)
6. Every difference over tolerance and every debit on a held or unlisted account is shown. (Approver)
7. Every question is addressed to a named role, and the decisions are left to the billing owner and the approver. (Approver)

## Acceptance tests

Proposed tests. None has been run.

1. **Household over a tier boundary.** Household value 1,200,100.00 on a household schedule with a 1,000,000.00 ceiling. Expected: both slices shown, one rounding, shares that add to the household fee.
2. **Approved waiver.** `waive` on one account with approver and date. Expected: fee before waiver, the waiver and a draft fee of 0.00; a debit equal to the pre-waiver fee reported as such.
3. **Waiver outside the period.** A discount that ended before the period start. Expected: not applied; listed under waivers not applied.
4. **Override without approval.** A rate override with no approver. Expected: account held as a negotiated override; schedule fee and requested-rate fee shown as reference only.
5. **Stale valuation.** Valuation 12 days before period end with a limit of 5. Expected: held; no draft line.
6. **Opened mid-period, rule none.** Expected: held as unclear proration with the days open and the days in the period; no draft line.
7. **Closed in the period, no valuation.** Expected: held as closed; the debit shown with no draft figure.
8. **Debit on an unlisted account.** Expected: listed under debits on accounts in no household link and included in the tie-out.
9. **Header mismatch.** A valuation file with `value` where `market_value` is expected. Expected: stops and asks.
10. **Asked to release a credit.** Expected: declines; names the approver.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a household fee check for the billing owner of an advisory
firm on the fee review date. You prepare; people decide. You never
debit, invoice, credit, release, post or send anything, never change a
record in any system, never decide that a waiver or override is
approved, never choose a proration rule, and never give a tax or
regulatory view. The billing owner confirms the rules and the
exceptions; an authorized approver releases any charge or credit. You
never ask for a password or a login code and need no access to any
system.

The user will supply: settings (firm, fee review date, fee period,
currency, debit window, stale limit in days (default 5), proration rule
(none or daily; default none), tolerance (default 0.00), billing owner,
approver, and optionally a contact for account questions); the valuation file (account_id, valuation_date, market_value,
currency); household links (household_id, household_name, account_id);
fee terms (household_id, schedule_id, basis, periods_per_year,
effective_from, effective_to); fee schedules (schedule_id, tier_floor,
tier_ceiling, annual_rate_pct); waivers (waiver_id, household_id,
account_id, type, value, valid_from, valid_to, approved_by,
approved_on); account dates (account_id, open_date, close_date); and
custodian debits (debit_id, account_id, debit_date, amount, currency).
If a required file or the period, currency or debit window is missing,
stop and say so. If a header does not match, or a file holds a column
these rules do not use, stop, list the headers found against those
expected, and ask. If the waivers file is missing, apply none and say so
in the status line.

1. Check the files: every account once in the valuation file; each
   schedule's first floor 0, each floor equal to the previous ceiling,
   only the last ceiling blank. Otherwise stop and ask.
2. Classify each account. Closed before the period start: excluded and
   listed. Otherwise calculate it or hold it, with the first reason in
   this order: closed (closed in the period, or no valuation row);
   unclear proration (opened in the period and the rule is none, or the
   rule is daily on a household-basis account); stale valuation (dated
   more than the stale limit before period end, or after it); negotiated
   override (a waiver with no approver or approval date, or an unknown
   type); other (no household link, no fee terms in force on the period
   end, two fee terms in force, no schedule, a different currency, a
   waiver ending inside the period, two waivers in force on one
   account). Note any further reasons on the same item.
3. A waiver is in force only with an approver, an approval date, a known
   type, valid_from on or before the period end and valid_to blank or on
   or after it. List every waiver not in force with its reason (ended,
   not yet started, no approval, unknown type); apply only those in force.
4. Fee: for each tier, the slice of value inside it times the annual
   rate, added up, divided by periods_per_year, rounded to the cent. On
   the household basis, use the household's total value, round once, and
   allocate to accounts in proportion to value, rounded; the remainder
   goes to the largest account. If any account in a household-basis
   household is held, hold the whole household and name the account.
5. With the daily rule, an account-basis account opened in the period
   gets its fee times days open (counting the open date and the period
   end) over days in the period, rounded.
6. Waivers: waive makes the fee 0.00; discount_pct takes that percentage
   off, rounded. A blank account_id covers the whole household. Show the
   fee before waiver, the waiver and the draft fee.
7. Draft the invoice lines: one line per calculated account, grouped by
   household, with the household's working and total above its lines,
   then the total of all lines and the amount waived.
8. Compare with debits inside the window: difference is debit minus
   draft fee. Flag any difference larger than the tolerance, say whether
   the debit is higher or lower, and note when it equals the fee before a
   waiver. Show debits on held accounts with no draft figure, debits on
   accounts in no household link (no review item; the question about
   each goes to the billing owner in section 6), debits outside the
   window (compare nothing) and drafted accounts with no debit.
9. Review list, in the order closed, unclear proration, stale valuation,
   negotiated override, other. One item per held account or household.
   Each item: the account, the facts, a reference figure only if every
   input is present, marked "Reference only, not a draft line", and a
   question for a named role (the settings' contact for account
   questions, else the billing owner). Reference figures: for an
   override, the schedule fee and, where the request gives a number, the
   fee at that number (read the number as an annual rate in percent and
   say so if the type is unknown); for a stale valuation, the fee at the
   supplied value; for an account opened in the period, the days open,
   the days in the period and the full-period fee. Reference figures
   never enter the draft lines or totals.
10. Tie out: debits in the window = drafted + held + unlisted; net
   difference = the listed differences; drafted + held + excluded
   accounts = accounts linked to a household. If anything fails, stop,
   report the figures and the difference, and draft nothing further.
   Never adjust a figure to make it tie.
11. Use the output format exactly. Decisions are written as facts and
    questions; recommend nothing unless the billing owner asks. End with
    the closing line of the output format.

Never fill a gap with an assumed value, date, rate or waiver. If asked to
debit, invoice, credit, release or send anything, to decide an override
is approved, to choose a proration rule or to give a tax or regulatory
view, decline and name the person who decides.
```

## What to customize

- Your export headings, or a standing column map for the valuation, debit and fee-terms exports.
- Your fee frequency and rounding, your stale valuation limit and your tolerance.
- Your proration rule: `none`, `daily`, or another method written into the rules before the run.
- Whether schedules apply to the household or to each account, and any fees these rules do not express, such as minimums, caps or fees on cash flows, which need the rules extended first.
- Who may approve a waiver or an override, and who releases a charge or a credit.
- The role named in each review question, such as the adviser, the operations lead or the custodian relationship owner.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Editorially reviewed. Tried once on its invented example, in Claude on 10 November 2026, with the record published beside it. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
