# Credit Risk & Model Risk Governance — Excel Portfolio

Three operational Excel workbooks built for regulated financial institutions. Each workbook solves a specific problem a credit risk, counterparty credit, or model risk team faces day to day. Each one is documented, auditable, and built to a standard a regulator would recognize.

**Author:** [Your Name]
**Status:** Portfolio — demonstration workbooks with representative data
**Related work:** [Python validation projects — Lending Club, Fannie Mae] · [Governance Documentation Studio]

---

## Why These Workbooks Exist

Most risk analyst portfolio pieces are notebooks. They show that the author can build a model. They do not show whether the author can build the **operational tool** a risk team uses to run the model — the register, the monitor, the dashboard that a credit committee actually opens on Monday morning.

These three workbooks are that layer. They sit between the model and the governance decision. They answer the questions a risk team asks every week:

- *Which of our counterparties is carrying the most exposure right now?*
- *Which models have open validation findings, and when is the next review due?*
- *Where is a counterparty approaching its credit limit, and who needs to act?*

Each workbook answers one of those questions. Together, they cover three of the most common entry points into a risk analyst role: **counterparty credit review, exposure monitoring, and model risk governance**.

---

## The Three Workbooks

### 1. Model Inventory & Findings Tracker

**Problem it solves:** A model risk function must know every model in use, its owner, its risk tier, when it was last validated, and whether open findings exist. Without a single governed register, models run past their review dates, findings get lost in email, and a regulatory exam becomes a scramble.

**What it demonstrates:**
- Model inventory with risk-based validation cadence (Tier 1 annual, Tier 2 every 18 months, Tier 3 every 24 months)
- Findings register linked to models via INDEX/MATCH, with severity, owner, due date, and automatic overdue flag
- Review calendar with computed "Days Until Due" and OVERDUE / Due Soon / On Track status
- Executive Summary dashboard for the Model Risk Committee

**Regulatory anchors:** OSFI E-23 s.3.1 (model inventory), s.3.2 (risk-based validation frequency), s.4.2 (findings tracked to resolution). Also compatible with SR 11-7 expectations.

**Data source:** Findings derived from two independent validation projects (Lending Club and Fannie Mae), anonymized for portfolio use.

**Workbook:** [`Model_Inventory_Findings_Tracker_v1.0_FINAL.xlsx`](./model-inventory-findings-tracker/Model_Inventory_Findings_Tracker_v1.0_FINAL.xlsx)

**Where to start:** Open the workbook and read the README tab. Then go to the Executive Summary.

---

### 2. Counterparty Credit Review Workbook

**Problem it solves:** A counterparty credit analyst must review a counterparty's financial health, compare it to its peers, and recommend a credit limit with a documented rationale. Without a structured template, reviews are inconsistent and the rationale is often missing.

**What it demonstrates:**
- Counterparty profile with credit rating and review metadata
- Ratio analysis across liquidity, leverage, profitability, and cash flow, with benchmark comparison
- Peer comparison against same-sector peers, with peer averages and a counterparty-vs-peer table
- Limit recommendation derived from credit rating and ratio analysis, with written rationale and analyst override field

**Regulatory and policy anchors:** Basel III large exposures framework, internal credit policy, OSFI E-23 where the counterparty is itself a model or AI vendor.

**Data source:** Corporate Credit Rating with Financial Ratios (Kaggle). Public company financials and credit ratings for major US firms, 2010–2016.

**Derivation note:** Credit limits are derived from credit rating and ratio analysis using simplified logic. They are illustrative and should not be used for actual credit decisions.

**Workbook:** [`Counterparty_Credit_Review_Workbook_v1.0_FINAL.xlsx`](./counterparty-credit-review/Counterparty_Credit_Review_Workbook_v1.0_FINAL.xlsx)

**Where to start:** Open the workbook and read the README tab. Then go to the Counterparty Profile.

---

### 3. Credit Limit & Exposure Monitor

**Problem it solves:** A credit risk team must monitor enterprise exposure against assigned limits, so accounts approaching or exceeding their limit are visible and escalated before they become a loss event. Without a monitor, limits are set and then forgotten until a breach occurs.

**What it demonstrates:**
- Exposure register with one row per enterprise: credit score, revenue, debt ratio, assigned limit, current exposure, utilization, and escalation status
- Derivation of credit limits from credit score and debt ratio, with a documented logic table
- Escalation logic: EXCESS (>100% utilization), Watch (>85%), Monitor (>70%), OK (≤70%)
- One-page escalation dashboard with portfolio-level utilization, a count of accounts by status, and a list of accounts requiring action

**Regulatory and policy anchors:** Basel III large exposures framework, internal credit policy, OSFI E-23 where the counterparty is a model or AI vendor.

**Data source:** Enterprise Financial Network Dataset (Kaggle). 2,934 enterprises with credit score, debt ratio, liquidity, revenue, and bankruptcy flag.

**Derivation note:** Credit limits and exposure are derived from enterprise financial attributes using simplified logic. They are illustrative and do not represent live counterparty exposure.

**Workbook:** [`Credit_Limit_Exposure_Monitor_v1.0_FINAL.xlsx`](./credit-limit-exposure-monitor/Credit_Limit_Exposure_Monitor_v1.0_FINAL.xlsx)

**Where to start:** Open the workbook and read the README tab. Then go to the Exposure Register, followed by the Escalation Dashboard.

---

## What All Three Workbooks Have in Common

Each workbook follows the same design discipline:

| Principle | How It Applies |
|-----------|----------------|
| **Business goal first** | The README opens with the decision the workbook supports, not the mechanism it uses |
| **Regulatory anchors named** | Specific clauses are cited (OSFI E-23 s.3.1, s.3.2, s.4.2; Basel III large exposures) |
| **Reader orientation** | Each tab has a short "What this tab answers" note so a reader knows what decision it supports |
| **Derivation documented** | Where figures are derived rather than observed, the logic is documented in the workbook and in the README |
| **Explicit scope limits** | Each README has a "What this workbook does NOT do" section |
| **Technical note** | Each workbook uses a consistent colour convention (blue = input, black = computed) |
| **Data note** | Each workbook states what the data is and is not, so the reader is not misled |

That consistency is deliberate. It reflects the standard a regulated institution applies to its operational tools: nothing is presented without a documented purpose, a regulatory anchor, and a stated limit.

---

## A Note on the Datasets

All three workbooks use publicly available Kaggle datasets. The datasets are used as a **proxy** for proprietary bank data. They contain real or representative financial attributes, but they are not bank portfolios. The workbooks are therefore best read as **templates and demonstrations** of how an operational risk tool would be built, not as live analyses of real counterparties.

Each workbook's README explains the dataset and the derivation logic in detail. If a figure in the workbook is derived rather than observed, the README says so, and the derivation table shows how it was calculated.

That transparency is deliberate. A reviewer should be able to open any workbook and know, within a minute, what the data is, what the workbook does with it, and what the output means.
