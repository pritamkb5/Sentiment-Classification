# 🎬 IMDb Sentiment Classification using Deep Learning (RNN, LSTM, Bi-LSTM, GRU)

> A deep learning–based NLP system that classifies IMDb movie reviews as **positive** or **negative** using four recurrent neural network architectures — with GRU achieving the best test accuracy of **88.54%**.

---

## 📌 Project Overview

- Built a binary sentiment classifier trained on the **IMDb dataset** (50,000 labeled movie reviews)
- Compared four RNN-based architectures: Simple RNN, LSTM, Bidirectional LSTM, and GRU
- Selected **GRU** as the final model based on superior accuracy and computational efficiency

---

## 📂 Dataset

- **Total Reviews:** 50,000
  - ✅ 25,000 Positive
  - ❌ 25,000 Negative
- **Label Encoding:** Positive → `1` | Negative → `0`
- **Split Strategy:** Stratified sampling into Train / Validation / Test sets to maintain balanced class distribution

---

## 🔧 Text Preprocessing

- Converted all text to **lowercase**
- Removed **HTML tags** (common in raw IMDb reviews)
- Removed **special characters and punctuation**
- Preserved **sentiment-critical negation words** (`not`, `never`, `no`)
- Normalized extra **whitespace**

---

## 🔢 Tokenization & Sequence Preparation

- Tokenized cleaned reviews using **Keras Tokenizer**
- Built a vocabulary of the **10,000 most frequent words**
- Converted reviews to **integer sequences**
- Analyzed sequence-length distribution to determine optimal input size
- Applied **sequence padding** to a fixed length of **200 tokens** for uniform input across all models

---

## 🧠 Embedding Layer

- Used an **Embedding layer** to represent each token as a **128-dimensional dense vector**
- Enables the model to learn **semantic relationships** between words during training

---

## 🏗️ Model Architectures

Four recurrent architectures were implemented and compared:

| # | Model | Description |
|---|-------|-------------|
| 1 | **Simple RNN** | Baseline model; suffers from vanishing gradient on long sequences |
| 2 | **LSTM** | Captures long-term dependencies using memory gates |
| 3 | **Bidirectional LSTM** | Processes sequences in both forward and backward directions |
| 4 | **GRU** | Lightweight, efficient alternative to LSTM with fewer parameters |

---

## ⚙️ Regularization & Hyperparameter Tuning

- **Dropout regularization** (rate = 0.5) applied to reduce overfitting
- Hyperparameter experiments conducted across:
  - Number of recurrent layers: `1`, `2`, `3`
  - Hidden units: `64`, `128`, `256`
  - Dropout rates: `0.3`, `0.5`, `0.7`

---

## 🏋️ Training Configuration

- **Optimizer:** Adam
- **Loss Function:** Binary Cross-Entropy
- **Batch Size:** 64
- **Max Epochs:** 10
- **Early Stopping:** Monitors validation loss and restores best weights automatically

---

## 📊 Model Performance Comparison

| Model | Test Accuracy | Training Time | Parameters |
|-------|:---:|:---:|:---:|
| Simple RNN | 51.47% | 11.05 min | 1,292,417 |
| LSTM | 87.63% | 66.03 min | 1,461,057 |
| Bidirectional LSTM | 84.17% | 22.03 min | 1,420,097 |
| **GRU** ⭐ | **88.54%** | **47.41 min** | **1,416,385** |

---

## 🔍 Key Observations

- **Simple RNN** suffered from **vanishing gradient** issues and failed to capture long-range dependencies, resulting in near-random accuracy (~51%)
- **LSTM** significantly improved performance by retaining contextual information across long sequences
- **Bidirectional LSTM** leveraged both past and future context but incurred a higher computational cost relative to its accuracy gain
- **GRU** achieved the **highest test accuracy (88.54%)** with fewer parameters and faster convergence than LSTM — making it the most efficient and effective model

---

## ✅ Final Model: GRU

- Selected as the final classifier based on **superior accuracy** and **computational efficiency**
- Validated on **custom reviews** with confidence scores for both positive and negative sentiment predictions

---

## 🛠️ Tech Stack

- Python
- TensorFlow / Keras
- NumPy, Pandas
- Matplotlib / Seaborn (for learning curves and analysis)
