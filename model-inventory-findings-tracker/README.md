# Model Inventory & Findings Tracker

A governed register of every model in use, its validation findings, and its review schedule — the core recurring deliverable of a Model Risk Management function.

---

## Business Goal

Give the Model Risk Committee a single, auditable view of which models are in use, which have open findings, and which are due for validation — so that no model runs past its review date without an approved exception.

---

## The Problem It Solves

Regulators (OSFI E-23, SR 11-7) require firms to know every model in use, its risk tier, when it was last validated, and whether open issues exist. Without a single governed register:

- Models get used past their review date
- Findings get lost in email
- A regulator or internal audit exam becomes a scramble

This workbook is the single source of truth that prevents all three.

---

## What the Workbook Contains

| Tab | Purpose |
|-----|---------|
| **README** | Explains purpose, regulatory anchors, and scope |
| **Executive Summary** | One-page dashboard for the Model Risk Committee |
| **Model Inventory** | One row per model: owner, purpose, risk tier, validation status, last and next validation date |
| **Findings Log** | Every validation finding, linked to its model via INDEX/MATCH, with severity, owner, due date, and automatic overdue flag |
| **Review Calendar** | Every model's next review date, with computed "Days Until Due" and OVERDUE / Due Soon / On Track status |
| **Lookup Tables** | Standardized dropdown values used across the workbook |

---

## Regulatory Anchors

- **OSFI E-23 s.3.1** — Model inventory: every model with non-negligible risk must be documented and tracked
- **OSFI E-23 s.3.2** — Risk-based validation frequency: higher-tier models validated more frequently
- **OSFI E-23 s.4.2** — Findings tracked to resolution: each finding must have an owner, a due date, and a status
- **SR 11-7** — Parallel US expectations for inventory, validation independence, and ongoing monitoring

---

## What This Workbook Does NOT Do

It does not perform the validation itself. It does not calculate model risk ratings. It does not store model documentation, validation reports, or technical specifications. It is a **register** — a control that sits alongside validation, not a substitute for it.

It does not replace the Model Risk Committee's judgment or the validator's findings. It tracks them.

---

## Data Note

The model names, owners, and findings shown in the workbook are anonymized for portfolio use. The findings are derived from two independent validation projects (Lending Club and Fannie Mae) and illustrate how findings flow from validation into a governed register. The structure, formulas, and governance logic are directly transferable to a live MRM function.

---

## How to Open It

1. Download `Model_Inventory_Findings_Tracker_v1.0_FINAL.xlsx`
2. Open in Excel 2019 or later (or Microsoft 365)
3. Read the **README** tab first
4. Go to the **Executive Summary** tab
5. If any metric is red, click through to the **Findings Log** or **Review Calendar** to see why

Blue cells are input. Black cells are formulas — do not overtype them.

---

## Screenshots

See the PNG images in the folder:

- `01-executive-summary.png` — the Model Risk Committee dashboard
- `02-model-inventory.png` — the governed register of models

---

## Design Notes

See [`NOTES.md`](./NOTES.md) for the design decisions behind the workbook structure, the risk-based validation cadence, and the findings-tracking logic.
