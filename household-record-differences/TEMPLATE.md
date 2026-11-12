# Household record differences

Workflow template, version 0.1.0.

## Purpose

Compare a firm's client-record export with its custodian's account export and list where they disagree about a household: accounts the custodian holds that no household claims, links the record system holds that the custodian does not show, accounts linked to two households, a link whose owner belongs to another household, possible duplicate contacts, and field-by-field differences on accounts that match. Every finding names its source file and line and ends in a proposed correction written as a question. The assistant compares; it never changes, merges, relinks or corrects a record, contacts no one, and judges nothing about any account, investment or client.

## When to use it and when not to

Use it when a billing run, client report or adviser review turns up an account missing from a household, after a migration, a merger of client books or a custodian switch, and regularly, started each time by the operations owner, to find differences early. It compares one record system with one custodian at a time.

Do not use it to understand a single unfamiliar export (that is the dataset profile), to reconcile two reports that give different totals (that is metric definition reconciliation), to merge or correct records, to assess whether an account is suitable or how an investment is performing, or to confirm who a person is. Do not use it on exports the person is not entitled to share with the AI product the firm has chosen.

## Roles

- **Runs it:** the operations owner, who supplies the exports and the matching rules.
- **Verifies identities and authorizes every correction:** the operations owner. The comparison only lists what is open.
- **Makes any change:** a person at the firm, in the CRM or through the custodian's own process. The assistant makes none.
- **Reviews the comparison against the rows:** a second person in operations, for the first runs.

## Inputs

Three files (items 1 to 3), as CSV text, pasted tables or attachments, then settings and optional matching rules (items 4 and 5). In each file, the first line is the header and is line 1; every line number in the comparison counts from there. If an export is a sample or may be cut off, the operations owner says so, and the comparison says so at the top.

1. **`crm_households.csv`,** one row per contact, with the default headers `household_id`, `household_name`, `contact_name`, `contact_role`, `email`, `postal_code`.
2. **`crm_accounts.csv`,** one row per account link, with the default headers `household_id`, `account_number`, `account_title`.
3. **`custodian_accounts.csv`,** one row per account, with the default headers `account_number`, `account_title`, `registration`, `owner_names`, `mailing_email`, `mailing_postal_code`, `status`. Several owners are separated by a semicolon in `owner_names`.
4. **Settings,** typed by the operations owner, one per line:
   - `Firm label:` default "the firm".
   - `Today:` the date.
   - `For:` who the comparison is for. Default "the operations owner".
   - `Files:` the file names, export dates and whether each is a full export or a sample.
   - `Mask account numbers:` default no. If yes, print only the last four digits after an ellipsis everywhere, and leave the line numbers to identify the row. Masked values can print the same when two numbers differ only in leading zeros (4531 and 004531), so describe such a difference in words.
5. **Matching rules,** optional, in plain sentences, such as how a trust, a custodial or a joint account names its primary owner. Apply a typed rule exactly as written and report it under "Rules applied". Where a rule conflicts with a default below, the typed rule wins. Without rules, use only the defaults.

If a header in any file does not match the defaults in name and order, or a column named here is missing, stop (procedure step 1). Do not guess a match, and do not rename headers for the person.

## The procedure

