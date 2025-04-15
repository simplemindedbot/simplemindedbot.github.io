Great — removing solutioning from the user story and aligning terminology with your naming conventions helps ensure clarity for business stakeholders, QA, and downstream implementers. Here’s a clean, revised user story that avoids technical implementation details and uses the proper field names.

⸻

User Story

Title: Replace iHub Account/Variable Names with Renamed Variable Names in Final JSON File

As a Data Engineer supporting the LLM integration,
I want to ensure that all metric labels in the final JSON file use the approved Renamed Variable Names rather than the original iHub Account/Variable Names,
So that the JSON payload sent to the LLM is consistent, human-readable, and aligned with business-approved terminology.

⸻

Description

The JSON payload currently includes metric labels that reflect the original iHub Account/Variable Name conventions. These names often include internal system suffixes such as FR, UCA, or PP, and may not match the polished terminology preferred by business stakeholders or optimal for LLM prompt design.

To address this, a mapping document has been provided that specifies the appropriate Renamed Variable Name for each corresponding iHub Account/Variable Name. All metric labels in the final JSON file must match the Renamed Variable Names exactly as defined in the mapping.

This update ensures consistency across internal data flows, improves interpretability by end users, and helps reduce ambiguity for the LLM.

⸻

Acceptance Criteria (in Gherkin Format)

Feature: Update JSON labels with Renamed Variable Names

  Scenario: Replace iHub Account/Variable Names with Renamed Variable Names
    Given a mapping document that defines Renamed Variable Names for each iHub Account/Variable Name
    And a JSON payload that currently uses iHub Account/Variable Names as keys
    When preparing the final JSON file for LLM delivery
    Then all keys must be replaced with their corresponding Renamed Variable Name

  Scenario: Remove internal system suffixes from final JSON labels
    Given iHub Account/Variable Names that contain suffixes like "FR", "UCA", or "PP"
    When the final JSON is produced
    Then those suffixes must not appear in any of the final JSON keys

  Scenario: Maintain the original metric values during renaming
    Given metric values associated with iHub Account/Variable Names
    When the renaming is applied
    Then the metric values must remain unchanged in the final JSON

  Scenario: Handle unmapped fields
    Given a metric in the JSON that does not have a Renamed Variable Name in the mapping
    When the final JSON is generated
    Then that metric must not appear in the final output



⸻

Let me know if you’d like to include a business justification, example before/after rows from the mapping file, or a related parent Feature to tie this into a broader epics-level tracking view.

Follow-up Questions
Q1: Should the iHub Account/Variable Name ever be retained as metadata in the JSON for traceability?
Q2: Are there any downstream systems or teams that need to be notified when these renamed labels are introduced?
Q3: Will this renaming standard apply to all LLM-bound JSONs going forward, or only to a specific use case or environment (e.g., testing vs production)?