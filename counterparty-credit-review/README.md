# Counterparty Credit Review Workbook

A structured template for reviewing a counterparty's financial health, comparing it to its peers, and recommending a credit limit with a documented rationale.

---

## Business Goal

Give a credit analyst a structured, repeatable way to review a counterparty's financial health, compare it to its peer group, and arrive at a defensible credit limit recommendation — with the analysis and the rationale documented in one place.

---

## The Problem It Solves

A counterparty credit review that is done in a spreadsheet, a memo, and an email is a review that is hard to audit. Without a structured template:

- Reviews are inconsistent across analysts
- The rationale for a limit is often missing
- Peer context is left out
- A committee cannot see how the recommendation was reached

This workbook makes the review structured, auditable, and comparable across counterparties.

---

## What the Workbook Contains

| Tab | Purpose |
|-----|---------|
| **README** | Explains purpose, regulatory anchors, and scope |
| **Counterparty Profile** | Company identity, credit rating, review metadata, and analyst assessment |
| **Ratio Analysis** | Liquidity, leverage, profitability, and cash flow ratios with benchmark comparison |
| **Peer Comparison** | Same-sector peers, peer averages, and a counterparty-vs-peer table |
| **Limit Recommendation** | Recommended limit derived from rating and ratio analysis, with rationale and override field |

---

## Regulatory and Policy Anchors

- **Basel III large exposures framework** — A firm must monitor and limit its exposure to any single counterparty or connected group. This workbook is the review layer that sits above the limit-setting process.
- **Internal credit policy** — Counterparty review, rating assignment, and limit recommendation follow the firm's credit policy.
- **OSFI E-23** — Where the counterparty is itself a model or AI vendor, model risk expectations may apply.

---

## What This Workbook Does NOT Do

It does not perform external credit bureau checks, sanctions screening, or KYC. It does not calculate regulatory capital or large-exposure ratios. It does not assign or approve credit limits — it recommends them. It does not replace the credit committee's judgment or the firm's credit policy.

It is a **review template**. The recommendation it produces is an input to a governance process, not the output of it.

---

## Data Note and Derivation

The dataset used here (Corporate Credit Rating with Financial Ratios, Kaggle) contains public company financial statements and credit ratings for major US firms between 2010 and 2016. It does not contain assigned credit limits, current exposure, or counterparty relationship data.

The credit limits shown in this workbook are derived from the credit rating and ratio analysis using a simplified scoring logic for demonstration. They are illustrative. They are not the output of a production credit model and should not be used for actual credit decisions. A production limit would also reflect the firm's credit policy, portfolio concentration limits, collateral, and committee judgment.

---

## How to Open It

1. Download `Counterparty_Credit_Review_Workbook_v1.0_FINAL.xlsx`
2. Open in Excel 2019 or later (or Microsoft 365)
3. Read the **README** tab first
4. Go to the **Counterparty Profile** tab
5. Work left to right: Profile → Ratio Analysis → Peer Comparison → Limit Recommendation

Blue cells are input. Black cells are formulas — do not overtype them.

---

## Screenshots

See the screenshots in this folder:

- `01-counterparty-profile.png` — the profile page with rating and assessment
- `02-limit-recommendation.png` — the limit recommendation with rationale

---

## Design Notes

See [`NOTES.md`](https://github.com/MiltonGreat/GRC-Credit-Analysis-Portfolio/blob/main/counterparty-credit-review/NOTES.md) for the design decisions behind the ratio selection, the peer group construction, and the limit recommendation logic.
