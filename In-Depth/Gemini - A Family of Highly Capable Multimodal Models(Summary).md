---
title: "Gemini: A Family of Highly Capable Multimodal Models"
aliases: [Gemini Paper Summary, Google Gemini Report]
tags:
  - AI
  - Multimodal
  - LLM
  - GoogleDeepMind
  - GeminiModel
  - SOTA
  - ResponsibleAI
---
![[Gemini_Unlocked__The_Native_Multimodality_and_Reasoning_Breakth.mp4]]
![[Google_Gemini_logo.svg.png]]
# Gemini: A Family of Highly Capable Multimodal Models

This report introduces **Gemini**, a new family of highly capable multimodal models developed by [[Google DeepMind]]. Gemini models exhibit remarkable capabilities across image, audio, video, and text understanding.

>[!NOTE] Key Distinguishing Feature
>Gemini models are **[[Natively Multimodal AI|Natively Multimodal]]**, trained jointly across various modalities from the beginning, rather than stitching together separate [[Unimodal Components]].

---
## Key Takeaways / Overview

*   **Model Family:** Consists of three sizes:
    *   **Ultra:** For highly complex tasks, achieving [[State-of-the-Art (SOTA) Model]] performance.
    *   **Pro:** Optimized for performance, scalability, and cost-effectiveness.
    *   **Nano (Nano-1 & Nano-2):** Designed for on-device, memory-constrained applications, trained via distillation.
    ![[_- visual selection (1).png]]
---
*   **State-of-the-Art Performance:**
    *   Gemini Ultra advances SOTA in **30 out of 32** widely used academic benchmarks.
    *   Notably, it's the first model to achieve **human-expert performance on [[MMLU (Massive Multitask Language Understanding)|MMLU]]** (Massive Multitask Language Understanding) with a score of 90.04%.
    *   Improves [[State-of-the-Art (SOTA) Model|SOTA]] in **all 20 [[Multimodal AI]] benchmarks** examined.
	
	![[_- visual selection (2).png]]
--- 
*   **Multimodal Capabilities:** Natively handles and reasons over interleaved text, images, audio, and video. Can also generate text and images.
*   **Deployment & Access:**
    *   Through services like [[Gemini App]] (formerly Bard) and [[Gemini Advanced]].
    *   Developer access via [[ Google AI Studio]] and [[Cloud Vertex AI]].
*   **Post-Training Variants:**
    *   **Gemini Apps models:** Chat-focused, optimized for conversational AI.
    *   **Gemini API models:** Developer-focused, optimized for a broader range of product integrations.

## Model Architecture & Innovations

*   Built on **[[Transformer Decoders]]** (Vaswani et al., 2017b).
*   Supports a **[[32k context length|32k context length]]**.
*   Employs efficient attention mechanisms like *multi-query attention* (Shazeer, 2019a).
*   **Visual Encoding:** Inspired by Flamingo, CoCa, and PaLI, but critically, Gemini is multimodal from the ground up.
*   **Native Image Output:** Can generate images using *discrete image tokens* (Ramesh et al., 2021; Yu et al., 2022b).
*   **Video Understanding:** Encodes video as a sequence of frames within its large context window, allowing natural interleaving with text/audio. Supports variable input resolution.
*   **Audio Ingestion:** Directly processes audio signals at 16kHz using features from [[Universal Speech Model (USM)]] (Zhang et al., 2023), capturing nuances often lost in text-only mapping.

## Training: Infrastructure & Dataset

### Infrastructure
*   Trained on Google's **[[TPUv4 and TPUv5e Accelerators]]**.
*   Gemini Ultra training involved a large fleet of [[TPUv4 and TPUv5e Accelerators|TPUv4]] across multiple datacenters.
*   Utilized JAX, Pathways, GSPMD partitioner, and the MegaScale XLA compiler for stable, large-scale training.
*   Achieved **97% goodput** for the largest training job by using redundant in-memory copies for rapid recovery from hardware failures (an improvement from 85% for PaLM/PaLM-2).
*   Addressed challenges like "[[Silent Data Corruption (SDC)]]" at scale.

