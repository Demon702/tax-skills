---
name: nra-tax-checklist
description: Walk a Non-Resident Alien through tax filing requirements and produce a personalized document checklist with detailed instructions. Use when user mentions NRA taxes, 1040-NR, F-1/J-1 tax filing, international student taxes, Sprintax, treaty benefits, Form 8843, or asks about tax obligations as an international student or worker in the US.
user-invocable: true
---

# NRA Tax Document Checklist Generator

Walk a Non-Resident Alien (NRA) through an interactive questionnaire and produce a personalized table of required tax documents with detailed instructions on how to obtain each one.

**Important:** This is an educational and organizational tool. It does not constitute tax advice. Recommend consulting a qualified tax professional for complex situations.

Ask questions **one at a time**. Each question must include prepopulated multiple-choice options (A, B, C, etc.) so the user can reply with just a letter. Always include an "Other" option for free-text answers. Allow shorthand answers (letter only or brief text). Skip questions that don't apply based on earlier answers. After receiving each answer, **briefly acknowledge what the user said and explain what it implies for their tax situation** (e.g., which forms they'll need, their filing status, exemptions, or key rules that apply) before asking the next question. Confirm all answers before generating output.

---

## Phase 1: Gather Information

### Category 1 — Visa & Residency (ask first — determines everything else)

Ask these questions **one at a time**, waiting for each answer before asking the next:

**Question 1 — Visa type:**
> What visa are you on?
> - A. F-1 (student)
> - B. J-1 (exchange visitor)
> - C. H-1B (specialty occupation)
> - D. L-1 (intracompany transfer)
> - E. O-1 (extraordinary ability)
> - F. TN (NAFTA professional)
> - G. Other (please specify)

> *(If user selected B (J-1), ask:)*
>
> **1a.** What is your J-1 category?
> - A. Student
> - B. Research scholar / Professor
> - C. Short-term scholar
> - D. Trainee / Intern
> - E. Other (please specify)
>
> *(This matters because J-1 students get a 5-year exemption from the Substantial Presence Test, while J-1 non-students (scholars, professors, researchers) only get a 2-year exemption.)*

