# Week 8

**Dates:** Aug 31 – Sep 6, 2026

## Goals

- Transition from MIMIC-III preprocessing and PHI-taxonomy refinement to the clinical NER modeling phase.
- Develop the initial non-private and differentially private NER workflow.
- Establish a consistent methodology for comparing standard training with DP-SGD.
- Begin planning how the modeling pipeline would connect to the agentic and distributed architecture.
- Continue developing the research paper.

## Approach and Implementation

Shifted focus from preprocessing toward the modeling phase of the project. Began developing a DistilBERT token-classification workflow using the processed MIMIC-III BIO data, including data loading, deterministic train/validation splitting, tokenization, BIO-label alignment, model training, and evaluation.

Worked through the requirements for incorporating Opacus DP-SGD while keeping the experiments feasible on available hardware. Defined the initial model configuration, privacy-accounting approach, and evaluation methodology that would later be used to compare non-private and differentially private training.

Established safeguards for evaluating the NER models correctly, including handling padding and special tokens, aligning BIO labels with WordPiece tokenization, maintaining separate training and validation data, and focusing evaluation on PHI detection rather than overall token accuracy.

Also began defining how the NER, privacy, retrieval, and evaluation responsibilities could remain modular for later integration with the team's distributed-computing work. Continued shaping the individual research paper around privacy-preserving clinical NER, model utility, explainability, and distributed execution.

## Results

- Created the initial DP-NER notebook framework and experimental workflow.
- Established the DistilBERT configuration for non-private and DP-SGD training.
- Defined the BIO/WordPiece alignment, deterministic splitting, and PHI-focused evaluation methodology.
- Established the initial privacy-accounting approach for upcoming DP experiments.
- Defined the high-level modular direction for the later agent architecture.
- Continued developing the methodology and scope of the research paper.

## Notes
- Complete and debug the first end-to-end non-private and DP-SGD experiments.
- Verify that the model learns PHI categories reliably before scaling to larger experiments.
- Preserve consistent preprocessing, splitting, and privacy-accounting settings across later experiments.