1. **Check the files.** Compare each file's headers with the defaults, by name and order. Count rows, columns and fields per row. Count households (distinct `household_id`) and distinct account numbers. Stop and list the details if a header differs, if a row has a different number of fields, or if any `account_number` is blank (give the lines). If an export contains a column outside the defaults, such as a birth date, a tax number or a balance, the header check stops the work by the rule above; tell the person the comparison does not need such columns and ask for the export without them.
2. **Fix the ways of comparing.** Names are compared after lowercasing, turning every character that is not a letter or digit into a space, and collapsing spaces; this is "normalised". A hyphen therefore splits a word in two, and the last word of "Okonjo-Reyes" is "Reyes". Emails are compared after trimming spaces and lowercasing. Account numbers are compared as text after trimming spaces; they are never read as numbers. A postal code is compared as text after trimming spaces and lowercasing. Titles are compared normalised. The primary owner of an account is the first name in `owner_names`, unless a typed rule says otherwise.
3. **Match the accounts.** Match each custodian account number to the CRM's. "Exact" means the same text. "After leading zeros" means no exact match, but the same text once leading zeros are removed from both; count these as matched and report them in step 8 (field-by-field differences) as an account number written differently. Everything else is "in the custodian export only" or "in the CRM only". If the same number appears twice in the custodian file, list it in step 7, and leave that account out of steps 4 to 6 and 8, with the reason.
4. **Accounts with no household.** For each custodian-only account, print its line and its fields. Then name every household that has a contact whose normalised name matches a normalised owner name, or whose email matches the mailing email, saying which matched and whether the postal code also agrees. Postal code alone never makes a household possible. If none, say "none; no contact matches an owner name or the mailing email". One question per account.
5. **Accounts the CRM links that the custodian does not show.** For each CRM-only account, print its line, household and title. If any custodian row shows a status such as closed, say whether the export includes such accounts. One question per account.
6. **Household links in question.**
   - An account number linked in the CRM to more than one household: print every line and household. Leave it out of step 8. One question.
   - A link conflict: an account matched to exactly one household where no contact in that household matches any owner name or the mailing email, but a contact in another household does. Print both households, the lines and what matched. Leave it out of step 8. One question.
   - State how many other matched, single-link accounts have a matching contact in their household.
7. **Possible duplicates.** Report, without choosing any record:
   - Contacts in different households with the same email, or with the same normalised name and the same postal code. Print the lines, name what is the same and what differs, including capitals, and any shared household name.
   - Similar names: contacts in different households with the same normalised last word, the same first letter of the first word, the same postal code, and not already reported above. Say they are similar, never that they are the same person.
   - Custodian account numbers that appear more than once.
   - Contacts sharing an email inside one household are not reported.
   - When two findings concern the same records, such as an account linked to two households and the two households that may be one, report each with its own question, and group their decisions on one line only where the options are the same.
8. **Field-by-field differences.** For each matched account with exactly one household link and no conflict, compare: `account_number` (exact or written differently); `account_title`, with the CRM's title; the primary owner's normalised name, against the contacts of the linked household; `mailing_email` against the email of the matched contact; `mailing_postal_code` against that contact's postal code. If the primary owner's name matches no contact but exactly one contact in the household has the same email, say so, report the name difference, and use that contact for the postal code. If no contact can be matched at all, report the name difference and leave email and postal code untested for that account, with the reason. Check every other named owner against the household's contacts and list those not found; a name that a typed rule says is not to be matched to a contact, such as a trust's own name, is not counted as an owner not found, and the output says it was not matched and which rule applies. A field blank on one side and filled on the other is a difference ("blank in the CRM"); blank on both is not. For each difference print the account, the field, both values and both lines. State how many accounts were tested, which were left out and why, and for each field how many agree. List the accounts that agree on every field.
9. **Questions for the operations owner.** One numbered question per finding that needs an answer from a person, in section order, each with its lines and values, answerable in a sentence. Each question proposes the correction as a question ("Should the CRM link this account to this household?"), never as an instruction, and offers no answer.
10. **Decisions for the operations owner.** One numbered line per open choice, grouping findings that call for the same options, naming the questions and only the options that fit: link or correct in the CRM, ask for the custodian's record to be corrected through the firm's usual route, treat as one record, keep as two, leave as it is, or wait for the answer. Recommend none. Final line: verifying each client's identity and authorizing each correction is the operations owner's decision.
11. **Not checked, and trace line.** Say what a comparison of files cannot see: whether people are who the records say, whether a link is right beyond what the files show, households with no accounts (say so; do not name them), other fields and systems, holdings, values and performance. End with the trace line.

## Exceptions and stop conditions

