---
tags:
  - AI
  - MachineLearning
  - ReinforcementLearning
  - RLHF
  - Alignment
  - LLM
  - TrainingTechnique
  - HumanFeedback
aliases: [RLHF, Learning from Human Preferences]
---

### Reinforcement Learning from Human Feedback (RLHF): The Core Concept (Simple Version)

**Reinforcement Learning from Human Feedback (RLHF)** is a technique to train an [[AI]] agent when it's hard to automatically calculate a reward score. Instead of automatic rewards, ==**humans provide feedback**== on the AI's behavior. This feedback trains a separate ==**Reward Model (RM)**== which acts like a **human judge**. The main [[Agent (RL)|AI agent]] then learns using [[Reinforcement Learning|RL]] by trying to perform actions that this "judge" model predicts humans would prefer[^1][^2].

> [!quote] In Essence
> It's like training an AI to be helpful or polite, not by programming rules, but by:
> 1.  Having humans rate the AI's attempts.
> 2.  Training a 'judge' based on those ratings.
> 3.  Having the AI try to impress that judge.

---

### More Detail on Reinforcement Learning from Human Feedback (Keeping it Simple)

Let's break down the typical workflow, especially for training helpful [[LLM|large language models]] like chatbots[^1][^3]:

> [!Problem] The Core Challenge
> How do you teach an AI complex, subjective goals like being "helpful," "honest," or "harmless"? These are hard to define with explicit reward functions. However, humans *can* evaluate which of two responses is better. RLHF leverages this human judgment.

1.  **Step 1: Start with a Base Model ([[Supervised Fine-Tuning|SFT]])**
    *   Begin with an AI model already pre-trained on a large dataset (e.g., a base [[LLM]] like GPT or Llama)[^3].
    *   Often, an initial ==supervised fine-tuning (SFT)== phase occurs. The model is trained on high-quality examples of desired behavior (e.g., prompt-response pairs curated by humans)[^1][^3]. This teaches the model the desired style and task format.

2.  **Step 2: Collect Human Preference Data**
    *   Give the SFT model a prompt (e.g., "Explain photosynthesis simply").
    *   Have the AI generate *multiple* different answers (Answer A, Answer B, ...).
    *   Show these answers to **human reviewers**.
    *   Ask the humans to **rank the answers** from best to worst based on specified criteria (helpfulness, accuracy, safety, etc.). Example: `Answer B > Answer A > Answer C`[^1][^2].
    *   This ==ranking data== is the critical **human feedback**.

3.  **Step 3: Train the "Judge" ([[Reward Model|RM]])**
    *   Use the collected human ranking data to train a *separate* AI model – the **Reward Model (RM)**[^1][^3].
    *   The RM takes a prompt and a potential answer as input and outputs a ==scalar score== representing the predicted human preference (how "good" that answer is)[^1].
    *   Its goal is to ==learn to mimic the preferences== expressed by the human reviewers during the ranking step.

4.  **Step 4: Fine-Tune the Main AI with RL (e.g., [[PPO]])**
    *   Use a [[Reinforcement Learning|RL]] algorithm (commonly ==Proximal Policy Optimization (PPO)==[^1][^3]) to fine-tune the SFT model (which now acts as the **[[Policy (RL)|policy]]** or **[[Agent (RL)|agent]]**).
        *   The [[Agent (RL)|Agent]] receives a prompt (**[[State (RL)|State]]**).
        *   It generates an answer (**[[Action (RL)|Action]]**).
        *   The generated (prompt, answer) pair is evaluated by the trained **[[Reward Model|Reward Model]]**.
        *   The RM outputs a **score ([[Reward (RL)|Reward]])**.
        *   The [[Agent (RL)|Agent]]'s [[Policy (RL)|policy]] is updated using the RL algorithm (PPO) to ==maximize this reward signal==. This encourages the agent to generate answers that the RM predicts humans will prefer[^1][^3].
        *   *Constraint:* Often, a penalty term (KL divergence) is added to the reward to prevent the RL policy from diverging too much from the original SFT model, preserving general capabilities and improving training stability[^1][^3].

> [!check] Why Use This Complex Process?
> *   **Handles Fuzzy Goals:** Enables training for complex, subjective goals (safety, ethics, helpfulness, style) that are hard to code directly but easier for humans to evaluate[^2].
> *   **AI Alignment:** A key technique for aligning AI behavior with human values and preferences[^1]. See [[AI Alignment]].
> *   **Scalability:** Collecting preference data (ranking A vs. B) can be more efficient and scalable than requiring humans to write perfect demonstration examples for every scenario (as in pure SFT)[^2][^4].

> [!example] Where is RLHF Used?
> *   Widely used to fine-tune large language models like ==ChatGPT==[^1], ==Claude==[^2], Sparrow, and others to improve their helpfulness, honesty, harmlessness, and overall conversational quality, going beyond simple next-word prediction.

> [!TIP] Simple Analogy: Training a Comedian AI
> 1.  **SFT:** Start with an AI that knows basic joke structures.
> 2.  **Human Feedback:** Have it tell jokes for a topic. Humans rank them by funniness.
> 3.  **Reward Model:** Train a "Funny Judge" AI based on these human rankings.
> 4.  **RL Fine-tuning:** The comedian AI tells jokes. The "Funny Judge" gives scores (rewards). The comedian AI uses [[PPO]] to learn to tell jokes that the judge rates highly.

In short, RLHF uses ==human preferences== to train a [[Reward Model|RM]], which then provides a reward signal for a standard [[Reinforcement Learning|RL]] process (like [[PPO]]). This allows optimizing AI behavior for ==complex, subjective goals== that are better judged by humans than by automated metrics.

---

**Note on Links:** The citations below `[^1]`, `[^2]`, etc., use standard Markdown footnote syntax. In Obsidian's *Reading View*, clicking a number like `[^1]` should take you to the corresponding footnote. Internal links like `[[Reinforcement Learning]]` connect to other notes in your vault.

**Sources:**

[^1]: Ouyang, L., Wu, J., Jiang, X., Almeida, D., Wainwright, C. L., Mishkin, P., ... & Lowe, R. (2022). *Training language models to follow instructions with human feedback.* Advances in Neural Information Processing Systems, 35, 27730-27744. ([arXiv:2203.02155](https://arxiv.org/abs/2203.02155)) (See also OpenAI Blog: [Instruction Following](https://openai.com/research/instruction-following))
[^2]: Bai, Y., Jones, A., Ndousse, K., Askell, A., Chen, A., DasSarma, N., ... & Kaplan, J. (2022). *Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback.* ([arXiv:2204.05862](https://arxiv.org/abs/2204.05862))
[^3]: Hugging Face Blog (Deep RL Course). *Reinforcement Learning from Human Feedback.* Accessed April 23, 2025. ([Link](https://huggingface.co/learn/deep-rl-course/unit8/introduction))
[^4]: Ziegler, D. M., Stiennon, N., Wu, J., Brown, T. B., Radford, A., Amodei, D., ... & Irving, G. (2019). *Fine-tuning language models from human preferences.* ([arXiv:1909.08593](https://arxiv.org/abs/1909.08593))