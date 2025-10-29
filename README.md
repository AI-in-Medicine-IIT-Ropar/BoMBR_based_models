# BoMBR_based_models
### Code for the paper: *BoMBR: Bone Marrow Biopsy Dataset for Segmentation of Reticulin Fibers*

This repository contains the official code accompanying the paper **“BoMBR: Bone Marrow Biopsy Dataset for Segmentation of Reticulin Fibers”**, published in the *Medical Imaging with Deep Learning for Biomedical Applications (MELBA) Journal*, Volume 3, Special Issue: MICCAI Open Data (2025).

The repository provides scripts to train and perform inference on both the **segmentation** and **classification** models described in the paper. Together, these models form a pipeline for analyzing bone marrow biopsy (BMB) images for fibrosis grading.

---
🧬 Repository Overview
```text
BoMBR_based_models/
│
├── Classification-Model/
│   ├── classification_model_architecture_and_training.ipynb   # Training notebook for fibrosis grade classification
│   └── publish.csv                                            # Metadata file (fibrosis grade, hemorrhage presence)
│
├── Segmentation-Model/
│   └── Xception_512_model_training.ipynb                      # Training script for segmentation model
│
├── inference_on_both_models.ipynb                             # Combined inference pipeline (segmentation → classification)
└── README.md
