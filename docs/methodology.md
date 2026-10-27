# Review Methodology & Evidence Audit Protocol

This document provides the complete methodological framework and PRISMA 2020-compliant reporting specification for the systematic review:

**"Mechanistic Interpretability of Safety Neurons in Vision-Language Models"**  
*Researcher:* Snigdha Gorai (Register Number: 24BCE7185)  
*Institution:* VIT-AP University | Course: CSE4006 – Deep Learning  
*Audit Reference Date:* 28 October 2026 (Search executed 18 October 2026)

---

## 1. Methodological Design & PRISMA 2020 Compliance

This systematic review was conducted in accordance with the **PRISMA 2020 (Preferred Reporting Items for Systematic Reviews and Meta-Analyses)** statement (Page et al., 2021). 

### Evidence Boundary Declaration:
The review employs a **bounded, auditable captured-results protocol**. It documents the systematic identification, deduplication, title/abstract screening, and full-text eligibility appraisal of **46 recorded candidate appearances**, consisting of:
- 30 visible result records captured from Google Scholar across three query sessions (the first 10 visible entries per query),
- 16 full-text research-paper PDFs assembled in the course archive.

```
       ┌────────────────────────────────────────────────────────────────────────┐
       │                      PRISMA 2020 FLOW SUMMARY                          │
       ├─────────────────────────────────┬──────────────────────────────────────┤
       │ Total Record Appearances        │ 46 (30 Scholar + 16 Archive PDFs)    │
       │ Duplicate Appearances Removed   │ 8 (2 intra-Scholar + 6 overlaps)     │
       │ Unique Records Screened         │ 38                                   │
       │ Excluded at Title/Abstract      │ 11                                   │
       │ Unresolved Candidate Records    │ 11 (missing from retained PDF corpus)│
       │ Full-Text PDFs Assessed         │ 16                                   │
       │ Context-Only Studies Retained   │ 2 (language-only mechanistic papers) │
       │ Excluded After Full-Text Review │ 6 (out-of-scope tasks / classifiers) │
       │ Core VLM Synthesis Studies      │ 8                                    │
       └─────────────────────────────────┴──────────────────────────────────────┘
```

> **Important Disclosure on Completeness:**  
> This review does not claim to have screened all ~15,300, ~12,700, and ~156 results estimated by the Google Scholar search interface. The 11 candidate studies that appeared potentially relevant from title/abstract screening but lacked full-text PDFs in the course archive are transparently categorized as *unresolved full-text appraisals*. No assertion is made that these works are unavailable online.

---

## 2. Search Strategy & Query Execution

Searches were executed on Google Scholar on **18 October 2026**. Search configuration: Articles, Sort by relevance, Date range: "Any time".

```
┌──────────┬───────────────────────────────────────────────────────────────────────────────────┬─────────────┬───────────┐
│ Query ID │ Exact Query Syntax                                                                │ Hits Est.   │ Retained  │
├──────────┼───────────────────────────────────────────────────────────────────────────────────┼─────────────┼───────────┤
│ S1       │ ("vision-language model" OR "multimodal large language model") AND               │ ~15,300     │ 10 items  │
│          │ (safety OR refusal OR jailbreak) AND (interpretability OR neuron OR circuit)      │             │ (Ranks 1–10)│
├──────────┼───────────────────────────────────────────────────────────────────────────────────┼─────────────┼───────────┤
│ S2       │ ("vision-language model" OR VLM OR MLLM) AND                                      │ ~12,700     │ 10 items  │
│          │ ("activation patching" OR probing OR ablation) AND (safety OR refusal)            │             │ (Ranks 1–10)│
├──────────┼───────────────────────────────────────────────────────────────────────────────────┼─────────────┼───────────┤
│ S3       │ ("safety neurons" OR "safety circuit" OR "safety subspace") AND                   │ ~156        │ 10 items  │
│          │ ("vision-language model" OR multimodal) AND (causal OR intervention OR steering)  │             │ (Ranks 1–10)│
└──────────┴───────────────────────────────────────────────────────────────────────────────────┴─────────────┴───────────┘
```

Full details on query syntax and search URLs are maintained in [`data/search-strategy.md`](../data/search-strategy.md).

---

## 3. Eligibility & Screening Criteria

A two-stage screening process (Title/Abstract screening followed by Full-Text assessment) was executed against five explicit eligibility dimensions:

| Dimension | Inclusion Criteria (Core Synthesis) | Exclusion Criteria |
| :--- | :--- | :--- |
| **Topic Scope** | Investigation of internal safety representations, circuits, neurons, or attention heads in multimodal foundation models. | General VLM benchmarking, black-box red-teaming datasets, or safety fine-tuning without internal mechanistic analysis. |
| **Methodological Rigor** | Empirical probing, ablation, activation patching, activation steering, causal mediation, or subspace projection. | Output-only behavioral evaluation, prompt engineering alone, or purely conceptual frameworks without empirical validation. |
| **Model Modality** | Vision-Language Models (VLMs) or Multimodal Large Language Models (MLLMs). | Unimodal language-only LLMs (categorized as context only) or unimodal vision classifiers (e.g. ImageNet classifiers). |
| **Evidence Quality** | Full-text empirical study available with inspectable technical methodology and quantitative results. | Incomplete workshop abstracts, extended summaries, or non-peer-reviewed blog posts. |
| **Language & Date** | English-language research published or preprinted between 2020 and 2026. | Non-English publications or studies published prior to 2020. |

---

## 4. Deduplication & Canonical Mapping

On 28 October 2026, an exhaustive deduplication audit reconciled the 46 record appearances into 38 unique research identities:
1. **Intra-Search Duplicates Removed ($n = 2$):**
   - Occurrence `S2-10` duplicates `S2-07` (*HiddenDetect: Detecting Jailbreak Attacks against Large Vision-Language Models via Monitoring Hidden States*, Jiang et al.).
   - Occurrence `S3-01` duplicates `S2-02` (*Diagnosing and Repairing Unsafe Channels in Vision-Language Models via Causal Discovery and Dual-Modal Safety Subspace Projection*, Fu et al.).
2. **Search-Archive Overlaps Removed ($n = 6$):**
   - Six studies appeared both in the Google Scholar search results and in the 16-PDF archive: Fu et al. (CARE), Wang et al. (ASTRA), Li et al. (IAR), Li et al. (Safety Neurons Across Modalities), Xie et al. (Dissecting the Safety Circuit), and Shi et al. (Precise Shield / Targeted Interpretable Safety Neuron Enhancement).
3. **Version & Bibliographic Reconciliation:**
   - Shi et al. (2026) appeared under working title *"Precise Shield: Explaining and Aligning VLLM Safety via Neuron-Level Guidance"* on arXiv and was reconciled with its formal version *"Targeted Interpretable Safety Neuron Enhancement for Multilingual Vision-Language Large Models"* (arXiv:2604.08881).
   - Li et al. (2025, *Internal Activation Revision*) author list was audited against the official AAAI-25 proceedings (Vol. 39, No. 26), confirming the seven-author citation including Derui Zhu.
   - Xie et al. (2026, *Dissecting the Safety Circuit*) was verified against the official ICML 2026 proceedings (PMLR Vol. 306).

---

## 5. Qualitative Study Appraisal Framework

Because the reviewed studies employ heterogeneous neural architectures, intervention targets, and benchmark datasets, **quantitative meta-analysis or statistical pooling was scientifically inappropriate**. Instead, each included study was appraised across four methodological dimensions:

```
┌─────────────────────────┬─────────────────────────────────────────────────────────────────────────────┐
│ Appraisal Dimension     │ Evaluation Criteria                                                         │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ 1. Internal Unit Stated │ Does the paper clearly define the target unit of analysis (individual       │
│                         │ neurons, attention heads, residual streams, or low-rank subspaces)?         │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ 2. Causal Intervention  │ Does the study apply direct causal manipulation (ablation, patching,        │
│                         │ steering, projection) rather than relying exclusively on probing?           │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ 3. Safety–Utility Check │ Does the study evaluate both safety improvement (e.g. ASR drop) AND general │
│                         │ multimodal utility preservation (VQA accuracy, visual grounding)?           │
├─────────────────────────┼─────────────────────────────────────────────────────────────────────────────┤
│ 4. Generalization Scope │ Is the method evaluated across multiple distinct VLM families and unseen    │
│                         │ adversarial attack distributions?                                           │
└─────────────────────────┴─────────────────────────────────────────────────────────────────────────────┘
```

The completed qualitative appraisal matrix for all included studies is documented in [`docs/paper-comparison.md`](paper-comparison.md).