### Dataset
*   **[[Multimodal AI|Multi-modal]] and [[Multilingual]]** pre-training dataset.
*   Sources: Web documents, books, code, and includes image, audio, and video data.
*   Utilizes a **[[SentencePiece Tokenizer]]** trained on a large sample of the entire corpus for improved vocabulary and efficiency, especially for non-Latin scripts.
*   Training token counts followed Hoffmann et al. (2022) for large models, while smaller models were trained for significantly more tokens (similar to Touvron et al., 2023a).
*   Applied quality filters and safety filtering.
*   **Staged training:** Mixture composition altered during training, increasing domain-relevant data towards the end.

>[!INFO] Dataset Strategy
>Data quality is deemed a crucial factor. Evaluation data was carefully removed from the training corpus to maintain integrity.

## Comprehensive Evaluation & SOTA Performance

Gemini models were evaluated across a wide range of benchmarks.

### Text Capabilities

*   **Overall Reasoning & Knowledge:**
    *   **[[MMLU (Massive Multitask Language Understanding)|MMLU]]:** Gemini Ultra achieves **90.04%** using a [[Novel CoT Prompting]] approach that accounts for model uncertainty (*uncertainty-routed chain-of-thought*), surpassing the prior SOTA (86.4%) and human-expert performance (89.8%).[[]]
        >[!SUCCESS] MMLU Landmark
        >First model to exceed human-expert performance on [[MMLU (Massive Multitask Language Understanding)|MMLU]].
    *   **[[BIG-Bench-Hard (BBH)]]:** Ultra scores 83.6%.
*   **Mathematics:**
    *   **[[GSM8K and MATH Benchmarks|GSM8K]]:** Ultra achieves 94.4% (up from 92%).
    *   **[[GSM8K and MATH Benchmarks|MATH Benchmark]]:** Ultra achieves 53.2% (4-shot).
    *   Outperforms GPT-4 on harder American Mathematical Competitions questions (32% vs 30%).
*   **Coding:**
    *   **[[HumanEval, Natural2Code, and Codeforces Benchmarks|HumanEval]]:** Instruction-tuned Gemini Ultra scores 74.4%.
    *   **[[HumanEval, Natural2Code, and Codeforces Benchmarks|Natural2Code]] (new held-out benchmark):** Ultra scores 74.9%.
    *   Powers [[AlphaCode & AlphaCode2|AlphaCode2]], which ranks in the top 15% on [[HumanEval, Natural2Code, and Codeforces Benchmarks|Codeforces Benchmark]] (up from top 50% for AlphaCode 1).
*   **Multilinguality:** (See [[Gemini - A Family of Highly Capable Multimodal Models.pdf|Gemini Multilingual Evaluation]])
    *   **[[WMT23 Translation, Very Low-Resource Languages, MGSM, and XLSum|WMT23 Translation]]:** Ultra achieves 74.4% avg BLEURT, outperforming GPT-4 (73.8%) and PaLM 2-L (72.7%). Particularly strong in out-of-English directions.
    *   **[[WMT23 Translation, Very Low-Resource Languages, MGSM, and XLSum|Very Low-Resource Languages]]:** chrF score of 27.0 (1-shot) vs PaLM 2-L's 25.3.
    *   **[[WMT23 Translation, Very Low-Resource Languages, MGSM, and XLSum|MGSM (Multilingual Math)]]:** Ultra scores 79.0% (8-shot).
    *   **[[WMT23 Translation, Very Low-Resource Languages, MGSM, and XLSum|XLSum (Multilingual Summarization)]]:** Ultra achieves 17.6 rougeL.
*   **Long Context:**
    *   Effectively utilizes its 32,768-token context length, shown by synthetic retrieval tests (98% accuracy) and decreasing NLL across sequence positions.
*   **Factuality:** (See [[Gemini - A Family of Highly Capable Multimodal Models.pdf|Gemini Factuality Evaluation]])
    *   [[Post-training]] significantly improves:
        *   Closed-Book Inaccuracy: Halved.
        *   Attribution (AIS score): Increased by 50%.
        *   Hedging Accuracy: Up to ~70% from 0%.
