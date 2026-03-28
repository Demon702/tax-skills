# tax-skills

A Claude Code plugin providing an interactive NRA tax document checklist for non-resident aliens filing US taxes.

---

## Who This Is For

This plugin is for **Non-Resident Aliens (NRAs)** — including F-1, J-1, H-1B, L-1, O-1, and TN visa holders — who need to file US taxes on **Form 1040-NR**.

This is **NOT** for:
- US citizens or lawful permanent residents (green card holders)
- Resident Aliens who pass the Substantial Presence Test
- Anyone who should be filing Form 1040 (use TurboTax, H&R Block, or FreeTaxUSA instead)

---

## Purpose

The `nra-tax-checklist` skill walks you through a personalized questionnaire covering your visa status, employment, income sources, stock compensation, brokerage accounts, HSA, and more. Based on your answers, it generates a **tailored document checklist** with exact step-by-step instructions for obtaining every form you need.

---

## What the Skill Provides

- **Tax status determination** — confirms NRA vs Resident Alien status and FICA exemption eligibility
- **Treaty benefit identification** — detects applicable tax treaties (e.g. India's $15,000 standard deduction under Article 21(2)) and notes required forms
- **Required documents table** — every form you need, with deadlines, sources, and NRA-specific notes
- **Platform-by-platform collection guide** — exact login URLs and navigation paths for Workday, Schwab Equity Awards, Robinhood, Fidelity, Marcus, and more
- **Forms to file** — complete list of IRS and state forms for your return (1040-NR, 8843, 8833, CA 540NR, etc.)
- **Key NRA tax rules** — covering capital gains, ESPP, RSUs, dividends, bank interest exemptions, and FBAR

---

## After Using the Skill

Use the generated checklist to collect all your documents, then file your return using:

- **[Sprintax](https://www.sprintax.com)** *(primary recommendation)* — supports Form 1040-NR, state returns, treaty benefits (Form 8833), and HSA handling
- **[Glacier Tax Prep](https://www.glaciertax.com)** — good alternative, often provided free by universities

**Do NOT use TurboTax, H&R Block, or FreeTaxUSA** — they do not support Form 1040-NR and will result in filing the wrong form.

---

## Setup

**Prerequisites:** [Claude Code](https://claude.ai/code) installed.

**1. Add this repo as a marketplace:**
```
/plugin marketplace add Demon702/tax-skills
```

**2. Install the plugin:**
```
/plugin install tax-skills@Demon702-tax-skills
```

**3. Reload plugins:**
```
/reload-plugins
```

---

## Usage

Once installed, invoke the skill in any Claude Code session:

```
/tax-skills:nra-tax-checklist
```

Claude will ask questions one at a time and generate a personalized tax document checklist at the end.

---

## Skills Included

| Skill | Command | Description |
|-------|---------|-------------|
| NRA Tax Document Checklist | `/tax-skills:nra-tax-checklist` | Interactive questionnaire that generates a personalized list of required tax documents, filing forms, and platform-specific collection instructions for NRA filers |

---

## Disclaimer

This plugin is an **educational and organizational tool only**. It does not constitute tax advice. Tax laws are complex and change frequently — always verify information with a qualified tax professional for your specific situation.
