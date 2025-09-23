---
tags:
  - AI
  - MachineLearning
  - DeepLearning
  - Hardware
  - Accelerators
  - GoogleCloud
aliases: [TPUv4, TPUv5e, Tensor Processing Unit v4, Tensor Processing Unit v5e, Cloud TPU v4, Cloud TPU v5e]
---

# TPUv4 and TPUv5e Accelerators

## Core Concept

**TPUv4** and **TPUv5e** are generations of Google's custom-designed [[ASIC|Application-Specific Integrated Circuits]] known as [[Tensor Processing Unit|Tensor Processing Units (TPUs)]]. These accelerators are engineered to ==dramatically speed up [[Machine Learning]] (ML) and [[Deep Learning]] workloads==, particularly those involving large-scale matrix operations and tensor computations, which are fundamental to [[Neural Network|neural networks]]. TPUv4 represents a significant leap in performance and efficiency over its predecessors, while TPUv5e is positioned as a more cost-efficient and versatile option, especially for inference and medium-to-large scale training. Both are integral to [[Google Cloud Platform|Google Cloud's]] AI infrastructure.

> [!quote] In Essence
> TPUv4 and TPUv5e are Google's high-performance [[Tensor Processing Unit|TPU]] [[ASIC|accelerators]] designed to ==optimize the training and inference of large-scale [[AI]] models==. TPUv4 focuses on maximum performance and scalability for the most demanding tasks, while TPUv5e offers a balance of performance, versatility, and cost-efficiency for a broader range of AI workloads.

---

## In-Depth Information

### Google's Tensor Processing Units (TPUs)

[[Tensor Processing Unit|Tensor Processing Units (TPUs)]] are Google's specialized hardware developed specifically for [[Machine Learning|ML]] tasks. Unlike general-purpose [[CPU|CPUs]] or even [[GPU|GPUs]] (which were originally for graphics), TPUs are tailored for the high volume of low-precision computations and tensor operations common in [[Deep Learning]].

### TPUv4

Announced around 2021, TPUv4 brought substantial performance improvements over TPUv3.

-   **Performance**: Delivers significantly higher performance per chip compared to TPUv3, with a peak of 275 TFLOPS (BF16 or INT8) per chip. Google reported that TPUv4 outperforms TPUv3 by an average of 2.1x on a per-chip basis and has a 2.7x improvement in performance per Watt.
-   **Architecture**: Each TPUv4 chip contains two TensorCores. Each TensorCore includes matrix-multiply units (MXUs), a vector unit, and a scalar unit. It also introduced third-generation SparseCores, dataflow processors that accelerate ML models reliant on embeddings.
-   **Memory**: Equipped with 32 GiB of High Bandwidth Memory (HBM) per chip.
-   **Interconnect & Scalability**: A key innovation in TPUv4 is the use of **Optical Circuit Switches (OCS)** for its inter-chip interconnect (ICI). This allows for dynamic reconfiguration of the network topology, connecting up to 4,096 chips in a pod with high bandwidth (1.1 ExaFLOPS peak compute per pod). The OCS technology improves scalability, availability, and performance, forming 3D mesh or 3D torus topologies.
-   **Cooling**: TPUv4 boards with four chips are liquid-cooled, a necessary step for managing the power density and enabling higher performance.
-   **Focus**: Primarily targets large-scale training for the most demanding AI models, such as large language models (LLMs) like PaLM.

> [!EXAMPLE] TPUv4 Pod
> A full TPUv4 Pod consists of 4,096 chips, capable of delivering over 1.1 exaflops of peak performance. The OCS enables these chips to be interconnected with a high degree of flexibility, optimizing for different workload requirements.

### TPUv5e

Announced in August 2023, TPUv5e is presented as a more cost-efficient and versatile successor, often referred to as "TPUv5 lite" or "efficiency" focused.

