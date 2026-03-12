# GPT From Scratch (Arabic)

## Project Overview

This project implements a GPT-style language model completely from scratch using PyTorch. The goal is to demonstrate the full lifecycle of a large language model, including tokenization, pretraining, supervised fine-tuning, and evaluation.

The model was trained on Arabic text and later fine-tuned on an instruction-following dataset.

---

## Model Architecture

Decoder-only Transformer (GPT style)

The following components were implemented from scratch:

- Byte Pair Encoding (BPE) tokenizer
- Multi-head self-attention
- Feed-forward layers
- Layer normalization
- Residual connections
- Training loop
- Text generation

Model configuration:

- Vocabulary size: 5000
- Context length: 128
- Embedding dimension: 256
- Attention heads: 4
- Transformer layers: 4
- Total parameters: ~5.7M

---

## Dataset

### Pretraining Data

Arabic corpus text.

- Size: ~1.1M characters
- Lines: 7803
- Format: UTF-8 text

The goal of pretraining was **next-token prediction**.

---

### Fine-Tuning Data

200 instruction-response pairs.

Instruction categories include:

- Question answering
- Paraphrasing
- Short creative writing

Example format:

Instruction:
اكتب فقرة قصيرة عن القمر

Response:
القمر يضيء السماء ليلاً ويمنحها جمالاً خاصاً. ينظر إليه الناس بإعجاب وهدوء. وهو من أجمل المشاهد في الليل.

---

## Training

### Pretraining

The model was trained using a next-token prediction objective with cross-entropy loss.

---

### Fine-Tuning

The pretrained model was fine-tuned on an instruction dataset using the following prompt format:

### Instruction
...

### Input
...

### Response
...

This allowed the model to learn basic instruction-following behavior.

---

## Evaluation

| Metric | Pretrained | Fine-tuned |
|------|------|------|
| Test Loss | 7.49 | 3.35 |
| Perplexity | 1803 | 28 |

Fine-tuning significantly improved model performance and instruction-following ability.

---

## Limitations

Due to the small dataset and model size, several limitations remain:

- Subword token fragmentation in Arabic
- Occasional repetition in generated text
- Limited coherence for long responses
- Weak instruction understanding in some cases

These limitations are expected for a small experimental model.

---

## Future Improvements

Possible improvements include:

- Larger pretraining dataset
- Better Arabic tokenizer
- Larger transformer model
- More diverse instruction data
- Sampling-based decoding methods

---

## Technologies Used

- Python
- PyTorch
- HuggingFace Tokenizers
- Google Colab

---

## Author

Mariam Alfayez
