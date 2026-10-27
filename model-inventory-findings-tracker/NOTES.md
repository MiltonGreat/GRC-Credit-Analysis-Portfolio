# Design Notes — Model Inventory & Findings Tracker

A short record of the decisions behind the workbook, so a reader can understand *why* it is built the way it is.

---

## Why the workbook is structured as a register, not a report

A report is something you produce once. A register is something you maintain. OSFI E-23 s.3.1 requires a *living* inventory of models, not a one-off snapshot. The workbook is designed so that the Model Inventory tab is the single source of truth, and the Executive Summary and Review Calendar are *views* of that register, not separate documents. Update the register, and the views update automatically.

---

## Why Tier 1 models are validated annually and Tier 3 every 24 months

OSFI E-23 s.3.2 requires risk-based validation frequency. The logic is that the cost of a model error scales with how the model is used. A Tier 1 model — a capital model, an IFRS 9 ECL model, a stress testing model — can affect the firm's financial statements or regulatory capital. A Tier 3 model — an internal reporting tool — cannot. The cadence is set proportionately so that validation effort goes where the risk is.

---

## Why findings are never deleted, only closed

A closed finding is evidence that a governance process worked. A deleted finding is evidence that someone did not want the finding seen. The workbook does not have a delete function. Findings are marked Closed when remediated, and they stay in the log. This is the audit trail that OSFI E-23 s.4.2 requires.

---

## Why the Review Calendar is a separate tab, not a column in the inventory

The Review Calendar is a *governance control* in its own right. Its job is to prove to a regulator that no model is running past its due validation date without an approved exception. If that control is buried as a column in the inventory, it is not visible. As a separate tab, it is the first thing a reviewer sees.

---

## Why the data note is explicit

The findings in this workbook are anonymized from two real validation projects (Lending Club and Fannie Mae). A reader who does not know this might assume the findings are fictional, which would undervalue the workbook. A reader who *does* know it can see that the findings are grounded in real validation work, which makes the workbook more credible, not less.

---

## What was left out and why

- **Model documentation** — the workbook is a register, not a document store. The inventory row links to the documentation, not the other way around.
- **Risk rating calculation** — the risk tier is assigned by the risk rating methodology, not calculated by the workbook. The workbook records the tier; it does not derive it.
- **Validation workflow** — the workbook tracks findings. It does not automate the validation process. That is what a workflow tool is for.
