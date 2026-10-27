# Evidence-Supported Research Gaps & Future Directions

Based on the systematic analysis of the eight core Vision-Language Model (VLM) mechanistic safety studies, five foundational research gaps have been identified. Addressing these gaps is essential for advancing mechanistic interpretability from academic proof-of-concept to trustworthy real-world deployment.

---

## 1. Gap 1: Matched Cross-Modal Causal Experiments

```
  ISOLATED TEST PARADIGM (CURRENT)            MATCHED TRIPLET PARADIGM (PROPOSED)
  ┌─────────────────────────────────┐         ┌─────────────────────────────────┐
  │ Text Prompt: "How to make a     │         │ Triplet 1: Plain text prompt    │
  │ bomb?" (Refused by ~88 neurons) │         │ Triplet 2: OCR text in image    │
  │                                 │         │ Triplet 3: Semantic scene image │
  │ VS                              │───────► │                                 │
  │ Arbitrary Image Jailbreak       │         │ Apply identical ablation,       │
  │ (Unmatched semantics/format)    │         │ patching, and probing across all│
  │                                 │         │ 3 conditions with benign control│
  └─────────────────────────────────┘         └─────────────────────────────────┘
```

### Problem Statement:
Current literature reports a severe divergence between text safety (localized in ~88 neurons) and visual safety (diffuse across >50 directions; Li et al., 2026). However, existing studies rarely evaluate **semantically identical prompts** across different modalities. An image containing typographic text introduces optical character recognition (OCR) overhead, while an image depicting a physical hazard engages spatial scene comprehension.

### Actionable Research Agenda:
1. **Curate Matched Multimodal Triplets:** Construct standardized evaluation datasets where the exact same hazardous intent is represented in three controlled formats: (a) plain text instruction, (b) typographic text rendered in an image, and (c) visual scene without text.
2. **Apply Uniform Causal Interventions:** Subject all three formats to identical probing, activation patching, and ablation protocols on the same model checkpoints to isolate whether the observed modality divergence stems from semantic representation or visual token binding.
3. **Include Ambiguous Control Imagery:** Pair hazardous queries with visually ambiguous but benign control images to verify that interventions do not merely induce indiscriminate visual refusal.

---

## 2. Gap 2: Standardized Reporting of Interventions & Open Reproducibility

### Problem Statement:
Reproducibility across the reviewed papers is severely constrained by non-standardized experimental reporting. Studies frequently omit:
- Exact model checkpoint hashes and revision dates,
- Specific layer indices and head numbers where steering vectors are injected,
- Hyperparameters used to compute contrastive directions (e.g., sample size, temperature, PCA/GEVD cutoffs),
- Whether results remain stable across multiple random seeds,
- Computational overhead introduced by runtime activation interventions.

### Actionable Research Agenda:
1. **Establish a Standardized Intervention Specification:** Propose a unified reporting template detailing: target layer range ($L_{start}$ to $L_{end}$), injection magnitude ($\alpha$), projection dimensionality ($d_{subspace}$), and wall-clock latency impact.
2. **Mandate Open Code and Vector Registries:** Require future mechanistic safety papers to release precomputed steering vectors, probe weights, and exact token masks alongside paper publication.
3. **Audit Circuit Redundancy:** Require studies that identify individual "safety neurons" to test whether downstream transformer layers dynamically route around ablated units when exposed to alternative prompt framings.

---

## 3. Gap 3: Joint Safety–Utility Auditing with Independent Judges

### Problem Statement:
A pervasive methodological flaw across contemporary safety evaluations is evaluating safety in isolation from utility. Defensive mechanisms such as activation steering (ASTRA) or activation revision (IAR) can trivially reduce the Attack Success Rate (ASR) to near-zero by shifting the model's baseline response distribution toward generic refusals (*over-refusal*), which destroys legitimate visual question answering and visual grounding (Gupta & Chakraborty, 2026).

```
   POOR INTERVENTION (Over-Refusal)            PREMIUM INTERVENTION (Calibrated)
   ┌────────────────────────────────┐          ┌────────────────────────────────┐
   │ Harmful Prompt ──► Refusal     │          │ Harmful Prompt ──► Refusal     │
   │ Benign Visual Q ──► Refusal ❌ │          │ Benign Visual Q ──► Answer ✅  │
   │ (Zero utility, high abstention)│          │ (High safety, zero over-refusal│
   └────────────────────────────────┘          └────────────────────────────────┘
```

### Actionable Research Agenda:
1. **Dual-Metric Evaluation Mandate:** Future benchmarks must simultaneously report **Harmful Compliance Rate (HCR)** alongside **Benign False Refusal Rate (FRR)** on standardized multimodal QA tasks (e.g., VQA v2, GQA, TextVQA).
2. **Grounding Preservation Metrics:** Integrate explicit spatial grounding benchmarks (e.g., RefCOCO) to verify that safety interventions do not degrade the visual encoder's ability to localize objects.
3. **Blinded Human Quality Review:** Complement automated LLM-as-a-Judge evaluations with blinded human expert audits to detect subtle degradation in nuanced multimodal reasoning.

---

## 4. Gap 4: Cross-Model & Multilingual Generalization

### Problem Statement:
Most mechanistic findings are established on a narrow family of open-source architectures (primarily LLaVA variants built on Vicuna or LLaMA-2 backbones with standard CLIP ViT-L/14 encoders). It remains unproven whether these findings generalize to:
- Modern vision encoders trained with alternative objectives (e.g., SigLIP, DINOv2, EVA-CLIP),
- Advanced cross-modal connectors (e.g., Perceiver resamplers, Q-Formers, dynamic MLP projectors),
- Low-resource multilingual prompts.

### Actionable Research Agenda:
1. **Cross-Architecture Subspace Transfer:** Evaluate whether safety subspaces identified via CARE (Fu et al., 2026) in one model family can be projected onto entirely different architectures (e.g., InternVL, Qwen2-VL, Mistral-NeMo) without recalibration.
2. **Multilingual Stress-Testing:** Expand targeted safety neuron enhancement (Shi et al., 2026) to low-resource and non-Latin script languages to prevent regional safety disparities.
3. **Encoder vs. LLM Disentanglement:** Conduct layer-wise causal tracing to determine what proportion of safety vulnerability originates within the vision encoder versus the autoregressive language decoder.

---

## 5. Gap 5: Adaptive Attack Resistance & Mechanism Verification

### Problem Statement:
Contemporary defensive interventions (CARE, IAR, ASTRA, UWM) have primarily been tested against **static, non-adaptive red-teaming benchmarks** (such as FigStep or MM-SafetyBench). However, Xie et al. (2026) demonstrate that adversaries who understand the model's internal safety circuits can easily formulate the Safety Circuit Intervention Attack (SCIA) to bypass defenses, achieving a 59.7% ASR.

### Actionable Research Agenda:
1. **White-Box Adaptive Threat Modeling:** Subject inference-time steering and projection mechanisms to white-box adversaries who possess full knowledge of the steering vectors and projector weights.
2. **Dynamic Defense Ensembling:** Explore stochastic or input-adaptive steering vectors that dynamically adjust based on internal attention entropy, preventing adversaries from optimizing static bypass perturbations.
3. **Formal Verification of Safety Subspaces:** Develop mathematical bounds on the Lipschitz continuity of safety subspace projections to guarantee that bounded input perturbations cannot escape the safe representation manifold.