- **A header differs, a row has the wrong number of fields, or an account number is blank:** stop; list the differences or line numbers; ask for the corrected file.
- **An export holds columns outside the defaults:** stop; ask for the export without them.
- **A file looks cut off or is a sample:** say so at the top and say the figures describe the rows supplied only.
- **Similar names or possible duplicate contacts:** list them with the lines and mark each "Needs a person's confirmation"; never settle it.
- **A trust or other account with shared contacts, or a disputed household link:** list it with the lines and a question; never settle it.
- **Asked to merge, relink, delete or correct a record, to produce a corrected file or an import file, or to say which of two records is the real client:** decline; the operations owner decides and makes the change in the firm's own systems.
- **Asked to contact a client, or to check who someone is:** decline; identity is verified by a person from the firm's own client records.
- **Asked whether an account is suitable, what an investment is worth or how it is doing, or whether an account should be closed or opened:** decline; the comparison covers record differences only.
- **Asked for a login, a connection to a system, or an account password:** decline; work only from the files supplied.
- **A figure cannot be recomputed from the rows supplied:** leave it out and say so.

## Output format

```
HOUSEHOLD RECORD DIFFERENCES: [firm label]

For: [who]. Prepared [Today] from [file names with export dates]. Nothing in any record has been changed.

1. THE FILES
Header check: [all three files match the defaults in name and order / the differences, then stop]. crm_households.csv: [n] rows, [n] households. crm_accounts.csv: [n] rows, [n] distinct account numbers. custodian_accounts.csv: [n] rows, [n] distinct account numbers. [Full exports / samples / may be cut off], as stated; the figures describe the rows supplied. Rules applied: [typed rules by number / defaults only].

2. ACCOUNT MATCH
Custodian accounts: [n]. Matched exactly: [n]. Matched after leading zeros: [n]. In the custodian export only: [n]. In the CRM only: [n]. CRM distinct account numbers: [n] ([matched exactly] + [after leading zeros] + [CRM only]).

3. ACCOUNTS WITH NO HOUSEHOLD (in the custodian export, not in the CRM)
- [account] (custodian line [n]): [title], [registration], owner [names], [email], [postal code], [status]. Possible household: [id and name (crm_households line [n], contact), matched on [what]; postal code agrees / differs] [or: none; no contact matches an owner name or the mailing email]. Question [n].
[If none: None found; every custodian account number appears in the CRM.]

4. ACCOUNTS IN THE CRM BUT NOT IN THE CUSTODIAN EXPORT
- [account] (crm_accounts line [n]): household [id and name], title "[title]". [Whether the export includes closed accounts.] Question [n].
[If none: None found; every CRM account number appears in the custodian export.]

5. HOUSEHOLD LINKS IN QUESTION
Linked to more than one household: [account] (crm_accounts lines [n] and [n]): [households and titles]. Left out of the field-by-field differences. Question [n].
Link conflicts: [account] (crm_accounts line [n]; custodian line [n]) is linked to [household], whose contacts are [names]. The owner and the mailing email match [no contact in it; the contact in [household], crm_households line [n]]. Left out of the field-by-field differences. Question [n].
The other [n] matched accounts, each linked to one household, have a contact in that household who matches an owner name or the mailing email.
[Where there are none of a kind: None found.]

6. POSSIBLE DUPLICATES
Contacts in different households that may be one person:
- [name] in [household] (crm_households line [n]) and [household] (line [n]): [what is the same; what differs]. Needs a person's confirmation. Question [n].
Similar names, same postal code, different households (not exact repeats):
- [name] in [household] (line [n]) and [name] in [household] (line [n]): [what is similar; what differs]. Needs a person's confirmation. Question [n].
Accounts repeated in the custodian export: [list with lines / none; [n] distinct account numbers among [n] rows].
[Where there are none of a kind: None found.]

7. FIELD-BY-FIELD DIFFERENCES
Tested: [n] accounts ([n] matched, less [accounts left out and why]).
- [account], [field]: CRM [value] ([file] line [n]); custodian [value] (custodian line [n]). Question [n].
Agreeing, of [n] tested: account_number [n]; account_title [n]; primary owner name [n]; mailing_email [n]; mailing_postal_code [n]. [n] accounts agree on every field: [list].
Other named owners not found among the household's contacts: [list / none].
[If there are no differences: None found; every tested field agrees.]

8. QUESTIONS FOR THE OPERATIONS OWNER
[n]. [Question with lines and values, proposing the correction as a question.]
[If there are none: No questions; nothing was found.]

9. DECISIONS FOR THE OPERATIONS OWNER
[n]. [Open choice (questions [n]): the options that fit.]
Verifying each client's identity and authorizing each correction is [the operations owner]'s decision.

10. NOT CHECKED
[What the files cannot show.] No record has been changed and no client has been contacted.

Every line number counts from the header as line 1 of its file, as supplied on [Today]. This comparison changes no record, contacts no client and judges nothing about any account or investment.
```

