# PRISMA 2020 Search Strategy & Identification Protocol

This document details the search strategy, query specifications, information sources, and deduplication audit implemented for the systematic literature review:

**"Mechanistic Interpretability of Safety Neurons in Vision-Language Models"**  
*Researcher:* Snigdha Gorai (Register Number: 24BCE7185)  
*Institution:* VIT-AP University | CSE4006 Deep Learning  
*Audit Date:* 28 October 2026 (Queries captured 18 October 2026)

---

## 1. Information Sources & Boundary Declaration

- **Primary Discovery Interface:** Google Scholar (`scholar.google.com`).
- **Capture Date:** 18 October 2026.
- **Audit & Deduplication Date:** 28 October 2026.
- **Interface Settings:** Articles; Sort by relevance; Date range: "Any time".
- **Evidence Boundary:** This review operates on an **auditable, bounded captured-results protocol**. Exactly 30 visible Google Scholar result records (the first 10 visible items from each of 3 query sessions) were recorded alongside 16 full-text research PDFs assembled in the course archive.
- **Important Disclosure:** This is not an automated full-database export or an exhaustive screening of all hits displayed by Google Scholar (~15,300, ~12,700, and ~156 approximate results). Instead, it provides an auditable, verifiable record ledger of 46 total appearances resolving to 38 unique research works.

---

## 2. Search Queries & Interface Telemetry

| Query ID | Search String / Query Syntax | Filter Settings | Displayed Interface Estimate | Visible Entries Captured |
| :--- | :--- | :--- | :--- | :--- |
| **S1** | `("vision-language model" OR "multimodal large language model") AND (safety OR refusal OR jailbreak) AND (interpretability OR neuron OR circuit)` | Articles, Relevance, Any time | ~15,300 | 10 entries (Rank 1–10) |
| **S2** | `("vision-language model" OR VLM OR MLLM) AND ("activation patching" OR probing OR ablation) AND (safety OR refusal)` | Articles, Relevance, Any time | ~12,700 | 10 entries (Rank 1–10) |
| **S3** | `("safety neurons" OR "safety circuit" OR "safety subspace") AND ("vision-language model" OR multimodal) AND (causal OR intervention OR steering)` | Articles, Relevance, Any time | ~156 | 10 entries (Rank 1–10) |

*Note on interface numbers:* Displayed counts (~15,300, ~12,700, ~156) represent Google Scholar's approximate indexing estimates. They are never summed or used as screening counts.

---

## 3. Supplementary Information Sources Consulted

1. **Retained Research PDF Archive:** 16 peer-reviewed conference and preprint PDFs collected during preliminary reading (12–16 October 2026).
2. **Publisher & Repository Verification:** Targeted cross-referencing on official proceedings (CVPR, ICCV, WACV via Computer Vision Foundation; ICML via PMLR; AAAI via OJS; ACL Anthology) and arXiv to verify exact author lists, publication statuses, and preprint-to-conference equivalencies.
3. **Excluded Databases:** No systematic query logs or exports were conducted on IEEE Xplore, Scopus, Web of Science, PubMed, or ACM Digital Library; no claims of coverage are made for these sources.

---

## 4. Deduplication & Record Reconciliation Arithmetic

The selection and screening ledger reconciles all 46 captured record appearances as follows:

```text
  30 Visible Google Scholar Results (10 per query S1, S2, S3)
+ 16 Retained Research-Paper PDFs in Course Archive
-----------------------------------------------------------
  46 Total Record Appearances

-  2 Duplicate appearances within Google Scholar search queries
     * S2-10 duplicates S2-07 ("HiddenDetect", Jiang et al.)
     * S3-01 duplicates S2-02 ("Diagnosing and Repairing Unsafe Channels", Fu et al.)
-  6 Overlapping appearances between Scholar results and PDF archive
     * Fu et al. (2026) [CARE]
     * Wang et al. (2025) [ASTRA]
     * Li et al. (2025) [IAR]
     * Li et al. (2026) [Safety Neurons Across Modalities]
     * Xie et al. (2026) [Dissecting the Safety Circuit]
     * Shi et al. (2026) [Precise Shield / Targeted Interpretable]
-----------------------------------------------------------
  38 Unique Research Records Screened
```

---

## 5. Screening & Eligibility Criteria

| Criterion | Include in Core Synthesis | Exclude from Core Synthesis |
| :--- | :--- | :--- |
| **Topic** | Internal safety-related representations, circuits, or interventions in VLMs / MLLMs | General safety benchmarking, red-teaming datasets, or training pipelines without internal analysis |
| **Method** | Empirical probing, ablation, activation patching, activation steering, causal mediation, or subspace projection | Output-only black-box evaluation, behavioral jailbreaks without internal representation analysis |
| **Modality** | Vision-Language Models (VLMs) or Multimodal Large Language Models (MLLMs) | Unimodal language-only models (retained as context only) or unimodal vision classifiers |
| **Evidence** | Full-text empirical paper available with verifiable methodology and outcomes | Insufficient technical documentation or primary scope outside safety interpretability |
| **Date & Language** | English-language peer-reviewed proceedings or preprints (2020–2026) | Non-English publications or publications outside the designated date window |

---

## 6. Screening Disposition & Breakdown

From the **38 unique research records**:
- **11 Excluded at Title / Abstract Screening:** Works focusing exclusively on surveys, attack prompts without internal analysis, or general fine-tuning.
- **11 Potentially Relevant Candidates Without Retained PDFs:** Distinct records identified from Scholar queries whose scope matched VLM safety mechanisms, but whose full-text PDFs were not in the course archive. These are transparently cataloged as *unresolved full-text appraisals* rather than declared ineligible.
- **16 Full-Text PDFs Assessed:**
  - **8 Included in Core Synthesis:** Empirical studies of VLM internal safety mechanisms (Li et al. 2026; Xie et al. 2026; Fu et al. 2026; Gupta & Chakraborty 2026; Li et al. 2025; Shi et al. 2026; Wang et al. 2025; D'Incà et al. 2026).
  - **2 Background / Context Studies:** Language-only mechanistic interpretability papers used to contextualize neuron localization and SAE features (Chen et al. 2025; Weng et al. 2026).
  - **6 Excluded After Full-Text Evaluation:** Specific exclusion reasons documented in `data/archive-screening-record.csv`.
