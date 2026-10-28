# Research Paper Comparison & Extraction Matrix

This document provides the exhaustive comparative synthesis of the **eight core empirical studies** included in the literature review, alongside profiles of the **two language-only contextual works** and the **six excluded full-text papers**.

All reported figures, metrics, and architecture descriptions are directly verifiable from the reviewed publications.

---

## 1. Master Comparative Extraction Matrix (8 Core VLM Studies)

| Study & Year | Research Objective | Method & Evaluated Models | Benchmark & Datasets | Reported Findings & Metrics | Critical Limitations & Gaps |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Li et al. (2026)**<br>*EMNLP 2026* | Compare text and visual safety pathways across 10 VLMs to determine if safety neurons are shared. | Neuron-level localization, iterative ablation, GEVD direction analysis across 10 open-source VLMs. | ViSafe-Detect and ViSafe-Eval (modality-isolated benchmarks). | Reports ~88 text-safety neurons per model (<0.01% of neurons). Text refusal effects concentrate in ~5 GEVD directions, while visual safety effects grow through 50 directions under tested interventions. | Specific to tested models, prompts, and refusal definitions; visual safety is not governed by a single universal safety neuron. |
| **Xie et al. (2026)**<br>*ICML 2026* | Investigate safety-related circuits and transferability of adversarial jailbreaks across black-box models. | Linear probing and Safety Circuit Intervention Attack (SCIA); tested on 6 open-source and 3 commercial VLMs. | FigStep, MM-SafetyBench, and Hades jailbreak benchmarks. | Reports 59.7% average Attack Success Rate (ASR) across open-source models; demonstrates that perturbing safety circuits transfers across models. *(Attack result, not defense)*. | Attack-oriented vulnerability study; does not provide a defensive mechanism or measure benign task utility preservation. |
| **Fu et al. (2026)**<br>*CVPR 2026* | Identify unsafe internal channels and eliminate unsafe responses while preserving multimodal reasoning. | Causal mediation analysis and dual-modal safety-subspace projection (CARE). | Multiple multimodal safety benchmarks; unseen and adaptive attack sets. | Reports improved safety robustness and transfer to unseen/adaptive attacks while preserving general multimodal task performance; no pooled score inferred. | Projection quality depends heavily on contrastive subspace construction; requires standardized matched utility protocols. |
| **Gupta & Chakraborty (2026)**<br>*arXiv:2608.18628* | Disentangle loss of visual grounding from refusal generation during safety alignment. | Hidden-state analysis, decoding dynamics, and targeted activation intervention. | Multiple VLM architectures; standard multimodal VQA and safety benchmarks. | Shows visual evidence remains influential in hidden states during safety abstention; targeted activation intervention restores grounded answering. | Restored answering is not automatically appropriate in all safety contexts; harmless abstention vs harmful compliance must be decoupled. |
| **Li et al. (2025)**<br>*AAAI 2025* | Mitigate multimodal jailbreaks without updating model parameters or expensive retraining. | Layer- and attention-head-level activation revision using revision vectors (IAR). | SafeBench, Safe-Unsafe, Unsafe, and MM-SafetyBench. | Reported benchmark-specific ASR reductions: 48.94% on SafeBench, 34.34% on Safe-Unsafe, 43.92% on Unsafe, and 52.98% on MM-SafetyBench; minimal impact on helpfulness. | Effect size depends on benchmark calibration and revision-vector construction; requires testing against adaptive adversaries. |
| **Shi et al. (2026)**<br>*arXiv:2604.08881* | Address coupled multilingual and multimodal safety vulnerabilities in foundation models. | Neuron-level identification and targeted parameter tuning / enhancement (Precise Shield). | Multilingual and multimodal safety evaluation suites. | Demonstrates targeted enhancement of safety-critical neurons improves safety across languages while preserving general reasoning capabilities. | Low-resource language coverage remains limited; requires independent multilingual red-teaming validation. |
| **Wang et al. (2025)**<br>*CVPR 2025* | Defend vision-language models against image-based jailbreaks during inference. | ASTRA: Adaptive activation steering using transferable harmful-response representation directions. | Diverse multimodal jailbreak datasets across multiple VLM architectures and baselines. | Demonstrates empirical resistance across multiple attack types with limited degradation on benign user inputs. | Steering directions may be prompt- and model-dependent; needs testing against adaptive white-box attackers; separates defense from causal proof. |
| **D’Incà et al. (2026)**<br>*WACV 2026* | Improve model safety while preserving pre-trained knowledge and safe-input capabilities. | SafeGround framework; activation-informed selection and negation of unsafe weights (UWM). | SafeGround benchmark and standard multimodal safety/utility evaluation suites. | Reports favorable safety-to-knowledge-preservation trade-off compared to fine-tuning and baseline parameter pruning. | Parameter manipulation is adjacent to, but distinct from, direct dynamic neuron-level causal intervention. |

