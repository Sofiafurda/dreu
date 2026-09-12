# Week 6

**Dates:** Aug 17 – Aug 21, 2026

## Goals

- Scale the MIMIC-III PHI extraction pipeline from the Week 5 sample to the full NOTEEVENTS corpus and resolve remaining tagging issues.
- Investigate the MultiCliNER dataset as an option for cross-lingual testing.
- Conduct a literature gap analysis to better define the project's research contribution.
- Build an initial DP-SGD implementation to validate the privacy accounting approach before integrating the full model.

## Approach and Implementation

Scaled the MIMIC-III extraction pipeline from the 1,500-note sample to the full NOTEEVENTS corpus. During validation, I found and fixed a bracket-boundary tagging bug that was including delimiters within PHI spans. I also examined the remaining OTHER labels to determine whether an ORGANIZATION subcategory should be added.

Investigated MultiCliNER as a possible dataset for cross-lingual testing. After reviewing its annotations, I determined that its clinical entities do not directly correspond to MIMIC-III's PHI categories, so it would be better suited as a separate generalization test.

Conducted a literature gap analysis across the main components of the project. Existing research covers these areas individually, but I did not identify prior work combining differential privacy, quantum methods, clinical PHI de-identification, and cross-lingual evaluation within the same pipeline.

Built and tested an initial DP-SGD skeleton using Opacus and synthetic data to validate the privacy-accounting workflow before integrating the real model and clinical dataset.

## Results

- Processed the full MIMIC-III NOTEEVENTS corpus of 2,083,112 notes.
- Extracted 12,596,141 PHI spans, with 80.9% of notes containing at least one PHI span.
- Generated full-corpus PHI token counts: DATE ~30.7M, NAME ~13.4M, OTHER ~3.9M, HOSPITAL ~2.4M, CONTACT ~1.5M, LOCATION ~779K, ID ~644K, and AGE ~140K.
- Identified and corrected the bracket-boundary tagging bug affecting PHI span accuracy.
- Scoped MultiCliNER as a potential dataset for cross-lingual generalization testing.
- Completed the literature gap analysis and refined the project's research contribution.
- Validated the initial DP-SGD privacy-accounting workflow on synthetic data, reaching ε ≈ 3.99 for a target ε of 4.

## Notes

- Finalize the PHI taxonomy, including whether unmatched company, job, and unit labels should form an ORGANIZATION category.
- Determine which MultiCliNER languages and entity types will be used for cross-lingual evaluation.
- Reconcile the methodology document's BioBERT/ClinicalBERT baseline with the BERT-CRF baseline specified in the brief.
- Transition from the synthetic DP-SGD test to the real NER model and clinical dataset.
