# Design Notes — Credit Limit & Exposure Monitor

A short record of the decisions behind the workbook, so a reader can understand *why* it is built the way it is.

---

## Why limits and exposure are derived rather than observed

The Enterprise Financial Network Dataset contains enterprise financial attributes (credit score, debt ratio, liquidity, revenue, bankruptcy flag), but it does not contain assigned credit limits or current exposure. Rather than fabricate a limit column, the workbook derives limits and exposure from the attributes using documented logic. The derivation table in the README shows exactly how each figure is produced. That transparency is what makes the workbook defensible.

---

## Why the derivation logic is simple

The limit bands (credit score → limit) and the debt-ratio multipliers are deliberately simple. The point is not to build a production-grade limit model — that would require a credit policy, committee judgment, and portfolio concentration data the dataset does not contain. The point is to demonstrate the *structure* of a monitoring workbook: how a limit is set, how utilization is calculated, how escalation is classified. A simple, documented logic is more credible than a complex, opaque one.

---

## Why the escalation thresholds are 100% / 85% / 70%

The thresholds are illustrative. EXCESS at 100% is a universal convention — over-limit means over-limit. The 85% and 70% thresholds are more conservative choices that reflect a "watch and monitor" philosophy: an account approaching its limit should be flagged before it crosses it. A production monitor would set these thresholds under the firm's credit policy. They are documented as illustrative in the README.

---

## Why the Exposure Register is deduplicated

The Enterprise Financial Network dataset is a relationship graph. Each enterprise may appear multiple times in the edge list — once per relationship. The register has been deduplicated to one row per enterprise, so each enterprise is counted once in the dashboard metrics. Without deduplication, the same enterprise would be counted multiple times, and the dashboard totals would be inflated.

---

## Why the dashboard has a "Derivation Documentation" section

A dashboard that shows numbers without showing where they come from is a dashboard a regulator cannot trust. The Derivation Documentation section at the bottom of the dashboard makes every metric auditable: the reader can see exactly which column of the register feeds each value, and which formula produces it. That section is the audit trail.

---

## Why the Requiring Action table is populated manually (or generated — depending on final build)

The table shows the five highest-utilization accounts. Ideally, it would be generated automatically from a rank column in the register. In this version of the workbook, the table is populated either manually (by sorting the register) or through a `RANK`/`MATCH` mechanism. The README documents which approach is used, so a reviewer knows what to expect.

---

## What was left out and why

- **Collateral and guarantees** — the dataset does not contain them. A production monitor would net them against exposure.
- **Netting arrangements** — same. A production monitor would reflect net exposure, not gross.
- **Real-time monitoring** — the workbook is a periodic snapshot, not a live feed. A production monitor would connect to the firm's systems.
- **Regulatory large-exposure ratios** — the workbook monitors exposure against assigned limits. It does not calculate the Basel III large-exposure ratios, which are a separate regulatory calculation.
