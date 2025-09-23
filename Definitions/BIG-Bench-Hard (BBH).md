---
tags:
  - AI
  - MachineLearning
  - DeepLearning
  - NLP
  - LLMs
  - Benchmark
  - Evaluation
aliases: [BBH, BIG-Bench Hard]
---

# BIG-Bench-Hard (BBH)

## Core Concept

**BIG-Bench-Hard (BBH)** is a subset of the **Beyond the Imitation Game benchmark (BIG-Bench)**, specifically curated to include only those tasks on which contemporary Large Language Models (LLMs) initially performed poorly. The primary purpose of BBH is to ==provide a more challenging and focused benchmark for evaluating the complex reasoning capabilities of LLMs== that are not yet saturated by current model performance. It aims to highlight tasks that remain difficult even for very large models, thereby guiding future research toward improving these more sophisticated reasoning skills.

> [!quote] In Essence
> BIG-Bench-Hard (BBH) is a ==challenging subset of the BIG-Bench benchmark, comprising tasks where large language models initially struggled==. It serves as a focused evaluation suite for advanced reasoning capabilities that are still beyond the grasp of current LLMs.

---

## In-Depth Information

### Background: BIG-Bench

-   **BIG-Bench (Beyond the Imitation Game benchmark)** is a large, collaborative benchmark designed to probe and evaluate the capabilities of LLMs across a diverse range of tasks. It contains over 200 tasks contributed by numerous researchers.
-   The goal of BIG-Bench was to create tasks that were believed to be beyond the capabilities of LLMs at the time of its creation.

### Creation of BIG-Bench-Hard

-   As LLMs rapidly improved, their performance on many BIG-Bench tasks quickly approached or surpassed average human rater performance.
-   To maintain a challenging evaluation set, researchers identified a subset of BIG-Bench tasks where model performance significantly lagged behind human performance, even after models were scaled up or prompted with techniques like Chain-of-Thought (CoT).
-   This subset became known as BIG-Bench-Hard (BBH).
-   Specifically, a study in 2022 by Suzgun et al. identified 23 "hard" BIG-Bench tasks where even a 540-billion parameter LLM (PaLM) with Chain-of-Thought prompting did not perform well initially. These tasks were selected because few-shot prompting with CoT on these models led to near-random performance without CoT, but significantly better performance with CoT, yet still often below human levels.

### Characteristics of BBH Tasks

Tasks included in BBH typically require:

-   **Multi-step Reasoning**: Problems that cannot be solved with simple pattern matching or information retrieval and require a sequence of logical deductions.
-   **Complex Instruction Following**: Understanding and adhering to intricate instructions and constraints.
-   **Commonsense Reasoning**: Applying real-world knowledge and understanding implicit assumptions.
-   **Symbolic Manipulation**: Tasks that involve manipulating symbols or abstract concepts according to given rules.
-   **Algorithmic Reasoning**: Following or deducing algorithmic procedures.

Examples of tasks that have been part of BBH include:

-   **Boolean Expressions**
-   **Causal Judgment**
-   **Date Understanding**
-   **Logical Deduction (often with multiple steps)**
-   **Multistep Arithmetic**
-   **Tracking Shuffled Objects**
-   **Dyck Languages**
-   **Word Sorting**

### Purpose and Significance of BBH

-   **Challenging Frontier Models**: BBH serves as a "stress test" for the most advanced LLMs, highlighting areas where they still fall short of human-like reasoning.
-   **Guiding Research**: By pinpointing persistent weaknesses, BBH helps direct research efforts towards developing new architectures, training techniques, or prompting strategies to improve these specific reasoning skills.
-   **Measuring Progress**: As models evolve, their performance on BBH can be a more sensitive indicator of true progress in reasoning capabilities compared to benchmarks where performance has saturated.
-   **Evaluating Prompting Techniques**: BBH is often used to evaluate the effectiveness of advanced prompting techniques like Chain-of-Thought (CoT), since these tasks particularly benefit from explicit reasoning steps. For example, it was observed that even very large models performed poorly on BBH tasks with standard few-shot prompting, but their performance significantly improved when CoT prompting was applied.

