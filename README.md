# Artificial Neural Networks and Deep Learning (A.Y. 2025-2026)

This repository collects the work carried out during the **Artificial Neural Networks and Deep Learning** course at Politecnico di Milano, organised by AIRLab.

## About the course

The course provides a broad introduction to neural networks (NNs), ranging from traditional feedforward (FFNNs) and recurrent (RNNs) networks to the most successful deep learning models, such as convolutional neural networks (CNNs) and long short-term memory (LSTM) networks. Application areas include time series modeling, gene expression modeling, and image recognition.

## Projects

The course hands-on component consisted of two challenges. Both were evaluated with the **F1-Score** on a Kaggle leaderboard, and both required a final report and fully reproducible notebooks.

| # | Challenge | Task | Data | Metric |
|---|-----------|------|------|--------|
| 1 | Time Series Classification | Sequence classification | Multivariate time series | F1-Score |
| 2 | Image Classification 2.0 | Image classification | Histopathology images (WSI) | F1-Score |

---

### Challenge 1 — Time Series Classification

**Competition:** AN2DL 2025-2026: Time Series Classification

**Task.** Given a collection of multivariate time series (661 samples, 160 time steps each, with pain survey scores, body-part counts and joint angles as input channels), assign each entire sequence to one of three classes: `no_pain`, `low_pain` or `high_pain`. The classes are heavily unbalanced (77% / 14% / 9%).

**Our approach.** An ensemble of bidirectional GRU networks with an attention layer, trained on sliding windows with focal loss to handle class imbalance. Hyperparameters were tuned with cross-validation, and the predictions of the best models were combined with soft voting.

**Resources.**
- 📄 Report: [Report_Challenge1_TigerTensors.pdf](challenge1-time-series/Report_Challenge1_TigerTensors.pdf)
- 📓 Notebook: [Challenge_KFoldAttention_WellCommented.ipynb](challenge1-time-series/Challenge_KFoldAttention_WellCommented.ipynb)


---

### Challenge 2 — Image Classification 2.0

**Competition:** AN2DL 2025-2026: Image Classification 2.0

**Task.** Given a collection of images, each coming from a low-magnification whole-slide image (WSI) of human tissue and paired with a binary mask indicating the most likely diseased regions, assign each image to one of four classes corresponding to molecular subtypes: `Luminal A`, `Luminal B`, `HER2(+)` and `Triple Negative`. The dataset is small, has different image sizes, a class imbalance on Triple Negative, and contains meaningless and noisy samples.

**Our approach.** A dual-path network: a ConvNeXt-Tiny backbone processes the RGB patches while a small auxiliary CNN processes the corresponding mask patches. Patch features are fused and aggregated with attention-based Multiple Instance Learning, and the final predictions are combined with soft voting.

**Resources.**
- 📄 Report: [Report_Challenge2_TigerTensor.pdf](challenge2-image-classification/Report_Challenge2_TigerTensor.pdf)
- 📓 Main Notebook: [traininingOptuna_toEvaluate.ipynb](challenge2-image-classification/traininingOptuna_toEvaluate.ipynb)

---

## Repository structure

```
.
├── challenge1-time-series/
│   ├── outlierDetection_toEvaluate.ipynb (to find outliers)
│   ├── visualizePatches_toEvaluate.ipynb (to visualize the augmentation)
│   ├── traininingOptuna_toEvaluate.ipynb (the model trained file)
│   └── report.pdf
├── challenge2-image-classification/
│   ├── Challenge_KFoldAttention_WellCommented.ipynb
│   └── report.pdf
└── README.md
```
## Tools and technologies

- Python
- Pytorch
- NumPy, Pandas, scikit-learn
- Matplotlib
- Kaggle / Google Colab (GPU)