*   **Nano Models (On-Device):**
    *   Nano-1 (1.8B) and Nano-2 (3.25B) show strong performance for their size in factuality, reasoning, STEM, coding, and multilingual tasks, excelling in summarization and reading comprehension with fine-tuning.

### Multimodal Prowess

Gemini Ultra sets new SOTA in 9/9 image, 6/6 video, and 5/5 speech benchmarks.

*   **Image Understanding:** (See [[Gemini Image Understanding Benchmarks]])
    *   **MMMU (Multimodal Reasoning):** Ultra achieves **62.4%** (Maj1@32), >5% over prior SOTA. Outperforms in 5/6 disciplines.
    *   **OCR-free tasks:** Superior zero-shot performance on tasks like TextVQA (82.3%), DocVQA (90.9%), ChartQA (80.8%), InfographicVQA (80.3%) without external OCR.
        >[!TIP] OCR-Free Advantage
        >Gemini's strong performance on text-rich images without external OCR highlights its native visual text recognition.
    *   **MathVista (Mathematical Reasoning):** 53.0%.
    *   **[[VQAv2]]:** 77.8%.
    *   **Multilingual Image Captioning (XM-3600):** Significant improvement over PaLI-X.
*   **Video Understanding:** (See [[Gemini Video Understanding Benchmarks]])
    *   **Few-shot Video Captioning:** SOTA on VATEX (62.7 CIDER), YouCook2 (135.4 CIDER).
    *   **Zero-shot Video QA:** SOTA on NextQA (29.9% WUPS), ActivityNet-QA (52.2% Acc).
*   **Image Generation:**
    *   Natively outputs images, allowing for interleaved image-text prompts in few-shot settings (e.g., generating blog post layouts with images).
*   **Audio Understanding:** (See [[Gemini Audio Understanding Benchmarks]])
    *   **[[ASR & AST]]:** Gemini Pro significantly outperforms [[USM]] and Whisper on FLEURS, [[VoxPopuli]], and [[CoVoST 2]]. Nano-1 also competitive.
    *   Qualitatively better on rare words and proper nouns.
*   **Modality Combination:**
    *   Demonstrated through complex tasks like the "omelet cooking" scenario (Table 13), processing interleaved audio queries and image states to provide instructions and assess cooking progress.
    *   Example: Rearranging [[matplotlib]] subplots based on an image prompt (Figure 5), requiring recognition, inverse graphics, instruction following, and abstract reasoning.

## Post-Training: Tailoring for Applications

Post-training adapts pre-trained Gemini models for specific use cases, improving quality, enhancing target capabilities, and ensuring alignment/safety.

*   **Gemini Apps vs. API Models:**
    *   **Apps (Gemini, Gemini Advanced):** Core models (Pro 1.0, Ultra 1.0) plus system interactions with tools (Google Flights, Maps, Workspace), response generation (filtering, ranking).
    *   **APIs (AI Studio, Vertex AI):** Support conversational and non-conversational use cases.
*   **Methods & Data:** (See [[ Post-Training Pipeline]])
    1.  **Prompt Data Collection:** Diverse, real-world prompts (vendor-created, licensed, synthetic).
    2.  **[[Supervised Fine-Tuning]]:** On demonstration data (human-written or model-generated & reviewed).
    3.  **[[Reward Model Training]]:** On feedback data (human preferences over candidate responses).
    4.  **[[Reinforcement Learning from Human Feedback (RLHF)]]:** Iteratively aligns model with human preferences.
*   **Enhanced Capabilities:**
    *   **Instruction Following:** Gemini Advanced (Ultra) achieves ~90% per-instruction accuracy on complex prompts, a significant improvement.
    *   **Tool Use:** Treated as code generation. Gemini Apps use Extensions; API models fine-tuned for tool use show improved academic benchmark performance (e.g., GSM8K, NQ).
    *   **[[Multilingual|Multilinguality]]:** For Apps, localization of English data to 40+ languages. For APIs, training on human-generated and translated non-English data with quality checks.
    *   **[[Multimodal Vision]]:** Fine-tuning on mixed text-only and image-text data. RLHF improves multimodal task performance without degrading text-only quality. SFT improves instruction-following for vision tasks.
    *   **Coding:** Post-training provides a significant boost to code quality and correctness.

