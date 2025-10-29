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
│   └── publish.csv                                            # Metadata file (image name, mf-grade, hemorrhage presence)
│
├── Segmentation-Model/
│   └── Xception_512_model_training.ipynb                      # Training script for segmentation model
│
├── inference_on_both_models.ipynb                             # Combined inference pipeline (segmentation → classification)
└── README.md

```
---

##  Description

###  Segmentation Model
- Implements a **U-Net-like architecture** with an **Xception** backbone pretrained on ImageNet.  
- Designed to segment **reticulin fibers** in bone marrow biopsy images.  
- The segmentation model output is an **integer-encoded mask** corresponding to the tissue regions.

**Input format:**  
- RGB histopathological biopsy image (resized to 512×512, normalized to [0,1])  

**Output format:**  
- Integer-encoded segmentation mask (values correspond to tissue classes)

---

###  Classification Model
- Takes as input the **segmentation output** and corresponding image features.  
- Predicts the **MF (Myelofibrosis) grade** of the bone marrow sample.  
- Uses the `publish.csv` file for ground-truth labels, including fibrosis grade and hemorrhage presence.

**Input format:**  
- Integer-encoded segmented image (output from segmentation model)

**Output format:**  
- MF grade (categorical classification output)

---

###  Inference Pipeline
The notebook `inference_on_both_models.ipynb` performs **end-to-end inference**:
1. Runs the segmentation model on input biopsy images.  
2. Passes the resulting segmentation maps to the classification model.  
3. Outputs predicted **fibrosis grades**.

---

##  Dataset

The dataset used in this project — **BoMBR (Bone Marrow Biopsy Reticulin dataset)** — is publicly available on **Zenodo**:

** Dataset DOI:** [https://doi.org/10.5281/zenodo.13690617](https://doi.org/10.5281/zenodo.13690617)

The dataset contains digitized bone marrow biopsy images with corresponding **integer-encoded segmentation masks** and **fibrosis grading annotations**.

---

##  Dependencies

The code has been tested with:
- **Python 3.10+**
- **TensorFlow / Keras 2.15**
- **NumPy, OpenCV, Matplotlib, glob, os**

GPU acceleration is recommended for model training.

---

##  How to Use

1. **Clone the repository**
   ```bash
   git clone https://github.com/AI-in-Medicine-IIT-Ropar/BoMBR_based_models.git
   cd BoMBR_based_models

2. **Prepare dataset paths**  
   Update paths in the training notebooks to point to the downloaded dataset structure (`images/`, `masks/`, etc.).

3. **Train models**  
   - Run segmentation training:  
     [`Segmentation-Model/Xception_512_model_training.ipynb`](Segmentation-Model/Xception_512_model_training.ipynb)  
   - Run classification training:  
     [`Classification-Model/classification_model_architecture_and_training.ipynb`](Classification-Model/classification_model_architecture_and_training.ipynb)

4. **Run inference**  
   Execute the full pipeline:  
   [`inference_on_both_models.ipynb`](inference_on_both_models.ipynb)  
   Performs **segmentation → classification** in sequence.

