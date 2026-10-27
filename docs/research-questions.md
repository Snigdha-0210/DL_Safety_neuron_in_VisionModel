# Research Objectives & Research Questions

This systematic literature review was guided by four explicit research objectives and four corresponding research questions (RQs). Each question addresses a foundational gap in understanding how safety representations emerge, function, and fail inside Vision-Language Models (VLMs).

---

## 1. Guiding Research Objectives

1. **Identify Internal Units of Analysis:** Systematically catalog the internal structural units evaluated in the literature for VLM safety—including individual MLP neurons, attention heads, residual streams, circuits, and low-dimensional linear subspaces.
2. **Evaluate Causal Evidence Methodologies:** Compare the evidentiary strength of correlational probing techniques against direct counterfactual interventions, such as iterative neuron ablation, activation patching, activation steering, and subspace projection.
3. **Assess Cross-Modal Alignment vs. Divergence:** Investigate the empirical degree to which text-induced safety pathways and vision-induced safety pathways overlap, share neuronal substrates, or diverge into modality-specific representations.
4. **Identify Methodological & Reporting Bottlenecks:** Uncover the reproducibility, benchmarking, and evaluation limitations that hinder cross-study comparison and practical deployment of mechanistic safety interventions.

---

## 2. Research Questions Breakdown & Synthesis Overview

```
                                      ┌────────────────────────────────────────────────────────┐
                                      │           VLM MECHANISTIC SAFETY SYNTHESIS             │
                                      └──────────────────────────┬─────────────────────────────┘
                                                                 │
                 ┌───────────────────────┬───────────────────────┴───────────────────────┬───────────────────────┐
                 ▼                       ▼                                               ▼                       ▼
           ┌───────────┐           ┌───────────┐                                   ┌───────────┐           ┌───────────┐
           │    RQ1    │           │    RQ2    │                                   │    RQ3    │           │    RQ4    │
           │Distribution│          │Causality &│                                   │Modality   │           │Reporting &│
           │of Features│           │Intervention│                                  │Disparity  │           │Eval Gaps  │
           └─────┬─────┘           └─────┬─────┘                                   └─────┬─────┘           └─────┬─────┘
                 │                       │                                               │                       │
         Neurons, Heads,         Correlation vs.                                 Localized Text vs.       Benchmark drift,
         Subspaces, Layers       Counterfactual Control                          Diffuse Vision Space     Over-refusal neglect
```

---

### RQ1: Distribution of Safety Representations Across Components & Modalities
> **RQ1:** *How are safety-related representations distributed across VLM components and input modalities?*

#### Scope & Motivation:
Does safety alignment in vision-language models reside in a compact, modular set of specialized "safety neurons," or is it an emergent, highly distributed property spread across thousands of multidimensional activation channels?

#### Key Synthesized Findings:
- **Neuron-Level Sparsity (Text):** Li et al. (2026) report that for text-driven refusal, safety behavior is highly localized: approximately 88 MLP neurons per model (representing less than 0.01% of total model parameters) govern the decision to refuse across 10 tested open-source VLMs.
- **Directional Sparsity (GEVD):** For text prompts, refusal dynamics concentrate heavily along ~5 dominant Generalized Eigenvalue Decomposition (GEVD) directions.
- **Layer-Wise Localization:** Intermediate-to-late transformer layers (specifically layers $k/3$ to $k$) exhibit the highest concentration of decodable safety features and refusal-steering sensitivity (Li et al., 2025; Fu et al., 2026).
- **Multimodal Diffusion:** In contrast to text, visual safety signals are diffuse and cannot be isolated to a single universal neuron or compact cluster.

---

### RQ2: Causal Role of Localized Safety Concepts via Interventions
> **RQ2:** *What can probing and activation-level interventions establish about the causal role of localized safety concepts?*

#### Scope & Motivation:
Does detecting a safety-predictive feature via linear probing prove that the model uses that feature to generate a refusal? What additional causal certainty is provided by direct activation-level interventions?

#### Key Synthesized Findings:
- **Probing Limits (Correlation $\neq$ Causation):** Linear probing confirms that safety-predictive representations are decodable from hidden states (e.g., Xie et al., 2026; Gupta & Chakraborty, 2026). However, decodability does not guarantee that the downstream unembedding layer relies on those features to produce an output token.
- **Ablation (Causal Necessity):** Iterative zeroing of candidate neurons (Li et al., 2026) confirms causal necessity—ablating the ~88 identified text-safety neurons causes a steep collapse in refusal capabilities.
- **Dynamic Steering (Causal Sufficiency & Control):** Inference-time activation steering (ASTRA; Wang et al., 2025) and layer-level activation revision (IAR; Li et al., 2025) demonstrate that injecting precomputed safety vectors into residual streams during the forward pass counterfactually forces safe refusal outputs, yielding up to 52.98% ASR reductions on MM-SafetyBench.
- **Dual-Use of Circuit Knowledge:** Xie et al. (2026) demonstrate that probe-identified safety circuits can be weaponized: the Safety Circuit Intervention Attack (SCIA) perturbs shared circuit pathways to achieve a 59.7% average attack success rate across open-source VLMs, proving the causal fragility of identified circuits.

---

### RQ3: Cross-Modal Pathway Overlap vs. Divergence
> **RQ3:** *How do text and visual safety pathways overlap, and where do they appear to differ?*

#### Scope & Motivation:
Why does a model that refuses a plain text query fail when the exact same query is presented inside an image? Do text and visual inputs engage the same internal safety circuits?

#### Key Synthesized Findings:
- **Severe Cross-Modal Disparity:** Text and visual safety representations exhibit stark structural divergence. While text refusal depends on ~5 dominant directions, visual safety effects expand continuously across up to 50 directions under tested interventions (Li et al., 2026).
- **Projector Bypass:** Unaligned visual features bypass the language model's early safety detection heads through the cross-modal projection connector (Fu et al., 2026).
- **Vision Overriding Safety:** Gupta & Chakraborty (2026) discover that during visual jailbreaks, visual grounding representations frequently override internal safety abstention signals in the late decoding layers, causing the model to generate detailed harmful responses despite internal perception of the hazard.
- **Dual-Modal Subspace Repair:** Fu et al. (2026) demonstrate that repairing unsafe behavior requires dual-modal subspace projection (CARE), confirming that unimodal interventions are insufficient to secure multimodal reasoning.

---

### RQ4: Evaluation and Reporting Gaps Limiting Practical Deployment
> **RQ4:** *Which evaluation and reporting gaps prevent reliable comparison and practical deployment?*

#### Scope & Motivation:
Why is it currently impossible to conduct a definitive meta-analysis of VLM safety interventions, and what standardized benchmarks are required for rigorous real-world deployment?

#### Key Synthesized Findings:
- **Metric Incommensurability:** Reviewed studies report non-standardized metrics across disparate benchmarks (e.g., raw ASR vs. percentage ASR reduction vs. custom abstention accuracy), preventing direct numerical pooling.
- **Neglect of Over-Refusal & Grounding:** Many proposed safety interventions suppress harmful compliance by simply driving the model into an indiscriminate refusal mode, severely degrading visual grounding and benign question answering.
- **Lack of Adaptive Threat Modeling:** Most defenses are evaluated only against static prompt libraries; few test resilience against white-box adversaries who have full knowledge of the intervention vectors.
- **Missing Low-Resource Multilingual Evidence:** While Shi et al. (2026) examine multilingual safety neuron enhancement, evaluation is skewed toward major languages, leaving low-resource cross-lingual vulnerability unexplored.
