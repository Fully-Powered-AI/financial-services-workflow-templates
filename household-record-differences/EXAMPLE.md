# Household record differences: an invented example

*Illustrative example with invented data.* The firm, the clients, the account numbers and every row below are invented. The firm is an invented advisory practice, called Firm F here, and every email address uses a reserved example domain. Its operations owner has noticed that a client's second account is missing from the household view and wants the CRM and the custodian's export compared. First come the inputs the operations owner supplied, in full, then the comparison the workflow template returned.

## The inputs

### 1. Settings and rules (typed by the operations owner)

```
Firm label: Firm F
Today: Tuesday 10 November 2026
For: the operations owner
Files: crm_households.csv, crm_accounts.csv (CRM, exported 2026-11-09); custodian_accounts.csv (custodian, exported 2026-11-09). All three are full exports.
Mask account numbers: no
Rule 1: For registration Trust, the first name in owner_names is the trust's name and is not matched to a contact; the second name is the primary owner.
```

### 2. crm_households.csv (header is line 1)

```
household_id,household_name,contact_name,contact_role,email,postal_code
H01,Quill household,Harlan Quill,primary,harlan@example.com,50011
H01,Quill household,Ione Quill,spouse,ione@example.com,50011
H02,Vasko household,Perrin Vasko,primary,perrin@example.org,60022
H03,Okonjo-Reyes household,Dara Okonjo-Reyes,primary,dara@example.net,70033
H03,Okonjo-Reyes household,Mateo Reyes,spouse,mateo@example.net,70033
H04,Brandt household,Tamsin Brandt,primary,tamsin@example.com,80044
H05,Brandt household,Tamsin Brandt,primary,Tamsin@Example.com,80044
H06,Lindqvist Family Trust,Ottoline Lindqvist,trustee,ottoline@example.org,90055
H07,Fenn household,Julius Fenn,primary,jules@example.com,10066
H08,Maddox household,Rhea Maddox,primary,rhea@example.org,20077
H09,Ashgrove household,Bryn Ashgrove,primary,bryn@example.net,40099
H10,Calloway household,Wyn Calloway,primary,wyn@example.com,30088
H11,Nair household,Priya Nair,primary,priya@example.com,11100
H12,Priyanka Nair household,Priyanka Nair,primary,priyanka@example.org,11100
```

### 3. crm_accounts.csv (header is line 1)

```
household_id,account_number,account_title
H01,100101,Quill joint
H01,100102,Ione Quill IRA
H02,200101,Perrin Vasko individual
H03,300101,Okonjo-Reyes joint
H04,400101,Tamsin Brandt individual
H05,400101,Tamsin Brandt individual
H06,500101,Lindqvist Family Trust
H07,600101,Jules Fenn individual
H08,700101,Maddox individual
H08,700102,Maddox joint
H09,4531,Bryn Ashgrove individual
H09,800101,Wyn Calloway individual
H11,110101,Priya Nair individual
H12,120101,Priyanka Nair individual
```

### 4. custodian_accounts.csv (header is line 1)

```
account_number,account_title,registration,owner_names,mailing_email,mailing_postal_code,status
100101,Quill joint,Joint,Harlan Quill; Ione Quill,harlan@example.com,50011,Open
100102,Ione Quill IRA,IRA,Ione Quill,ione@example.com,50011,Open
200101,Perrin Vasko individual,Individual,Perrin Vasko,perrin@example.org,60023,Open
300101,Okonjo-Reyes joint,Joint,Dara Okonjo-Reyes; Mateo Reyes,dara@example.net,70033,Open
300102,Mateo Reyes individual,Individual,Mateo Reyes,mateo@example.net,70033,Open
400101,Tamsin Brandt individual,Individual,Tamsin Brandt,tamsin@example.com,80044,Open
500101,Lindqvist Family Trust,Trust,Lindqvist Family Trust; Ottoline Lindqvist,ottoline@example.org,90055,Open
600101,Jules Fenn individual,Individual,Jules Fenn,jules@example.com,10066,Open
700101,Rhea Maddox individual,Individual,Rhea Maddox,rhea@example.org,20077,Open
004531,Bryn Ashgrove individual,Individual,Bryn Ashgrove,bryn@example.net,40099,Open
800101,Wyn Calloway individual,Individual,Wyn Calloway,wyn@example.com,30088,Open
900101,Seren Holt individual,Individual,Seren Holt,seren@example.org,12200,Closed
110101,Priya Nair individual,Individual,Priya Nair,priya@example.com,11100,Open
120101,Priyanka Nair individual,Individual,Priyanka Nair,priyanka@example.org,11100,Open
```

