
Great question. If the  **user story is coming from the data science team** , the framing should reflect their goals: ensuring  **model performance, interpretability, data consistency** , and reducing  **prompt ambiguity** . While the structure of the story remains similar, the **persona shifts** from product manager to data scientist, and the motivation moves toward **supporting model behavior** and  **improving downstream outputs** .

---

## ✅ **Adjusted User Story (Data Science Perspective)**

**Title:** Structure Precalculated Financial Metrics Hierarchically to Improve Model Interpretability and Prompt Performance

**As** a data scientist working on Credit Intelligence,

**I want** precalculated financial data to be structured hierarchically into raw inputs, intermediate calculations, and derived insights,

**So that** the model receives unambiguous, context-rich inputs that support more accurate and explainable credit narratives.

---

## 🎯 **Acceptance Criteria**

| **ID**                                                                 | **Acceptance Criteria**                                                                                                                                                                            |
| ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AC1**                                                                | All precalculated metrics must be organized into three structured tiers:                                                                                                                                 |
| →`raw_inputs`(e.g., base values from financials)                          |                                                                                                                                                                                                          |
| →`intermediate_metrics`(e.g., computed values like financing requirement) |                                                                                                                                                                                                          |
| →`derived_insights`(e.g., summary narratives for prompts)                 |                                                                                                                                                                                                          |
| **AC2**                                                                | Final narrative elements passed into the model (e.g., “Financing Requirement funded by external sources”) must be derived only from values in the `derived_insights`layer.                           |
| **AC3**                                                                | Input data for the model must avoid naming collisions or duplication across layers (e.g., nested “Total Assets” values), to prevent model confusion.                                                   |
| **AC4**                                                                | Each insight in the `derived_insights`layer must be traceable to its calculation path via metadata or references to upstream values.                                                                   |
| **AC5**                                                                | Previously used flat year-over-year metrics are replaced with structured forms (e.g.,`from`,`to`,`change`,`direction`) that allow models to understand the magnitude and direction of change.    |
| **AC6**                                                                | The CB Tech financing logic—including `financing_position`,`total_external_financing`, and `funding_scenario`—is implemented as the first hierarchical use case, validated against example data. |
| **AC7**                                                                | The model’s prompt-generation logic must be tested to confirm it consumes the `derived_insights`layer and ignores lower-level inputs unless explicitly configured.                                    |
| **AC8**                                                                | If legacy flat metrics are retained during transition, a configuration setting controls their inclusion to enable prompt testing and model A/B comparison.                                               |

---

## 🧠 Rationale (From a Data Science Lens)

* **Model Behavior** : LLMs are sensitive to naming repetition and structure. Flattened or ambiguous metrics (e.g., nested “Total Assets”) degrade quality.
* **Interpretability** : Clear traceability supports trust in generated insights and helps with regulatory audits or user questions.
* **Prompt Precision** : Layered data supports better prompt tuning by providing the right level of abstraction (raw vs. interpreted).
* **Data Hygiene** : Hierarchies prevent leakage of conflicting signals and help create cleaner, more semantically consistent inputs.

---

## 🧪 Example Prompt Input (Before vs After)

### **Before (Flat and Duplicative):**

```
"Total Assets": "Increased by 56.3MM",
"Total Assets": "Includes Current Assets",
"Current Assets": "Increased by 48.41MM"
```

### **After (Structured):**

```json
{
  "intermediate_metrics": {
    "total_assets_summary": {
      "from": 655.21,
      "to": 711.51,
      "change": 56.3
    }
  },
  "derived_insights": {
    "narrative_summary": "Total assets increased by $56.3MM, driven primarily by a $48.41MM rise in current assets."
  }
}
```

---

## 🔁 Optional Additions for DS Teams

* Model validation checkpoints can test whether prompts built using hierarchical `derived_insights` lead to more accurate or concise generations.
* Tracking performance of hierarchical vs. legacy prompts in production.
* Schema enforcement or linting step before passing inputs to the model.

---

### Q: Want this as a Jira-ready card with subtasks and testing notes?

### Q: Would it help to pair this story with prompt output samples or A/B test specs?

Let me know how you’d like to extend this next—model eval framework, schema, or implementation planning!