## Reviewer checklist

1. The header check is right: each file's headers match the defaults, or the comparison stopped. (Operations owner)
2. The account counts in section 2 add up: matched plus custodian-only equals the custodian rows, and matched plus CRM-only equals the CRM's distinct numbers. (Second person in operations)
3. Every finding names a file and a line, and each line shows the value quoted. (Second person in operations)
4. Every possible household in section 3 rests on a name or email match, never on a postal code alone. (Operations owner)
5. Similar names are labelled similar, not the same, and no record is chosen over another. (Operations owner)
6. Every proposed correction is a question, with no answer offered. (Operations owner)
7. The typed rules were applied as written and listed under "Rules applied". (Operations owner)
8. Nothing says which client is real, whether an account is suitable, or how an investment is doing. (Operations owner)

## Acceptance tests

Proposed tests. The one run so far, on the invented example, is recorded in the trial; none of these ten has been run as a test, though that run did exercise the ordinary-path content of tests 2 to 6 and 8 on the example.

1. **Header mismatch.** Rename one header in the custodian file. Expected: stops after the header check and lists the difference; no section after it.
2. **Account with no household.** Remove one account from the CRM links while its owner stays a contact. Expected: listed in section 3 with the household that matches on name and email, and a question.
3. **Number written differently.** Write one CRM account number without its leading zeros. Expected: counted as matched after leading zeros, reported under field-by-field differences as an account number difference.
4. **Account in two households.** Link one account to two households. Expected: section 5; left out of the field-by-field differences.
5. **Link conflict.** Link an account to a household none of whose contacts matches its owner. Expected: section 5 names the household that does match.
6. **Near match.** Two contacts in different households with the same postal code and names that differ by a few letters. Expected: under similar names, never called the same person.
7. **Postal code alone.** A custodian-only account whose postal code matches a household but whose name and email do not. Expected: no possible household named.
8. **Typed trust rule.** A Trust account whose owner_names starts with the trust's name. Expected: the second name is treated as the primary owner, and rule 1 is listed.
9. **Asked to fix.** Ask for a corrected CRM file. Expected: declines and leaves the decision with the operations owner.
10. **Extra column.** Add a birth-date column to an export. Expected: stops at the header check and asks for the export without it.

## Instructions for the AI assistant

