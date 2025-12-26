# 🤖 AI-Research-Study-2026
> **Paper Study: [Attention Is All You Need]**

## 1. The Macro Structure: Stacks of $N=6$ Layers
* **Architecture:** The model consists of an **Encoder stack** and a **Decoder stack**, each containing 6 identical layers ($N=6$).
* **Flow:** * The **Encoder** processes the input sequence as a whole to extract deep contextual meanings.
  * The **Decoder** generates the output sequence one token at a time, referencing the Encoder's final output at every layer.
* **Analogy:** Building a 6-story building where each floor refines the information more abstractly and precisely.

---

## 2. The Encoder: The Deep Contextualizer
* **Goal:** To convert raw input into "context-rich vectors."
* **Sub-layers:**
  1. **Multi-Head Self-Attention:** Understands relationships between all words in the input sentence.
  2. **Feed-Forward Network (FFN):** Acts as a "vector refiner." It expands the dimension ($512 \rightarrow 2048$) to capture intricate features and then compresses it back.
* **Mechanism:** Uses **Residual Connections** ($x + \text{Sublayer}(x)$) and **Layer Normalization** to prevent information loss and stabilize training.

---

## 3. The Decoder: The Masked Generator
* **Goal:** To predict the next token based on previous outputs and encoder "hints."
* **Key Components:**
  1. **Masked Self-Attention:** Prevents "cheating" by masking future tokens ($-\infty$ in the score matrix). It ensures the model only looks at the past.
  2. **Encoder-Decoder Attention:** The "bridge." The Decoder (Query) asks the Encoder (Key, Value) for relevant information to determine the next word.
* **Input Shift:** Uses "Offset by one" (Teacher Forcing) to align inputs and targets during training.

---

## 4. The Core Objective: Finding Optimal Weights
* **Training Process:** 1. **Parallelism:** Feed the entire sequence at once.
  2. **Masking:** Mask future tokens to simulate real-world generation.
  3. **Loss:** Calculate the difference between the predicted token and the ground truth.
  4. **Optimization:** Use **Backpropagation** to adjust millions of weights.
* **Ultimate Goal:** Finding the **optimal weight matrices ($W^Q, W^K, W^V$, etc.)** that represent the universal patterns of language and context.

---

### 💡 Jun-hyeok's Insight
> *"Attention gathers the raw ingredients (relationships), and the Feed-Forward layer cooks them into a refined, unambiguous context. The entire process is a high-dimensional optimization problem to find the best weights."*
