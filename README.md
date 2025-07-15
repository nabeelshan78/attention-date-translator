# 🧠 Attention-Based Date Format Translator

This repository implements a custom sequence-to-sequence model with an attention mechanism to **translate natural language date formats** (e.g., `"21st of August 2016"`) into machine-readable formats (e.g., `"2016-08-21"`). The model is built from scratch using **TensorFlow/Keras**, and includes a **custom attention layer**, a **Bi-LSTM encoder**, and an **LSTM decoder**.

---

## Project Structure
```
attention-date-translator/
│
├── notebook.ipynb # Main Jupyter notebook (training + inference)
├── models/
│ └── model.h5 # Saved trained model
├── data/
│ ├── dataset.pkl # Serialized dataset
│ ├── human_vocab.json # Input vocabulary (character-level)
│ ├── machine_vocab.json # Output vocabulary
│ └── inv_machine_vocab.json # Inverse output vocab (for decoding)
├── images/
│ ├── attn_mechanism.png # Attention mechanism diagram
│ └── attn_model.png 
└── README.md
```

---

## Model Overview

- **Input**: `"3rd of March 2023"`
- **Output**: `"2023-03-03"`
- **Architecture**:
  - Bi-LSTM encoder
  - Custom-built attention mechanism
  - LSTM decoder
  - Dense output layer with softmax
- **Training**: Character-level, multi-class classification at each output time step

---

## 🧠 How Attention Works

<p align="center">
  <img src="images/attn_mechanism.png" width="500"/>
</p>

Each decoder step **attends** over all encoder hidden states to produce a context vector that helps predict the correct output character.

---

## Sample Predictions

```python
Input:    "21st of August 2016"
Predicted Output: "2016-08-21"

Input:    "Tuesday May 5 2009"
Predicted Output: "2009-05-05"

Input:    "1 March 2001"
Predicted Output: "2001-03-01"
```
---

## Dataset
Generated synthetically using the faker and babel libraries.

Human-readable dates are randomly created in various formats.

Output format is consistent: YYYY-MM-DD.
