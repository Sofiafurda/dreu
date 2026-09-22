# Week 10

**Dates:** Sep 14 – Sep 20, 2026

## Goals

- Scale and validate the NER experiments using the controlled 10k dataset.
- Complete the ε = 1, 2, 4, and 8 privacy-budget comparison.
- Implement and validate the standalone agent architecture for later MPI integration.
- Complete the SHAP explainability and stability analysis.
- Evaluate the portability of the architecture beyond the original MIMIC-III PHI task.
- Complete the ICMLDE 2026 revisions and continue polishing the final DREU paper.

## Approach and Implementation

Scaled the validated NER methodology to the controlled 10k experiment while preserving the preprocessing, deterministic split, model architecture, training configuration, and evaluation protocol established during the earlier experiments. Completed the non-private baseline followed by the ε=4 DP-SGD experiment and verified the resulting privacy and utility metrics.

Built the full privacy-budget evaluation around the validated ε=4 reference and completed independent DP-SGD experiments for ε = 1, 2, and 8 at δ=1e-5. This produced the complete ε = 1, 2, 4, and 8 privacy–utility comparison under consistent experimental conditions.

Designed and implemented four standalone Python agents for Retrieval, NER/Inference, Differential Privacy, and Evaluation using a common run(request: dict) -> dict interface. Validated the architecture locally and evaluated all 1,987 held-out records to verify that the standalone components reproduced the saved ε=4 results. Prepared the project and documentation for later integration with the MPI/distribution component.

Expanded the evaluation beyond the primary MIMIC-III experiment. Completed the planned SHAP attribution and stability analysis across the non-private and four DP checkpoints and conducted a bounded MultiClinNER experiment to evaluate portability to multilingual clinical concepts.

Substantially revised the ICMLDE 2026 manuscript in response to reviewer feedback and completed the resubmission process. Continued polishing the final DREU research paper by incorporating the validated privacy–utility, architecture, explainability, and portability results.

Evaluated the feasibility of applying a quantum-kernel workflow to frozen clinical token representations and completed the final MultiClinNER sliding-window experiment to examine the effect of extending document coverage beyond the original fixed prefix.

## Results

- Completed the 10k non-private baseline with F1≈0.9985 and the validated 10k DP-SGD ε=4 experiment with actual ε≈3.9938 and F1≈0.9170.
- Completed the full ε = 1, 2, 4, and 8 privacy-budget sweep, with F1 ranging from approximately 0.8888 at ε=1 to 0.9209 at ε=8.
- Implemented and validated the standalone Retrieval, NER/Inference, Differential Privacy, and Evaluation agents.
- Reproduced the validated ε=4 results across all 1,987 held-out records using the standalone architecture and prepared the components for later MPI integration.
- Completed the fixed 32-record SHAP attribution and stability experiment across the non-private and four DP checkpoints.
- Completed the initial seven-language MultiClinNER portability experiment.
- Completed the ICMLDE 2026 revisions and resubmission and continued polishing the final DREU research paper.
- Completed the four-qubit Qiskit Aer quantum-kernel feasibility experiment, with the ideal quantum kernel achieving F1≈0.4571 compared with F1≈0.8966 for the classical RBF control.
- Completed the MultiClinNER sliding-window experiment, increasing entity coverage from 25.49% to 99.9973% and improving F1 from 0.4236 to 0.4952 on the controlled prefix-covered subset.

## Notes

- The privacy-budget experiments provide the completed ε = 1, 2, 4, and 8 comparison at δ=1e-5 under consistent experimental conditions.
- The standalone components were prepared for MPI integration, but MPI itself was not implemented as part of this work.
- The quantum experiment was a bounded feasibility study and should not be interpreted as evidence of quantum advantage or representative clinical NER performance.
- The MultiClinNER sliding-window improvement was interpreted descriptively because windowing increased both document coverage and supervised training exposure.
- Finalize the DREU paper and research documentation and coordinate the final presentation with the team.
