# Introduction & Research Background

**Research Title:** Mechanistic Interpretability of Safety Neurons in Vision-Language Models  
**Subtitle:** A Structured Literature Review of Probing, Activation Patching, and Localized Safety Representations  
**Author:** Snigdha Gorai (Register Number: 24BCE7185)  
**Institution:** VIT-AP University | Course: CSE4006 – Deep Learning  
**Assessment:** Digital Assessment 2 & 3 (Academic Year 2026–2027)

---

## 1. Context: The Multimodal Safety Paradox

Vision-Language Models (VLMs) and Multimodal Large Language Models (MLLMs)—such as LLaVA, InternVL, Qwen-VL, and commercial equivalents—integrate high-capacity vision encoders (typically Vision Transformers like CLIP ViT or SigLIP) with autoregressive language model backbones via projection layers or cross-modal attention mechanisms. This architectural synthesis allows VLMs to solve complex reasoning tasks: interpreting dense visual scenes, extracting optical character recognition (OCR) content, analyzing diagrams, and answering grounded conversational queries.

However, multimodal integration introduces an asymmetric safety vulnerability: **the multimodal safety paradox**. While state-of-the-art language models have undergone extensive safety alignment (via Reinforcement Learning from Human Feedback [RLHF], Direct Preference Optimization [DPO], and supervised safety fine-tuning) that makes them resistant to direct textual jailbreaks, that alignment frequently degrades or collapses entirely when hazardous concepts are introduced through visual channels.

Empirical studies demonstrate that a harmful request (such as synthesizing toxic compounds or executing physical exploitation) that is reliably refused when submitted as plain text is often answered compliantly when:
1. Rendered as typographic text within an image (*typographic jailbreaks*),
2. Coupled with suggestive visual scenes that prime benign semantic contexts,
3. Perturbed with adversarial visual noise designed to disrupt the language model's safety triggers.

---

## 2. Why Black-Box Output Evaluation Is Insufficient

Historically, model safety has been appraised through behavioral black-box testing: presenting a suite of red-teaming prompts and calculating the **Attack Success Rate (ASR)** or refusal rate based on final generated tokens.

While output-only evaluation measures whether a failure occurred, it provides zero insight into **how** or **where** the failure unfolded:
- Did the vision encoder fail to identify the hazardous concept in the image?
- Did the cross-modal projection layer fail to translate the visual concept into the language model's representation space?
- Did the language backbone perceive the hazard, activate its internal refusal representations, and then have those representations overridden by visual grounding attention heads?
- Or is multimodal safety governed by an entirely different internal circuit than text-only safety?

Without answers to these questions, developers are forced to rely on reactive, black-box heuristics—such as system-prompt wrappers or output filter classifiers—which are easily bypassed by adaptive adversarial perturbations.

---

## 3. The Promise of Mechanistic Interpretability

**Mechanistic interpretability** seeks to reverse-engineer deep neural networks from the inside out. Rather than treating neural architectures as opaque black boxes, it inspects internal activations, locates specific features or circuits responsible for distinct concepts, and performs controlled counterfactual interventions to evaluate causal dependency.

In the context of VLM safety, mechanistic interpretability investigates:
- **Neuron Localization:** Do individual neurons or small clusters of neurons within Multilayer Perceptron (MLP) blocks act as dedicated "safety switches" that trigger refusal?
- **Circuit Analysis:** Which attention heads and residual stream channels mediate safety-critical information across layers?
- **Cross-Modal Subspaces:** Do visual inputs and text inputs activate a shared, modality-agnostic safety concept, or do they travel through disparate internal representation directions?
- **Intervention Mechanics:** Can internal activations be steered, patched, ablated, or projected at inference time to prevent harmful responses without retraining billions of weights?

---

## 4. Scope and Contributions of this Review

This systematic literature review provides a structured, evidence-audited synthesis of empirical research on internal safety representations in vision-language models. 

### Core Contributions:
1. **Audited Evidence Base:** Reconciles 46 identified record appearances from Google Scholar and an assembled research-paper archive into 38 unique records, examining 16 full texts and synthesizing 8 core empirical VLM mechanistic studies.
2. **Causal Evidence Appraisal:** Establishes a rigorous distinction between observational/correlational findings (e.g., linear probing) and counterfactual causal findings (ablation, activation revision, subspace projection).
3. **Modality Disparity Mapping:** Analyzes why localized safety representations in text do not trivially translate to visual safety, synthesizing findings from Li et al. (2026), Fu et al. (2026), and Gupta & Chakraborty (2026).
4. **Safety–Utility Balance:** Documents the critical tension between mitigating harmful compliance and preventing catastrophic over-refusal / loss of legitimate visual grounding.
5. **Actionable Research Roadmap:** Outlines five evidence-backed research gaps to guide future empirical investigations into trustworthy multimodal foundation models.

