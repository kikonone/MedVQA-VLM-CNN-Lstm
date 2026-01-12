# Dataset (VQA-RAD)

This project uses the **VQA-RAD** dataset (Visual Question Answering in Radiology), which contains radiology images paired with clinician-generated questions and answers.

## Source
- Kaggle: https://www.kaggle.com/datasets/shashankshekhar1205/vqa-rad-visual-question-answering-radiology
- Original paper: Lau et al., Scientific Data (2018)

## What to download
After downloading from Kaggle, unzip it locally / in Google Drive. You should have:
- `VQA_RAD Dataset Public.json`
- `VQA_RAD Image Folder/` (all images)


## How to set the path (Colab)
In the notebooks, set:
```python
DATA_ROOT = "/content/drive/MyDrive/Colab Notebooks/archive"

