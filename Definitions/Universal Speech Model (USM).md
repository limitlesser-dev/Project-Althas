---
tags:
  - AI
  - MachineLearning
  - DeepLearning
  - SpeechRecognition
  - NLP
  - GoogleAI
aliases: [USM, Google USM, Chirp]
---

# Universal Speech Model (USM)

## Core Concept

The **Universal Speech Model (USM)** is a family of state-of-the-art [[Speech Recognition|speech recognition]] models developed by Google AI. It is designed to understand and transcribe spoken language across a vast number of languages, including those with limited available data (low-resource languages). USM aims to be a foundational technology for Google's "1,000 Languages Initiative," which seeks to build an AI model supporting the world's thousand most-spoken languages, thereby increasing global information accessibility and inclusion.

> [!quote] In Essence
> Google's Universal Speech Model (USM) represents a significant advancement in ==[[Automatic Speech Recognition|Automatic Speech Recognition (ASR)]] technology, capable of transcribing speech from hundreds of languages==, including under-resourced ones, by leveraging large-scale pre-training and a robust architecture.

---

## In-Depth Information

### Architecture and Training

-   **Foundation**: USM is built upon a Conformer architecture, which is a convolution-augmented [[Transformer Models|Transformer]] model. This architecture combines the strengths of convolutional layers for local feature extraction and transformer layers for capturing global context.
-   **Parameters and Data**: The USM family includes models with up to 2 billion parameters, trained on an extensive dataset comprising 12 million hours of speech and 28 billion sentences of text, spanning over 300 languages.
-   **Training Pipeline**: The training process typically involves multiple stages:
    1.  **Self-Supervised Pre-training**: The Conformer encoder is pre-trained on a large unlabeled multilingual speech dataset (e.g., YouTube audio). Techniques like BERT-based speech pretraining (BEST-RQ) are used.
    2.  **Multi-Objective Supervised Pre-training (Optional)**: This stage incorporates knowledge from additional text data to improve quality and language coverage. The model is trained jointly on unlabeled speech, labeled speech, and text data.
    3.  **Fine-tuning**: The pre-trained encoder is then fine-tuned on smaller sets of labeled data for specific downstream tasks, such as ASR or Automatic Speech Translation (AST). This approach allows the model to adapt effectively to new languages and tasks even with limited supervised data.

### Key Features and Capabilities

-   **Extensive Language Coverage**: USM can perform ASR for over 100 languages, significantly outperforming previous models in its breadth of language support. This includes widely spoken languages like English and Mandarin, as well as under-resourced languages such as Amharic, Cebuano, Assamese, and Azerbaijani.
-   **State-of-the-Art Performance**: USM has demonstrated state-of-the-art results on various multilingual ASR and speech-to-text translation benchmarks. It has shown significantly lower Word Error Rates (WER) compared to other models, including OpenAI's Whisper, across many languages. For instance, on YouTube captions across 73 languages, USM achieved an average WER of less than 30%.
-   **Adaptability**: The model's training process is effective for adapting to new languages and data.
-   **Robustness**: It shows strong performance even on under-represented languages despite limited supervised data for those specific languages during fine-tuning.
-   **Scalability**: The architecture and training pipeline are designed to be scalable, forming a foundation for expanding speech modeling to Google's goal of 1,000 languages.
-   **Chunk-wise Attention**: To address quality degradation in Conformer models with long-form audio, some USM versions incorporate a chunk-wise attention mechanism.

### Google Cloud Integration (Chirp)

-   The technology behind USM is available through Google Cloud Speech-to-Text API v2 under the model identifier "chirp".
-   Chirp represents the next generation of Google's speech-to-text models, unifying data from multiple languages into a single model.
-   While a single model, users still specify the language for recognition.
-   Chirp is suitable for both short audio (<1 min) via `Speech.Recognize` and long audio (1 min to 8 hrs) via `Speech.BatchRecognize` but might not be ideal for true real-time use due to processing in larger chunks.

### Significance and Goals

-   **Inclusivity**: A primary goal of USM is to bring greater digital inclusion to billions of people by supporting a wider range of languages, especially those with fewer speakers or limited data resources.
-   **Information Accessibility**: It aligns with Google's mission to organize the world's information and make it universally accessible.
-   **Foundation for Future Models**: USM serves as a foundational step for developing even more comprehensive multilingual speech models.

