# MedVQA-VLM-CNN-Lstm

This repository implements and compares two approaches for **Medical Visual Question Answering (MedVQA)** on the **VQA-RAD** dataset:

- **Method 1 (Baseline)**: CNN (ResNet-18) + LSTM (classification)
- **Method 2 (VLM)**: BLIP-2 + LoRA (generative)

## Dataset
We use **VQA-RAD** (Visual Question Answering in Radiology).
- Dataset instructions: see [`Data/DATASET.md`](Data/DATASET.md)
- Note: the raw image folder is NOT uploaded to GitHub.

## Repository Structure
```bash
├─ Data/
│ └─ DATASET.md
├─ notebooks/
│ ├─ 01_data_split_and_eda.ipynb
│ ├─ 02_baseline_cnn_lstm.ipynb
│ └─ 03_blip2_lora.ipynb
├─ Model output/
│ └─ (predictions / figures / logs)
├─ requirements.txt
└─ README.md
## Methods
### Method 1: CNN + LSTM (Baseline)
- Image encoder: ResNet-18 (pretrained)
- Text encoder: Embedding + LSTM
- Fusion: concatenate image feature and text feature
- Output: classification over answer vocabulary
```
### Method 2: BLIP-2 + LoRA (VLM)
- Base model: `Salesforce/blip2-opt-2.7b`
- Fine-tuning: LoRA on attention projection layers (q_proj, v_proj)
- Training tricks: fp16, small batch + gradient accumulation
- Output: generated text answers

## Results (Test Set)
| Method | Overall Acc | Closed-ended Acc | Open-ended Acc |
|---|---:|---:|---:|
| CNN+LSTM | 37.03% | 58.46% | 4.47% |
| BLIP-2 + LoRA | 50.33% | 68.01% | 23.46% |

Additional metric:
- Clean BLEU-1 (Open-ended, BLIP-2+LoRA): **0.0842**

## How to Run
1. Prepare dataset following [`Data/DATASET.md`](Data/DATASET.md)
2. Install dependencies:
```bash
pip install -r requirements.txt
```

