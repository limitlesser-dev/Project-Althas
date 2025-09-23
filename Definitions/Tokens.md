---
tags:
  - AI
  - LLM
  - NLP
  - Tokenization
aliases: [AI Tokens, LLM Tokens, Token]
---
# Tokens (in AI/LLMs)

## Core Concept

In the context of [[Artificial Intelligence|AI]], particularly **[[Large Language Models|LLMs]]**, ==**Tokens**== are the **fundamental units of text** that the model processes[^1]. Think of them as pieces of words, whole words, or even punctuation marks and characters that text is broken down into before the AI can understand or generate language. Models don't see raw text; they see sequences of these tokens, which are then typically converted into numbers (`token IDs`)[^1][^2][^4].

> [!quote] In essence
> Tokens are the ==building blocks==, like Lego bricks, that [[AI]] models use to read, understand, and write text.

---

## In-Depth Information

### What is [[Tokenization]]?

**[[Tokenization]]** is the process of converting raw text into a sequence of tokens[^1][^2]. It's a necessary first step because AI models operate on numerical data, not raw strings of characters.

-   A program or algorithm called a ==**tokenizer**== performs this process.
-   Each tokenizer has a predefined ==**vocabulary**== – the set of all possible unique tokens it knows[^2]. The size of this vocabulary is a key parameter.

### Why Use Tokens Instead of Words or Characters?

Using tokens, especially ==**subword tokens**== (parts of words), offers several advantages over pure word or character-level processing:

1.  **Handling Vocabulary & Rare Words:** Subword tokens allow models to handle complex language, including new or rare words (`out-of-vocabulary` words for word-level models), typos, and different word forms (e.g., `running`, `ran`). By breaking unknown words into known smaller pieces (subwords), the model can still process them meaningfully[^3][^4].
2.  **Efficiency:** Provides a good balance between `vocabulary size` (number of unique tokens) and `sequence length` (number of tokens per text piece). Character tokens have a tiny vocabulary but produce very long sequences; word tokens have huge vocabularies and struggle with unseen words. Subwords are a compromise[^4].
3.  **Morphological Awareness:** Subword units can sometimes capture parts of word meaning (e.g., `token` + `ization`)[^3].
4.  **Numerical Representation:** Enables conversion of text into sequences of numbers (`token IDs`), which are the input to the next stage, often [[Embeddings|embedding layers]], which convert these IDs into dense vector representations capturing semantic meaning[^1].

### Common [[Tokenization]] Methods

1.  **Word Tokenization:** Splits text based on spaces and punctuation. *Simple but limited (large vocab, OOV issues).*
2.  **Character Tokenization:** Splits text into individual characters. *Handles any word, small vocab, but creates very long sequences & loses word-level meaning initially.*[^5]
3.  **[[Subword Tokenization]]** (Most common in modern [[LLM|LLMs]]): Breaks words into smaller, meaningful units. Frequent words might be single tokens; rare words are broken down. Common algorithms include:
    *   **[[Byte-Pair Encoding|BPE]]**: Starts with characters/bytes, iteratively merges the most frequent pairs to build the vocabulary[^3]. Used by [[GPT Models|GPT]] models[^5]. `Byte-level BPE` ensures any text sequence can be tokenized.
    *   **`WordPiece`**: Similar to BPE, but merges pairs based on maximizing the likelihood of the training data. Used by [[BERT]][^6].
    *   **`SentencePiece`**: Treats text as a raw sequence (including spaces), uses BPE or `Unigram` methods. Language-agnostic[^7]. Used by models like T5, ALBERT.
    *   **`Unigram`**: Starts with a large vocabulary and iteratively removes tokens that least decrease the likelihood of the data, given a language model.

### Significance of Tokens

