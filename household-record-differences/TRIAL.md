# Household record differences: tried once on its example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the workflow template's own invented example, and no client data was used. The firm, the clients, the account numbers and every row are invented. The run used the three files, the settings and the one typed rule (Rule 1, for trusts) from the inputs section of `public/example.md`. The assistant read the template's instructions and output format first, produced the comparison, and only then read the example's published output to compare. The assistant was not the template's author.

## What came out

This is the comparison as produced, before the published example was read.

```
HOUSEHOLD RECORD DIFFERENCES: Firm F

For: the operations owner. Prepared Tuesday 10 November 2026 from crm_households.csv and crm_accounts.csv (CRM, exported 2026-11-09) and custodian_accounts.csv (custodian, exported 2026-11-09). Nothing in any record has been changed.

1. THE FILES
Header check: all three files match the defaults in name and order. crm_households.csv: 14 rows, 12 households. crm_accounts.csv: 14 rows, 13 distinct account numbers. custodian_accounts.csv: 14 rows, 14 distinct account numbers. Full exports, as stated; the figures describe the rows supplied. Rules applied: rule 1 (Trust registrations); defaults for the rest.

2. ACCOUNT MATCH
Custodian accounts: 14. Matched exactly: 11. Matched after leading zeros: 1. In the custodian export only: 2. In the CRM only: 1. CRM distinct account numbers: 13 (11 + 1 + 1).

3. ACCOUNTS WITH NO HOUSEHOLD (in the custodian export, not in the CRM)
- 300102 (custodian line 6): Mateo Reyes individual, Individual, owner Mateo Reyes, mateo@example.net, 70033, Open. Possible household: H03 Okonjo-Reyes household (crm_households line 6, contact Mateo Reyes), matched on owner name and mailing email; postal code 70033 also agrees. Question 1.
- 900101 (custodian line 13): Seren Holt individual, Individual, owner Seren Holt, seren@example.org, 12200, Closed. Possible household: none; no contact matches an owner name or the mailing email. Question 2.

4. ACCOUNTS IN THE CRM BUT NOT IN THE CUSTODIAN EXPORT
- 700102 (crm_accounts line 11): household H08 Maddox household, title "Maddox joint". The custodian export does include closed accounts (900101, custodian line 13, is Closed), so closure alone is not shown as the reason. Question 3.

5. HOUSEHOLD LINKS IN QUESTION
Linked to more than one household: 400101 (crm_accounts lines 6 and 7): H04 Brandt household and H05 Brandt household, both titled "Tamsin Brandt individual". Left out of section 7. Question 4.
Link conflicts: 800101 (crm_accounts line 13; custodian line 12) is linked to H09 Ashgrove household, whose contact is Bryn Ashgrove (crm_households line 12). The owner Wyn Calloway and the mailing email wyn@example.com match no contact in H09; they match the contact Wyn Calloway in H10 Calloway household, crm_households line 13. Left out of section 7. Question 5.
The other 10 matched accounts, each linked to one household, have a contact in that household who matches an owner name or the mailing email.

6. POSSIBLE DUPLICATES
Contacts in different households that may be one person:
- Tamsin Brandt in H04 (crm_households line 7) and H05 (line 8): same name; same email apart from capitals (tamsin@example.com, Tamsin@Example.com); same postal code 80044; both households are named "Brandt household". Needs a person's confirmation. Question 6.
Similar names, same postal code, different households (not exact repeats):
- Priya Nair in H11 (line 14) and Priyanka Nair in H12 (line 15): similar names, same last word, same first letter, same postal code 11100; the emails differ (priya@example.com, priyanka@example.org). Needs a person's confirmation. Question 7.
Accounts repeated in the custodian export: none; 14 distinct account numbers among 14 rows.

7. FIELD-BY-FIELD DIFFERENCES
Tested: 10 accounts (12 matched, less 400101 for two household links and 800101 for a link conflict, both explained in section 5).
- 200101, mailing_postal_code: CRM 60022 (crm_households line 4, Perrin Vasko); custodian 60023 (custodian line 4). Question 8.
- 600101, primary owner name: custodian "Jules Fenn" (custodian line 9) matches no contact in H07; the one contact with the same email, jules@example.com, is "Julius Fenn" (crm_households line 10). That contact was used for the postal code, which agrees (10066). Question 9.
- 700101, account_title: CRM "Maddox individual" (crm_accounts line 10); custodian "Rhea Maddox individual" (custodian line 10). Question 10.
- 4531 / 004531, account_number: CRM "4531" (crm_accounts line 12); custodian "004531" (custodian line 11). Matched after leading zeros; every other field agrees. Question 11.
Agreeing, of 10 tested: account_number 9; account_title 9; primary owner name 9; mailing_email 10; mailing_postal_code 9. 6 accounts agree on every field: 100101, 100102, 300101, 500101, 110101, 120101.
Other named owners not found among the household's contacts: none (100101: Ione Quill found; 300101: Mateo Reyes found). On 500101 the trust's name was not matched, by rule 1; Ottoline Lindqvist was compared.

8. QUESTIONS FOR THE OPERATIONS OWNER
1. Account 300102 (custodian line 6, owner Mateo Reyes, mateo@example.net, 70033) is not in the CRM; Mateo Reyes is a contact in H03 (crm_households line 6) with the same email and postal code. Should the CRM link 300102 to H03?
2. Account 900101 (custodian line 13, owner Seren Holt, Closed) is not in the CRM and no contact matches. Should it be linked to a household, or left unlinked?
3. The CRM links 700102 (crm_accounts line 11) to H08, but the custodian export has no such number. Should the link be corrected or removed?
4. Account 400101 is linked to H04 and to H05 (crm_accounts lines 6 and 7). Which household should hold it?
5. Account 800101 is linked to H09 (crm_accounts line 13), but its owner Wyn Calloway and email wyn@example.com match the contact in H10 (crm_households line 13). Should the CRM link 800101 to H10 instead?
6. Are H04 and H05 (crm_households lines 7 and 8: Tamsin Brandt, the same email apart from capitals, postal code 80044) one household recorded twice? If so, which record should remain?
7. Are Priya Nair (H11, line 14) and Priyanka Nair (H12, line 15) the same person, or two people sharing a postal code?
8. Which postal code is current for Perrin Vasko, the CRM's 60022 (crm_households line 4) or the custodian's 60023 (custodian line 4), and which record should change?
9. Is the contact Julius Fenn (crm_households line 10) the account owner Jules Fenn (custodian line 9), and which spelling is correct?
10. Which title is right for 700101: "Maddox individual" (crm_accounts line 10) or "Rhea Maddox individual" (custodian line 10)?
11. Should the CRM write account 4531 (crm_accounts line 12) as "004531", as the custodian does (line 11)?

9. DECISIONS FOR THE OPERATIONS OWNER
1. Accounts to link (questions 1, 2, 4, 5): link in the CRM, leave as it is, or wait for the answer.
2. The CRM-only link (question 3): correct in the CRM, ask for the custodian's record to be corrected through the firm's usual route, leave as it is, or wait.
3. Possible duplicates (questions 6, 7): treat as one record, keep as two, or wait for the answer.
4. Field differences (questions 8 to 11): correct in the CRM, ask for the custodian's record to be corrected through the firm's usual route, leave as it is, or wait.
Verifying each client's identity and authorizing each correction is the operations owner's decision.

10. NOT CHECKED
Whether any owner or contact is who the records say; whether a household link is right beyond what the files show; households with no accounts; contact fields other than those in the exports; other systems; holdings, values and performance. No record has been changed and no client has been contacted.

Every line number counts from the header as line 1 of its file, as supplied on Tuesday 10 November 2026. This comparison changes no record, contacts no client and judges nothing about any account or investment.
```