---

## 2. Qualitative Study Appraisal Matrix

| Study | Internal Unit Analyzed | Intervention Type | Safety–Utility Evaluated? | Generalization Tested? | Methodological Caution |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Li et al. (2026)** | Individual MLP neurons & GEVD directions | Targeted iterative ablation | Yes (general multimodal capability reported) | Evaluated across 10 diverse open-source VLMs | Intervention effects depend on specific prompt definitions and model checkpoint. |
| **Xie et al. (2026)** | Safety circuits, attention heads, neurons | Neuronal intervention attack (SCIA) | No (primary objective was adversarial transfer) | Tested across 6 open-source and 3 commercial VLMs | Attack-focused study; identifies vulnerability rather than establishing a defense. |
| **Fu et al. (2026)** | Unsafe channels & dual-modal subspaces | Dual-modal subspace projection (CARE) | Yes (general multimodal task utility monitored) | Tested against unseen and adaptive attack variants | Subspace construction requires contrastive pairs; metric definitions vary across baselines. |
| **Gupta & Chakraborty (2026)** | Hidden states & late decoding layers | Targeted activation-level intervention | Yes (visual grounding preservation is central) | Tested across multiple model families and benchmarks | Restoring visual grounding must be carefully balanced against accidental harmful compliance. |
| **Li et al. (2025)** | Layer- & head-level activations | Inference-time activation revision (IAR) | Yes (general helpfulness evaluated) | Evaluated across four distinct safety benchmarks | Benchmark-specific reduction numbers cannot be directly compared without matched protocols. |
| **Shi et al. (2026)** | Multilingual safety neurons | Targeted parameter enhancement | Yes (joint safety and multilingual reasoning evaluated) | Cross-lingual and multimodal evaluation | Cross-lingual transfer to low-resource languages requires further scrutiny. |
| **Wang et al. (2025)** | Harmful representation directions | Adaptive activation steering (ASTRA) | Yes (benign-input task degradation monitored) | Tested against multiple attack formats and architectures | Steering vectors are empirical heuristics; adaptive attackers could potentially circumvent them. |
| **D’Incà et al. (2026)** | Activation-informed weight parameters | Weight selection and parameter negation (UWM) | Yes (safe-input knowledge retention is central) | Evaluated on SafeGround across multiple models | Parameter manipulation alters static weights; distinct from dynamic runtime activation steering. |

---

## 3. Profiles of Context-Only Studies (Language-Only)

These studies were evaluated in full text but excluded from the core VLM count because they examine unimodal language models. They provide essential theoretical context on interpretability techniques:

### 1. Chen et al. (2025) — *Towards Understanding Safety Alignment: A Mechanistic Perspective from Safety Neurons*
- **Publication:** Advances in Neural Information Processing Systems (NeurIPS 38).
- **Core Contribution:** Identifies safety neurons in language-only LLMs using activation contrasting and dynamic activation patching. Reports that ~5% of neurons can be isolated as safety-critical, and restoring/patching these neurons recovers >90% of safety performance on red-teaming benchmarks.
- **Contextual Value:** Establishes the foundational concept of localized "safety neurons" in pure NLP. Demonstrates the power of dynamic activation patching for counterfactual verification.
- **Why Excluded from Core Synthesis:** Focuses exclusively on text-only autoregressive LLMs. Findings cannot be assumed to hold in multimodal architectures where visual cross-attention alters activation dynamics.

