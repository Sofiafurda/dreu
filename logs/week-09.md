# Week 9

**Dates:** Sep 7 – Sep 13, 2026

## Goals

- Complete and debug the first end-to-end non-private and DP-SGD NER pipeline.
- Diagnose initial model-performance issues and validate the evaluation methodology.
- Establish a meaningful small-data baseline before scaling the experiments.
- Refine plans for the privacy-budget comparison, agent architecture, and explainability analysis.
- Continue polishing the final DREU paper.
- Begin addressing revisions for the ICMLDE 2026 conference paper.

## Approach and Implementation

Completed the first end-to-end notebook capable of running both non-private and Opacus DP-SGD training. The initial smoke test successfully exercised the complete training and privacy-accounting workflow at a target ε=4 and δ=1e-5, but the resulting NER performance was near zero.

Performed a detailed audit of the pipeline to determine why the model was not learning effectively. Reviewed class imbalance, training and validation label distributions, predicted labels, PHI counts, ignored-token handling, BIO/WordPiece alignment, subword behavior, and train/validation separation. Verified that padding and special tokens were excluded correctly and that evaluation focused on strict PHI precision, recall, and F1 rather than token accuracy dominated by the O class.

Refined the small-data training configuration and repeated the experiments until both the non-private and private models learned meaningful PHI patterns. Used the successful 1k experiment to establish a controlled methodology for the later 10k experiments, including consistent preprocessing, deterministic splitting, model configuration, privacy accounting, and evaluation.

Developed the experimental plan for comparing privacy budgets of ε = 1, 2, 4, and 8 while keeping the experimental conditions consistent. Also refined the planned separation of retrieval, NER/inference, differential privacy, and evaluation responsibilities and established SHAP-based analysis as the approach for examining model explanations across privacy levels.

Continued developing and polishing the individual DREU research paper. Received the ICMLDE 2026 revision decision, reviewed the reviewer feedback, and began organizing revisions to the methodology, literature review, quantitative evidence, limitations, and presentation.

## Results

- Completed the first functioning end-to-end non-private and Opacus DP-SGD NER pipeline.
- Identified and corrected the issues affecting the initial near-zero model performance.
- Validated BIO/WordPiece alignment, ignored-token handling, train/validation separation, and strict PHI-focused evaluation.
- Completed the 1k non-private proof-of-concept experiment with F1≈0.9825.
- Completed the corresponding 1k DP-SGD ε=4 experiment at δ=1e-5 with actual ε≈3.9917 and F1≈0.7970.
- Established the controlled methodology for scaling the experiments to 10k records.
- Defined ε = 1, 2, 4, and 8 as the planned privacy-budget comparison and established the evaluation approach.
- Refined the modular agent architecture and planned SHAP-based explainability evaluation.
- Continued polishing the final DREU research paper.
- Received the ICMLDE 2026 revision decision and began addressing the requested revisions.

## Notes

- Scale the validated methodology to the controlled 10k experiments.
- Run the full privacy-budget comparison under consistent experimental conditions.
- Implement and validate the standalone agent architecture.
- Complete the SHAP explainability analysis after the final model checkpoints are available.
- Continue the ICMLDE revisions and individual-paper development.