### Performance on BBH

-   Initial evaluations showed that even large models like PaLM (540B parameters) had difficulty with BBH tasks without CoT prompting. With CoT, performance improved substantially, but still often remained below human levels.
-   Later models, such as GPT-4, have shown very strong performance on BBH, sometimes surpassing average human rater performance when combined with advanced prompting strategies.
-   However, the difficulty of BBH means that it continues to be a useful benchmark for differentiating the capabilities of leading-edge models.
-   Performance on BBH is sensitive to factors like model scale, the quality of CoT prompting, and the number of exemplars provided.

### Limitations

-   **Dynamic Nature**: As models improve, tasks within BBH might eventually become "easy." This necessitates ongoing efforts to identify new, challenging tasks or create harder versions of existing ones.
-   **Focus**: While BBH focuses on hard reasoning tasks, it doesn't cover all aspects of intelligence or all types of challenging problems (e.g., real-world interaction, continuous learning).
-   **Potential for "Teaching to the Test"**: As with any benchmark, there's a risk that models might be specifically optimized to perform well on BBH tasks without necessarily achieving genuine, generalizable improvements in reasoning.

> [!SUMMARY] In Summary
> BIG-Bench-Hard (BBH) is a curated and challenging subset of the broader BIG-Bench benchmark, consisting of tasks that initial evaluations showed to be difficult for even large language models, especially without advanced prompting techniques like Chain-of-Thought. ==BBH focuses on multi-step reasoning, complex instruction following, and other demanding cognitive abilities==. Its primary purpose is to ==provide a rigorous testbed for evaluating the frontier of LLM reasoning capabilities, track genuine progress, and guide research towards overcoming persistent limitations in AI reasoning==.

---

**Sources:**

[^1]: Suzgun, M., Scales, N., Schärli, N., Gehrmann, S., Tay, Y., Chung, H. W., ... & Wei, J. (2022). *Challenging BIG-Bench tasks and whether chain-of-thought can solve them*. arXiv preprint arXiv:2210.09261.
[^2]: BIG-Bench Authors. (Accessed 2025-05-22). *BIG-Bench: Beyond the Imitation Game*. ([Link to the official BIG-Bench GitHub or website](https://github.com/google/BIG-bench))
[^3]: Srivastava, A., et al. (2022). *Beyond the Imitation Game: Quantifying and extrapolating the capabilities of language models*. arXiv preprint arXiv:2206.04615. (The main BIG-Bench paper).
[^4]: OpenAI. (2023). *GPT-4 Technical Report*. arXiv preprint arXiv:2303.08774.
[^5]: Papers with Code. *BIG-bench Benchmark*. ([Link](https://paperswithcode.com/dataset/big-bench))
[^6]: Google AI Blog. (2022-10-20). *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models*. (Often discusses performance on hard tasks like those in BBH).
[^7]: Wei, J., Wang, X., Schuurmans, D., Bosma, M., Chi, E., Le, Q., & Zhou, D. (2022). *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models*. arXiv preprint arXiv:2201.11903. (Foundation for CoT, relevant to BBH context).
[^8]: DeepMind Blog. (2022-06-09). *Beyond the Imitation Game: A new benchmark for large language models*.
[^9]: The Register. (2022-10-21). *Google AI team finds even its biggest language models can't handle complex reasoning*. (Article discussing the BBH paper).
[^10]: MarkTechPost. (2022-11-02). *Google AI Researchers Introduce 'BIG-Bench Hard' (BBH), A New Benchmark For Evaluating The Reasoning Capabilities Of Large Language Models (LLMs)*.
[^11]: GitHub - suzgunmirac/BIG-Bench-Hard. (Accessed 2025-05-22). *Provides the list of tasks included in BBH*. ([Link](https://github.com/suzgunmirac/BIG-Bench-Hard))

---