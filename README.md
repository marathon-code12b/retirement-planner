# retirement-planner

Here is a comprehensive, production-ready `README.md` designed to act as the master documentation for your Retirement Matrix Engine. It breaks down the mechanical logic, UI systems, and architectural workflow of the model.

---

# ⚡ RETIREMENT MATRIX ENGINE v4.6

### *Strategic Roth Conversion & Cascading Liquidation Protocol Model*

---

## ## 1. CORE CONCEPT & OBJECTIVE

The **Retirement Matrix Engine** is an advanced financial simulation sandbox designed to model long-term multi-container decumulation. Its primary objective is to **outpace pre-tax growth via aggressive, structured Roth conversions**, minimizing the impact of Required Minimum Distributions (RMDs) and Medicare Part B/D IRMAA premium surcharges.

Unlike generic retirement calculators, this engine enforces strict, dynamic cascading asset liquidations and complex tax policy modeling to help users identify the optimal income-valley window between retirement and the onset of statutory RMDs.

---

## ## 2. ARCHITECTURAL FLOW MATRIX

```
[ annual spending budget ] 
          │
          ▼
[ LESS: guaranteed income floors ] (Social Security, Pensions, etc.)
          │
          ▼
[ NET FUNDING DEFICIT ] 
          │
          ▼
┌────────────────────────────── CASCADE LIQUIDATION PATH ──────────────────────────────┐
│                                                                                      │
│ 1. STATUTORY MANDATES ──► Distribute Age-Driven RMDs first.                          │
│                                                                                      │
│ 2. TAXABLE VAULT      ──► Pull from Cash & Brokerage Assets to clear net deficit.    │
│                                                                                      │
│ 3. PRE-TAX CORE       ──► Draw from Traditional Accounts ONLY if Brokerage is $0.00. │
│                                                                                      │
│ 4. ROTH SHIELD        ──► Pull from Roth Accounts last to protect tax-free growth.  │
└──────────────────────────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────── ROTH CONVERSION SPACE FILLER ─────────────────────────────┐
│                                                                                      │
│ Calculate Current AGI (Floors + RMDs + Deficit Traditional Withdrawals)              │
│                                                                                      │
│ Target Selected Bracket Top Ceiling + Standard Deduction                             │
│                                                                                      │
│ Execute Max Roth Conversion = [Target Bracket Ceiling] - [Current AGI]               │
└──────────────────────────────────────────────────────────────────────────────────────┘
          │
          ▼
┌─────────────────────────────── TAX ACCOUNTING PASS ──────────────────────────────────┐
│                                                                                      │
│ Compute Combined Federal, State, and Local Income Tax Burden                         │
│                                                                                      │
│ Settlement Rule: Debit Cash/Brokerage. Pull from Pre-Tax ONLY if liquid cash = $0.00.│
└──────────────────────────────────────────────────────────────────────────────────────┘

```

---

## ## 3. USER INTERFACE & BUTTON MAP

### ### Detailed Inputs (Tab 1)

* **Simulation Core:**
* *Calculation Mode:* Toggle between **Deterministic** (straight-line constant returns) and **Stochastic** (150-run Monte Carlo simulation tracking market variance/sequence of returns risk).
* *Filing Status:* Sets standard deduction thresholds and tax bracket widths (`SINGLE` vs `MFJ`).


* **Timeline Core:** Establishes milestones for current age, retirement (spending kick-off), and macro horizon limits.
* **Spending & Inflation:** Adjusts baseline structural living costs, compound-inflated annually.
* **Tax Policy & State:**
* *Bracket Ceiling:* The target maximum tax bracket to "fill to the top" with Roth conversions.
* *Tax Sunset:* Toggles between maintaining current rules vs modeling the 2026 TCJA sunset adjustments.


* **Income Floors & Asset Containers:** Editable relational tables to insert customizable, time-bounded pension flows and asset starting balances.

### ### Strategy Sandbox (Tab 2)

* **🛡️ Lock 2-Yr Cash Safety Runway:** When active, halts aggressive conversions if liquid cash + brokerage balances fall below 30% of your projected annual spending needs.
* **⚡ Total Pre-Tax Pre-RMD Drain:** Forces an aggressive, accelerated shift—overriding lower settings to maximize conversions right up to the 24% bracket ceiling prior to age 72.
* **Macro Strategic Presets:** One-click shortcuts to instantly switch parameters to highlight standard retirement pitfalls (`Valley Target` vs `IRMAA Trap`).

---

## ## 4. DATA MATRIX GUIDES (INPUT & OUTPUT)

### ### Data Entry Mapping (Input)

* **Asset Type Syntax Rules:**
* `Traditional` $\rightarrow$ Subject to compounding growth, annual RMD mandates, and ordinary income taxation upon withdrawal/conversion.
* `Brokerage` $\rightarrow$ Taxable liquidity layer. Sources standard capital draws and settles outstanding tax liabilities.
* `Roth` $\rightarrow$ Tax-free compound shielding container.



### ### Ledger Outputs & Highlighting System

The engine outputs a color-coded data grid mapping the math behind every year's movement:

* **— (Gray Zero Indicator):** Instantly flags fields completely devoid of financial activity, streamlining scannability.
* **Red Values ($xx.xk):** Outflows, asset liquidations, and tax friction payments.
* **Green Values ($xx.xk):** Inflows and compounding container asset balances.
* **Purple Values ($xx.xk):** Pure strategic Roth conversions executed within the target tax gap.
* **Yellow Values ($xx.xk):** Funding deficits requiring liquidation actions.

---

## ## 5. SCENARIO STORAGE & PORTABILITY

Because this application runs entirely client-side via your browser, **it does not send your sensitive data to an external server**. This protects your privacy but requires manual local handling to save work.

### ### Saving Scenarios Locally

To capture a specific setup for future analysis, you can export the data block directly from the HTML code:

1. Right-click the `.html` file and open it in a plain text editor (e.g., Notepad, VS Code, TextEdit).
2. Locate the input elements in the HTML structure (e.g., `value="1450000"`).
3. Modify those hardcoded default values to match your personal scenario.
4. Save the file under a unique name (e.g., `Matrix_Engine_Baseline.html`, `Matrix_Engine_AggressiveRoth.html`).

### ### Extracting Ledger Results

To drop the data grid into Excel, Google Sheets, or a document:

1. Run your simulation in the browser.
2. Click and drag to highlight the rows in the **Ledger Display Panel** (or press `Ctrl+A` / `Cmd+A` to capture the whole page).
3. Copy (`Ctrl+C`) and paste (`Ctrl+V`) directly into an Excel worksheet. The browser HTML structure maps perfectly into native spreadsheet rows and columns.
