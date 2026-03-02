# microGPT – Tiny Shakespeare (Colab Implementation)

A minimal, educational implementation of a GPT-style Transformer trained on the Tiny Shakespeare dataset.

This project was implemented and trained entirely in **Google Colab** using pure Python (no deep learning frameworks like PyTorch or TensorFlow).

---

## 📌 Project Overview

This project builds a GPT-style language model completely from scratch, including:

- Manual autograd engine
- Transformer architecture
- Multi-head self-attention
- RMSNorm
- MLP feed-forward layers
- Adam optimizer
- Character-level tokenizer

The goal is to understand **what actually happens when a GPT model trains and generates text**.

---

## 📂 Dataset – Tiny Shakespeare

The model is trained on the Tiny Shakespeare dataset, a compact corpus commonly used for character-level language modeling.

Dataset Properties:

- Plain text format
- Character-level tokens
- Next-character prediction objective
- Small enough for CPU training

---

## 🧠 Model Architecture

Configuration:

- Embedding dimension: 16  
- Number of attention heads: 4  
- Number of transformer layers: 1  
- Block size (context length): 16  
- Vocabulary: Character-level + BOS token  

---

### Transformer Components

1️⃣ Token Embeddings  
Each character is mapped to a learned vector representation.

2️⃣ Position Embeddings  
Encodes token position within the sequence.

3️⃣ Multi-Head Self-Attention  
Implements scaled dot-product attention:
- Query (Q)
- Key (K)
- Value (V)
- KV cache for sequential token processing

4️⃣ RMSNorm  
Used instead of LayerNorm for normalization.

5️⃣ MLP Block  
Two-layer feed-forward network:
- Expansion (4× embedding size)
- ReLU activation
- Projection back to embedding size

6️⃣ Residual Connections  
Improves gradient flow and training stability.

---

## 🔁 Training Objective

The model is trained using next-token prediction:

Loss = -log(P(target_token))

Cross-entropy loss averaged across sequence length.

---

## ⚙️ Optimizer

Adam optimizer implemented manually with:

- Learning rate decay
- First moment (m) buffer
- Second moment (v) buffer
- Bias correction
- Manual gradient reset

---

## 🔄 Training Process

Each training step:

1. Select a text sequence
2. Add BOS tokens
3. Forward pass through transformer
4. Compute softmax probabilities
5. Compute loss
6. Backpropagate gradients
7. Update parameters using Adam

---

## 📊 Model Size

Total Parameters: 4,192

This is intentionally small for educational clarity.

---

## 🚀 Text Generation

After training, the model generates text by:

1. Starting from BOS token
2. Sampling from output probability distribution
3. Feeding generated token back into model
4. Repeating until stopping condition

Generation is probabilistic (softmax sampling).

---

## 🧪 Running in Google Colab

Steps:

1. Upload the Tiny Shakespeare dataset as `input.txt`
2. Run all notebook cells sequentially
3. Monitor training loss
4. Execute generation cell to sample text

No external dependencies required.

---

## 🎯 Learning Outcomes

This project demonstrates:

- How Transformers work internally
- How attention is computed mathematically
- How backpropagation works
- How autograd engines operate
- How GPT models generate text

---

## 🏁 Conclusion

This microGPT implementation shows that GPT models are structured combinations of:

- Linear algebra
- Attention mechanisms
- Gradient-based optimization

It provides a complete educational walkthrough of building a Transformer from scratch in Google Colab.

---