## What was observed

- **Every required part was produced.** All ten sections of the output format are present, in order. No stop condition was met: the headers matched, no row had the wrong number of fields, no account number was blank and no extra columns were present. Nothing in the run called for declining.
- **Agreement with the published example.** Every count, every finding, every line number and every quoted value matched the published example: the same two accounts with no household, the same CRM-only account, the same two household-link problems, the same two duplicate groups, the same four field differences, and the same 6 accounts agreeing on every field. I found no fact in either output that is not in the inputs.
- **Differences from the example, all in wording.** These compare my output with the example as it stood at the time of the run; the example has since been edited (see the edits below). The example's section 4 says "No custodian row carries this number, exactly or after leading zeros"; mine says closure alone is not shown as the reason. The example's question 3 offers "removed, or corrected to a different number"; mine says "corrected or removed". My section 6 adds "Needs a person's confirmation" to both duplicate groups, as the template's stop conditions describe; the example does not. The example's section 10 names H10 as having no accounts; mine left it out, since the template does not say to list such households. The example's decision 2 offers "remove it, correct it"; mine uses the template's wording ("correct in the CRM, ask for the custodian's record to be corrected"). I dated the report "Tuesday 10 November 2026", as typed; the example drops the weekday.
- **Where the instructions were ambiguous and I had to choose.**
  - The template's steps run 1 to 11 but its output sections run 1 to 10, so "step 8" and "section 7" name the same thing. The numbering is easy to confuse.
  - The order of findings inside the field-difference section is not stated. I used the custodian's line order; the example uses the same order.
  - The trust's own name on account 500101 is a named owner, but rule 1 says not to match it to a contact. The template does not say whether it belongs in "other named owners not found". I left it out and said so.
  - The two Tamsin Brandt records produce two questions (4 and 6) about the same pair of households. The template says one question per finding but not how to treat overlapping findings. I kept two questions and grouped them into one decision line only where the options matched.
  - The instruction block says "similar names" need the same last word. For hyphenated names, "last word" depends on normalisation (Okonjo-Reyes becomes two words). It made no difference here.
  - The template does not say whether "Closed" status explains an account missing from the CRM, only to say whether the export includes closed accounts. I stated the fact and drew no conclusion.
