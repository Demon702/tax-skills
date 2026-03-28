# tax-skills

A collection of tax filing skills for Claude Code. Designed as a **Claude Code plugin** (recommended), but can also be used directly with any Claude agent by copying the skill content into your conversation.

---

## Using With Claude Code (Recommended)

Claude Code is the recommended way to use these skills — it handles plugin installation, skill invocation, and memory across sessions automatically.

### Step 1 — Install Claude Code

**macOS / Linux:**
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**macOS (Homebrew):**
```bash
brew install --cask claude-code
```

**Windows (PowerShell):**
```powershell
irm https://claude.ai/install.ps1 | iex
```

**Windows (WinGet):**
```powershell
winget install Anthropic.ClaudeCode
```

Requires a [Claude Pro, Max, Teams, or Enterprise](https://claude.com/pricing) account, or API credentials from [console.anthropic.com](https://console.anthropic.com).

### Step 2 — Start Claude Code and log in

```bash
claude
```

Your browser will open for authentication. Once logged in, credentials are stored and you won't need to log in again.

### Step 3 — Add this repo as a plugin marketplace

```
/plugin marketplace add Demon702/tax-skills
```

### Step 4 — Install the plugin

```
/plugin install tax-skills@Demon702-tax-skills
```

### Step 5 — Reload plugins

```
/reload-plugins
```

---

## Using With Other Claude Agents

These skills can also be used with any Claude-powered tool — including [Claude.ai](https://claude.ai), the Claude mobile app, or any agent built on the Anthropic API — without installing Claude Code.

**To use manually:**
1. Open the skill's `SKILL.md` file from this repo (e.g. `skills/nra-tax-checklist/SKILL.md`)
2. Copy the full contents
3. Paste it into your Claude conversation as the first message, then ask Claude to begin

Claude Code is still recommended because it handles skill invocation and session context automatically — but the skills work anywhere Claude is available.

---

## Skills

### `nra-tax-checklist` — NRA Tax Document Checklist

**Command:** `/tax-skills:nra-tax-checklist`

#### Who this is for

**Non-Resident Aliens (NRAs)** — including F-1, J-1, H-1B, L-1, O-1, and TN visa holders — who need to file US taxes on Form 1040-NR.

This is **NOT** for:
- US citizens or lawful permanent residents (green card holders)
- Resident Aliens who pass the Substantial Presence Test
- Anyone who should be filing Form 1040 (use TurboTax, H&R Block, or FreeTaxUSA instead)

#### What it does

Walks you through a personalized questionnaire covering your visa status, employment, income sources, stock compensation, brokerage accounts, HSA, and more. Based on your answers, it generates a **tailored document checklist** with exact step-by-step instructions for obtaining every form you need.

#### What it covers

- Visa type and NRA status determination
- Employment, RSUs, ESPP, and stock sales
- Personal brokerage accounts and dividends
- Bank interest, HSA, and retirement accounts
- Tax treaty benefits by country
- State-specific filing rules

#### Output includes

- Tax status summary (NRA basis, FICA exemption, treaty eligibility)
- Required documents table with deadlines and how-to-obtain steps
- Treaty benefit identification (e.g. India's $15,000 deduction under Article 21(2))
- Platform-by-platform collection guide (Workday, Schwab Equity Awards, Robinhood, Fidelity, Marcus, etc.)
- Complete list of IRS and state forms to file (1040-NR, 8843, 8833, CA 540NR, etc.)
- Key NRA tax rules for your specific situation

#### After using the skill

Use the generated checklist to collect all your documents, then file your return using:

- **[Sprintax](https://www.sprintax.com)** *(primary recommendation)* — supports Form 1040-NR, state returns, treaty benefits (Form 8833), and HSA handling
- **[Glacier Tax Prep](https://www.glaciertax.com)** — good alternative, often provided free by universities

**Do NOT use TurboTax, H&R Block, or FreeTaxUSA** — they do not support Form 1040-NR and will result in filing the wrong form.

---

## Disclaimer

This plugin is an **educational and organizational tool only**. It does not constitute tax advice. Tax laws are complex and change frequently — always verify information with a qualified tax professional for your specific situation.
