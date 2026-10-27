# MECHANISTIC INTERPRETABILITY OF SAFETY NEURONS IN VISION-LANGUAGE MODELS
## A Structured Literature Review of Probing, Activation Patching, and Localized Safety Representations

**Submitted by:** Snigdha Gorai  
**Register Number:** 24BCE7185 | **Class-list No.:** 41 | **Class ID:** AP2026272000664 | **Slot:** A2+TA2  
**Course:** CSE4006 – Deep Learning | **Digital Assessment:** DA-2 & DA-3  
**Institution:** VIT-AP University | **Academic Year:** 2026–2027  
**Report Date:** 28 October 2026  
**Review Scope:** Bounded Captured-Results Audit (30 Google Scholar Entries, 16 Retained PDFs, 8 Core Studies)

---

## Abstract

Vision-language models (VLMs) can interpret both images and text, but they do not always make equally safe decisions across the two modalities. A harmful request may be refused when written plainly and handled differently when embedded in a picture. This review asks what happens inside the model when it makes these decisions. It compares research on safety neurons, internal circuits, probing, ablation, and activation-level interventions, rather than judging safety only from final answers.

Across the papers, there is no clear evidence for one universal "safety neuron" that controls every safe response. One study links text refusal to a relatively small group of neurons, while visual safety appears to involve a broader set of representational directions. Other work examines how safety-related circuits can be exploited in attacks and how internal interventions might reduce unsafe outputs. A useful distinction throughout this review is that finding information in an activation is not the same as proving that the information causes a model's response.

The review uses a bounded, traceable identification record: 30 visible Google Scholar results captured across three queries and 16 retained research PDFs. Deduplicating their 46 appearances gives 38 distinct records. Eleven were excluded at title/abstract screening; eleven additional potentially relevant works were not present in the retained PDF corpus; and sixteen full texts were assessed. Eight VLM studies entered the core comparison. Because models and benchmarks differ, the results are synthesized qualitatively rather than pooled.

**Keywords:** vision-language models; mechanistic interpretability; safety neurons; activation patching; probing; activation steering; PRISMA 2020.

---

## 1. Introduction

Vision-language models combine an image encoder with language-processing components so that they can answer questions about pictures, read text in images, and respond to instructions that refer to visual details. These abilities make them useful, but they also introduce safety questions. For example, a model might refuse a harmful request when it is typed directly but respond differently when the request is embedded in an image. Recent work has started to examine whether safety behaviour follows the same internal path in both cases (Li et al., 2026; Fu et al., 2026).

A model's final answer shows the outcome, but it does not explain how the model reached it. Mechanistic interpretability addresses this problem by examining internal activations and testing what happens when selected components are changed. The papers in this review use several approaches, including probing, neuron ablation, activation revision, and safety-subspace projection (Li et al., 2025; Li et al., 2026; Fu et al., 2026). These methods answer different questions, so their findings need to be interpreted according to the kind of evidence each method provides.

### Problem Statement
The problem addressed here is that the internal basis of safety in VLMs is still not fully understood. Safety behaviour might depend on a small number of neurons, a larger circuit, or features distributed across multiple directions. It may also differ depending on whether a request arrives as text or through an image. A related concern is how strong a causal claim can be made from each method. The reviewed studies use different models, harmful-content categories, benchmarks, and metrics, so a fair comparison must preserve those differences rather than treating the experiments as directly equivalent.

### Scope and Contribution
This review focuses on internal representations associated with safe and unsafe responses in vision-language models. It considers safety neurons, probing, activation patching, activation steering, and other causal interventions. Eight VLM studies from the supplied archive form the main comparison; two language-only papers are used only to explain related interpretability methods. The review does not claim to cover every publication in this growing area. Its contribution is a structured comparison of the available studies, with attention to the difference between identifying a representation and demonstrating that it has a causal role in model behaviour.

---

## 2. Objectives and Research Questions

