# Design Notes — Counterparty Credit Review Workbook

A short record of the decisions behind the workbook, so a reader can understand *why* it is built the way it is.

---

## Why the workbook uses only ratios the dataset contains

The Corporate Credit Rating dataset provides pre-computed ratios (Current Ratio, Debt/Equity, Net Profit Margin, ROE, ROA, Operating Cash Flow per Share, Free Cash Flow per Share). It does not provide the underlying balance-sheet line items (current assets, inventory, cash, current liabilities), so Quick Ratio and Cash Ratio cannot be derived from it.

Rather than fabricate those ratios, the workbook uses only ratios the dataset supports. The README documents this. A reviewer who sees a workbook that names its own limits trusts it more than one that quietly omits them.

---

## Why leverage ratios are assessed in the opposite direction

For most ratios, a higher value than peers is a strength. For leverage ratios — Long-term Debt/Capital, Debt/Equity — a higher value than peers is a weakness, because it means the counterparty is carrying more debt than its peers. The assessment formula is reversed for these ratios. The conditional formatting reflects this: a debt ratio above the peer average is red, not green.

---

## Why the peer group is small and same-sector

A counterparty that looks healthy in isolation may be weak relative to its peers, or vice versa. Peer context is what turns ratio analysis into a defensible judgment. The peer group is deliberately small (4–5 same-sector companies) for demonstration. In production, the peer group would be built from a defined sector classification and a larger comparator set.

---

## Why the limit recommendation is derived, not observed

The dataset does not contain assigned credit limits. The workbook derives the recommendation from the credit rating and the ratio analysis using a simplified scoring logic. The derivation is documented in the workbook's README tab and in the Rationale field. A production limit would reflect credit policy, concentration limits, collateral, and committee judgment, none of which the dataset contains.

---

## Why the override field exists

A model produces a recommendation. An analyst produces a judgment. When the analyst has information the model cannot see — a pending regulatory decision, a parent guarantee, a change in sector outlook — the override records the departure and the reason. The override field is not for second-guessing the model's arithmetic. It is for injecting judgment the model cannot provide. That is why the rationale is required when the override is used.

---

## What was left out and why

- **External credit data** — the workbook reviews the counterparty's own financials. It does not pull bureau data, sanctions lists, or news. Those are separate inputs to a live review.
- **Collateral and guarantees** — the dataset does not contain them, and a production limit would reflect them. The workbook documents this in the Limitations section.
- **Regulatory capital calculation** — the workbook recommends a limit. It does not calculate RWA or capital impact. Those are downstream processes.