- **Shortcomings of the template found.**
  - Its version notes still say "Not yet tried on its example" and its acceptance tests say "None has been run". Both are now out of date; I was told not to change them.
  - The instruction block is a compressed version of the procedure, and it leaves out the "needs a person's confirmation" mark that the exceptions section requires. I applied it from the exceptions section; a run from the instruction block alone could omit it.
  - The run covered one example only. Ten acceptance tests, including the header-mismatch stop and the decline cases, were not exercised.
- **Limits of this trial.** One run, by one model, in one product, on invented data. It shows the instructions can be followed to the published result on this example. It does not show the template works on a real firm's exports, with other registrations or larger files, or in other AI products.

## Edits made after this run, not run again

After an independent review, the template, profile and example were edited. The record above is unchanged. The edits were wording only and none changes an input row or a result:

- The version notes and the profile now say the template was tried once; they no longer say it was not tried.
- The "Needs a person's confirmation" mark is now in the output format and the instruction block for possible duplicates and similar names (the run applied it from the stop conditions), and the example shows it.
- The instruction block now states the fallback match by email, that a field blank on both sides is not a difference, that a trust's own name set aside by a typed rule is not counted among owners not found, that overlapping findings each keep a question, and that a hyphen splits a word when names are normalised.
- Field-by-field differences are named by title instead of by section number, so procedure steps and output sections no longer collide.
- The example now keeps the weekday in the date, leaves households with no accounts unnamed, and words its decisions with the options the template offers.

- A later pass added clauses to the instruction block: a custodian account number that appears twice is left out of the comparison steps with the reason, the closed-accounts statement is in the step for CRM-only accounts, and masked account numbers carry an ellipsis with any difference in leading zeros described in words. None changes a result on the example.

These edits have not been run again.