### Performance Benchmarks

-   On the FLEURS benchmark (102 languages), USM showed significantly lower WER compared to Whisper, both with and without in-domain fine-tuning.
-   For English (US), USM demonstrated a 6% relative lower WER compared to Google's previous internal state-of-the-art model.
-   Across 18 languages that Whisper could decode with less than 40% WER, USM showed, on average, a 32.7% relative lower WER.

> [!SUMMARY] In Summary
> Google's Universal Speech Model (USM) is a family of powerful [[Automatic Speech Recognition|ASR]] models built on a Conformer architecture and trained on vast amounts of speech and text data spanning over 300 languages. Its key strengths lie in its ==extensive language coverage (100+ languages for ASR), state-of-the-art performance, and ability to effectively recognize speech in under-resourced languages through sophisticated pre-training and fine-tuning techniques==. As part of Google's "1,000 Languages Initiative," USM, also accessible via Google Cloud as "Chirp," aims to make information and technology more inclusive and universally accessible.

---

**Sources:**

[^1]: Google AI Blog. (2023-03-06). *Universal Speech Model (USM): State-of-the-art speech AI for 100+ languages*.
[^2]: AssemblyAI. (2024-04-03). *Introducing Universal-1*. (Note: This is AssemblyAI's model, distinct from Google's USM, but included in search results. The response focuses on Google's USM).
[^3]: MarkTechPost. (2023-03-08). *Google AI Introduces Universal Speech Model (USM): A Family of State-of-the-Art Speech Models with 2B Parameters Trained on 12 Million Hours of Speech and 28 Billion Sentences of Text*.
[^4]: Google Research. (2023-03-06). *Universal Speech Model*.
[^5]: AssemblyAI. (2024-10-30). *Universal-2-TF: Robust All-Neural Text Formatting for ASR*. (Note: This is AssemblyAI's model).
[^6]: InfoQ. (2023-05-16). *Google's Universal Speech Model Performs Speech Recognition on Hundreds of Languages*.
[^7]: InfoQ. (2023-03-16). *Google AI Updates Universal Speech Model to Scale Automatic Speech Recognition beyond 100 Languages*.
[^8]: The Economic Times. (2023-03-07). *Google building AI language model that supports 1000 different languages*.
[^9]: AssemblyAI. (Accessed 2025-05-21). *Introducing Universal-2*. (Note: This is AssemblyAI's model).
[^10]: CMS Wire. (2023-03-09). *Microsoft Introduces AI Assistant, Google USM Advances, More News*.
[^11]: Synced Review. (2023-03-09). *Google's Universal Speech Model Scales Automatic Speech Recognition to 100+ Languages*.
[^12]: Slator. (2023-03-10). *Google Sheds More Light on Its 1,000+ Languages Universal Speech Model*.
[^13]: arXiv. (2023-09-25). *Google USM: Scaling Automatic Speech Recognition Beyond 100 Languages*.
[^14]: LinkedIn post by Olewave. (2024-05-06). *Google's Universal Speech Model for 100+ languages beats OpenAI's Whisper Model*. (Note: This is a commentary/summary of the Google USM paper).
[^15]: Gladia. (2025-04-02). *Introducing Solaria, the first truly universal speech-to-text model*. (Note: This is Gladia's model).
[^16]: ISCA Archive. (2020). *Universal Speech Transformer*. (Note: This is an older paper on a different "Universal Speech Transformer" concept).
[^17]: ResearchGate. (2023-03-03). *Google USM: Scaling Automatic Speech Recognition Beyond 100 Languages (PDF)*. (Link to the research paper).
[^18]: MKAI. (Accessed 2025-05-21). *Universal Speech Model (USM): State-of-the-art speech AI for 100+ languages*.
[^19]: Google Cloud Documentation. (Accessed 2025-05-21). *Chirp: Universal speech model | Cloud Speech-to-Text V2 documentation*.
[^20]: Gadgets Now. (2023-03-20). *Google AI Universal Speech Model: What is it, what does it do, its usage and more queries answered*.