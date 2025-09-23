Overview
----------------------------
- OK, let's start. Gemini is [[Multimodal AI]], meaning it can understand image, text, audio, and video.
- It comes in three (3) sizes: Ultra, Pro, and Nano.
- The Ultra model is best at complex reasoning.
- Gemini Ultra is the **first** **model** to achieve **human-expert performance** on the [[MMLU (Massive Multitask Language Understanding)]].
- It's a [[State-of-the-Art (SOTA) Model]].
- This paper also talks about how they handle post-training and responsible deployment via services like **[Gemini, Gemini Advanced](https://gemini.google.com/app), [Google AI Studio](https://aistudio.google.com/prompts/new_chat), and [Cloud Vertex AI](https://cloud.google.com/vertex-ai?hl=en#common-uses)** 
- This paper also talks about how they handle post-training and responsible deployment via services like **[Gemini, Gemini Advanced](), [Google AI Studio](https://aistudio.google.com/prompts/new_chat), and [Cloud Vertex AI](https://cloud.google.com/vertex-ai?hl=en#common-uses)** 

Let's dive into this and put thought around it.


Introduction
--
So, this is a **family of highly capable multimodal models**, and we can expect more versions in the future.
- Their goal was to make a **[[Generalist AI Model]]** by training it on different data types like image, video, audio, and text.
- Gemini or Gemini 1.0 is their first version and comes in three (3) sizes:
	- **Ultra** - for highly complex tasks (they didn't specify how high, but alright).
	- **Pro** for enhanced performance and deployability. simply put, it's better than Nano.
	- **Nano** for on-device applications so folks like you can ask it (Will I ever get what I want?).
- Training Process:
	1.  **Pre-train** on a large scale dataset.
	2. **Post-train** for overall quality improvement, enhance target capabilities, and ensure alignment & safety. (A lot of English, I Know.)
- There are two post-trained Gemini models:
	- **Chat-focused variants** --> used in Gemini and Gemini Advanced (paid). Which is Conversational AI service formerly known as Bard (damn, the dead man is alive!).
	- **Developer-focused variants**, accessed via **Gemini API** available on **Google AI Studio and Cloud Vertex AI**
- The performance of pre- and post-trained Gemini models is evaluated in both internal and external benchmarks. In a wide range of topics: language, coding (Yaaa!), reasoning, and multimodal tasks.
- Gemini Ultra(SOTA) has been tested on sevral benchmarks 10 of 12 on text and reasoning, 9 of 9 on image understanding, 6 of 6 on video understanding , 5 of 5 on speech recognition and speech translation in total 30 of 32 benchmarks.
- Gemini Ultra has reached the threshold of 90% in the MMLU benchmark outperforming human experts on that benchmark. 
- Gemini Ultra has achived score of 62.4% in MMMU benchmark, that comprises questions about images on multi-discipline tasks requiring college-level subject knowledge and deliberate reasoning.
- Outperformed a pervious best model by +5% points in MMMU benchmark
- It has given uniform perfomance lift on video and audio understanding benchmarks too. 
- According to the paper the Gemini Ultra has shown impressive reslutes in crossmodal{[[Crossmodal AI]]} reasoning capabilities with the understanding and reason across sequence of audio, image, and text Natively{[[Natively Multimodal AI]]}  
- The model is able to understand messy handwriting (fig 1)
- The AlphaCode Team Built AlphaCode2, a new Gemini-model-powered agent
- alphacode 2 ranks within top 15% of entrants on the Codeforces competitive programming

Gemini Nano
--
- Gemini Nano is a series of small models for on device deployment.
- summarization, reading comprehension, text completion tasks and STEM, coding, multimodal and Multilingual tasks and some level in reasoning this Nano excels.

Model Architecture
--
- Build upon Transformer Decoders enhanced with improvements in architecture and model optimization for training at scale
- optimized inference on Google's Tensor Processing Units.
- 32k context length 
- 