The review was guided by four practical objectives:
1. Identify the internal units used to analyse safety in VLMs, including neurons, layers, attention heads, circuits, and subspaces.
2. Compare probing with interventions such as ablation, activation patching, steering, and causal mediation.
3. Assess what the studies indicate about shared versus modality-specific safety mechanisms.
4. Identify reproducibility, evaluation, and generalization gaps that limit deployment confidence.

### Research Questions
- **RQ1.** How are safety-related representations distributed across VLM components and input modalities?
- **RQ2.** What can probing and activation-level interventions establish about the causal role of localized safety concepts?
- **RQ3.** How do text and visual safety pathways overlap, and where do they appear to differ?
- **RQ4.** Which evaluation and reporting gaps prevent reliable comparison and practical deployment?

---

## 3. Review Methodology

### Reporting Approach and Information Sources
Google Scholar was the documented discovery interface. Three query result pages were recorded on 18 October 2026, with their first ten visible entries retained for each query. On 28 October, those 30 entries were audited against the 16 PDFs previously collected. This is a bounded captured-results audit, not a claim to have exported or screened every result shown by Google Scholar.

Three Google Scholar query strings and the displayed interface counts recorded on 18 October 2026 are:
- **S1:** `("vision-language model" OR "multimodal large language model") AND (safety OR refusal OR jailbreak) AND (interpretability OR neuron OR circuit)` — *~15,300 results displayed.*
- **S2:** `("vision-language model" OR VLM OR MLLM) AND ("activation patching" OR probing OR ablation) AND (safety OR refusal)` — *~12,700 results displayed.*
- **S3:** `("safety neurons" OR "safety circuit" OR "safety subspace") AND ("vision-language model" OR multimodal) AND (causal OR intervention OR steering)` — *~156 results displayed.*

The displayed totals for S1–S3 are approximate search-interface estimates; they were not used as screening counts. Instead, the accompanying search evidence provides exactly 30 visible result appearances (10 per query). Two appearances represent repeated Scholar records, and six archive PDFs match search entries; these eight duplicate appearances were removed from the combined 46-item record.

That leaves 38 distinct records for a documented screening audit. Eleven were screened out from the available title/abstract evidence because they were surveys, attack-only evaluations or outside the narrow VLM safety-mechanism scope. Eleven more looked potentially relevant but had no PDF in the retained sixteen-paper archive, so their full-text eligibility assessment was not completed. Sixteen available PDFs were evaluated in full; eight met the core inclusion rules.

### Eligibility Criteria

| Criterion | Include in Core Synthesis | Exclude from Core Synthesis |
| :--- | :--- | :--- |
| **Topic** | Internal safety-related representations or interventions in VLMs/MLLMs | General safety benchmark or training work without internal analysis |
| **Method** | Empirical probing, ablation, patching, steering, causal analysis, or internal feature intervention | Output-only testing without internal representation analysis |
| **Modality** | Vision-language or multimodal language model | Language-only papers (contextual use only) or vision-only classifier studies |
| **Evidence** | Full-text PDF available and methods/outcomes described | Insufficient information or a primary task outside the review question |
| **Date/Language** | English-language work dated 2020–2026 | Outside date range or non-English full text |

---

## 4. Results: Screening Flow and Corpus Composition

### Audited Selection Stage Arithmetic

| Selection Stage | Count | Interpretation |
| :--- | :---: | :--- |
| **Records Identified** | **46** | Thirty saved Scholar entries and sixteen retained PDF entries |
| **Duplicate Appearances Removed** | **8** | Two within Scholar listing; six overlaps with PDF collection |
| **Unique Records Screened** | **38** | All distinct titles screened using captured evidence |
| **Screened Out by Title/Abstract** | **11** | Surveys, attack-only work, or wrong model/mechanistic scope |
| **Additional Candidates Without Retained PDFs** | **11** | Potentially relevant; full texts not part of archived evidence set |
| **Full-Text PDFs Assessed → Core Included** | **16 → 8** | Eight exclusions: six outside core scope; two language context studies |

