# Week 5

**Dates:** Aug 10 – Aug 14, 2026

## Goals

- Load the approved i2b2/MIMIC-III dataset and build the data pipeline for PHI extraction.
- Produce a class-imbalance breakdown of PHI category frequencies.
- Draft the methodology document, including a flow diagram of the proposed pipeline and a description of each step and why it was chosen.

## Approach and Implementation

Received approval and downloaded the clinical notes file from PhysioNet (MIMIC-III v1.4). Built the data pipeline using regex extraction of MIMIC-III's built-in [...] de-identification brackets as ground-truth PHI spans. Tokenized the notes and assigned BIO tags (B-/I-/O) based on bracket category. Validated extracted dates against MIMIC-III's documented 2100–2200 shifted date range and refined the category-mapping logic across two passes after identifying a date-format gap that was inflating the OTHER category. Processed a 1,500-note sample end-to-end and produced a PHI category class-imbalance breakdown.

Drafted the methodology document outlining the proposed pipeline. The planned approach uses a classical NER baseline (fine-tuned BioBERT/ClinicalBERT, without DP) as an accuracy ceiling, with RAG-based context retrieval for NER disambiguation. Differentially private training will then be parallelized with MPI using Opacus across ε = 1, 2, 4, and 8. The pipeline branches into a quantum-kernel comparison (PCA + ZZFeatureMap + SVM, compared against a classical RBF) and a SHAP faithfulness analysis. These results will converge into a final privacy-utility analysis consisting of a three-curve performance chart and a SHAP degradation curve across ε. The methodology document also provides the rationale for the RAG retrieval, MPI parallelization, and quantum/SHAP components.

## Results

- Downloaded and gained working access to the MIMIC-III v1.4 dataset.
- Built and validated a working data pipeline: PHI bracket extraction, BIO tagging, and date-range validation.
- Processed a 1,500-note sample and produced a PHI category token-count breakdown (DATE: 420,472; NAME: 183,777; HOSPITAL: 53,761; CONTACT: 33,648; LOCATION: 20,516; ID: 10,823; OTHER: 7,236; AGE: 1,899), showing significant class imbalance led by DATE.
- Completed a draft methodology document with a full pipeline flow diagram and per-step rationale, covering data preparation, classical NER baseline, RAG retrieval, MPI-parallelized DP training, the quantum kernel and SHAP branches, and the privacy-utility tradeoff output

## Notes/Next Steps
- Determine whether bare numbers in the notes (e.g., 63, 68, 70) should be classified as AGE which will require context-based checks (e.g., "y.o." nearby) rather than label matching alone.
- Decide whether Company/Job Number/Unit Number should become their own ORGANIZATION category or fold into an existing one.
- Finalize the PHI category taxonomy based on the above open questions.
- Scale the extraction pipeline from the 1,500-note sample to the full training set.
- Begin the classical NER baseline: fine-tune BioBERT/ClinicalBERT to establish the accuracy ceiling.
- Address the class imbalance (DATE outnumbers AGE by roughly 220:1) during baseline training.
