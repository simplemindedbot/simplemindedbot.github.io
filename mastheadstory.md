Excellent — thanks for the reset and the clear direction. Based on your updated guidance, here’s a clean version of the **user story** and **Gherkin-formatted acceptance criteria**, aligned with those two specific goals:

---

## ✅ User Story: Align CREDIT INTELLIGENCE Branding with Wells Fargo Standards

**Title:** Update CREDIT INTELLIGENCE Masthead Font and Remove Redundant Page-Level Instances  
**As a** web content manager for the CBCI site,  
**I want** the “CREDIT INTELLIGENCE” text in the masthead to use the Wells Fargo-standard font,  
**and I want** all redundant instances of “Credit Intelligence” removed from page titles and page headers,  
**so that** the site's visual presentation adheres to Wells Fargo brand standards and avoids redundant labeling.

---

### 📝 Description:

- The **masthead** currently contains the title **“CREDIT INTELLIGENCE”**, which is **correctly placed**, but it uses a **non-standard font**.
- Additionally, the phrase **“Credit Intelligence”** is **repeated in page titles or headers** on many pages, leading to **visual redundancy** and inconsistent branding.
- This story focuses on:
  1. Updating the **masthead font** to conform to Wells Fargo typography standards (e.g., font family, size, weight, letter spacing, and case treatment).
  2. Removing “Credit Intelligence” from **within the white page body**, specifically from:
     - Combined page titles (e.g., “Credit Intelligence – Market Summary” → “Market Summary”)
     - Any standalone headers or section headers that redundantly state “Credit Intelligence”
- The masthead should remain visually prominent and maintain responsive behavior across breakpoints.

---

## ✅ Acceptance Criteria (Gherkin Format)

```gherkin
Feature: Credit Intelligence Brand Update in Masthead and Page Titles

  Scenario: Apply Wells Fargo-standard font to masthead title
    Given I am on any page of the CBCI site
    When the page loads
    Then the text "CREDIT INTELLIGENCE" appears in the masthead
    And it uses the official Wells Fargo font, size, weight, and letter spacing as defined in the branding guidelines

  Scenario: Remove "Credit Intelligence" from combined page titles
    Given a page previously displayed the title "Credit Intelligence – Market Summary"
    When I view the updated page
    Then the title displays only "Market Summary"
    And there is no "Credit Intelligence" prefix or repetition

  Scenario: Remove standalone "Credit Intelligence" headers within page content
    Given a page has a header or section title that says "Credit Intelligence"
    When I view the updated page
    Then that header is removed entirely unless required for navigation or structure
    And the visual layout adjusts accordingly

  Scenario: Ensure accessibility and semantic structure are preserved
    Given I am using a screen reader or accessibility tool
    When I navigate through the masthead and page titles
    Then the "CREDIT INTELLIGENCE" masthead is announced appropriately
    And the page title hierarchy remains semantically correct (e.g., `<h1>` for the page title)

  Scenario: Responsive design compliance
    Given I view the site on desktop, tablet, or mobile
    When the page loads
    Then the "CREDIT INTELLIGENCE" masthead text maintains proper styling and legibility
    And redundant “Credit Intelligence” references do not reappear on smaller screens
```

---

## 📌 Optional Implementation Notes:

- Reference the Wells Fargo brand standards documentation for the exact font stack and CSS specs.
- If “Credit Intelligence” is hardcoded or appended via CMS templates, logic updates will be required to suppress it.
- Regression testing should validate that all pages show correct page titles and that no accessibility regressions occur.

---

Would you like to track this as two subtasks under an epic (e.g., “CBCI Brand Compliance: Phase 1”)? That could help separate the **masthead styling** from the **content de-duplication** workstreams.

---

**Q1:** Should the “CREDIT INTELLIGENCE” masthead remain in all caps, or does the WF standard suggest title or sentence case?  
**Q2:** Is there a fallback font or font weight if the primary Wells Fargo brand font isn't available on all devices?  
**Q3:** Do you want to add a QA step or stakeholder review checkpoint to confirm no business-critical headers are removed by mistake?