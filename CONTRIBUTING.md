# Contributing to the VLM Mechanistic Safety Review

Thank you for your interest in contributing to this academic literature review repository.

This project is maintained as an open, reproducible research repository supporting the systematic study of internal safety mechanisms in Vision-Language Models (VLMs).

---

## 1. Principles of Academic Contribution

We welcome contributions from researchers, graduate students, and AI safety practitioners. To maintain academic rigor, all proposed updates must adhere to the following standards:

1. **Empirical Traceability:** Any claim regarding a model's internal representations, neuron counts, or benchmark performance must cite an inspectable peer-reviewed conference publication or verifiable arXiv preprint.
2. **PRISMA 2020 Compliance:** Proposed additions of literature must include full bibliographic details (authors, title, venue, year, DOI/URL) and an explicit screening appraisal justifying inclusion or exclusion based on the established eligibility criteria in [`docs/methodology.md`](docs/methodology.md).
3. **No Fabricated Benchmarks:** Do not submit pooled averages or comparative metrics across papers that were evaluated under non-identical benchmark configurations.
4. **No Copyrighted PDF Uploads:** Do not commit copyrighted full-text research papers or commercial PDF files to this repository. Provide links to the official publisher or open-access repository instead.

---

## 2. Types of Contributions

### A. Correcting Extraction or Typographical Errors
If you identify an error in an author name, benchmark citation, publication venue, or reported metric:
1. Open an Issue with the prefix `[Correction]`, detailing the file, line number, and verified publisher source.
2. Submit a Pull Request targeting the `main` branch with the minimal necessary correction.

### B. Suggesting New Studies for Synthesis
If you are the author of or have identified an empirical study investigating internal safety representations in VLMs (e.g., published in 2025–2026):
1. Open an Issue with the prefix `[Candidate Study]`.
2. Provide:
   - Complete citation and DOI/arXiv link,
   - Evaluated models and internal units analyzed (neurons, circuits, subspaces, layers),
   - Causal intervention methodology (probing, patching, steering, projection),
   - Evaluated benchmarks and reported findings.

### C. Auditing the PRISMA Screening Ledger
If you wish to independently verify the PRISMA identification flow or evaluate one of the 11 candidate studies currently categorized as *unresolved full-text appraisals* in [`data/unique-record-decisions.csv`](data/unique-record-decisions.csv), please submit an issue documenting your full-text eligibility appraisal.

---

## 3. Pull Request Workflow

1. Fork the repository and create your branch from `main`:
   ```bash
   git checkout -b feature/suggested-update
   ```
2. Ensure markdown formatting is clean and all relative links render correctly.
3. Validate BibTeX entries in `references/bibliography.bib` using standard syntax checkers.
4. Submit your PR with a concise description of changes and supporting citations.

---

## 4. Code of Academic Conduct

Contributors are expected to uphold standards of professional academic discourse, scholarly honesty, and constructive collaboration. Plagiarism, misattribution of findings, or unverified claims will result in immediate PR rejection.