---

## 5. Comparison of Included Studies

| Study / Year | Objective | Method / Model | Dataset / Metrics / Reported Finding | Limitation and Research Gap |
| :--- | :--- | :--- | :--- | :--- |
| **Li et al. (2026)**<br>*"Do VLMs Share Safety Neurons Across Modalities?"* | Compare text and visual safety pathways across 10 VLMs. | Neuron-level localization, iterative ablation, modality-isolated ViSafe-Detect and ViSafe-Eval benchmarks. | Evaluated across 10 VLMs. Reports ~88 text-safety neurons per model (<0.01% of neurons). Text refusal effects concentrate in ~5 GEVD directions, while visual effects grow through 50 directions under tested intervention. | Result specific to tested models, prompts, and benchmarks. Visual safety is not shown to be governed by one universal neuron. |
| **Xie et al. (2026)**<br>*"Dissecting the Safety Circuit"* | Study safety-related circuits and transferability of adversarial attacks. | Linear probing and Safety Circuit Intervention Attack (SCIA), which intervenes on safety and transferable circuits. | Evaluated on 6 open-source and 3 commercial VLMs using FigStep, MM-SafetyBench, and Hades. Reports 59.7% average Attack Success Rate (ASR) across open-source models. (Attack-transfer metric, not defense). | Attack-oriented evidence identifies a vulnerability, not a defense. Highlights need to test circuit overlap across architectures. |
| **Fu et al. (2026)**<br>*"Diagnosing and Repairing Unsafe Channels"* | Identify unsafe internal channels and reduce unsafe behaviour while retaining multimodal capability. | Causal mediation and dual-modal safety-subspace projection (CARE). | Evaluates CARE on multiple safety benchmarks; reports improved safety robustness, transfer to unseen/adaptive attacks, and preservation of general multimodal capability. | Projection quality depends on how safety subspaces and contrast pairs are constructed; matched utility metrics are needed. |
| **Gupta & Chakraborty (2026)**<br>*"When Safety Overrides Vision"* | Distinguish loss of visual grounding from refusal-oriented generation. | Hidden-state analysis and targeted activation-level intervention across VLMs and multimodal benchmarks. | Tests multiple VLM architectures and benchmarks. Reports visual evidence remains influential during safety abstention and targeted intervention can restore grounded answering. | A restored answer is not automatically appropriate in every safety context. Harmless abstention and harmful compliance must both be measured. |
| **Li et al. (2025)**<br>*"Internal Activation Revision"* | Reduce multimodal jailbreak vulnerability without updating model parameters. | Layer- and attention-head-level activation revision using revision vectors. | Reports average ASR reductions: 48.94% on SafeBench, 34.34% on Safe-Unsafe, 43.92% on Unsafe, and 52.98% on MM-SafetyBench. | Performance depends on benchmark and revision-vector construction; safety gains must be evaluated alongside helpfulness and generalization. |
| **Shi et al. (2026)**<br>*"Targeted Interpretable Safety Neuron Enhancement..."* | Address coupled multilingual and multimodal safety risks. | Neuron-level safety-neuron identification and targeted safety tuning. | Evaluates a neuron-targeted approach to coupled multilingual and multimodal safety. Reports improved safety while preserving general capabilities. | Cross-lingual transfer and coverage of low-resource languages need careful independent evaluation. |
| **Wang et al. (2025)**<br>*"Steering Away from Harm"* | Defend VLMs against image-based jailbreaks with inference-time intervention. | ASTRA: Adaptive activation steering using transferable harmful-response directions. | Evaluates ASTRA against multimodal jailbreak attacks across multiple models and baselines. Reports resistance across several attack types with limited benign-input degradation. | Steering directions can be prompt/model dependent; report should separate attack robustness from causal explanation of safety neurons. |
| **D’Incà et al. (2026)**<br>*"Safe Vision-Language Models via Unsafe Weights Manipulation"* | Improve safety while preserving knowledge and safe-input behaviour. | SafeGround evaluation and activation-informed selection/negation of parameters associated with unsafe content. | Uses SafeGround evaluation to examine safety alongside preservation of knowledge on safe inputs. Reports favourable safety–knowledge-preservation trade-off. | Weight manipulation is adjacent to, but not identical with, neuron-level causal localization; evaluation on benign inputs is essential. |

