---
tags:
  - AI
  - MachineLearning
  - DeepLearning
  - NLP
  - LLMs
  - Benchmark
  - Evaluation
  - MathReasoning
aliases: [GSM8K, MATH Benchmark, Grade School Math 8K, Mathematical Problem Solving]
---

# GSM8K and MATH Benchmarks

This note covers two distinct but related benchmarks used for evaluating the mathematical reasoning capabilities of Large Language Models: **GSM8K** and **MATH**.

## GSM8K (Grade School Math 8K)

### Core Concept

**GSM8K (Grade School Math 8K)** is a dataset of ==8,500 high-quality, linguistically diverse grade school math word problems==. It was created to measure the multi-step mathematical reasoning abilities of [[Large Language Models|Large Language Models (LLMs)]]. Each problem in GSM8K requires a sequence of elementary arithmetic operations (addition, subtraction, multiplication, division) to solve, typically involving 2 to 8 steps. The dataset is designed to be challenging, requiring models to understand natural language descriptions of mathematical scenarios and translate them into logical computational steps.

> [!quote] In Essence
> GSM8K is a benchmark focused on ==evaluating an LLM's ability to perform multi-step arithmetic reasoning by solving grade school level math word problems==.

### In-Depth Information

-   **Dataset Composition**:
    -   Approximately 7.5K training problems and 1K test problems.
    -   Problems are written in natural language and are designed to be solvable by proficient middle school students.
    -   Solutions consist of step-by-step reasoning leading to a final numerical answer.
