# Credit Limit & Exposure Monitor

A monitoring template for enterprise exposure against assigned credit limits, with utilization tracking, escalation classification, and a one-page escalation dashboard.

**Workbook:** [`Credit_Limit_Exposure_Monitor_v1.0_FINAL.xlsx`](./Credit_Limit_Exposure_Monitor_v1.0_FINAL.xlsx)
**Part of:** [Credit Risk & Model Risk Governance — Excel Portfolio](../README.md)

---

## Business Goal

Give a credit risk analyst a single view of enterprise exposure against assigned limits, so that accounts approaching or exceeding their limit are visible and escalated before they become a loss event.

---

## The Problem It Solves

A firm that sets credit limits and then does not monitor exposure against them is a firm that discovers over-limit accounts only when a default occurs. Without a monitor:

- Exposure drifts against limits without anyone noticing
- Escalation happens after the loss, not before
- The credit committee sees exposure at a point in time, not as a live position

This workbook is the monitoring layer that sits above the limit-setting process.

---

## What the Workbook Contains

| Tab | Purpose |
|-----|---------|
| **README** | Explains purpose, regulatory anchors, derivation logic, and scope |
| **Exposure Register** | One row per enterprise: credit score, revenue, debt ratio, assigned limit, current exposure, utilization, and escalation status |
| **Escalation Dashboard** | Portfolio-level utilization, count of accounts by status, and accounts requiring action |
| **Lookup Tables** | Limit bands, debt-ratio multipliers, and escalation thresholds |

---

## Regulatory and Policy Anchors

- **Basel III large exposures framework** — A firm must monitor and limit its exposure to any single counterparty or connected group. This workbook is the monitoring layer that sits above the limit-setting process.
- **Internal credit policy** — Utilization thresholds, escalation triggers, and the escalation path are set by the firm's credit policy.
- **OSFI E-23** — Where the counterparty is itself a model or AI vendor, model risk expectations may apply.

---

## What This Workbook Does NOT Do

It does not set credit limits — it monitors exposure against limits that are assumed to exist. It does not calculate regulatory large-exposure ratios or capital requirements. It does not perform real-time monitoring or connect to live systems. It does not replace the firm's treasury, credit, or risk reporting systems.

It is a **monitoring template**. The escalation statuses it produces are an input to a governance process, not the output of it.

---

## Data Note and Derivation

The dataset used here (Enterprise Financial Network Dataset, Kaggle) contains enterprise-level financial attributes: credit score (500–850), debt ratio, liquidity ratio, revenue, and a bankruptcy flag. It does not contain assigned credit limits, current exposure, counterparty relationships, collateral, guarantees, or netting arrangements.

The credit limits, exposure figures, utilization percentages, and escalation statuses shown in this workbook are derived from the enterprise's credit score, debt ratio, liquidity, and revenue using a simplified logic for demonstration. They are not the output of a production credit limit system and should not be used for actual credit decisions. A production exposure monitor would also reflect committed facilities, collateral, guarantees, netting arrangements, and the firm's credit policy.

**Derivation logic:**

| Derived Field | Derived From | Logic |
|---------------|--------------|-------|
| Credit Limit | `src_credit_score` | Higher credit score produces a larger limit (800–850 → $50M; 750–799 → $35M; 700–749 → $20M; 650–699 → $10M; below 650 → $5M) |
| Adjusted Limit | Credit Limit and `src_debt_ratio` | Lower debt ratio produces a higher multiplier (≤0.30 → 1.00×; ≤0.50 → 0.85×; ≤0.70 → 0.70×; above 0.70 → 0.50×) |
| Exposure | `src_revenue` and `src_debt_ratio` | Simulated as revenue × (0.30 + (1 − debt ratio) × 0.40) |
| Utilization | Exposure ÷ Adjusted Limit | Standard utilization ratio |
| Escalation | Utilization | EXCESS >100%, Watch >85%, Monitor >70%, OK ≤70% |

---

## How to Open It

1. Download `Credit_Limit_Exposure_Monitor_v1.0_FINAL.xlsx`
2. Open in Excel 2019 or later (or Microsoft 365)
3. Read the **README** tab first
4. Go to the **Exposure Register** to see the source data
5. Go to the **Escalation Dashboard** to see the one-page view

Blue cells are input. Black cells are formulas — do not overtype them.

---

## Screenshots

See the [`screenshots/`](./screenshots/) folder:

- `01-exposure-register.png` — the register of enterprises with limits, exposure, and escalation
- `02-escalation-dashboard.png` — the one-page dashboard for the credit committee

---

## Design Notes

See [`NOTES.md`](./NOTES.md) for the design decisions behind the derivation logic, the escalation thresholds, and the dashboard layout.
