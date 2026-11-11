# Household fee check: one trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs for this trial are the invented example in `public/example.md` (settings, valuation file, household links, fee terms, fee schedules, waivers, account dates and custodian debits for Advisory Firm A, third quarter of 2026). No client data was used. The run was done once, by a model that had not written the template, which followed the instruction block and the output format on those inputs before looking at the published output.

## What came out

The run produced all six sections of the output format. In substance:

- Status: DRAFT, not ready to release: 4 accounts held, 2 differences over tolerance, 1 debit on an unlisted account. Inputs not supplied: none.
- Accounts: 10 linked to a household, 9 valued, 6 with a draft line, 4 held, 0 excluded. Debits: 11 inside the window, 1 outside it (D-0, 2,800.00), not compared.
- Draft lines: Household A on the household basis, value 1,200,100.00, fee (1,000,000.00 at 1.00% + 200,100.00 at 0.80%) / 4 = 2,900.20, shared as 1,546.64, 990.82 and 362.74. Household B: B-201 2,220.00; B-202 fee before waiver 285.00, approved waiver W-1, draft fee 0.00. Household E: E-502 585.00. Six lines, total 5,705.20, waived 285.00.
- Differences: A-102 debit 990.28 against draft 990.82 (-0.54, debit lower); B-202 debit 285.00 against draft 0.00 (+285.00, debit higher, equal to the fee before the waiver); the other four match.
- Held for review: E-501 closed in the period with no valuation (debit 640.00); D-401 opened 2026-08-15, 47 of 92 days, rule none (reference full-period fee 1,125.00); C-301 valued 12 days before period end (reference fee 675.00); F-601 with an unapproved override W-2 (reference 922.50 at the schedule, 768.75 at 0.75 percent). Debit D-11 on Z-999 (50.00) is on no household link.
- Tie-out: debits in the window 9,248.41 = 5,989.66 + 3,208.75 + 50.00; net difference 284.46 = -0.54 + 285.00; 6 + 4 + 0 = 10 accounts.
- Decisions left to the billing owner and the approver; nothing debited, invoiced or credited.

## What was observed

Every required part was produced, every figure recomputed by hand from the inputs, and every tie-out held. No stop condition was triggered: the headers matched, each account appeared once, the schedule tiers were continuous, and no file held an unused column. The assistant was not tempted to release, credit or decide anything.

Against the published example, every figure and every classification was the same. The differences were in wording and presentation:

1. The run counted excluded accounts explicitly ("0 excluded" in sections 1 and 5), as the output format asks. The published example leaves that count out.
2. The run listed the unapproved override W-2 under waivers not applied, as well as W-3 (the instruction block says to list waivers not in force). The published example lists only W-3.
3. The published example adds a fifth review item for the debit on the unlisted account Z-999. The template's step for the review list covers held accounts and households only, so the run reported Z-999 in section 3 and the status line and asked its question in section 6.
4. The published example addresses every question to "Billing owner A". The template asks for a named role (such as the adviser or the operations lead); the run named roles for account facts and the billing owner for rules.

No fact appears in either output that is not in the inputs. The published example's questions ("was a final fee due...", "whose account is Z-999?") are questions, not facts.

## Where the template was ambiguous or needed a guess

- **Which waivers to list as not applied.** The procedure lists only waivers that ended before the period start or begin after its end; the instruction block lists every waiver not in force. A waiver with no approver (W-2) is covered by one reading and not the other.
- **The override reference figure.** The procedure gives "the fee at that number" where the request gives a number. W-2 has an unknown type and a value of 0.75; reading 0.75 as an annual rate in percent is a guess, since the type is unknown. It is the reading the debit supports, but the template does not say how to read the value of an unknown type.
- **Unlisted debits.** Step 9 says one review item per held account or household, yet the output format and the tie-out treat debits on unlisted accounts as something to show and question. Nothing says where the question goes.
- **Which role to name.** The roles section names the person who answers questions about an account as "the person named in the question", but the settings name only a billing owner and an approver. A run has to choose.
- **Version notes.** The template's version notes still say it has not been tried on its invented example; they were not changed by this trial.
- **What counts as a difference over tolerance.** B-202 is counted as a difference over tolerance even though the debit equals the fee before a waiver. This follows the rules as written but could confuse a reader.

## Changes made after the trial

After an independent review, on 10 November 2026, the template and the published example were edited to remove the differences and ambiguities listed above. The run recorded above was not repeated and its record is unchanged.

- The published example now shows the excluded counts (0), puts the differences line after the review items, drops the fifth review item (a debit on an unlisted account is questioned in section 6, as the run did) and lists the unapproved override W-2 as a waiver not applied, as the run did.
- The template now says that every waiver not in force is listed with its reason, where a question about an unlisted debit goes, that questions go to the billing owner when no other contact is named, and how each reference figure is worked out, including reading the value of an unknown-type override as an annual rate in percent and saying so.
- The version notes and the profile now state that the template was tried once on its invented example.

These edits were not re-run.
