# 🔬 Blood Cell Classification & Counting Using CNN

<p align="center">
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/detection_output.png" width="600" alt="Blood Cell Detection Output"/>
</p>

<p align="center">
  <a href="https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/stargazers">
    <img src="https://img.shields.io/github/stars/amanadhikari45/Blood-Cell-Classification-CNN?style=for-the-badge&color=yellow" alt="Stars"/>
  </a>
  <a href="https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/network">
    <img src="https://img.shields.io/github/forks/amanadhikari45/Blood-Cell-Classification-CNN?style=for-the-badge&color=blue" alt="Forks"/>
  </a>
  <a href="https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/issues">
    <img src="https://img.shields.io/github/issues/amanadhikari45/Blood-Cell-Classification-CNN?style=for-the-badge&color=red" alt="Issues"/>
  </a>
  <a href="https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/amanadhikari45/Blood-Cell-Classification-CNN?style=for-the-badge&color=green" alt="License"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.6%20|%203.7-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white"/>
  <img src="https://img.shields.io/badge/Computer%20Vision-CNN-blueviolet?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Domain-Medical%20Imaging-red?style=for-the-badge"/>
</p>

---

## 📌 Overview

This project implements an **automated blood cell detection and counting system** using a Convolutional Neural Network (CNN). Given a blood smear microscopy image, the model identifies and counts three types of blood cells:

| Cell Type | Description |
|-----------|-------------|
| 🔴 **RBC** | Red Blood Cells (Erythrocytes) |
| ⚪ **WBC** | White Blood Cells (Leukocytes) |
| 🟡 **Platelets** | Thrombocytes |

Accurate automated blood cell counting has direct applications in **clinical diagnostics**, reducing the time and cost of manual Complete Blood Count (CBC) tests.

---

## 🏗️ Architecture & Approach

- **Model:** Custom CNN with YOLO-style object detection head built using **TF-Slim**
- **Input:** Blood smear images (`640 x 480` resolution)
- **Output:** Bounding boxes + class labels for each detected cell
- **Post-processing:** KNN + IOU-based duplicate prediction filtering
- **High-Resolution Inference:** Grid/patch-based sliding window approach for images up to `3872 x 2592`

---

## 📁 Dataset

The **Complete Blood Count (CBC) Dataset** was used for training, validation, and testing. It contains annotated blood smear images with labeled RBC, WBC, and Platelet instances.

Download the dataset from [this repository](https://github.com/amanadhikari45/Complete-Blood-Cell-Count-Dataset) and place the `Training`, `Testing`, and `Validation` folders in the working directory.

---

## ⚙️ Requirements

```bash
Python          3.6 / 3.7
TensorFlow-GPU  2.1.0 / 2.2.0 / 2.3.0
TF-Slim         1.1.0
```

Install dependencies:
```bash
conda install tensorflow-gpu
pip install tf-slim==1.1.0
```

Download the pre-trained weights and place the `weights/` folder in the working directory:

[![Download Weights (OneDrive)](https://img.shields.io/badge/Download%20Weights-OneDrive-0078D4?style=for-the-badge&logo=microsoft-onedrive)](https://1drv.ms/u/s!AlXVRhh1rUKThlxTievX0X1CpXd0?e=9cKxYb)
[![Download Weights (MEGA)](https://img.shields.io/badge/Download%20Weights-MEGA-D60000?style=for-the-badge&logo=mega)](https://mega.nz/#F!2kVUnKjS!z15tM9WLfga3l1gCNSLNGw)

---

## 🚀 Quick Start

### Run Detection
```bash
python detect.py
```

### Run on High-Resolution Images
```bash
python predict_HRI.py
```

For a complete step-by-step setup guide, refer to the [**Wiki: How to Run the Code**](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/wiki/A-Step-by-Step-Guide-of-How-to-Run-the-Code).

---

## 📊 Results

### Standard Detection Output

<p align="center">
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/detection_output.png" width="500" alt="Detection Output"/>
</p>

### KNN + IOU Based Duplicate Filtering

In some cases the model predicts the same platelet twice. A **k-nearest neighbor (KNN) + intersection over union (IOU)** verification step is applied — allowing a maximum of 10% overlap between adjacent platelet predictions. Predictions exceeding this threshold are discarded.

| Before Verification | After Verification |
|:---:|:---:|
| <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/before_verification.jpg" width="340"/> | <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/after_verification.jpg" width="340"/> |

### High-Resolution Image (HRI) Prediction

For images significantly larger than the training resolution, a **grid/patch-based inference** strategy is used — dividing the image into overlapping tiles, running detection on each, then merging the results.

<p align="center">
  <b>Grid Division</b><br/>
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/grid_patch.jpg" width="600"/>
</p>

<p align="center">
  <b>Combined Output</b><br/>
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/combined_output.jpg" width="600"/>
</p>

---

## 🧠 Training on a Custom Dataset

A seven-step guide to training the model on your own annotated blood cell dataset is available in the [**Wiki: How to Train on Your Dataset**](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/wiki/How-to-Train-on-Your-Dataset).

---

## 🔄 Version History

| Version | TensorFlow | Notes |
|---------|-----------|-------|
| v2.1 (current) | 2.x | Stable, tested on 2.1–2.3 |
| v2.0 | 2.x | Initial TF2 migration |
| [v1.0](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/releases/tag/v1.0) | 1.x | Original implementation |

---

## 🐛 Issues & Contributions

Found a bug or have a suggestion? [Open an issue](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/issues) or [get in touch](https://amanadhikari45.github.io/#contact).

---

## 📄 License

This project is licensed under the **GPL-3.0 License** — see the [LICENSE](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/blob/master/LICENSE) file for details.
