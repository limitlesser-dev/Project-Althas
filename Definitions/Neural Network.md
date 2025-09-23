---
tags:
  - AI
  - MachineLearning
  - DeepLearning
  - NeuralNetwork
  - ANN
  - CoreConcept
aliases: [ANN, Artificial Neural Network, Neural Net]
---

# Neural Network

## Core Concept

A **Neural Network** (often called an **Artificial Neural Network** or **ANN**) is a type of computing system broadly inspired by the interconnected structure of neurons in a biological brain. Its main purpose is to enable computers to **==learn complex patterns directly from data==** (like [[Image|images]], [[Audio|sounds]], [[Text]], or numerical information) without needing explicitly programmed rules for every situation. It achieves this using layers of connected processing units ('[[Neuron (Artificial)|neurons]]') that pass signals to each other. The strength ('[[Weight (AI)|weight]]') of these connections is automatically adjusted based on many examples during a '[[Training (AI)|training]]' process, allowing the network to progressively get better at tasks like [[Classification]], [[Regression|prediction]], or generation (e.g., creating text).

> [!quote] In Essence
> Neural Networks are computational models, inspired by the brain, that ==learn from data by adjusting connections== between simple processing units, enabling them to recognize patterns and solve complex problems.

---

## In-Depth Information

### The Brain Inspiration (Analogy Revisited)

> [!TIP] Brain Analogy
> While not a literal biological replica, the core idea comes from how biological neurons connect and strengthen connections ([[Synapse|synapses]]) when learning. ANNs are mathematical models that capture this concept of interconnected units learning by adjusting connection strengths.

### The Building Blocks

1.  **[[Neuron (Artificial)|Neurons]] (or Nodes):** The fundamental computational units. Each neuron:
    *   Receives input signals from other neurons or the initial data.
    *   Combines these inputs (usually a weighted sum).
    *   Applies an **[[Activation Function]]** (a simple mathematical rule, often non-linear) to determine its output signal.
    *   Sends this output signal to other neurons in the next layer.
2.  **Connections (or Edges):** These are the pathways linking neurons. They transmit signals from one neuron to the next.
3.  **[[Weight (AI)|Weights]]:** Every connection has an associated weight. This number represents the ==_strength_ and _sign_== (excitatory or inhibitory) of the connection. A higher absolute weight means the signal has more influence. **==Learning in a neural network primarily involves finding the right set of weights.==**
4.  **Layers:** Neurons are typically organized into distinct layers:
    *   **[[Input Layer]]**: Receives the raw data fed into the network (e.g., pixels of an [[Image]], [[Token|tokens]] in a sentence). No computation happens here; it just passes the data along.
    *   **[[Hidden Layer|Hidden Layer(s)]]**: One or more layers situated between the input and output layers. This is where most of the complex pattern recognition and feature extraction happens. Neurons here transform the data based on the learned weights and activation functions. Networks with many hidden layers are called "[[Deep Neural Network|Deep Neural Networks]]", forming the basis of **[[Deep Learning]]**.
    *   **[[Output Layer]]**: Produces the final result of the network's computation (e.g., the probability that an image contains a cat, the predicted numerical value, the next word in a sequence). The structure and activation functions here depend heavily on the specific task ([[Classification]], [[Regression]], etc.).

### How Information Flows ([[Forward Pass]])

When the network makes a prediction:

1.  Data is fed into the [[Input Layer]].
2.  Signals propagate forward through the connections, layer by layer.
3.  Each neuron in a [[Hidden Layer]] or the [[Output Layer]] calculates its output based on the weighted inputs from the previous layer and its [[Activation Function]].
4.  This process continues until the [[Output Layer]] computes the final prediction.

### How It Learns ([[Training (AI)|Training]] / [[Backpropagation]])

Neural networks typically learn from labeled examples ([[Supervised Learning]]):

1.  **Prediction:** The network processes an input example and makes a prediction (==[[Forward Pass]]==).
2.  **Error Calculation:** The prediction is compared to the known correct answer (the 'label'). A **[[Loss Function]]** quantifies how inaccurate the prediction was (the 'error' or 'loss').
3.  **Weight Adjustment ([[Backpropagation]]):** The network calculates how much each [[Weight (AI)|weight]] contributed to the overall error (using calculus, specifically the chain rule). It then uses an **[[Optimizer (AI)|Optimizer]]** algorithm (like [[Stochastic Gradient Descent|SGD]] or [[Adam Optimizer|Adam]], often managed by [[AI Frameworks]]) to adjust the weights slightly in a direction that will reduce the error for that example. This backward flow of error information and subsequent weight update is called ==**backpropagation**==.
4.  **Iteration:** Steps 1-3 are repeated for thousands or millions of examples in the training dataset, often multiple times (**[[Epoch]]s**). With each iteration, the network's weights are gradually fine-tuned, making its predictions progressively more accurate on the training data. (Requires subsequent evaluation on unseen test data to check for generalization).

### What Are They Good At? (Applications)

Their ability to learn complex, non-linear patterns makes them powerful for:

*   [[Image Recognition]] & [[Computer Vision]] (Object Detection, Segmentation)
*   [[Natural Language Processing|NLP]] ([[Machine Translation]], [[Sentiment Analysis]], [[Text Generation]])
*   [[Speech Recognition]] and [[Text-to-Speech|Speech Synthesis]]
*   [[Recommendation Systems]]
*   Medical Image Analysis
*   Financial Modeling & [[Time Series Forecasting]]
*   [[Autonomous Driving]] Systems
*   Playing Complex Games ([[Reinforcement Learning]])

### Common Types (Architectures)

Different problems benefit from different network structures:

*   **[[Feedforward Neural Network|Feedforward Neural Networks (FNNs)]]:** Simplest type, information flows only forward from input to output. Includes Multilayer Perceptrons (MLPs).
*   **[[Convolutional Neural Network|Convolutional Neural Networks (CNNs)]]:** Specialized for grid-like data (like [[Image|images]]), using 'convolution' operations to detect spatial hierarchies of features.
*   **[[Recurrent Neural Network|Recurrent Neural Networks (RNNs)]]:** Designed for sequential data ([[Text]], [[Time Series]]) by having connections that form cycles, giving them a form of 'memory'. [[LSTM]] (Long Short-Term Memory) and [[GRU]] (Gated Recurrent Unit) are advanced variants designed to handle long-range dependencies better.
*   **[[Transformer Models|Transformers]]:** A more recent architecture excelling particularly in [[NLP]] (and increasingly vision), using '[[Attention Mechanisms|attention mechanisms]]' to weigh the importance of different parts of the input sequence, allowing for better handling of long-range dependencies and parallel processing.

> [!SUMMARY] In Summary
> Neural Networks are powerful function approximators that learn from data. By adjusting the ==weights== between interconnected ==neurons== organized in ==layers==, using processes like ==backpropagation== driven by a ==loss function==, they can model complex relationships and solve problems in diverse fields like vision, language, and prediction. [[Deep Learning]] involves using neural networks with many hidden layers.