## The comparison

```
HOUSEHOLD RECORD DIFFERENCES: Firm F

For: the operations owner. Prepared Tuesday 10 November 2026 from crm_households.csv and crm_accounts.csv (CRM, exported 2026-11-09) and custodian_accounts.csv (custodian, exported 2026-11-09). Nothing in any record has been changed.

1. THE FILES
Header check: all three files match the defaults in name and order. crm_households.csv: 14 rows, 12 households. crm_accounts.csv: 14 rows, 13 distinct account numbers. custodian_accounts.csv: 14 rows, 14 distinct account numbers. Full exports, as stated; the figures describe the rows supplied. Rules applied: typed rule 1 (Trust registrations); defaults for the rest.

2. ACCOUNT MATCH
Custodian accounts: 14. Matched exactly: 11. Matched after leading zeros: 1. In the custodian export only: 2. In the CRM only: 1. CRM distinct account numbers: 13 (11 + 1 + 1).

3. ACCOUNTS WITH NO HOUSEHOLD (in the custodian export, not in the CRM)
- 300102 (custodian line 6): Mateo Reyes individual, Individual, owner Mateo Reyes, mateo@example.net, 70033, Open. Possible household: H03 Okonjo-Reyes household (crm_households line 6, contact Mateo Reyes), matched on owner name and mailing email; the postal code 70033 also agrees. Question 1.
- 900101 (custodian line 13): Seren Holt individual, Individual, owner Seren Holt, seren@example.org, 12200, Closed. Possible household: none; no contact matches an owner name or the mailing email. Question 2.

4. ACCOUNTS IN THE CRM BUT NOT IN THE CUSTODIAN EXPORT
- 700102 (crm_accounts line 11): household H08 Maddox household, title "Maddox joint". No custodian row carries this number, exactly or after leading zeros. The export does include closed accounts (900101 is one). Question 3.

5. HOUSEHOLD LINKS IN QUESTION
Linked to more than one household: 400101 (crm_accounts lines 6 and 7): H04 Brandt household and H05 Brandt household, both titled "Tamsin Brandt individual". Left out of the field-by-field differences. Question 4.
Link conflicts: 800101 (crm_accounts line 13; custodian line 12) is linked to H09 Ashgrove household, whose only contact is Bryn Ashgrove (crm_households line 12, bryn@example.net). The owner Wyn Calloway and the mailing email wyn@example.com match no contact in H09; both match the contact Wyn Calloway in H10 Calloway household (crm_households line 13). Left out of the field-by-field differences. Question 5.
The other 10 matched accounts, each linked to one household, have a contact in that household who matches an owner name or the mailing email.

6. POSSIBLE DUPLICATES
Contacts in different households that may be one person:
- Tamsin Brandt in H04 (crm_households line 7) and H05 (line 8): same name; same email apart from capitals (tamsin@example.com, Tamsin@Example.com); same postal code 80044; both households are named "Brandt household". Needs a person's confirmation. Question 6.
Similar names, same postal code, different households (not exact repeats):
- Priya Nair in H11 (line 14) and Priyanka Nair in H12 (line 15): same family name, same first letter, postal code 11100; the emails differ (priya@example.com, priyanka@example.org). Needs a person's confirmation. Question 7.
Accounts repeated in the custodian export: none; 14 distinct account numbers among 14 rows.

7. FIELD-BY-FIELD DIFFERENCES
Tested: 10 accounts (12 matched, less 400101 and 800101, which section 5 explains).
- 200101, mailing_postal_code: CRM 60022 (crm_households line 4, Perrin Vasko); custodian 60023 (custodian line 4). Question 8.
- 600101, primary owner name: the custodian owner "Jules Fenn" (custodian line 9) is not among the contacts of H07; the contact with the same mailing email, jules@example.com, is "Julius Fenn" (crm_households line 10). Email and postal code (10066) agree with that contact. Question 9.
- 700101, account_title: CRM "Maddox individual" (crm_accounts line 10); custodian "Rhea Maddox individual" (custodian line 10). Question 10.
- 4531 / 004531, account_number: CRM "4531" (crm_accounts line 12); custodian "004531" (custodian line 11). Matched after leading zeros; every other field agrees. Question 11.
Agreeing, of 10 tested: account_number 9; account_title 9; primary owner name 9; mailing_email 10 (for 600101 the contact was found through the email); mailing_postal_code 9. Six accounts agree on every field: 100101, 100102, 300101, 500101, 110101, 120101.
Other named owners not found among the household's contacts: none (100101: Ione Quill; 300101: Mateo Reyes). On 500101 the trust's name was not matched, by rule 1; Ottoline Lindqvist was compared.

8. QUESTIONS FOR THE OPERATIONS OWNER
1. Account 300102 (custodian line 6) is held by Mateo Reyes, a contact in H03 (crm_households line 6) with the same email and postal code, and the CRM links no household to it. Should the CRM link 300102 to H03?
2. Account 900101 (custodian line 13, Closed, owner Seren Holt) has no household and no contact matching its owner or email. Should it be linked to a household, or left unlinked because it is closed?
3. The CRM links 700102 (crm_accounts line 11) to H08, but the custodian export has no such account. Should the link be removed, or corrected to a different number?
4. Account 400101 is linked to both H04 and H05 (crm_accounts lines 6 and 7). Which household should hold it?
5. Account 800101 is linked to H09, but its owner and email match the contact Wyn Calloway in H10 (crm_households line 13). Should the CRM link 800101 to H10 instead of H09?
6. Are H04 and H05 (crm_households lines 7 and 8: Tamsin Brandt, the same email apart from capitals, postal code 80044) one household recorded twice? If so, which record should remain?
7. Are Priya Nair (H11, line 14) and Priyanka Nair (H12, line 15) the same person, or two people sharing a postal code?
8. Which postal code is current for Perrin Vasko, the CRM's 60022 or the custodian's 60023, and which system should change?
9. Is the contact Julius Fenn (crm_households line 10) the account owner Jules Fenn (custodian line 9), and which spelling is correct?
10. Which title is right for 700101: "Maddox individual" or "Rhea Maddox individual"?
11. Should the CRM write account 4531 as "004531", as the custodian does?

9. DECISIONS FOR THE OPERATIONS OWNER
1. Links to add or move (questions 1, 2, 4, 5): link in the CRM, leave as it is, or wait for the answer.
2. The link to 700102 (question 3): correct in the CRM, ask for the custodian's record to be corrected through the firm's usual route, leave as it is, or wait.
3. Possible duplicates (questions 6, 7): treat as one record, keep as two, or wait for the answer.
4. Field differences (questions 8 to 11): correct in the CRM, ask for the custodian's record to be corrected through the firm's usual route, leave as it is, or wait.
Verifying each client's identity and authorizing each correction is the operations owner's decision.

10. NOT CHECKED
Whether any owner or contact is who the records say; whether a household link is right beyond what the files show; households with no accounts; contact fields other than those in the exports; account holdings, values and performance; any other system. No record has been changed and no client has been contacted.

Every line number counts from the header as line 1 of its file, as supplied on Tuesday 10 November 2026. This comparison changes no record, contacts no client and judges nothing about any account or investment.
```