```
You compare a firm's CRM household records with its custodian's account
export and list the differences for the operations owner. You never change,
merge, relink or correct a record, you never contact anyone, and an
operations owner approves every correction. You say nothing about whether an
account is suitable, how an investment is doing, or who a person really is.

The user will supply three files: crm_households.csv (household_id,
household_name, contact_name, contact_role, email, postal_code),
crm_accounts.csv (household_id, account_number, account_title) and
custodian_accounts.csv (account_number, account_title, registration,
owner_names, mailing_email, mailing_postal_code, status), plus settings and
any matching rules in plain sentences. Line 1 of each file is the header and
every line number counts from it. Apply a typed rule exactly as written; it
beats a default. Use no other rule.

1. Check the headers against the defaults, by name and order. If a header
   differs, an extra column is present (such as a birth date, tax number or
   balance), a row has the wrong number of fields, or an account number is
   blank, stop, list the details and ask for a corrected file. Never guess a
   match.
2. Compare names after lowercasing, turning non-letters and non-digits into
   spaces and collapsing spaces (so a hyphen splits a word, and the last
   word of Okonjo-Reyes is Reyes). Compare emails and postal codes trimmed and
   lowercased, account numbers as text. The primary owner is the first name
   in owner_names unless a rule says otherwise.
3. Match custodian accounts to the CRM: exact, or equal after removing
   leading zeros (matched, but reported as a difference in the
   field-by-field comparison, step 8), else
   custodian-only or CRM-only. A custodian account number that appears twice
   is listed under duplicates (step 7) and left out of steps 4 to 6 and 8,
   with the reason.
4. For each custodian-only account, print its line and fields and name every
   household with a contact whose name matches an owner or whose email
   matches the mailing email. A postal code alone never makes a household
   possible.
5. For each CRM-only account, print its line, household and title. If any
   custodian row has a status such as closed, say whether the export includes
   such accounts.
6. Report accounts linked to more than one household, and link conflicts
   (no contact in the linked household matches the owner or email, but a
   contact in another household does). Leave both out of the field-by-field
   comparison (step 8).
7. Report possible duplicates, each marked "Needs a person's confirmation":
   contacts in different households with the same email, or the same name
   and postal code; then similar names (same last word, same first letter,
   same postal code) labelled similar, never the same person; then
   custodian account numbers repeated (no mark). Where two findings concern the same
   records, give each its own question.
8. For matched single-link accounts, compare account number, title, primary
   owner name, mailing email and postal code, and list differences with both
   values and both lines. A field blank on both sides is not a difference; a
   field blank on one side only is. If the primary owner's name matches no
   contact but exactly one contact in the household has the same email, report
   the name difference and use that contact for the postal code; if no contact
   can be matched, report the name difference and leave email and postal code
   untested, with the reason. List other named owners not found among the
   household's contacts, but not a name a typed rule says not to match. Give
   how many were tested, what was left out and why, and how many agree per
   field.
9. Write one numbered question per finding, with lines and values, proposing
   the correction as a question and offering no answer.
10. List the decisions for the operations owner with the options that fit,
    recommend none, and end with: verifying identities and authorizing every
    correction is the operations owner's decision.
11. Say what was not checked (households with no accounts are not named),
    then use the output format exactly, printing
    "None found" with what was checked where a section is empty, and end
    with the trace line. If account numbers are to be masked, print only the
    last four digits after an ellipsis, and describe in words any
    account-number difference the masked values would not show (such as
    leading zeros).

Decline to merge or fix records, produce a corrected or import file, contact
a client, verify an identity, say which record is the real client, or judge
any account or investment. Ask for no password, login code or connection;
work only from the files supplied.
```

## What to customize

- Your matching rules: how joint, trust and custodial accounts name their primary owner, and which fields link an account to a household.
- The file names and column headers, if your exports differ; rename the headers before the run, since a mismatch stops it.
- Whether account numbers are masked, and whether the exports must be cut down before they go to an AI product.
- Which differences the operations owner wants listed first, and how often the comparison runs.
- Who verifies identities and authorizes corrections, and where each decision is recorded.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. It was tried once on its invented example in Claude on 10 November 2026; the record of that run is published with it. Afterward the wording of the instruction block, the output format and the stop conditions was clarified (the "Needs a person's confirmation" mark, the fallback match by email, blank fields, the trust's own name, overlapping findings, hyphenated names, section names in place of numbers); those edits have not been run again. A later pass added clauses to the instruction block (a repeated custodian number, whether closed accounts are included, masking and leading zeros); these have not been run either. Not yet tested in a client environment.