### Contextual Papers (Language-Only)
- **Chen et al. (2025):** Examines safety neurons in language-only LLMs using activation contrasting and dynamic activation patching. Reports ~5% of neurons act as safety neurons and patching restored >90% of safety performance on red-teaming benchmarks.
- **Weng et al. (2026) [Safe-SAIL]:** Analyzes sparse autoencoder (SAE) features for fine-grained safety analysis in language models.

---

## 6. Cross-Study Synthesis and Discussion

### Localization Is Not the Same as a Universal Safety Switch
A clear difference in the reviewed evidence is the contrast between text and visual safety. Li et al. (2026) report that, in the models they tested, text refusal could be linked to a relatively small set of neurons, whereas visual safety was spread across more representational directions. The study compares ten VLMs and separates text and visual evaluations, but the result still depends on the tested architectures, prompts, and definition of refusal. It would be premature to conclude that one fixed group of neurons controls safety in every model and situation.

For this reason, the phrase "safety neuron" should be used with care. What looks localized can depend on the task, the layer being examined, and the number of components changed during an intervention. A probe may show that safety-related information is present in an activation without proving that the model uses it to decide whether to refuse.

### Probing, Patching, Ablation, and Causal Intervention
Probing asks whether information about safety can be recovered from a model's internal activations. It is useful for locating candidate features, but a successful probe does not by itself show that the model relies on those features. Ablation and activation patching go further by changing internal components and observing whether the output changes. Even these interventions need controls: other pathways may carry similar information, the model may compensate for the change, or the intervention may damage general capability.

The study by Xie et al. (2026) also shows why it is important to distinguish understanding a circuit from using it as a defense. Their Safety Circuit Intervention Attack (SCIA) uses probe-identified circuits to help adversarial images transfer to black-box VLMs, reporting a 59.7% average attack success rate across evaluated open-source models. This is an attack result, not a measure of defense effectiveness.

### Safety Must Be Evaluated with Usefulness and Grounding
A model that refuses every difficult image question might appear safe on a narrow harmful-compliance metric, but it would also be less useful. Gupta and Chakraborty (2026) report that visual information can remain influential even when safety alignment leads the model to abstain. D’Incà et al. (2026) also emphasize preserving knowledge on safe inputs. A balanced evaluation should measure harmful compliance and appropriate refusal separately, alongside over-refusal, visual grounding, ordinary task performance, and robustness to new attacks.

---

## 7. Research Gaps and Future Directions

1. **Matched Cross-Modal Causal Experiments:** Build matched triplets in which the same harmful request is presented as plain text, as text embedded in an image, and as a visual scene. Apply the same probing, patching, and ablation procedures to each version.
2. **Standardized Reporting of Interventions:** Consistently report model checkpoint hashes, exact layers changed, intervention strength, vector construction methods, prompt templates, decoding settings, and computational cost.
3. **Safety–Utility Evaluation with Independent Judges:** Simultaneously measure harmful compliance and over-refusal, reporting VQA accuracy, visual grounding, helpfulness, and correctness.
4. **Generalization Across Models, Attacks, and Languages:** Test interventions on held-out model families, unseen adaptive attack styles, multilingual prompts, and low-resource languages.
5. **Mechanism-Level Robustness and Independent Replication:** Evaluate interventions against adaptive white-box attackers who possess knowledge of the intervention vectors.