1.  **Model Input/Output Limits ([[Context Window]]):** [[LLM|LLMs]] have a maximum limit on the number of tokens they can process at once (input + output), known as the ==`context window`== (e.g., 4096, 8192, 32k, 128k+ tokens)[^8]. This directly impacts how much history/information the model can consider or how long a response it can generate.
2.  **Cost:** Many [[LLM]] APIs ==charge based on the number of tokens== processed (both input prompt tokens and generated output tokens)[^9]. Understanding token count is crucial for cost estimation and management.
    > [!TIP] Rough English Guide
    > *   1 token ≈ 4 characters
    > *   1 token ≈ ¾ of a word
    > *   100 tokens ≈ 75 words
3.  **Performance and Behavior:** The choice of tokenizer and vocabulary impacts model performance, computational load during training/inference, and can sometimes cause unexpected model behavior (e.g., difficulty with spelling specific words, simple arithmetic, reversing strings) if the tokenization splits things unnaturally for the task[^2].

### Example Tokenization

Consider the text: `Tokenization is important!`

*   **Word Tokens (Simple Example):**
    ```
    ["Tokenization", "is", "important!"]
    ```
*   **Subword Tokens (Illustrative `BPE`/`WordPiece`):**
    ```
    ["Token", "ization", " is", " important", "!"]
    ```
    *(Note: Spaces often get merged into the start of subsequent tokens)*
*   **Character Tokens:**
    ```
    ["T", "o", "k", "e", "n", "i", "z", "a", "t", "i", "o", "n", " ", "i", "s", " ", "i", "m", "p", "o", "r", "t", "a", "n", "t", "!"]
    ```
*   **Numerical Representation (Example `Token IDs`):**
    ```
    [2345, 4567, 678, 8910, 101]
    ```
    *(Actual IDs depend entirely on the specific tokenizer's vocabulary)*

---

**Note on Links:** Citations use standard Markdown footnotes. Internal links like `[[Large Language Models]]` link to other notes in your vault.

**Sources:**

[^1]: Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., ... & Polosukhin, I. (2017). *Attention Is All You Need.* ([arXiv:1706.03762](https://arxiv.org/abs/1706.03762)). While focusing on the Transformer architecture, tokenization and embeddings are fundamental prerequisites mentioned.
[^2]: Hugging Face Documentation. *Summary of the tokenizers.* Accessed April 23, 2025. ([Link](https://huggingface.co/docs/transformers/main_classes/tokenizer))
[^3]: Sennrich, R., Haddow, B., & Birch, A. (2016). *Neural Machine Translation of Rare Words with Subword Units.* (Introduced BPE for NLP). ([arXiv:1508.07909](https://arxiv.org/abs/1508.07909))
[^4]: OpenAI Documentation. *What are tokens and how to count them?* Accessed April 23, 2025. ([Link](https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them))
[^5]: Radford, A., Wu, J., Child, R., Luan, D., Amodei, D., & Sutskever, I. (2019). *Language Models are Unsupervised Multitask Learners.* (GPT-2 Paper, mentions byte-level BPE). ([Link - PDF](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)) *See also Karpathy blog for general character/word context:* Karpathy, A. (Blog Post). *The unreasonable effectiveness of Recurrent Neural Networks*. ([Link](http://karpathy.github.io/2015/05/21/rnn-effectiveness/))
[^6]: Devlin, J., Chang, M. W., Lee, K., & Toutanova, K. (2019). *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding.* (Mentions use of WordPiece). ([arXiv:1810.04805](https://arxiv.org/abs/1810.04805))
[^7]: Kudo, T., & Richardson, J. (2018). *SentencePiece: A simple and language independent subword tokenizer and detokenizer for Neural Text Processing.* ([arXiv:1808.06226](https://arxiv.org/abs/1808.06226))
[^8]: Various LLM Documentation (e.g., OpenAI, Anthropic, Google AI). Context window limits are specified in model documentation and API references. (Example: OpenAI Models page accessed April 23, 2025. [Link](https://platform.openai.com/docs/models))
[^9]: OpenAI API Documentation. *Pricing.* Accessed April 23, 2025. ([Link](https://openai.com/pricing)). (Illustrates token-based pricing common across many providers).