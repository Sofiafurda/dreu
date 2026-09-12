# Week 7

**Dates:** Aug 24 – Aug 30, 2026

## Goals

- Refine the MIMIC-III PHI taxonomy and resolve classification issues identified during the full-corpus analysis.
- Add context-aware handling for ambiguous numeric PHI labels and reduce the number of labels remaining in OTHER.
- Re-run and validate the full MIMIC-III extraction pipeline with the updated classification rules.
- Draft and revise the conference paper for submission to Elsevier ICMLDE 5.0.
- Meet with the research team to review progress and clarify plans for the individual papers and combined journal article.

## Approach and Implementation

Refined the MIMIC-III extraction pipeline by adding context-aware handling for ambiguous numeric labels. Added detection for apostrophe-prefixed abbreviated years and nearby age-related context to better distinguish DATE and AGE mentions that could not be classified reliably from the label alone.

Expanded the PHI taxonomy by adding an ORGANIZATION category for company, job number, unit number, university, and college labels. I also extended the ID mapping rules to capture additional identifier types and added handling for several remaining unmatched label patterns.

Re-ran the updated pipeline across the full NOTEEVENTS corpus and audited the resulting PHI categories. Validated DATE classifications against MIMIC-III's shifted-year range, reviewed remaining unmatched labels, and generated an updated PHI category distribution for the full dataset.

Drafted, edited, and revised our conference paper and submitted it to the Elsevier 5th International Conference on Machine Learning and Data Engineering (ICMLDE 5.0), 2026. Met with the research team to review our progress and clarify the direction of our individual papers and the planned combined journal article.

## Results

- Implemented context-aware classification for ambiguous numeric PHI labels, including abbreviated DATE values and AGE mentions.
- Added the ORGANIZATION category and expanded the ID mapping rules, substantially reducing the number of tokens remaining in OTHER.
- Processed 2,083,180 notes with the updated pipeline.
- Produced updated full-corpus PHI token counts: DATE 30,779,348; NAME 13,421,328; ID 4,204,694; HOSPITAL 2,354,438; CONTACT 1,522,662; LOCATION 779,315; OTHER 183,286; AGE 140,690; ORGANIZATION 80,145.
- Audited DATE classifications and identified 180,590 out-of-range year-token occurrences.
- Generated an updated full-corpus PHI category distribution chart for use in the research materials.
- Submitted the conference paper to Elsevier ICMLDE 5.0.
- Met with the research team and aligned on the direction of the individual papers and combined journal article.

## Notes

- Review the remaining OTHER labels and determine whether any additional classification rules are necessary.
- Reconcile the methodology documentation with the finalized PHI taxonomy and updated mapping rules.
- Transition from data-pipeline refinement toward the classical NER baseline and agentic architecture.
- Continue developing the individual research paper and coordinate its direction with the team's combined journal article.