**Question 2 — Arrival date:**
> When did you first arrive in the US on a student or exchange visitor visa? If you have been in the US on multiple visas, enter the earliest arrival date.
> - A. 2025
> - B. 2024
> - C. 2023
> - D. 2022
> - E. 2021
> - F. 2020 or earlier (please specify year)
>
> *(Tip: You can also type a month/year like "Aug 2021" — I'll count the calendar years for you.)*

**Question 3 — Country of citizenship:**
> What country are you a citizen of?
> - A. India
> - B. China
> - C. South Korea
> - D. Canada
> - E. Mexico
> - F. Japan
> - G. Taiwan
> - H. Other (please specify)

**Question 4 — Current status:**
> What is your current status?
> - A. Full-time student
> - B. On OPT (Optional Practical Training — initial 12 months)
> - C. On STEM OPT extension (24-month extension)
> - D. On CPT (Curricular Practical Training)
> - E. Full-time employee (H-1B, L-1, O-1, TN, or other work visa)
> - F. Other (please specify)

**Question 5 — Filing status:**
> What is your filing status?
> - A. Single
> - B. Married

> *(If user selected B (Married), ask:)*
>
> **5a.** Is your spouse a US citizen or resident alien?
> - A. Yes — US citizen or green card holder
> - B. Yes — resident alien (passes Substantial Presence Test)
> - C. No — also a non-resident alien
> - D. Not sure
>
> *(This determines your filing status. Married NRAs almost always file as "Married Filing Separately" on 1040-NR. The only exception is if both spouses elect to be treated as residents under IRC 6013(g) — but this means filing Form 1040, not 1040-NR.)*

**Question 5b — Visa change:**
> Did your visa type change at any point during the tax year?
> - A. No — same visa all year
> - B. Yes — changed from F-1 to H-1B
> - C. Yes — changed from J-1 to H-1B
> - D. Yes — other change (please specify)
>
> *(If yes, ask:)* When did the change take effect? (month/year)

After receiving all answers from Category 1, determine NRA vs Resident Alien status using Phase 2 logic before continuing. If the user is determined to be a Resident Alien, stop and redirect them to standard filing tools (TurboTax, H&R Block, FreeTaxUSA).

### Category 2 — Employment & Income

Ask these questions **one at a time**, skipping any that clearly don't apply based on earlier answers:

**Question 6 — W-2 employment:**
> Do you have W-2 wage income?
> - A. Yes
> - B. No
>
> *(If yes, ask the following sub-questions one at a time:)*
>
> **6a.** How many W-2 employers did you have in the tax year?
> - A. 1
> - B. 2
> - C. 3 or more (please specify)
>
> **6b.** *(Ask once per employer. If only 1 employer, ask once. If 2+, label them Employer 1, Employer 2, etc.)*
> For [Employer N]: What is the company name, what state do you work in, and is this full-time or part-time?
> *(Example answer: "NVIDIA, California, full-time")*
>
> **6c.** *(Ask once per employer)* Which payroll system does [Employer N] use?
> - A. ADP
> - B. UKG (UltiPro)
> - C. Workday
> - D. Paycom
> - E. Other / Not sure
>
> *(Tip: If you only have one employer, this is quick — just three extra questions. If you have multiple, I'll ask about each one so we can track your W-2s separately.)*

**Question 7 — Stock compensation:**
> Do you have any stock compensation through any of your employers? (select all that apply)
> - A. RSUs (Restricted Stock Units)
> - B. ESPP (Employee Stock Purchase Plan)
> - C. Stock options (ISOs or NSOs)
> - D. Multiple — specify which (e.g., "A and B")
> - E. None
>
> *(If user selected A, B, C, or D, ask:)*
>
> **7a.** Which platform manages your stock compensation?
> - A. Schwab Equity Awards (formerly Charles Schwab)
> - B. E*Trade (Morgan Stanley at Work)
> - C. Fidelity Stock Plan Services (NetBenefits)
> - D. Shareworks (Morgan Stanley)
> - E. Other (please specify)
>
> *(Note: Stock compensation is typically offered only by full-time employers. If you have multiple employers, this usually applies to your primary full-time employer.)*

**Question 8 — Personal brokerage accounts:**
> Do you have any personal investment or brokerage accounts **separate from** your employer stock compensation platform? (select all that apply)
> - A. Robinhood
> - B. Charles Schwab (personal brokerage, not Schwab Equity Awards)
> - C. Fidelity (personal brokerage, not NetBenefits stock plan)
> - D. Vanguard
> - E. Interactive Brokers
> - F. Webull
> - G. Other (please specify)
> - H. None — I only have my employer stock plan
>
> *(This is separate from your employer stock compensation account from Q7a. Personal portfolios generate their own tax documents — a separate Consolidated 1099 — even if they happen to be at the same institution.)*

**Question 9 — Stock sales:**
> Did you sell any stocks this year — across any of your accounts (employer stock plan or personal brokerage)?
> - A. Yes — had gains
> - B. Yes — had losses only
> - C. Yes — had both gains and losses
> - D. No
>
> *(If user selected A, B, or C, ask:)*
>
> **9a.** Which account(s) did you sell stocks through? (select all that apply)
> - A. Employer stock plan platform (from Q7a)
> - B. Personal brokerage (from Q8)
> - C. Other brokerage not mentioned before (please specify)
>
> *(Tip: If you sold RSUs/ESPP shares through your employer stock plan AND also sold stocks in your personal portfolio, select both A and B. Each platform will issue its own 1099-B.)*

**Question 10 — Dividends:**
> Did you receive any dividend income — from either your employer stock plan or personal brokerage accounts?
> - A. Yes
> - B. No
> - C. Not sure
>
> *(If user selected A or C, ask:)*
>
> **10a.** Which account(s) generated dividends? (select all that apply)
> - A. Employer stock plan platform (from Q7a)
> - B. Personal brokerage (from Q8)
> - C. Other account not mentioned before (please specify)
>
> *(Tip: Dividends can come from both your employer RSUs/ESPP held at your stock plan platform AND from stocks in your personal brokerage. Each platform issues its own 1099-DIV or Consolidated 1099 — check both.)*

**Question 11 — Bank/savings interest:**
> Do you have a savings account, HYSA, or CDs that earned interest?
> - A. Yes
> - B. No
>
> *(If user selected A, ask:)*
>
> **11a.** Which bank(s) hold your savings/HYSA/CDs? (select all that apply)
> - A. Marcus by Goldman Sachs
> - B. Ally Bank
> - C. Discover Bank
> - D. Capital One
> - E. Wealthfront Cash Account
> - F. SoFi
> - G. Apple Savings (via Goldman Sachs)
> - H. Other (please specify)

**Question 12 — Scholarship/fellowship:**
> Did you receive any scholarship or fellowship income?
> - A. Yes — for tuition/fees only
> - B. Yes — includes room/board/living expenses
> - C. Yes — not sure what it covers
> - D. No

*(Skip this question if user is a full-time employee and not a student.)*

*(Note: If your assistantship income (TA/RA) appears on a W-2, it is already covered under the W-2 questions above. This question is about non-W-2 scholarship or fellowship income.)*

**Question 13 — Self-employment:**
> Did you do any freelance work or receive 1099-NEC income?
> - A. Yes
> - B. No

**Question 13b — Cryptocurrency/digital assets:**
> Did you buy, sell, exchange, or receive any cryptocurrency or digital assets (e.g., Bitcoin, Ethereum, stablecoins)?
> - A. Yes — sold or exchanged (had gains)
> - B. Yes — sold or exchanged (had losses only)
> - C. Yes — received as income (staking, mining, airdrop)
> - D. Yes — both sold/exchanged and received as income
> - E. No
>
> *(If user selected A, C, or D, ask:)*
>
> **13c.** Which platform(s) did you use? (select all that apply)
> - A. Coinbase
> - B. Kraken
> - C. Gemini
> - D. Crypto.com
> - E. Other (please specify)
>
> *(Note: The IRS requires all filers to answer a mandatory yes/no digital asset question on Form 1040-NR. Starting with tax year 2025, exchanges may issue Form 1099-DA or 1099-B for crypto transactions.)*

**Question 14 — Rental income:**
> Did you receive any rental income from US property?
> - A. Yes
> - B. No

**Question 14b — Gambling or lottery winnings:**
> Did you have any gambling or lottery winnings (casino, sports betting, lottery)?
> - A. Yes
> - B. No
>
> *(NRA gambling winnings from US sources are subject to 30% flat rate withholding. Casinos issue Form W-2G. Unlike US residents, NRAs cannot deduct gambling losses.)*

### Category 3 — Benefits & Accounts

**Question 15 — HSA:**
> Do you have a Health Savings Account (HSA)?
> - A. Yes
> - B. No
>
> *(If yes, ask three follow-ups one at a time:)*
>
> **15a.** Did your employer contribute to it? (check W-2 Box 12 Code W)
> - A. Yes
> - B. No
> - C. Not sure
>
> **15b.** Did you make personal after-tax contributions to your HSA (not through payroll)?
> - A. Yes
> - B. No
>
> **15c.** Did you take any distributions (withdrawals) from your HSA?
> - A. Yes — for medical expenses
> - B. Yes — for non-medical expenses
> - C. No
>
> **15d.** Who is your HSA provider?
> - A. Fidelity
> - B. Optum Bank (UnitedHealth)
> - C. HealthEquity
> - D. HSA Bank (Webster Bank)
> - E. Lively
> - F. Other (please specify)

**Question 16 — 401k/retirement:**
> Do you contribute to a 401k or other retirement plan?
> - A. Yes
> - B. No
>
> *(If yes, ask:)*
>
> **16a.** Did you take any distributions or withdrawals from your 401k, IRA, or other retirement account this year?
> - A. Yes
> - B. No

**Question 17 — Health insurance:**
> Where does your health insurance come from?
> - A. Employer
> - B. University/school
> - C. Healthcare marketplace (ACA)
> - D. None / uninsured
> - E. Other (please specify)

### Category 4 — Special Situations

**Question 18 — Electric vehicle:**
> Did you buy or lease an electric vehicle this year?
> - A. Yes — purchased
> - B. Yes — leased
> - C. No

**Question 19 — Foreign accounts:**
> Do you have any bank accounts outside the US?
> - A. Yes — combined balance exceeded $10,000 at some point
> - B. Yes — combined balance stayed under $10,000
> - C. No

**Question 20 — Estimated payments:**
> Did you make any estimated tax payments directly to the IRS or state tax office (not through your employer)?
> - A. Yes
> - B. No

**Question 21 — Prior returns:**
> Have you filed US tax returns in prior years?
> - A. Yes
> - B. No
> - C. This is my first year needing to file

**Question 22 — States:**
> Which state(s) did you live and/or work in during the tax year?
> - A. California
> - B. New York
> - C. Texas
> - D. Washington
> - E. Massachusetts
> - F. Illinois
> - G. New Jersey
> - H. Other (please specify)
> - I. Multiple states (please list them)

### Confirm Before Generating

After all questions are answered, present a summary of the user's answers and ask them to confirm before generating the output. Example:

> **Your Tax Profile Summary:**
> - Visa: F-1 OPT | Years in US: 4 | Country: India | Status: Full-time employee
> - Employer 1: NVIDIA (California, full-time) | Payroll: Workday
> - Employer 2: Starbucks (California, part-time) | Payroll: ADP *(only show if multiple employers)*
> - RSUs: Yes (Schwab Equity Awards) | ESPP: Yes (Schwab Equity Awards)
> - Stock sales: Losses only (Robinhood) | Dividends: Yes (Robinhood, Schwab)
> - Bank interest: Yes — Marcus, Apple Savings | HSA: Yes via Fidelity (employer contributions + distributions)
> - Foreign accounts: No | EV: Leased | Prior returns: Yes
>
> Does this look correct? I'll generate your document checklist.

---

## Phase 2: Determine Tax Status

### NRA vs Resident Alien Decision Tree

**F-1 visa (and J-1 students):**
- 5 or fewer calendar years in the US → **Non-Resident Alien** (exempt individual, does not count days for Substantial Presence Test)
- More than 5 calendar years → Apply Substantial Presence Test. If they pass → **Resident Alien**. If they fail → still NRA.
- Note: The 5-year count is by calendar year, not exact days. Arriving in December 2020 counts as 1 full year.

**J-1 non-students (scholars, professors, researchers, short-term scholars):**
- 2 or fewer calendar years in the US → **Non-Resident Alien** (exempt individual)
- More than 2 calendar years → Apply Substantial Presence Test.
- Note: J-1 non-students have a shorter exemption period than J-1 students. The 2-year count is by calendar year.

- **CPT (Curricular Practical Training):** CPT participants are still F-1 students for tax purposes. The same NRA determination and FICA exemption rules apply as for any other F-1 student.

**H-1B, L-1, O-1, TN visa:**
- These visas are NOT exempt from the Substantial Presence Test
- If present in the US for 183+ days in the current year, OR meet the 3-year lookback formula → **Resident Alien**
- Most H-1B/L-1/O-1/TN holders who have been in the US for a full year are Resident Aliens
- Flag: "Based on your visa type and time in the US, you are likely a Resident Alien. This means you file Form 1040 (not 1040-NR) and can use standard tax filing tools like TurboTax, H&R Block, or FreeTaxUSA. The rest of this checklist is designed for NRAs — would you like to continue anyway, or would you prefer guidance for Resident Alien filing?"

**F-1 to H-1B mid-year transition (most common visa change):**
- If the user changed from F-1 to H-1B during the tax year (typically October 1):
  - FICA exemption ends on the H-1B effective date. The user may have two W-2s, or one W-2 with a mid-year FICA change.
  - If the F-1 portion was within the 5-year window AND the H-1B portion is too short to pass SPT → still NRA for the full year. File 1040-NR.
  - If the H-1B portion causes the user to pass SPT → Resident Alien for the full year (or dual-status). File Form 1040 (not 1040-NR).
  - Flag: "You changed visas mid-year. Your FICA exemption ended on your H-1B start date. Check that your W-2 correctly reflects FICA withholding only for the H-1B portion. If your total days in the US in the calendar year exceed 183, you likely pass the Substantial Presence Test and are a Resident Alien — use TurboTax or H&R Block instead."

**Dual-status filing year:**
- Applies when a person is an NRA for part of the year and a Resident Alien for the rest.
- File Form 1040 with a "Dual-Status Statement" attached (not Form 1040-NR).
- Cannot use the standard deduction on a dual-status return.
- This most commonly happens when an H-1B holder passes SPT mid-year.
- Sprintax has limited dual-status support. Consult a tax professional specializing in international tax.

**Other edge cases (mid-year marriage to US citizen, multiple visa changes, etc.):**
- Flag: "Your situation is complex and may involve dual-status filing or a Section 6013(g) election. Consult a tax professional who specializes in international tax."

### FICA Exemption Determination

- **F-1/J-1 with 5 or fewer calendar years:** EXEMPT from Social Security and Medicare taxes. W-2 Box 3 (Social Security wages) and Box 5 (Medicare wages) should be $0.00 on ALL of your W-2s. If any W-2 shows a non-zero amount, that employer may have incorrectly withheld FICA — first ask that employer to correct it, then file Form 843 for a refund if they cannot.
- **F-1/J-1 with more than 5 years:** NOT exempt. FICA applies normally.
- **F-1/J-1 in 6th+ calendar year who is still NRA:** You lose the FICA exemption but may still be an NRA if you fail the Substantial Presence Test (e.g., due to extensive travel). In this case, your W-2 Boxes 3 and 5 WILL show amounts — this is correct. You file 1040-NR but owe FICA. This is an unusual combination — verify with a tax professional.
- **J-1 non-students (scholars, professors, researchers):** Only exempt from FICA for the first 2 calendar years (not 5). After 2 years, FICA applies normally.
- **H-1B/L-1/O-1/TN:** NOT exempt. FICA applies normally.

---

## Phase 3: Generate Output

Generate all six sections below. Only include rows/items that apply to the user's specific situation.

### Section A: Tax Status Summary

| Item | Details |
|------|---------|
| Filing status | [Single / Married Filing Separately] |
| Tax form | Form 1040-NR |
| Visa type | [F-1/J-1/etc.] |
| NRA status basis | [Exempt individual / Substantial Presence Test failure] |
| FICA exempt? | [Yes — first 5 calendar years / No] |
| Treaty eligible? | [Yes — [Country] treaty / No treaty available] |
| Treaty benefit | [Amount/type from treaty-reference.md] |
| Treaty form | Form 8833 (treaty-based return position disclosure) |
| State filing | [State return name, e.g., CA 540NR] |

### Section B: Required Documents Table

Generate this table with ONLY the rows that apply. Each row should have detailed "How to Obtain" instructions.

| Document | Purpose | Source | How to Obtain | Deadline | Required? | NRA-Specific Notes |
|----------|---------|--------|---------------|----------|-----------|-------------------|

**Conditional rows — include only if applicable:**

**If user has W-2 employment:**
| W-2 | Reports wages and tax withholding | Employer payroll system(s) | Log into each employer's payroll portal (see Section F for platform-specific steps based on your payroll system). Navigate to Tax Documents or Pay > Tax Forms. Download all copies. Copy B is for federal, Copy 2 is for state. If unavailable online, contact that employer's HR/Payroll department. **If you have multiple employers, you will receive a separate W-2 from each. Download and enter each one separately in Sprintax.** | Employer must issue by Jan 31 | Required | Check Box 3/5 = $0 if FICA exempt — **check this on ALL W-2s if you have multiple employers**, as each employer withholds FICA independently. Box 12 Code W (HSA) is excluded from federal wages but some states add it back — this explains Box 1 vs Box 16 discrepancy. RSU income is already included in Box 1 — do NOT double-count. |

**If user has RSUs:**
| Equity Activity Statement | Confirms RSU vesting details and withholding rates | [User's stock plan platform from Q7a] | See Section F for platform-specific steps to download this from [platform name]. | Available by Feb 15 | Informational | RSU income is already in your W-2 Box 1. This statement is for your records to verify withholding rates (typically 22% federal, 10.23% CA). Net share settlement means shares were withheld for taxes — no 1099-B is issued, which is expected. |

**If user has ESPP and did NOT sell shares:**
| Form 3922 | ESPP purchase information | [User's stock plan platform from Q7a] | See Section F for platform-specific steps to download this from [platform name]. | Available by Jan 31 | Informational only — do NOT file | No tax impact until shares are sold. Keep this for future reference — you'll need the purchase price and FMV when you eventually sell. |

**If user has ESPP and DID sell shares:**
| Form 3922 | ESPP purchase information | [User's stock plan platform from Q7a] | See Section F for platform-specific steps to download this from [platform name]. | Available by Jan 31 | Required for calculating gain/loss | Compare Form 3922 purchase price with sale price to determine if qualifying or disqualifying disposition. |

**If user sold stocks with gains:**
| 1099-B or 1042-S | Reports stock sales proceeds and cost basis | [User's brokerage from Q9a] | See Section F for platform-specific steps to download this from [platform name]. May be part of a Consolidated 1099. Some platforms (especially employer stock plan platforms) may issue 1042-S instead of 1099-B to NRAs — check your Tax Documents for whichever form was issued. Both are valid for filing. | Available by Feb 15 (1099-B) or March 15 (1042-S) | Required | Most brokerages issue 1099-B to all customers, including NRAs — this is normal. However, some platforms (including employer stock plan platforms like Schwab Equity Awards, E\*Trade, and Fidelity NetBenefits) may issue 1042-S instead. Either form is valid. NRA capital gains taxed at 30% flat rate (if present 183+ days in US). Some treaty rates may reduce this. Report on Schedule NEC or Schedule D of 1040-NR. |

**If user sold stocks with losses only:**
| (No 1099-B needed) | — | — | — | — | — | NRAs cannot deduct capital losses. If you sold at a loss, there is nothing to report. You may still receive a 1099-B from your broker — you can disregard the loss portion. If your broker issued a 1099-DIV or 1042-S for dividends from the same account, enter that separately under dividend income. |

**If user has cryptocurrency gains:**
| 1099-DA or 1099-B | Reports digital asset sale proceeds | [User's crypto platform from Q13c] | Log into your exchange (Coinbase: coinbase.com, Kraken: kraken.com, Gemini: gemini.com) → Tax Center or Tax Documents. Download 1099-DA or 1099-B. | Available by Feb 15 | Required | NRA crypto capital gains follow the same rules as stock gains — taxed at 30% flat rate if present 183+ days, potentially exempt if present fewer than 183 days. Losses are NOT deductible for NRAs. |

**If user has dividends:**
| 1099-DIV or 1042-S | Reports dividend income | [User's brokerage from Q10a] | See Section F for platform-specific steps to download this from [platform name]. May be part of a Consolidated 1099. **You may receive either 1099-DIV or 1042-S** depending on how your broker/platform classifies your account — check your Tax Documents for whichever form was issued. Both are valid for filing. | Available by Feb 15 (1099-DIV) or March 15 (1042-S) | Required | Most US personal brokerages (Robinhood, Vanguard, Webull, etc.) classify NRAs as US persons and issue 1099-DIV. However, some platforms — especially employer stock plan platforms (Schwab Equity Awards, E\*Trade, Fidelity NetBenefits) and brokerages where you filed a W-8BEN (notably Interactive Brokers) — may issue 1042-S instead. Either form is valid. Enter whichever you receive in Sprintax as-is. For 1042-S: Income Code 06 = dividends; check that the tax rate and withholding match your treaty rate. The dividend tax rate for NRAs is 30% or reduced treaty rate (e.g., 25% for India, 10% for China). |

**If user has bank/savings interest:**
| 1099-INT | Reports interest income | [User's bank(s) from Q11a] | See Section F for platform-specific steps to download this from [bank name]. Note: banks only issue 1099-INT if interest earned is $10 or more. If you earned less than $10, no form will be issued. | Available by Jan 31 | Required (if issued) | Bank deposit interest is EXEMPT from federal tax for NRAs under IRC 871(i)(2)(A). Enter in Sprintax and select "paid to me by a U.S. bank" — Sprintax will apply the exemption. Note: your STATE may still tax this income (e.g., California does). Most US banks issue 1099-INT to all customers regardless of NRA status — this is normal. You may optionally submit Form W-8BEN to your bank for NRA classification, but the federal tax exemption applies either way. |

**If user has HSA distributions:**
| 1099-SA | Reports HSA distributions | [User's HSA provider from Q15d] | See Section F for platform-specific steps to download this from [HSA provider name]. | Available by Jan 31 | Required | Requires Form 8889 to be filed. If using Sprintax, do NOT enter this in the standard flow — contact Sprintax support after payment and provide your W-2 + 1099-SA. Sprintax tax experts handle Form 8889 manually. If distribution was for qualified medical expenses, no tax or penalty. |

**If user has employer health insurance:**
| 1095-C | Employer health coverage proof | Employer payroll system | Log into your employer's payroll portal. Navigate to Tax Documents. Download Form 1095-C. | Available by March 2 | Informational only — do NOT file | This form proves you had health coverage. It is NOT filed with your tax return. Keep for your records. |

**If user has scholarship/fellowship income:**
| 1042-S and/or 1098-T | Reports scholarship/fellowship amounts | University financial aid office | Check your university's student portal for tax documents. The financial aid or bursar's office can also provide these. Your university may issue a 1042-S, a 1098-T, or both — check your student portal for all available tax documents. | 1042-S by March 15; 1098-T by Jan 31 | Required | Scholarship amounts used for tuition/fees/books are generally tax-free. Amounts for room/board/living expenses are taxable. Treaty benefits may exempt some or all of this income. |

**If user has self-employment income:**
| 1099-NEC | Reports non-employee compensation | Client/payer who paid you | Request from the business that paid you, or check for it in their payment portal. | Available by Jan 31 | Required | NRA self-employment income may require different treatment. May need to file Schedule C with 1040-NR. Consult a tax professional for self-employment tax obligations. |

**If user has gambling winnings:**
| W-2G | Reports gambling/lottery winnings | Casino or gaming platform | Casinos issue Form W-2G at the time of the win or mail it by Jan 31. Check with the casino's player services if not received. For online sports betting, check the platform's tax documents section. | Available by Jan 31 | Required | NRA gambling winnings are subject to 30% flat rate withholding (or reduced treaty rate). Unlike US residents, NRAs CANNOT deduct gambling losses against winnings. Some treaty countries have reduced rates on gambling income. |

**If user took 401k/IRA distributions:**
| 1099-R | Reports retirement plan distributions | 401k plan administrator or IRA custodian | Log into your retirement plan provider's website → Tax Documents or Statements. | Available by Jan 31 | Required | Early distributions (before age 59½) are subject to 10% penalty + 30% NRA withholding. The plan administrator typically withholds at 30% for NRAs. Report on Form 1040-NR. |

**If FICA was incorrectly withheld (W-2 Box 3/5 non-zero for FICA-exempt individual):**
| Form 843 | Claim for refund of incorrectly withheld FICA | Self-prepared | First ask your employer to correct and refund. If they cannot, file Form 843 with the IRS. Attach: copy of W-2, letter from employer stating they cannot correct, copy of I-94, copy of I-20/DS-2019, and Form 8316. Mail to the IRS service center for your area. | File after employer refuses correction | Required if applicable | Only needed if your employer incorrectly withheld Social Security and/or Medicare taxes while you were FICA exempt. |

**If user made estimated tax payments:**
| Estimated payment confirmations | Verify credits on your return | IRS and/or state tax office | For IRS: check IRS.gov account or keep confirmation numbers from IRS Direct Pay / EFTPS. For state: check your state's tax website payment history. | N/A | Required for accuracy | Enter the total estimated payments made when filing your return so they are credited against your tax liability. Keep confirmation numbers and payment dates. |

**If user has healthcare marketplace (ACA) insurance:**
| 1095-A | Health Insurance Marketplace statement | Healthcare.gov or state marketplace | Log into healthcare.gov or your state marketplace → Tax Forms. Download Form 1095-A. | Available by Jan 31 | Required | Form 1095-A reports advance premium tax credits. NRAs are generally not eligible for the Premium Tax Credit, but the form must still be reconciled on the return. Note: some states (CA, NJ, MA, DC, RI) have individual mandate penalties for being uninsured. |

**Always include for F-1/J-1 visa holders:**
| I-20 (F-1) or DS-2019 (J-1) | Required for Form 8843 | University international office | Check your university's international student portal. If expired or lost, contact the International Student Services Office (ISSO/ISSS) to request a copy. You need the SEVIS ID and program dates. | Keep current | Required | Needed to complete Form 8843 (Exempt Individual statement). Sprintax will ask for your SEVIS ID number from this form. |

**Always include for NRAs:**
| I-94 Record | Entry/exit record for residency determination | CBP (Customs and Border Protection) | Visit i94.cbp.dhs.gov. Click "Get Most Recent I-94." Enter your name, DOB, and passport info. Print or save your I-94. Also click "View Travel History" and download/print your complete travel history. | Always available online | Required | Needed for Substantial Presence Test and to verify entry dates. Sprintax requires your most recent I-94 admission number and travel history. |

**Always include for NRAs:**
| Passport copy | Identity verification for filing | Your own document | Make a clear photo or scan of your passport's biographical data page (the page with your photo). | Keep current | Required | Sprintax and some filing tools require a passport copy. Keep a digital copy accessible. |

**If user filed prior year returns:**
| Prior year tax returns | Reference for filing and treaty tracking | Your records or prior filing tool | If filed with Sprintax: log into sprintax.com → My Account → Past Returns. If filed with Glacier Tax Prep: log into your Glacier account. If mailed paper returns: check your personal files. | N/A | Recommended | Useful for verifying treaty month count (some treaties have cumulative limits), comparing withholding, and referencing prior Form 8833 positions. |

**If user has foreign accounts exceeding $10K aggregate:**
| FBAR (FinCEN Form 114) | Report foreign financial accounts | Self-filed electronically | File online at bsaefiling.fincen.gov. You will need: bank name, account number, maximum balance during the year, and bank address for EACH foreign account. This is filed separately from your tax return — it does NOT go to the IRS. | April 15 (auto-extension to Oct 15) | Required | Required if the AGGREGATE balance of ALL foreign accounts exceeded $10,000 at ANY point during the year. This includes checking, savings, fixed deposits, PPF, NRE/NRO accounts (for Indian citizens). US bank accounts do NOT count. Penalties for non-filing are severe ($10,000+ per violation). |

**If user leased an EV:**
| (No form needed) | — | — | — | — | — | The $7,500 EV tax credit on a leased vehicle goes to the LESSOR (the leasing company), not to you. It is typically applied as a capitalized cost reduction on your lease agreement. Check your lease agreement for a line item showing the EV credit. You do not file anything for this. |

**If user purchased an EV:**
| Form 8936 | Clean Vehicle Credit | Self-prepared or filing tool | Included in your tax return. You will need the VIN of the vehicle, purchase date, and purchase price. Check irs.gov/credits-deductions/credits-for-new-clean-vehicles to verify the vehicle qualifies. | Filed with return | Required | NRA eligibility for the EV credit is limited. The credit may only apply if you have US-source income that is effectively connected with a US trade or business. Consult a tax professional. |

### Section C: Forms to File

List only the forms this specific user needs to include in their tax return:

| Form | Purpose | How It's Generated | Notes |
|------|---------|-------------------|-------|
| **1040-NR** | Main federal NRA tax return | Sprintax generates automatically | This is your primary federal return. Do NOT file Form 1040. |
| **Form 8843** | Exempt individual statement (F-1/J-1 only) | Sprintax generates automatically | Mandatory for ALL F-1/J-1 holders, even with zero income. Lists your visa type, exempt days, and SEVIS info. |
| **Form 8833** | Treaty-based return position disclosure | Sprintax generates automatically | Required if claiming ANY treaty benefit. Discloses which treaty article you're relying on. |
| **Form 8889** | HSA activity report | Sprintax tax experts handle after payment | Only if you have an HSA. Contact Sprintax support post-payment with your W-2 and 1099-SA. |
| **Schedule NEC** | Income not effectively connected with US trade/business | Sprintax generates | For capital gains, dividends, interest, and other investment income taxed at flat rates. |
| **[State Return]** | State income tax return | Sprintax generates | Varies by state. Read `state-rules.md` for state-specific form names and rules. |
| **FBAR (FinCEN 114)** | Foreign account report | Filed separately at bsaefiling.fincen.gov | NOT part of your tax return. Filed separately. Only if foreign accounts exceeded $10K aggregate. |

Include only forms that apply. For example, omit Form 8889 if no HSA, omit FBAR if no foreign accounts, omit Form 8833 if no treaty benefit.

### Section D: Key NRA Tax Rules

Include only rules relevant to this user's situation. Draw from the knowledge base below.

### Section E: Recommended Filing Tools

| Tool | Recommendation | Handles 1040-NR? | Handles State? | Handles Treaty (8833)? | Price Range |
|------|---------------|-------------------|----------------|----------------------|-------------|
| **Sprintax** | Primary recommendation for NRAs | Yes | Yes | Yes | $50-200+ |
| **Glacier Tax Prep** | Good alternative (often provided by universities) | Yes | Yes | Yes | Free-$50 (check with university) |
| TurboTax | Do NOT use for NRA returns | No (only Form 1040) | N/A | No | N/A |
| H&R Block | Do NOT use for NRA returns | No (only Form 1040) | N/A | No | N/A |
| FreeTaxUSA | Do NOT use for NRA returns | No (only Form 1040) | N/A | No | N/A |

**Warning:** TurboTax, H&R Block, and FreeTaxUSA do NOT support Form 1040-NR. Using them as an NRA will result in filing the wrong form (1040 instead of 1040-NR), which can trigger IRS notices, delays, and penalties.

### Section F: Platform-by-Platform Document Collection Guide

Organize the user's required documents by platform so they can collect everything in one login session per platform. **Only include platforms the user actually selected in the questionnaire.** For each platform, provide the exact login URL, navigation path, and list of documents to download. If the user selected "Other" for any platform, provide generic instructions: "Log into your [type] account and search for 'Tax Documents' or 'Tax Center' in the navigation menu. Download all available tax forms for the tax year."

**Use the following platform-specific instructions based on the user's answers:**

---

#### Stock Plan Platforms (from Q7a)

**Schwab Equity Awards** (if Q7a = Schwab):
1. Log in at **eac.schwab.com** (Schwab Equity Award Center)
2. Navigate to: **History → Equity Award Activity** (filter by tax year, then Export) for the Equity Activity Statement
3. Navigate to: **Tax Center → Tax Documents** for tax forms
4. Download:
   - [ ] **Equity Activity Statement** — RSU vesting details and withholding verification
   - [ ] **Form 3922** — ESPP purchase information (if ESPP applies)
   - [ ] **1099-B** or **1042-S** — stock sale proceeds (if shares were sold through this platform). You may receive either form depending on how Schwab classifies your account — both are valid for filing.
5. Tip: Schwab Equity Awards (eac.schwab.com) is a SEPARATE login from personal Charles Schwab brokerage (schwab.com). Check both if you have both accounts. Tax documents may appear under a separate "Tax Center" tab. NRAs may receive 1042-S instead of 1099 forms from this platform — check your Tax Documents section for whichever form was issued.

**E\*Trade / Morgan Stanley at Work** (if Q7a = E\*Trade):
1. Log in at **us.etrade.com/etx/sp/stockplan**
2. Navigate to: **My Account → Tax Center → Tax Documents**
3. Download:
   - [ ] **Equity Activity Statement** — RSU vesting details and withholding verification
   - [ ] **Form 3922** — ESPP purchase information (if ESPP applies)
   - [ ] **1099-B** or **1042-S** — stock sale proceeds (if shares were sold through this platform). NRAs may receive either form.
4. Tip: E\*Trade consolidates stock plan and personal brokerage tax docs in the same Tax Center if both accounts exist under one login. NRAs may receive 1042-S instead of 1099 forms — check your Tax Documents for whichever was issued.

**Fidelity Stock Plan Services / NetBenefits** (if Q7a = Fidelity):
1. Log in at **netbenefits.fidelity.com**
2. Navigate to: **Statements & Tax Forms → Tax Forms**
3. Download:
   - [ ] **Equity Activity Statement** — RSU vesting details and withholding verification
   - [ ] **Form 3922** — ESPP purchase information (if ESPP applies)
   - [ ] **1099-B** or **1042-S** — stock sale proceeds (if shares were sold through this platform). NRAs may receive either form.
4. Tip: Stock plan documents are on NetBenefits (netbenefits.fidelity.com), which is SEPARATE from personal Fidelity brokerage (fidelity.com). Check both if applicable. NRAs may receive 1042-S instead of 1099 forms — check your Tax Forms section for whichever was issued.

**Shareworks (Morgan Stanley)** (if Q7a = Shareworks):
1. Log in at **shareworks.com**
2. Navigate to: **My Account → Tax Documents** or **Reports → Tax Forms**
3. Download:
   - [ ] **Equity Activity Statement** — RSU vesting details and withholding verification
   - [ ] **Form 3922** — ESPP purchase information (if ESPP applies)
   - [ ] **1099-B** or **1042-S** — stock sale proceeds (if shares were sold through this platform). NRAs may receive either form.
4. Tip: Some employers are migrating from Shareworks to E\*Trade. If you can't find documents, check with your HR/Stock Plan team. NRAs may receive 1042-S instead of 1099 forms — check your Tax Documents for whichever was issued.

---

#### Personal Brokerage Platforms (from Q9a/Q10a)

**Robinhood** (if Q9a or Q10a = Robinhood):
1. Log in at **robinhood.com** (or app → Account → Tax Documents)
2. Navigate to: **Account → Tax Center → Tax Documents**
3. Download:
   - [ ] **Consolidated 1099** — includes 1099-B (stock sales), 1099-DIV (dividends), and 1099-INT (interest) in one document
4. Tip: Robinhood issues ONE Consolidated 1099 covering all income types. Available by mid-February. Robinhood classifies all users as US persons — you will receive 1099 forms, NOT 1042-S. This is normal for NRAs.

**Charles Schwab** (personal brokerage, if Q9a or Q10a = Schwab):
1. Log in at **schwab.com**
2. Navigate to: **Accounts → Statements & Tax Forms → Tax Forms**
3. Download:
   - [ ] **Consolidated 1099** — includes 1099-B, 1099-DIV, 1099-INT as applicable
4. Tip: Schwab personal brokerage (schwab.com) and Schwab Equity Awards (eac.schwab.com) have SEPARATE logins and SEPARATE tax documents. Make sure you check both if you have both accounts.

**Fidelity** (personal brokerage, if Q9a or Q10a = Fidelity):
1. Log in at **fidelity.com**
2. Navigate to: **Accounts & Trade → Tax Forms**
3. Download:
   - [ ] **Consolidated 1099** — includes 1099-B, 1099-DIV, 1099-INT as applicable
4. Tip: Personal brokerage docs are at fidelity.com; stock plan docs are at netbenefits.fidelity.com. These are SEPARATE logins — check both if applicable.

**Vanguard** (if Q9a or Q10a = Vanguard):
1. Log in at **vanguard.com**
2. Navigate to: **My Accounts → Tax Forms** (under Documents)
3. Download:
   - [ ] **Consolidated 1099** — includes 1099-B, 1099-DIV, 1099-INT as applicable
4. Tip: Tax forms are typically available by mid-February. Vanguard may issue corrected forms — check again through March for updates.

**Interactive Brokers** (if Q9a or Q10a = Interactive Brokers):
1. Log in at **interactivebrokers.com**
2. Navigate to: **Performance & Reports → Tax → Tax Forms**
3. Download:
   - [ ] **Consolidated 1099** OR **1042-S** — depends on your W-8BEN status
4. Tip: Interactive Brokers is one of the few brokerages that properly classifies NRAs. If you have a W-8BEN on file, you may receive 1042-S instead of 1099. Check which form you received — both are valid for filing with Sprintax.

**Webull** (if Q9a or Q10a = Webull):
1. Log in at **webull.com** (or app → More → Tax Documents)
2. Navigate to: **More → Tax Documents** or **Account → Tax Center**
3. Download:
   - [ ] **Consolidated 1099** — includes 1099-B, 1099-DIV as applicable
4. Tip: Webull partners with Apex Clearing — your 1099 may come from Apex Clearing rather than Webull directly. Available by mid-February.

---

#### Bank Platforms (from Q11a)

**Marcus by Goldman Sachs** (if Q11a = Marcus):
1. Log in at **marcus.com**
2. Navigate to: **Documents → Tax Documents**
3. Download:
   - [ ] **1099-INT** — interest income from savings/CDs
4. Tip: Only issued if interest earned was $10 or more.

**Ally Bank** (if Q11a = Ally):
1. Log in at **ally.com**
2. Navigate to: **Statements & Tax Forms → Tax Forms**
3. Download:
   - [ ] **1099-INT** — interest income from savings/CDs
4. Tip: Available by January 31.

**Discover Bank** (if Q11a = Discover):
1. Log in at **discover.com**
2. Navigate to: **More → Statements & Tax Documents**
3. Download:
   - [ ] **1099-INT** — interest income from savings/CDs
4. Tip: Available by January 31.

**Capital One** (if Q11a = Capital One):
1. Log in at **capitalone.com**
2. Navigate to: **Account Services → Statements & Documents → Tax Documents**
3. Download:
   - [ ] **1099-INT** — interest income from 360 Savings / Performance Savings / CDs
4. Tip: Available by January 31.

**Wealthfront** (if Q11a = Wealthfront):
1. Log in at **wealthfront.com**
2. Navigate to: **Documents → Tax Documents**
3. Download:
   - [ ] **1099-INT** — interest income from cash account
   - [ ] **Consolidated 1099** — if you also have an investment account
4. Tip: Cash account interest appears on 1099-INT; investment account income on Consolidated 1099.

**SoFi** (if Q11a = SoFi):
1. Log in at **sofi.com**
2. Navigate to: **Account → Tax Documents**
3. Download:
   - [ ] **1099-INT** — interest income from savings
4. Tip: Available by January 31.

**Apple Savings** (if Q11a = Apple Savings):
1. In the **Wallet app** on iPhone → Savings → Statements → Tax Documents. Or log in at **goldman.com**.
2. Download:
   - [ ] **1099-INT** — interest income from Apple Savings
3. Tip: Apple Savings is operated by Goldman Sachs. The 1099-INT comes from Goldman Sachs, not Apple. If not visible in the Wallet app, check the Goldman Sachs online portal.
4. **Important (2026):** Goldman Sachs announced in January 2026 that Apple Card and Apple Savings are transitioning to JPMorgan Chase (expected completion ~2028). For the 2025 tax year, Goldman Sachs still issues your 1099-INT. In future years, check whether your 1099-INT comes from Goldman Sachs or JPMorgan Chase.

---

#### HSA Platforms (from Q15d)

**Fidelity HSA** (if Q15d = Fidelity):
1. Log in at **netbenefits.fidelity.com** (if employer-linked) or **fidelity.com**
2. Navigate to: **Statements & Tax Forms → Tax Forms**
3. Download:
   - [ ] **1099-SA** — HSA distributions (if you took withdrawals)
   - [ ] **Form 5498-SA** — contribution summary (arrives later, typically May)
4. Tip: If your HSA is through your employer, check NetBenefits. If it's a personal HSA, check fidelity.com.

**Optum Bank** (if Q15d = Optum):
1. Log in at **optumbank.com**
2. Navigate to: **Statements & Docs → Tax Forms**
3. Download:
   - [ ] **1099-SA** — HSA distributions (if you took withdrawals)
   - [ ] **Form 5498-SA** — contribution summary
4. Tip: Available by January 31.

**HealthEquity** (if Q15d = HealthEquity):
1. Log in at **healthequity.com**
2. Navigate to: **Account → Tax Center → Tax Forms**
3. Download:
   - [ ] **1099-SA** — HSA distributions (if you took withdrawals)
   - [ ] **Form 5498-SA** — contribution summary
4. Tip: Available by January 31.

**HSA Bank (Webster Bank)** (if Q15d = HSA Bank):
1. Log in at **hsabank.com**
2. Navigate to: **Account → Tax Information → Tax Forms**
3. Download:
   - [ ] **1099-SA** — HSA distributions (if you took withdrawals)
   - [ ] **Form 5498-SA** — contribution summary
4. Tip: Available by January 31.

**Lively** (if Q15d = Lively):
1. Log in at **livelyme.com**
2. Navigate to: **Documents → Tax Forms**
3. Download:
   - [ ] **1099-SA** — HSA distributions (if you took withdrawals)
   - [ ] **Form 5498-SA** — contribution summary
4. Tip: Available by January 31.

---

#### Employer Payroll Portal(s) (always include if user has W-2 employment)

*(If the user has multiple employers, generate a separate subsection below for each employer using their name and payroll system from Q6b/Q6c. If only one employer, generate a single subsection.)*

**ADP** (if Q6c = ADP):
1. Log in at **adp.com** (or my.adp.com)
2. Navigate to: **Pay → Tax Statements → Year [tax year]**
3. Download:
   - [ ] **W-2** — Copy B (federal) and Copy 2 (state). Must be available by Jan 31.
   - [ ] **1095-C** — health coverage proof (if employer health insurance). Available by March 2. Informational only — do NOT file.
4. Tip: If your employer uses ADP Workforce Now, you may see "Pay & Taxes → Tax Statements." Some employers brand the portal differently — check any HR portal links your company provided.

**UKG / UltiPro** (if Q6c = UKG):
1. Log in at **ultipro.com** (or your company's UKG URL)
2. Navigate to: **Menu → Myself → Pay → Tax Forms**
3. Download:
   - [ ] **W-2** — Copy B (federal) and Copy 2 (state). Must be available by Jan 31.
   - [ ] **1095-C** — health coverage proof (if employer health insurance). Available by March 2. Informational only — do NOT file.
4. Tip: UKG was formerly called UltiPro. Your company may have a custom login URL — check your HR emails for the portal link.

**Workday** (if Q6c = Workday):
1. Log in at **myworkday.com/[company]** (or your company's Workday URL)
2. Navigate to: **Pay → Tax Documents** or search "Tax Documents" in the Workday search bar
3. Download:
   - [ ] **W-2** — Copy B (federal) and Copy 2 (state). Must be available by Jan 31.
   - [ ] **1095-C** — health coverage proof (if employer health insurance). Available by March 2. Informational only — do NOT file.
4. Tip: In Workday, the URL is typically myworkday.com/[companyname]. You can also search "W-2" directly in the Workday search bar.

**Paycom** (if Q6c = Paycom):
1. Log in at **paycom.com** (Employee Self-Service)
2. Navigate to: **Pay → Tax Forms → Year [tax year]**
3. Download:
   - [ ] **W-2** — Copy B (federal) and Copy 2 (state). Must be available by Jan 31.
   - [ ] **1095-C** — health coverage proof (if employer health insurance). Available by March 2. Informational only — do NOT file.
4. Tip: Paycom's mobile app also provides access to tax forms under Pay > Tax Forms.

**Other / Not Sure** (if Q6c = Other):
1. Log in to your employer's payroll or HR portal
2. Navigate to: **Tax Documents**, **Tax Forms**, or **Pay → Year-End Tax Statements**
3. Download:
   - [ ] **W-2** — Copy B (federal) and Copy 2 (state). Must be available by Jan 31.
   - [ ] **1095-C** — health coverage proof (if employer health insurance). Available by March 2. Informational only — do NOT file.
4. Tip: If you can't find tax documents online, search your email for "payroll portal" or "W-2" from your employer, or contact your HR/Payroll department directly.

*(If the user has multiple employers, repeat the relevant payroll subsection for each employer, labeled with the employer name from Q6b. Then add:)*
> **Important:** You will receive a separate W-2 from each employer — download and enter each one separately in Sprintax. Only your primary full-time employer typically provides 1095-C.

---

#### Government Websites (always include for NRAs)

**I-94 Record** — i94.cbp.dhs.gov:
1. Visit **i94.cbp.dhs.gov**
2. Click "Get Most Recent I-94" → enter name, DOB, passport info
3. Download:
   - [ ] **I-94** — admission number, class of admission, admit until date
   - [ ] **Travel History** — click "View Travel History" and save/print complete entry-exit history
4. Sprintax requires both the I-94 and travel history.

**FBAR** (only if foreign accounts exceeded $10K) — bsaefiling.fincen.gov:
1. Visit **bsaefiling.fincen.gov**
2. File FinCEN Form 114 electronically
3. You need: bank name, account number, maximum balance, bank address for EACH foreign account
4. This is filed SEPARATELY from your tax return — not through Sprintax.

---

At the end of Section F, include a personalized collection checklist summarizing all platforms:

> **Your Document Collection Checklist:**
> - [ ] [Platform 1] ([URL]): [N] documents
> - [ ] [Platform 2] ([URL]): [N] documents
> - [ ] [Platform 3] ([URL]): [N] documents
> - [ ] [Employer 1 name] ([Payroll system], [URL]): W-2, 1095-C
> - [ ] [Employer 2 name] ([Payroll system], [URL]): W-2 *(only include if user has multiple employers)*
> - [ ] I-94 from i94.cbp.dhs.gov
> - [ ] Passport copy (photo/scan of bio page)
> - [ ] I-20/DS-2019 (if F-1/J-1)
> - [ ] Prior year returns (if applicable)

---

## NRA Tax Knowledge Base

Use this knowledge to answer follow-up questions and populate Section D.

### Income Rules

- **W-2 wages:** Taxable on 1040-NR Line 1a. Effectively connected income (ECI).
- **RSU income:** Already included in W-2 Box 1 wages. Do NOT double-count. Net share settlement means shares are withheld for taxes — no 1099-B is issued for the vesting event (this is expected, not an error).
- **ESPP:** No tax impact until shares are SOLD. Form 3922 is informational and is not filed. Keep it for cost basis calculations when you eventually sell.
- **Stock options (ISO/NSO):** Complex NRA treatment. ISOs have no tax at exercise for NRAs if not effectively connected. NSOs taxed at exercise — income appears on W-2 or 1042-S. Consult a professional.
- **Capital gains:** If present in the US for 183 or more days during the tax year, taxed at 30% flat rate (or treaty rate) on US-source gains. If present for fewer than 183 days, capital gains from stock sales are generally NOT subject to US tax (exempt under IRC 871(a)(2)). Capital LOSSES are NOT deductible for NRAs and do not need to be reported. No carry-forward.
- **Bank deposit interest (HYSA, savings, CDs):** EXEMPT from federal tax for NRAs under IRC 871(i)(2)(A). This includes interest from US banks like Marcus, Ally, Discover, Capital One, etc. State tax may still apply.
- **Dividends:** Taxable at 30% flat rate or reduced treaty rate (e.g., 25% for India, 10% for China). Reported on Schedule NEC.
- **Scholarship/fellowship:** Amounts for tuition and required fees/books are tax-free. Amounts for room, board, and living expenses are taxable. Treaty may exempt some/all.
- **Rental income:** Taxable. Can elect to treat as ECI (file Schedule E) to deduct expenses, or pay 30% flat on gross income.
- **Cryptocurrency/digital assets:** Crypto sales and exchanges generate capital gains, subject to the same 183-day rule as stock sales. Staking rewards, mining income, and airdrops are taxable as ordinary income. The IRS requires a mandatory yes/no digital asset question on Form 1040-NR. Exchanges may issue Form 1099-DA or 1099-B.
- **Gambling/lottery winnings:** Subject to 30% flat rate withholding for NRAs (or reduced treaty rate). Reported on Form W-2G. NRAs CANNOT deduct gambling losses, unlike US residents. Some treaty countries have reduced rates.
- **401k/IRA distributions:** Early distributions (before age 59½) incur a 10% penalty plus NRA withholding (typically 30%). Reported on Form 1099-R. The plan administrator usually withholds at the NRA rate. Report on Form 1040-NR.

### Document Classification Rules

- **1099 vs 1042-S:** In theory, NRAs should receive Form 1042-S for investment income. In practice, many US personal brokerages and banks (Robinhood, Vanguard, Webull, Ally, Marcus, etc.) classify NRAs as US persons and issue standard 1099 forms (1099-DIV, 1099-INT, 1099-B). This is normal and does NOT indicate an error. However, employer stock plan platforms (Schwab Equity Awards, E\*Trade/Morgan Stanley at Work, Fidelity NetBenefits, Shareworks) and some brokerages where the user filed a W-8BEN (notably Interactive Brokers) may properly classify NRAs and issue 1042-S instead. **Either form is valid for filing.** Enter whichever form you receive in Sprintax as-is — it handles both. When generating the checklist, always note that users may receive either 1099 or 1042-S from any platform, and should check their Tax Documents for whichever was issued.
- **W-2 Box 12 Code W (HSA):** This amount is excluded from federal wages (Box 1) but some states (notably California) add it back to state wages. This is why Box 16 (state wages) may be higher than Box 1 (federal wages). The difference equals the HSA contribution.
- **W-2 Box 3/5 (Social Security/Medicare wages):** Should be $0.00 on ALL W-2s if you are FICA exempt (F-1/J-1, first 5 years). If any W-2 shows a non-zero amount, that employer may have incorrectly withheld FICA taxes. First ask that employer to correct it, then file Form 843 (Claim for Refund) with the IRS to recover the overwithheld amount. If you have multiple employers, check each W-2 independently — one employer may withhold correctly while another does not.
- **W-2 Box 13 (Retirement Plan checkbox):** May be disabled or grayed out in NRA filing tools like Sprintax. This is expected behavior and has no tax impact on NRA returns.
- **EV credit on leased vehicles:** The $7,500 federal EV tax credit goes to the LESSOR (leasing company), not the lessee. It is typically applied as a capitalized cost reduction on the lease. The lessee files nothing and claims nothing.
- **1095-C:** Informational only. Proves you had employer health coverage. Do NOT file with your tax return.

### HSA Rules for NRAs

- HSA distributions require Form 8889 to be filed with your return
- Employer HSA contributions (W-2 Box 12 Code W) are excluded from federal wages but NOT from state wages in some states (e.g., California)
- Personal after-tax HSA contributions (NOT through payroll) may be deductible on federal return
- Distributions for qualified medical expenses (doctor visits, prescriptions, glasses, medical equipment) are tax-free
- Distributions for non-qualified expenses are taxable income + 20% penalty
- Sprintax handles Form 8889 via tax experts after payment — contact support with W-2 + 1099-SA

### FBAR Rules

- **Threshold:** Required if the AGGREGATE balance of ALL foreign financial accounts exceeded $10,000 at ANY point during the calendar year
- **What counts:** Checking, savings, fixed deposits, mutual funds, PPF, NRE/NRO accounts (India), investment accounts held at foreign institutions
- **What doesn't count:** US bank accounts (BofA, Chase, etc.), US brokerage accounts, retirement accounts (401k, IRA)
- **Filing:** Electronically at bsaefiling.fincen.gov — NOT with your tax return
- **Deadline:** April 15 with automatic extension to October 15 (no form needed for extension)
- **Penalties:** $10,000+ per violation for non-willful failure to file; up to $100,000 or 50% of account balance for willful violations
- **Common mistake:** Many NRAs don't know about FBAR. If you have any foreign accounts, check whether you need to file.

### Treaty Benefits

For country-specific treaty details, read `references/treaty-reference.md` in this skill directory.

Key rules:
- Treaty benefits apply to FEDERAL taxes only. Most states (including California, New York, Massachusetts) do NOT honor treaty provisions.
- Must file Form 8833 to claim any treaty benefit — failure to disclose can result in the benefit being denied.
- Some treaties have cumulative time limits (e.g., benefits only for the first N months/years of US presence). Track this carefully across tax years.
- Common treaty benefits for students: standard deduction (India $15,750 (2025)), income exemption (China $5,000), scholarship exemption.

### State Tax Rules

For state-specific rules, read `references/state-rules.md` in this skill directory.

Key rules:
- No income tax states: Alaska, Florida, Nevada, New Hampshire (interest/dividends only), South Dakota, Tennessee, Texas, Washington, Wyoming
- Most states with income tax do NOT honor federal treaty benefits — you pay full state tax on all income
- Some states (CA) do not recognize HSA contributions, adding Box 12 Code W back to state wages
- File the non-resident or part-year resident version of the state return

### Rules NRAs Often Ask About

- **Education credits (AOTC/LLC):** NRAs are NOT eligible for the American Opportunity Tax Credit or Lifetime Learning Credit. These credits are only available to Resident Aliens and US citizens. If you receive a 1098-T from your university, it is used for scholarship reporting, not for claiming education credits.
- **Dependents:** NRAs generally cannot claim dependents on Form 1040-NR. Limited exceptions exist for residents of Canada, Mexico, South Korea, and India under specific treaty articles. If you have dependents, consult a tax professional.
- **Form 8843 for dependents:** If you have a spouse or children on F-2 or J-2 dependent visas, EACH of them must file their own Form 8843, even with zero income. Sprintax can generate these.
- **Form W-8BEN:** You may need to provide Form W-8BEN (Certificate of Foreign Status) to banks, brokerages, and other US payers to certify your NRA status. This ensures proper withholding rates (including treaty rates) are applied. W-8BEN is NOT filed with your tax return — it is given directly to the payer.
- **ITIN (Individual Taxpayer Identification Number):** If you do not have a Social Security Number, you may need an ITIN to file your return. Apply using Form W-7, submitted with your tax return. Sprintax can help with ITIN applications.
- **IRS Free File:** The IRS Free File program does NOT support Form 1040-NR. Do not attempt to use it for NRA returns.
- **Amended returns:** If you discover errors or receive corrected documents (e.g., corrected 1099) after filing, you can file Form 1040-X (Amended Return). Corrected 1099s commonly arrive through March.

---

## How to Obtain Documents — Quick Reference

If the user asks "where do I get [document]?", use these detailed instructions:

### W-2
1. Log into your employer's payroll portal (ADP: adp.com | UKG: ultipro.com | Workday: myworkday.com | Paycom: paycom.com)
2. Navigate to: Tax Documents, Tax Forms, or Pay > Year-End Tax Statements
3. Download the W-2. You'll typically get a multi-page PDF with Copy B (Federal), Copy 2 (State), Copy C (Employee Record)
4. Must be available by January 31. If not available, contact your HR/Payroll department.
5. For Sprintax: Upload Copy B for federal entry, Copy 2 for state entry
6. **Multiple employers:** If you had more than one W-2 employer, repeat these steps for each employer's payroll portal. Each employer issues its own W-2 — enter each one separately in Sprintax.

### 1042-S (if issued by broker or stock plan platform)
1. Log into your brokerage or stock plan account (Schwab Equity Awards: eac.schwab.com | E\*Trade: us.etrade.com | Fidelity NetBenefits: netbenefits.fidelity.com | Interactive Brokers: interactivebrokers.com | or whichever platform issued it)
2. Navigate to: Account > Tax Documents, Tax Center, or Statements & Tax
3. Look for Form 1042-S — this means the platform classified you as an NRA. Check Income Code (06 = dividends, 27 = short-term capital gains, etc.) and verify withholding rate matches your treaty rate.
4. Available by March 15 (later than 1099 forms)
5. If you received 1099 forms instead of 1042-S, that is also common for NRAs — both are valid for filing. Enter whichever you receive in Sprintax.

### 1099-DIV or 1042-S (dividends)
1. Log into your brokerage or stock plan account (see Section F for platform-specific instructions)
2. Navigate to: Tax Documents or Tax Center
3. Download 1099-DIV (may be part of a Consolidated 1099) or 1042-S — check for whichever form was issued
4. Available by February 15 (1099-DIV) or March 15 (1042-S)
5. For 1099-DIV: Check Box 1a (Total ordinary dividends). For 1042-S: Check Income Code 06 (dividends) and verify withholding rate matches your treaty rate.
6. Note for NRAs: You may receive either 1099-DIV or 1042-S depending on how the platform classifies your account. Personal brokerages (Robinhood, Vanguard) typically issue 1099-DIV. Employer stock plan platforms (Schwab Equity Awards, E\*Trade, Fidelity NetBenefits) may issue 1042-S. Either form is valid — enter it in Sprintax as-is.

### 1099-INT
1. Log into your bank's website (see Section F for platform-specific instructions)
2. Navigate to: Tax Center, Statements & Documents, or Tax Documents
3. Download 1099-INT
4. Available by January 31
5. Note: Only issued if interest earned is $10 or more. If you earned less, no form is issued and you technically don't need to report it.
6. Note for NRAs: Most US banks issue 1099-INT regardless of NRA status — this is normal. The federal tax exemption for bank deposit interest applies either way.

### 1099-SA
1. Log into your HSA provider (see Section F for platform-specific instructions)
2. Navigate to: Tax Forms, Statements, or Account Activity
3. Download Form 1099-SA
4. Check Box 1 (Gross distribution) and Box 3 (Distribution code — Code 1 = Normal)
5. Available by January 31

### 1099-B or 1042-S (stock sales)
1. Log into your brokerage or stock plan account (see Section F for platform-specific instructions)
2. Navigate to: Tax Documents or Tax Center
3. Download 1099-B (Proceeds from Broker and Barter Exchange Transactions) or 1042-S — check for whichever form was issued. 1099-B may be part of a Consolidated 1099.
4. Available by February 15 (1099-B) or March 15 (1042-S)
5. Note: Most personal brokerages issue 1099-B to all customers, including NRAs. Employer stock plan platforms (Schwab Equity Awards, E\*Trade, Fidelity NetBenefits) may issue 1042-S instead. Either form is valid for filing. If you only sold at a loss, there is still nothing to report for NRA purposes (capital losses are not deductible), but you may still receive a 1099-B or 1042-S.

### Form 3922
1. Log into your stock plan account (see Section F for platform-specific instructions)
2. Navigate to: Tax Documents or Tax Information
3. Download Form 3922 (Transfer of Stock Acquired Through an ESPP)
4. Available by January 31
5. This is informational only — do not file it, but keep it for when you sell the shares

### 1095-C
1. Log into your employer's payroll portal (same as W-2)
2. Navigate to: Tax Documents
3. Download Form 1095-C
4. Available by March 2
5. This is informational — do NOT file with your return

### I-94
1. Visit: https://i94.cbp.dhs.gov
2. Click "Get Most Recent I-94"
3. Enter your full name (as on passport), date of birth, passport number, and country of citizenship
4. Print or save your I-94 (shows admission number, class of admission, admit until date)
5. Also click "View Travel History" and save/print your complete entry-exit history
6. Sprintax requires both the I-94 and travel history

### I-20 (F-1) / DS-2019 (J-1)
1. Check your university's international student portal (common systems: iStart, Terra Dotta, Sunapsis)
2. If not available online, contact your International Student Services Office (ISSO/ISSS)
3. You need the SEVIS ID number (starts with N) and program start/end dates
4. If you've graduated, your last I-20 with OPT/CPT endorsement is what you need

### Prior Year Returns
1. If filed with Sprintax: Log into sprintax.com → My Account → My Tax Returns → Download PDFs
2. If filed with Glacier Tax Prep: Log into your Glacier account → Past Returns
3. If paper-filed or lost: Request a tax transcript from the IRS at irs.gov/individuals/get-transcript (may require an IRS account)
