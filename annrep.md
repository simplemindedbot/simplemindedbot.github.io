Here are user story components for each of the requirements you’ve outlined. These are written in standard format with Title, Description, and Acceptance Criteria using Gherkin-style where applicable.

⸻

1. Identify Annual vs Non-Annual Data in Uploaded File

Description:
As a data science engineer, I want to identify whether the uploaded file contains annual or non-annual data so that the model can treat the data appropriately during ingestion.

Acceptance Criteria:
	•	GIVEN a file has been uploaded
WHEN the file is parsed
THEN the ingestion process should label the data as “annual” or “non-annual” based on in-file indicators (e.g., title, section headers, or dates)

⸻

2. Use File Upload Location as Identifier (CTech)

Description:
As a credit technology engineer, I want to use the file upload location as an identifier so that each file’s source can be reliably traced in downstream processing.

Acceptance Criteria:
	•	GIVEN a file is uploaded to a specific location
WHEN the ingestion process begins
THEN the system should log and associate the file with its upload location for audit and classification purposes

⸻

3. Include Section Identifiers in Single File Input

Description:
As a credit technology engineer, I want to ensure the system supports single file uploads containing multiple sections, each with a unique identifier, so that ingestion can handle compound documents.

Acceptance Criteria:
	•	GIVEN a single file contains multiple document sections
WHEN the file is processed
THEN each section should be tagged with its own identifier for model segmentation and analysis

⸻

4. Evaluate Additional Data Integrity Controls

Description:
As a product manager, I want to evaluate additional data integrity controls that can be applied to the uploaded reports so that the ingestion process remains robust and trustworthy.

Acceptance Criteria:
	•	GIVEN a set of ingestion control options
WHEN product review occurs
THEN product should identify additional controls (e.g., checksums, schema validation, duplication detection) to implement or defer with rationale

⸻

5. Associate Annual Footnotes with Most Recent Annual Optimist Statement

Description:
As a data science engineer, I want to ensure annual footnotes are correctly associated with the most recent annual Optimist financial statement so that the model uses the correct contextual data.

Acceptance Criteria:
	•	GIVEN an uploaded file contains annual footnotes
AND an annual Optimist statement has been selected
WHEN ingestion occurs
THEN the footnotes should be mapped to the corresponding statement if they match in reporting period or naming convention

⸻

6. Use First Page Date to Identify Footnote Period (CBTech)

Description:
As a CBTech engineer, I want to use the date on the first page of the document to identify the applicable period for the associated footnotes so that they can be correctly indexed.

Acceptance Criteria:
	•	GIVEN a document is uploaded
WHEN the first page date is extracted
THEN the footnotes should be tagged with the period identified by that date

⸻

7. Validate Date Logic Across Additional Statements

Description:
As a product manager, I want to validate that the logic for using the first page date to identify footnote periods holds across multiple statement formats so that ingestion rules can be generalized confidently.

Acceptance Criteria:
	•	GIVEN a sample of annual and YTD statements
WHEN product reviews the footnote-date alignment logic
THEN product should confirm whether this logic holds or identify exceptions requiring rule changes

⸻

Let me know if you’d like these grouped into Epics, or turned into Jira-friendly format with labels and task types.

Q1: Would you like these stories grouped by theme (e.g., ingestion logic, metadata tagging, validation)?
Q2: Should I create Epics and Features for organizing these into a Jira backlog?
Q3: Do you want a shared definition of “annual” vs. “non-annual” to include in the documentation for these stories?