### 2. Weng et al. (2026) — *Safe-SAIL: Towards a Fine-grained Safety Landscape of Large Language Models via Sparse Autoencoder Interpretation Framework*
- **Publication:** Findings of the Association for Computational Linguistics (ACL 2026): 18916–18935.
- **Core Contribution:** Utilizes Sparse Autoencoders (SAEs) to decompose dense neural activations into monosemantic, interpretable safety features.
- **Contextual Value:** Provides state-of-the-art methodology for overcoming the polysemanticity of individual neurons by projecting activations into overcomplete feature dictionaries.
- **Why Excluded from Core Synthesis:** Implemented on language-only LLMs without visual inputs.

---

## 4. Documentation of Excluded Full-Text Papers

Six papers in the 16-PDF archive were evaluated in full text and formally excluded from the core VLM synthesis according to the pre-specified PRISMA criteria:

```
┌────┬──────────────────────────────────────────┬─────────────────────────────────┬────────────────────────────────────────────┐
│ No │ Paper Title                              │ Lead Author & Year              │ Specific Exclusion Reason                  │
├────┼──────────────────────────────────────────┼─────────────────────────────────┼────────────────────────────────────────────┤
│ 1  │ Do VLMs Have Bad Eyes?                   │ Vaithinathan Aravindan et al.   │ Excluded: Mechanistic study of             │
│    │                                          │ (2025)                          │ compositional visual reasoning failures,   │
│    │                                          │                                 │ not model safety alignment or refusal.     │
├────┼──────────────────────────────────────────┼─────────────────────────────────┼────────────────────────────────────────────┤
│ 2  │ Do We Really Need Curated Malicious Data │ Wang et al. (2025)              │ Excluded: Multimodal safety alignment      │
│    │ for Safety Alignment in MLLMs?           │                                 │ and dataset fine-tuning focus; lacks       │
│    │                                          │                                 │ internal mechanistic analysis.             │
├────┼──────────────────────────────────────────┼─────────────────────────────────┼────────────────────────────────────────────┤
│ 3  │ Hyperbolic Safety-Aware VLMs             │ Poppi et al. (2025)             │ Excluded: Safety-aware representation and  │
│    │                                          │                                 │ retrieval geometry; does not investigate   │
│    │                                          │                                 │ internal safety neurons or refusal circuits│
├────┼──────────────────────────────────────────┼─────────────────────────────────┼────────────────────────────────────────────┤
│ 4  │ ScVLM: Enhancing Vision-Language Model   │ Shi et al. (2025)               │ Excluded: Focuses on safety-critical scene │
│    │ for Safety-Critical Event Understanding  │                                 │ understanding (e.g. autonomous driving),   │
│    │                                          │                                 │ not AI alignment or harmful output control.│
├────┼──────────────────────────────────────────┼─────────────────────────────────┼────────────────────────────────────────────┤
│ 5  │ TAB: Transformer Attention Bottlenecks   │ Rahmanzadehgervi et al. (2025)  │ Excluded: General visual debugging and user│
│    │                                          │                                 │ intervention; not safety-circuit analysis. │
├────┼──────────────────────────────────────────┼─────────────────────────────────┼────────────────────────────────────────────┤
│ 6  │ What Can Activation Patching Tell Us     │ Rathi & Yu (2024)               │ Excluded: Examines activation patching on  │
│    │ About Adversarial Examples?              │                                 │ vision-only classifiers (ResNet/ViT);      │
│    │                                          │                                 │ lacks language model backbone.             │
└────┴──────────────────────────────────────────┴─────────────────────────────────┴────────────────────────────────────────────┘
```

