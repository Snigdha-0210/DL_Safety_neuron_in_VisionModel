# Threats to Validity & Review Limitations

Academic integrity requires transparent disclosure of the methodological constraints, selection boundaries, and epistemological limitations governing this systematic literature review.

---

## 1. Information Retrieval & Selection Boundary Limitations

### Bounded Captured-Results Audit
The primary limitation of this review is its reliance on a **bounded captured-results identification protocol** rather than an automated full-database export:
- The identification ledger documents exactly **30 visible Google Scholar records** (the top 10 displayed results from three queries captured on 18 October 2026) alongside **16 research-paper PDFs** assembled in the course archive.
- Google Scholar's search interface displayed approximate result estimates of ~15,300 (Query S1), ~12,700 (Query S2), and ~156 (Query S3). **This review does not claim to have screened or downloaded these tens of thousands of hits.** 
- Due to the absence of full database exports and automated pagination dumps, there is a risk of availability and ranking bias inherent to Google Scholar's proprietary search algorithms.

### Unresolved Full-Text Appraisals ($n = 11$)
During title/abstract screening of the 38 unique records, **11 candidate records** appeared potentially relevant to the mechanistic interpretability of VLM safety (e.g., *VLM-Guard*, *Spot Risks Before Speaking*, *SafeSteer*, *SafeNexus*), but did not have retained full-text PDFs in the course archive.
- **Transparent Accounting:** These 11 records were not discarded or retroactively declared ineligible based on title alone; they are formally documented as *unresolved full-text appraisals*.
- No claim is made that these papers are unavailable online; rather, they fell outside the archived evidence corpus assembled for this university assessment. A fully exhaustive systematic review would require retrieving and evaluating all 11 full texts.

### Unsearched Commercial Bibliographic Databases
No systematic search logs or record exports were performed on commercial or specialized indexing databases, including **IEEE Xplore, Scopus, Web of Science, ACM Digital Library, PubMed, SpringerLink, or ScienceDirect**. Coverage is bounded strictly to Google Scholar and verified open-access / preprint repositories.

---

## 2. Inappropriateness of Statistical Meta-Analysis

### Benchmark & Metric Incommensurability
A quantitative meta-analysis or statistical pooling of effect sizes was neither feasible nor scientifically defensible due to profound methodological heterogeneity across the eight core studies:
- **Disparate Metrics:** Li et al. (2025) report percentage reduction in Attack Success Rate ($\Delta$ASR), Xie et al. (2026) report raw attack transfer ASR under an adversarial attack, Li et al. (2026) report ablation-induced refusal drop rates, and Gupta & Chakraborty (2026) evaluate visual grounding restoration accuracy.
- **Checkpoint Divergence:** Studies evaluate different revisions of LLaVA (v1.5, v1.6), InternVL, Qwen-VL, MiniGPT-4, and proprietary black-box APIs (GPT-4V, Claude 3).
- **Prompt & Attack Heterogeneity:** Threat models vary from typographic OCR text (FigStep) to adversarial visual perturbations (Hades) and semantic jailbreak framing (MM-SafetyBench).

Treating these distinct numerical metrics as interchangeable data points in a statistical meta-analysis would produce fundamentally misleading conclusions. Consequently, findings are synthesized qualitatively.

---

## 3. Qualitative Risk-of-Bias Appraisal

In accordance with course review guidelines, study quality was appraised qualitatively across predefined dimensions (internal unit clarity, intervention rigor, safety-utility balancing, and generalization scope). The review did not employ a standardized clinical risk-of-bias tool (such as Cochrane RoB-2 or ROBINS-I), as these instruments are tailored for randomized clinical trials rather than empirical deep learning computer science publications.

---

## 4. Academic Identity Declaration: Literature Review

**Explicit Disclaimer:**  
This project represents a **systematic literature review and theoretical/methodological synthesis**, submitted for university course assessment (CSE4006 – Deep Learning, Digital Assessment 2 & 3).

- The researcher (Snigdha Gorai) **did not personally train, fine-tune, or experimentally execute** the deep learning models, probing classifiers, or activation interventions described in the reviewed papers.
- All reported quantitative values (such as the 88 text-safety neurons in Li et al., the 59.7% ASR in Xie et al., or the 52.98% ASR reduction in Li et al.) are attributed strictly to the original peer-reviewed or preprint publications.
- Conceptual architecture and workflow diagrams presented in this repository illustrate synthesized theoretical models and do not represent verified implementations of a single specific system.