---

## 8. Threats to Validity and Limitations

The major limitation is selection coverage. Although the revised audit gives real counts for the 30 captured Scholar entries and 16 saved PDFs, each query contributed only its first ten visible results. Complete database exports were not preserved, and the tens of thousands of approximate search hits were not screened. Eleven potentially relevant works found in the captured results lacked copies in the retained PDF corpus.

Differences in model families, visual encoders, prompt design, harm categories, attack strength, and score definitions also prevent direct statistical pooling or meta-analysis. Mechanistic claims additionally depend on the task and intervention: showing that a probe predicts refusal does not establish causality, while an intervention that changes outputs on one dataset does not establish a universal safety switch.

---

## 9. Conclusion

This review examined how mechanistic interpretability is being used to study safety-related representations in vision-language models. The eight core studies examine neurons, circuits, layers, attention heads, and feature subspaces, and several intervene on these components to investigate or reduce unsafe behaviour. The evidence supports internal activation analysis as a useful research approach, but it does not show that one small, universal set of safety neurons controls all multimodal safety behaviour.

The next step should not be limited to finding more candidate neurons. Researchers need to compare equivalent requests presented through text and images, intervene on the internal features they identify, and check whether the model can still answer harmless visual questions correctly.

---

## 10. References

1. Chen, J., Wang, X., Yao, Z., Bai, Y., Hou, L., & Li, J. (2025). Towards Understanding Safety Alignment: A Mechanistic Perspective from Safety Neurons. *Advances in Neural Information Processing Systems 38*.
2. D’Incà, M., Peruzzo, E., Xu, X., Shi, H., Sebe, N., & Mancini, M. (2026). Safe Vision-Language Models via Unsafe Weights Manipulation. *Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision*, 4682–4692.
3. Fu, J., Lou, Y., Si, Q., Zhang, S., & Su, S. (2026). Diagnosing and Repairing Unsafe Channels in Vision-Language Models via Causal Discovery and Dual-Modal Safety Subspace Projection. *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition*, 31693–31702.
4. Gupta, M., & Chakraborty, T. (2026). When Safety Overrides Vision: Exploring Dynamics between Vision Influence and Safety Alignment in Vision-Language Models. *arXiv:2608.18628*.
5. Li, J., Zhang, J., Vo, D. M., Nguyen, H. H., Kavumba, P., & Wataoka, K. (2026). Do VLMs Share Safety Neurons Across Modalities? *arXiv:2608.30750* (accepted to EMNLP 2026).
6. Li, Q., Geng, J., Zhu, D., Chen, Z., Song, K., Ma, L., & Karray, F. (2025). Internal Activation Revision: Safeguarding Vision Language Models Without Parameter Update. *Proceedings of the AAAI Conference on Artificial Intelligence*, 39(26), 27428–27436.
7. Page, M. J., McKenzie, J. E., Bossuyt, P. M., Boutron, I., Hoffmann, T. C., Mulrow, C. D., et al. (2021). The PRISMA 2020 statement: An updated guideline for reporting systematic reviews. *BMJ*, 372, n71.
8. Shi, E., Shen, F., Shi, C., Miao, S., Zhu, L., Shao, P., Tang, J., & Chua, T.-S. (2026). Targeted Interpretable Safety Neuron Enhancement for Multilingual Vision-Language Large Models. *arXiv:2604.08881*.
9. Wang, H., Wang, G., & Zhang, H. (2025). Steering Away from Harm: An Adaptive Approach to Defending Vision Language Model Against Jailbreaks. *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition*, 29947–29957.
10. Xie, C., Chen, K., Guo, S., Zhang, S., Liu, J., Zhang, T., & Xiang, T. (2026). Dissecting the Safety Circuit: Neuronal Intervention for Transferable Adversarial Attacks on VLMs. *Proceedings of the 43rd International Conference on Machine Learning*, PMLR 306, 139323–139338.