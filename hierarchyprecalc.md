
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


Certainly! Here's the **Gherkin-formatted version** of the  **data science–driven acceptance criteria** , aligning each criterion with the **Given / When / Then** structure. These scenarios express clear behaviors and expectations tied to the hierarchical precalculation structure for Credit Intelligence.

---

## ✅ **Gherkin Acceptance Criteria: Hierarchical Precalculation for Credit Intelligence**

### **Scenario 1: Organizing financial data into hierarchical layers**

```gherkin
Given the financial data is extracted from source systems
When the precalculation process runs
Then the output must organize metrics into three tiers:
  | Layer               | Description                          |
  | raw_inputs          | Original extracted values            |
  | intermediate_metrics| Calculated values based on logic     |
  | derived_insights    | Interpreted insights for the model   |
```

---

### **Scenario 2: Final insights are derived from intermediate and raw layers**

```gherkin
Given a derived insight is generated (e.g., Financing Requirement narrative)
When the insight is constructed
Then it must reference supporting intermediate metrics and raw inputs used in the calculation
```

---

### **Scenario 3: Metric names are unique and disambiguated**

```gherkin
Given there are metrics with similar labels (e.g., "Total Assets")
When the hierarchical structure is created
Then each key must be uniquely named within its layer
And there must be no duplicated or nested identical metric names
```

---

### **Scenario 4: Derived insights must include rationale and traceability**

```gherkin
Given a derived insight is created
When that insight is included in the model input
Then it must include a human-readable rationale
And a reference to the metric path used to calculate it (e.g., via metadata or key hierarchy)
```

---

### **Scenario 5: Replace flat YoY metrics with structured change representation**

```gherkin
Given a year-over-year metric previously existed in flat form
When the hierarchical output is generated
Then the YoY change must be represented with:
  | Field     | Example          |
  | from      | 55.12            |
  | to        | 46.02            |
  | change    | -9.10            |
  | direction | decreased        |
```

---

### **Scenario 6: Validate CB Tech metrics in the hierarchical structure**

```gherkin
Given CB Tech financial logic is implemented
When the precalculation outputs for FYE and YTD are reviewed
Then the following must be present:
  | Metric                 |
  | financing_requirement |
  | total_external_financing |
  | funding_scenario      |
  | financing_position    |
```

---

### **Scenario 7: Prompts consume only derived insights unless configured otherwise**

```gherkin
Given a prompt is generated by the system
When the model accesses data from the precalculation output
Then it must use only values from the derived_insights layer
Unless explicitly configured to include lower-tier data
```

---

### **Scenario 8: Toggle inclusion of legacy flat metrics**

```gherkin
Given legacy year-over-year metrics may still be required
When the system is configured with a legacy output toggle
Then it must either:
  - Include both flat and structured YoY metrics
  - Or exclude the legacy metrics if the toggle is set to false
```

---

Let me know if you'd like these Gherkin scenarios turned into BDD test specs or linked to actual schema tests or LLM prompt evaluations!



Here’s the **Jira-formatted version** of the feature and associated story, structured for copy-paste into your Jira instance. This format follows Jira best practices for clarity, traceability, and alignment with agile workflows.

---

### 🔹 **Feature (Jira Epic)**

**Name:** Hierarchical Precalculation for Model-Ready Financial Insights

**Issue Type:** Epic

**Summary:**

Implement a three-tier precalculation structure to organize financial data as raw inputs, intermediate metrics, and derived insights. This structure will support improved model performance, interpretability, and traceability in Credit Intelligence prompt generation.

**Description:**

This feature introduces a standardized hierarchy for all precalculated financial metrics, beginning with CB Tech’s financing logic. The hierarchy enables LLMs to consume clean, disambiguated inputs, while allowing analysts and audit systems to trace insights back to the underlying financial values.

**Business Value:**

* Reduces confusion in model prompts due to duplicate or nested metric names
* Enables clear, rational insight generation with full traceability
* Replaces legacy flat YoY metrics with structured alternatives
* Lays groundwork for future expansion of financial logic (e.g., liquidity, coverage ratios)

**Labels:** `credit-intelligence`, `data-science`, `precalculation`, `model-inputs`

**Components:** Credit Intelligence, Prompt Engineering, Data Pipeline

---

### 🔸 **User Story**

**Name:** Structure CB Tech Financial Precalculations Using a Hierarchical Format

**Issue Type:** Story

**Parent Epic:** Hierarchical Precalculation for Model-Ready Financial Insights

**Summary:**

Introduce a hierarchical format for CB Tech financial logic to support more structured and interpretable prompt inputs for Credit Intelligence.

**Description:**

As a data scientist working on Credit Intelligence,

I want precalculated financial data to be structured hierarchically into raw inputs, intermediate metrics, and derived insights,

So that the model receives unambiguous, context-rich inputs that support more accurate and explainable credit narratives.

---

### ✅ **Acceptance Criteria (in Gherkin format)**

*Place in the **Description** or **Acceptance Criteria** field of the Jira story.*

```gherkin
Scenario: Organizing financial data into hierarchical layers
Given the financial data is extracted from source systems
When the precalculation process runs
Then the output must organize metrics into three tiers:
  | Layer               | Description                          |
  | raw_inputs          | Original extracted values            |
  | intermediate_metrics| Calculated values based on logic     |
  | derived_insights    | Interpreted insights for the model   |

Scenario: Final insights are derived from intermediate and raw layers
Given a derived insight is generated (e.g., Financing Requirement narrative)
When the insight is constructed
Then it must reference supporting intermediate metrics and raw inputs used in the calculation

Scenario: Metric names are unique and disambiguated
Given there are metrics with similar labels (e.g., "Total Assets")
When the hierarchical structure is created
Then each key must be uniquely named within its layer
And there must be no duplicated or nested identical metric names

Scenario: Derived insights must include rationale and traceability
Given a derived insight is created
When that insight is included in the model input
Then it must include a human-readable rationale
And a reference to the metric path used to calculate it (e.g., via metadata or key hierarchy)

Scenario: Replace flat YoY metrics with structured change representation
Given a year-over-year metric previously existed in flat form
When the hierarchical output is generated
Then the YoY change must be represented with:
  | Field     | Example          |
  | from      | 55.12            |
  | to        | 46.02            |
  | change    | -9.10            |
  | direction | decreased        |

Scenario: Validate CB Tech metrics in the hierarchical structure
Given CB Tech financial logic is implemented
When the precalculation outputs for FYE and YTD are reviewed
Then the following must be present:
  | Metric                 |
  | financing_requirement |
  | total_external_financing |
  | funding_scenario      |
  | financing_position    |

Scenario: Prompts consume only derived insights unless configured otherwise
Given a prompt is generated by the system
When the model accesses data from the precalculation output
Then it must use only values from the derived_insights layer
Unless explicitly configured to include lower-tier data

Scenario: Toggle inclusion of legacy flat metrics
Given legacy year-over-year metrics may still be required
When the system is configured with a legacy output toggle
Then it must either:
  - Include both flat and structured YoY metrics
  - Or exclude the legacy metrics if the toggle is set to false
```

---

Let me know if you'd like a **subtask breakdown** (e.g., data layer, naming conventions, prompt integration), a  **definition of done** , or a **reporting dashboard** view for tracking rollout!