-   **Task**: The model is given a word problem and must generate the correct sequence of reasoning steps and the final numerical answer.
-   **Evaluation Metric**: The primary metric is **accuracy** – whether the final numerical answer produced by the model matches the correct answer. Some evaluations also consider the correctness of the intermediate reasoning steps, although this is harder to automate.
-   **Purpose and Significance**:
    -   **Measures Multi-Step Reasoning**: Unlike simpler math datasets, GSM8K requires models to perform a chain of calculations.
    -   **Linguistic Diversity**: Problems are phrased in varied ways, testing the model's natural language understanding capabilities.
    -   **Benchmark for LLM Reasoning**: It has become a standard benchmark for assessing the mathematical reasoning progress of LLMs. Improvements on GSM8K are often highlighted as evidence of enhanced reasoning abilities.
    -   **Drives Research in Reasoning Techniques**: The challenges posed by GSM8K have spurred research into prompting techniques like [[Transformer Models#Novel CoT Prompting Approach|Chain-of-Thought (CoT)]] prompting, which significantly improves performance by encouraging models to output intermediate reasoning steps.
-   **Challenges for Models**:
    -   Understanding the problem statement accurately.
    -   Identifying the correct sequence of operations.
    -   Performing arithmetic calculations correctly.
    -   Avoiding distractions from irrelevant information in the problem.
-   **Performance Trends**:
    -   Early LLMs struggled significantly with GSM8K.
    -   The introduction of CoT prompting led to substantial performance gains.
    -   State-of-the-art models like GPT-4, PaLM 2, and Gemini have achieved very high accuracy, with some models surpassing 90% and even approaching human-level performance on this dataset.

## MATH (Mathematical Problem Solving)

### Core Concept

The **MATH** dataset is a benchmark designed to evaluate the mathematical problem-solving abilities of machine learning models on ==more advanced competition-level mathematics problems==. It covers a wide range of difficulty levels, from pre-algebra to calculus, linear algebra, number theory, and geometry. Problems in MATH generally require more complex reasoning, deeper mathematical knowledge, and often more creative problem-solving strategies than those in GSM8K.

> [!quote] In Essence
> The MATH benchmark assesses an LLM's proficiency in ==solving challenging competition-level mathematics problems across various advanced mathematical disciplines==.

### In-Depth Information

-   **Dataset Composition**:
    -   Consists of 12,500 problems sourced from math competitions (e.g., AMC 10, AMC 12, AIME).
    -   Problems are categorized into five difficulty levels (Level 1 to Level 5) and seven subject areas: Prealgebra, Algebra, Number Theory, Counting & Probability, Geometry, Intermediate Algebra, and Precalculus.
    -   Each problem includes a full step-by-step solution in LaTeX format, in addition to the final answer.
-   **Task**: Given a math problem, the model needs to generate a complete derivation (the thought process or solution steps) and the final answer.
-   **Evaluation Metric**:
    -   The primary metric is **accuracy** based on the final answer.
    -   Correctness of the generated solution steps can also be evaluated, though this is often done qualitatively or with more sophisticated methods.
-   **Purpose and Significance**:
    -   **Tests Advanced Mathematical Reasoning**: Goes beyond basic arithmetic to assess understanding of complex mathematical concepts and problem-solving techniques.
    -   **Covers Diverse Mathematical Topics**: Provides a broad assessment across different areas of mathematics.
    -   **Challenges Frontier Models**: Remains a difficult benchmark for even the most advanced LLMs, highlighting areas where further improvement is needed in formal reasoning.
    -   **Encourages Development of Formal Reasoning**: Success on MATH requires models to not just "guess" answers but to perform rigorous, step-by-step derivations.
    -   **Tool Use Integration**: Solving MATH problems often benefits from or even requires the use of external tools like code interpreters (e.g., Python for calculations or symbolic manipulation), which is an active area of research for LLMs.
-   **Challenges for Models**:
    -   Requires deep understanding of mathematical definitions, theorems, and techniques.
    -   Involves complex symbolic manipulation.
    -   Often requires insight or non-obvious steps to arrive at a solution.
    -   Ambiguity in natural language problem statements can be difficult to resolve.
    -   Generating formally correct and complete step-by-step solutions is very challenging.
-   **Performance Trends**:
    -   Performance on MATH is generally lower than on GSM8K, reflecting its higher difficulty.
    -   Techniques like Chain-of-Thought, Program-Aided Language Models (PALs – where models write code to solve problems), and tool-augmented LLMs have shown promise in improving performance.
    -   Even the best models still have considerable room for improvement, particularly on the higher difficulty levels.
    -   Google's Minerva model, specifically trained on mathematical and scientific text, demonstrated strong performance on this benchmark. More recent models like GPT-4 and Gemini have also shown significant capabilities.

### Comparison: GSM8K vs. MATH

| Feature             | GSM8K                                        | MATH                                                                 |
| :------------------ | :------------------------------------------- | :------------------------------------------------------------------- |
| **Primary Focus**   | Multi-step arithmetic word problems          | Advanced competition-level mathematics problems                      |
| **Difficulty**      | Grade school / Middle school level           | High school competition to undergraduate level                       |
| **Math Concepts**   | Basic arithmetic (+, -, \*, /)               | Algebra, geometry, number theory, calculus, probability, etc.        |
| **Reasoning Steps** | Typically 2-8 simpler steps                | Often more numerous and complex, requiring deeper insight          |
| **Solution Format** | Numerical answer with natural language steps | Numerical/symbolic answer with LaTeX formatted step-by-step solution |
| **Current LLM Perf.**| High, approaching human levels for SOTA      | Moderate to good, still significant room for improvement for SOTA    |

> [!SUMMARY] In Summary
> **GSM8K** and **MATH** are two critical benchmarks for evaluating the mathematical reasoning abilities of Large Language Models. ==GSM8K focuses on multi-step arithmetic reasoning in the context of grade school word problems, testing fundamental natural language understanding and sequential calculation==. ==MATH, on the other hand, presents a more formidable challenge with competition-level problems spanning advanced mathematical disciplines, requiring deeper conceptual understanding, complex symbolic manipulation, and sophisticated problem-solving strategies==. Both benchmarks have been instrumental in driving progress in LLM reasoning, particularly through the development and refinement of techniques like Chain-of-Thought prompting and tool integration.

---

**Sources:**

*   **GSM8K:**
    [^1]: Cobbe, K., Kosaraju, V., Bavarian, M., Chen, M., Jun, H., Kaiser, L., ... & Sutskever, I. (2021). *Training Verifiers to Solve Math Word Problems*. arXiv preprint arXiv:2110.14168.
    [^2]: Papers with Code. *GSM8K*. ([Link](https://paperswithcode.com/dataset/gsm8k))
    [^3]: Wei, J., Wang, X., Schuurmans, D., Bosma, M., Chi, E., Le, Q., & Zhou, D. (2022). *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models*. arXiv preprint arXiv:2201.11903. (Often uses GSM8K for evaluation).

*   **MATH:**
    [^4]: Hendrycks, D., Burns, C., Kadavath, S., Arora, A., Basart, S., Tang, E., ... & Steinhardt, J. (2021). *Measuring Mathematical Problem Solving With the MATH Dataset*. arXiv preprint arXiv:2103.03874.
    [^5]: Papers with Code. *MATH*. ([Link](https://paperswithcode.com/dataset/math))
    [^6]: Lewkowycz, A., Andreassen, A., Dohan, D., Dyer, E., Michalewski, H., Ramasesh, V., ... & Urban, C. (2022). *Solving Quantitative Reasoning Problems with Language Models*. arXiv preprint arXiv:2206.14858. (Introduced Minerva, which showed strong MATH performance).
    [^7]: Gao, L., Madaan, A., Zhou, S., Alon, U., Liu, P., Yang, Y., ... & Callan, J. (2023). *PAL: Program-aided Language Models*. arXiv preprint arXiv:2211.10435. (Uses MATH for evaluation).

*   **General LLM Evaluation (often reference these benchmarks):**
    [^8]: OpenAI. (2023). *GPT-4 Technical Report*. arXiv preprint arXiv:2303.08774.
    [^9]: Google Research. (Multiple blog posts and papers on PaLM, PaLM 2, and Gemini often discuss performance on these math benchmarks).

---