-   **Performance & Cost-Efficiency**: Designed to offer better performance per dollar compared to TPUv4. Google claims up to 2x higher training performance per dollar and up to 2.5x higher inference performance per dollar for LLMs and generative AI models compared to TPUv4. It provides 197 BF16 TFLOPS and 393 INT8 TOPS per chip.
-   **Architecture**: Each TPUv5e chip contains one TensorCore (unlike TPUv4's two per chip, and the unannounced full TPUv5 which is expected to have two). This TensorCore has four MXUs, a vector unit, and a scalar unit.
-   **Memory**: Comes with 16 GB of HBM2e memory per chip, with a bandwidth of 819.2 GB/s.
-   **Interconnect & Scalability**: TPUv5e pods can scale up to 256 chips. Unlike TPUv4, TPUv5e pods use a simpler, flat 2D Torus interconnect topology without OCS inside the pod, which contributes to its cost-efficiency. However, multiple TPUv5e pods can be connected over the datacenter spine network using Google's "Multislice" technology, enabling scaling to tens of thousands of chips for very large models. Each TPUv5e chip has an aggregate inter-chip interconnect (ICI) bandwidth of 1.6 Tbps (400 Gbps to four neighbors).
-   **Cooling**: TPUv5e is air-cooled, simplifying deployment and reducing costs compared to liquid-cooled systems. While not explicitly stated in all search results, the "e" for efficiency and focus on cost often aligns with air cooling for broader adoption.
-   **Focus**: Optimized for both cost-efficient training (especially for models less than ~200 billion parameters) and high-performance inference. It supports various virtual machine configurations, making it versatile for different model sizes.
-   **Availability**: More broadly available geographically compared to the initial rollout of TPUv4.

> [!TIP] TPUv5e Suffix
> The "e" in TPUv5e stands for "efficiency". This highlights its design goal of providing strong AI acceleration capabilities with a focus on better cost-effectiveness and power efficiency, making advanced AI more accessible.

### Key Differences Summarized (TPUv4 vs. TPUv5e)

| Feature             | TPUv4                                      | TPUv5e                                                |
| :------------------ | :----------------------------------------- | :---------------------------------------------------- |
| **Primary Focus**   | Peak performance, largest scale training   | Cost-efficiency, versatile training & inference     |
| **TensorCores/Chip**| 2                                          | 1                                                     |
| **Peak BF16 TFLOPs**| 275 per chip                           | 197 per chip                                      |
| **Peak INT8 TOPS**  | 275 per chip (assumed same as BF16)    | 393 per chip                                      |
| **HBM per Chip**    | 32 GiB                                 | 16 GB                                             |
| **Pod Size (Max)**  | 4,096 chips                            | 256 chips (per pod, can scale larger with Multislice) |
| **Interconnect**    | Optical Circuit Switch (OCS), 3D Torus/Mesh | 2D Torus (flat, no OCS in pod), ICI          |
| **Cooling**         | Liquid-cooled                         | Air-cooled (implied by efficiency focus)              |
| **Cost**            | Higher                                     | Lower (less than half the cost of TPUv4 per chip hour) |

### How They Are Used

-   **Training**: Both TPUv4 and TPUv5e are used for training AI models. TPUv4 is suited for the largest and most complex models, while TPUv5e offers a cost-effective solution for a wide range of training tasks, including fine-tuning.
-   **Inference**: TPUv5e is particularly highlighted for its inference capabilities, offering significant performance per dollar improvements. TPUv4 also has an inference-optimized variant (TPUv4i).
-   **[[Google Cloud Platform|Google Cloud Integration]]**: Both are available through Google Cloud, integrated with services like [[Google Kubernetes Engine|Google Kubernetes Engine (GKE)]] and [[Vertex AI]]. They support popular ML frameworks like [[TensorFlow]], [[PyTorch]], and [[JAX]].
-   **Large-Scale Systems**: Google employs "Multislice" technology, especially with TPUv5e, to allow scaling beyond single pod limits, enabling the training and serving of extremely large models by connecting tens of thousands of chips.

### Advancements and Future

-   Google continues to iterate on its TPU architecture, with TPUv5p (a more powerful version of the 5th gen) also announced, positioned as more powerful than TPUv5e and competitive with other high-end accelerators.
-   The recently announced Trillium (TPU v6) promises even greater performance leaps over TPUv5e.

> [!SUMMARY] In Summary
> TPUv4 and TPUv5e represent critical components in Google's AI hardware offerings. ==TPUv4 is a powerhouse designed for extreme-scale training, featuring advanced optical interconnects and high per-chip performance==. ==TPUv5e, on the other hand, emphasizes cost-efficiency and versatility, making it a strong contender for a broader range of AI training and inference workloads==, with significant improvements in performance per dollar over TPUv4. Both leverage Google's sophisticated system architecture and software stack to accelerate the development and deployment of state-of-the-art AI models.

---

**Sources:**

[^1]: SemiAnalysis. (2023-09-01). *TPUv5e: The New Benchmark in Cost-Efficient Inference and Training for*.
[^2]: Wikipedia. *Tensor Processing Unit*.
[^3]: The Next Platform. (2022-10-11). *Deep Dive On Google's Exascale TPUv4 AI Systems*.
[^4]: HPCwire. (2023-08-30). *Google TPU v5e AI Chip Debuts after Controversial Origins*.
[^5]: USENIX. (2024-04-18). *Resiliency at Scale: Managing Google's TPUv4 Machine Learning Supercomputer*.
[^6]: Google Cloud. *TPU v5e*.
[^7]: HPCwire. (2024-05-17). *Google Announces Sixth-generation AI Chip, a TPU Called Trillium*.
[^8]: Google Cloud Blog. (2023-12-06). *Introducing Cloud TPU v5p and AI Hypercomputer*.
[^9]: Google Cloud. *TPU v4*.
[^10]: Google Cloud Blog. (2023-09-12). *Performance per dollar of GPUs and TPUs for AI inference*.
[^11]: Glasp. (2024-06-03). *TPUv5e: The New Benchmark in Cost-Efficient Inference and Training for <200B Parameter Models*.
[^12]: The Futurum Group. (2023-08-30). *Google Cloud's TPU v5e Accelerates the AI Compute War*.
[^13]: TechInsights. *TPUv4 Adds Large On-Chip Memory*.
[^14]: ServeTheHome. (2023-08-29). *Google Details TPUv4 and its Crazy Optically Reconfigurable AI Network*.
[^15]: Google Cloud Blog. (2023-11-09). *Cloud TPU v5e is generally available*.
[^16]: louisbouchard.ai. (2023-04-11). *Introducing TPU v4: Googles Cutting Edge Supercomputer for Large Language Models*.
[^17]: The Register. (2023-08-29). *Details on Google's AI updates to cloud infrastructure*.
[^18]: Economize Cloud. (2024-10-07). *GKE Enterprise, TPU v5e & A3 VMs: What you need to know?*
[^19]: GitHub Pages. (2025-02-04). *How to Think About TPUs | How To Scale Your Model*.
[^20]: FS Community. (2024-09-25). *What is Tensor Processing Unit (TPU)*.
[^21]: DataCamp. (2024-05-30). *Understanding TPUs vs GPUs in AI: A Comprehensive Guide*.
[^22]: Medium. (2024-08-07). *So what is a Tensor processing unit (TPU) and why will it be the future of Machine Learning?*
[^23]: ActuIA. (2021-05-19). *Google I/O: fourth generation TPU announced and exaflopian pods launched*.
[^24]: arXiv. *exploring tpus for ai applications*.
[^25]: Techovedas. (2024-08-08). *How has Google's TPUs Evolved in AI Acceleration over 10 years*.
[^26]: cs.princeton.edu - People. *TPU v4: An Optically Reconfigurable Supercomputer for Machine Learning with Hardware Support for Embeddings*.
[^27]: Google Cloud. *TPU architecture*.
[^28]: TechPowerUp. (2023-09-01). *Google Introduces Cloud TPU v5e and Announces A3 Instance Availability*.
[^29]: GIGAZINE. (2023-08-30). *Google announces the 5th generation model 'TPU v5e' of the AI specialized processor TPU...*
[^30]: Glasp. (2024-06-03). *TPUv5e: The New Benchmark in Cost-Efficient Inference and Training for <200B Parameter Models*. (Duplicate of, specific reference to HBM2e and bandwidth).
[^31]: Google Cloud Blog. (2023-04-05). *TPU v4 enables performance, energy and CO2e efficiency gains*.
[^32]: Times of India. (2023-08-30). *Google launches AI chip to handle faster training performance of LLMs*.

---