## Responsible Deployment & Safety

(See [[Gemini Responsible AI Framework]])
A structured approach to identify, measure, and manage societal impacts.

1.  **Impact Assessment:**
    *   **Model Assessment:** Identifies benefits (e.g., efficient information processing) and risks (e.g., unsafe content, surveillance, bias, cybersecurity threats) across modalities.
    *   **Product Assessment:** For specific applications like Gemini Advanced, including red teaming and adversarial testing.
2.  **Safety Policies:**
    *   Standardized criteria for development and launch readiness.
    *   Covers child safety, hate speech, harassment, dangerous content, malicious use, and bias.
    *   Guidelines for neutrality and reflecting global user base.
3.  **Mitigations:**
    *   **Data Curation:** Filtering high-risk content, ensuring quality, responsible sourcing.
    *   **Model Mitigation:**
        *   SFT and RLHF on ~20 types of harm-inducing queries (adversarial).
        *   "Constitutional AI" inspired methods for SFT data generation.
        *   Specific efforts for multimodal queries (e.g., filtering dangerous images, custom SFT for multimodal harm).
        *  [[ i18n locale-specific safety data generation]].
4.  **Safety Evaluations:**
    *   **Development & Assurance Evals:** Internal, against policies, on held-out datasets (human & auto classifiers). Covers content safety, representational harms (Winogender, BBQ, MIAP, Dollarstreet), and dangerous capabilities.
        *   *Text-to-text findings:* Sequential improvement in policy violation rates.
        *   *Image-to-text findings:* Dedicated multimodal safety mitigation improved performance.
        *   *Video-to-text findings:* Some ungrounded inferences observed.
        *   *Representational Harms:* BBQ bias score near zero; Dollarstreet shows Poorer performance on lower socioeconomic regions. Ungrounded inferences about people in images can occur.
    *   **Dangerous Capabilities Evaluation:** (Shevlane et al., 2023)
        *   *Offensive Cybersecurity:* Solved entry-level CTFs, struggled with long-range planning. Low accuracy on patch/vulnerability identification.
        *   *Persuasion & Deception:* Mixed results in 1-on-1 human studies.
        *   *Self-Proliferation:* Agents not close to succeeding on relevant tasks.
        *   *Situational Awareness:* Generally incapable of noticing infrastructure modification opportunities without hints.
        *   *CBRN Risks:* Unlikely to provide information leading to catastrophic harm.
    *   **External Evaluations:** Independent groups tested a Dec 2023 API Ultra checkpoint for model safety (CBRN, cyber, societal risks).
    *   **Red Teaming:**
        *   *Model-level:* Adversary simulations (unstructured testing) by in-house and external experts on Dec 2023 API Ultra. Early versions vulnerable to jailbreaks; mitigated.
        *   *Structured Red Teaming:* Sociotechnical approach testing policy violations and disproportionate impacts across demographics.
        *   *Gemini Advanced Product-Level:* Multiple rounds, including safety and persona evals by 164 global testers, scaled safety evals (100k+ ratings), dogfooding.

## Limitations and Future Vision

*   **Limitations:**
    *   Subject to "[[hallucinations]]" common to LLMs.
    *   Struggles with high-level reasoning (causal understanding, logical deduction, counterfactuals) despite strong exam benchmark performance.
*   **Future Vision:** Gemini is a step towards Google's mission to solve intelligence. The aim is to develop a large-scale, modularized system with broad generalization capabilities.

## Key Appendices & Further Reading

*   [[Gemini Ultra Model Card]] (Section 10.1)
*   [[Gemini Chain-of-Thought MMLU Comparison]] (Section 10.2)
*   [[Gemini Benchmark List]] (Section 10.3)
*   [[Gemini Qualitative Examples]] (Section 10.4 onwards)