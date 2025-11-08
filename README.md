# 🧠 Image Caption Generator

An end-to-end multimodal deep learning project that automatically generates natural-language captions for images by combining **Computer Vision** and **Natural Language Processing**.  
Author: **Amir Khosravi** 

---

## 🌍 Overview

This project trains a neural network to *see* an image and *describe* it in words.  
It integrates a **CNN encoder** (for visual understanding) with an **LSTM decoder** (for language generation).

- **Encoder:** A pretrained `ResNet-50` extracts visual features from images.  
- **Decoder:** A multi-layer LSTM generates textual captions token by token.  
- **Dataset:** > **Dataset:** [Flickr8k](https://github.com/jbrownlee/Datasets/releases) — a public dataset of 8,000 images, each paired with five human-written captions.
> The dataset used in this project was obtained from the official [jbrownlee/Datasets](https://github.com/jbrownlee/Datasets/releases) repository, which provides ready-to-download research datasets in ZIP format.  
- **Evaluation:** BLEU-n scores computed using `torcheval.metrics.BLEUScore`.

---

## ✨ Key Features

| Capability | Description |
|-------------|-------------|
| 🧠 **CNN + LSTM Architecture** | Combines visual and textual modalities in a unified encoder–decoder pipeline. |
| 🗂️ **Custom PyTorch Dataset** | Handles image–caption pairs, tokenization, vocabulary building, and batching. |
| ⚙️ **Training Framework** | Includes gradient clipping, checkpoint saving, and validation loops. |
| 📊 **Metrics & Visualization** | Tracks loss curves and BLEU scores, prints target vs. generated captions. |
| 💾 **Reproducibility** | Controlled random seeds and modular functions for repeatable experiments. |

---

## 🗃️ Dataset Workflow

1. **Download & unzip** Flickr8k images and captions.  
2. **Tokenize captions** with `torchtext`’s basic English tokenizer.  
3. **Build vocabulary** with special tokens (`<pad>`, `<unk>`, `<sos>`, `<eos>`).  
4. **Convert captions** to tensors and align with image files.  
5. **Split** data into train / validation / test sets.  
6. **Batch** data with a custom `collate_fn` that pads sequences correctly.

---

## 🧠 Technical Highlights

* **Frameworks:** PyTorch, TorchText, TorchVision
* **Architecture:** ResNet-50 encoder + multi-layer LSTM decoder
* **Loss Function:** Cross-Entropy (ignoring `<pad>` tokens)
* **Optimizer:** SGD with momentum and weight decay
* **Training Stability:** Gradient clipping (`max_norm = 0.25`)
* **Evaluation Metric:** BLEU-n (1–4) via `torcheval.metrics.BLEUScore`
* **Visualization:** Matplotlib loss curves and qualitative caption examples

---

## 🔮 Future Work & Roadmap

The next development goals are realistic extensions that build on the current implementation:

### 🧩 1. Model Improvements

* Replace the LSTM decoder with a **Transformer-based** text generator.
* Add **attention mechanisms** for more context-aware captioning.
* Explore **Vision Transformer (ViT)** or hybrid encoder–decoder architectures.

### ⚙️ 2. Training Enhancements

* Implement **beam search** for more fluent sentence generation.
* Add **scheduled sampling** to reduce exposure bias.
* Evaluate additional metrics (CIDEr, METEOR, ROUGE-L).

### 🗄️ 3. Dataset Scaling

* Extend experiments to **MS COCO** and **Flickr30k** datasets.
* Support multilingual caption generation (e.g., English + Italian).

### 🌐 4. Deployment Plans

* Build a **FastAPI** or **Flask** backend for inference.
* Add a **Streamlit / Gradio / React**-based frontend for interactive demos.
* Host the model and UI on **Hugging Face Spaces** for public access.

These upgrades will gradually turn this into a complete applied AI project — from training to online deployment.

