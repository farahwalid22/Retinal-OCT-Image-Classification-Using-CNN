# Retinal-OCT-Image-Classification-Using-CNN
This project presents a deep learning solution for automatic classification of retinal diseases from OCT (Optical Coherence Tomography) images.

---

##  Overview

We utilize a dataset of 66,788 retinal OCT images categorized into four classes:
- CNV (Choroidal Neovascularization)
- DME (Diabetic Macular Edema)
- Drusen
- Normal

**Our goal** is to build a robust CNN-based model to aid ophthalmologists in early and accurate diagnosis of retinal diseases.

---

## Dataset

The dataset is sourced from publicly available OCT scans:
- 66,788 images
- Varying resolutions (128x128 to 192x192)
- Class labels assigned automatically or through image folders

---

## Preprocessing

Two preprocessing strategies were applied:

### Basic Pipeline (Model 1)
- Shuffle image paths
- Label retrieval
- Resize images to (192, 192)
- Batch (64), Prefetch, and Create Datasets

### Enhanced Pipeline (Models 2-5)
- Automatic label assignment
- Standardization
- Class weight calculation
- Optimized data loading (caching)
- Efficient dataset creation

### GAN Trial:
Used resolution enhancement techniques to improve the consistency and quality of input images.

---

## Models Summary

| Model | Layers & Features | Loss | Val Loss | Acc | Val Acc |
|-------|-------------------|------|----------|-----|---------|
| M1 | 3 Conv2D + 2 MaxPool, Dense(128) | — | — | 99% | 90% |
| M2 | 2 Conv2D + 2 MaxPool, Dense(256) | 0.011 | 0.5 | 99% | 90% |
| M3 | 4 Conv2D, 2 MaxPool, BN, Dropout, padding | 0.361 | 0.154 | 98.9% | 94.9% |
| M4 | 5 Conv2D, 4 MaxPool, 3 BN, 2 Dropout (0.2–0.5) | 0.027 | 0.179 | 98.97% | 95.66% |
| M5 | 4 Conv2D, 2 MaxPool, 3 BN, 2 Dropout (0.2–0.5) | 0.062 | 0.240 | — | — |

---

## Best Performing Model
**Model 4** achieved:
- 🟢 Training Accuracy: 98.97%
- 🟢 Validation Accuracy: 95.66%
- ✅ Balanced performance due to use of dropout, batch normalization, and optimized architecture

---

## Future Work
- Try EfficientNet and ResNet pretrained models
- Apply Explainable AI (e.g., Grad-CAM)
- Extend to multi-disease multi-label classification
- Build a web app for clinical integration

---

## 🚀 Kaggle Notebook
[Retinal OCT Image Classification Using CNN](https://www.kaggle.com/code/farahwalidelsayed/retina-scan-using-deep-learning)
