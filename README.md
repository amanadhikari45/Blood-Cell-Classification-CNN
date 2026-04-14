## Automatic Identification and Counting of Blood Cells
[![GitHub stars](https://img.shields.io/github/stars/amanadhikari45/Blood-Cell-Classification-CNN)](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/amanadhikari45/Blood-Cell-Classification-CNN)](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/network)
[![GitHub issues](https://img.shields.io/github/issues/amanadhikari45/Blood-Cell-Classification-CNN)](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/issues)
[![Version](https://img.shields.io/badge/version-2.1-green.svg?longCache=true&style=flat)](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN)
[![GitHub license](https://img.shields.io/github/license/amanadhikari45/Blood-Cell-Classification-CNN)](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/blob/master/LICENSE)

## Dataset
The [```Complete Blood Count (CBC) Dataset```](https://github.com/amanadhikari45/Complete-Blood-Cell-Count-Dataset) has been used for automatic identification and counting of blood cells. Download the dataset, unzip and put the ```Training```, ```Testing```, and ```Validation``` folder in the working directory.

## Requirements
![requirements](https://img.shields.io/badge/Python-3.6-3480eb.svg?longCache=true&style=flat&logo=python)
![requirements](https://img.shields.io/badge/Python-3.7-3480eb.svg?longCache=true&style=flat&logo=python)

- Tensorflow-GPU==2.2.0 (tested on 2.1.0, 2.2.0, and 2.3.0) ```conda install tensorflow-gpu```
- TF-slim==1.1.0 ```pip install tf-slim==1.1.0```
- Weights: [```download```](https://1drv.ms/u/s!AlXVRhh1rUKThlxTievX0X1CpXd0?e=9cKxYb) the trained weights file for blood cell detection and put the ```weights``` folder in the working directory.

[![Download](https://img.shields.io/badge/download-weights-blue.svg?longCache=true&style=flat&logo=microsoft-onedrive)](https://1drv.ms/u/s!AlXVRhh1rUKThlxTievX0X1CpXd0?e=9cKxYb)
[![Download](https://img.shields.io/badge/download-weights-ff160a.svg?longCache=true&style=flat&logo=mega)](https://mega.nz/#F!2kVUnKjS!z15tM9WLfga3l1gCNSLNGw)

## Update
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-f57418.svg?longCache=true&style=flat&logo=tensorflow)](https://www.tensorflow.org/install)

The code was originally written and developed with `TensorFlow v1.x`. The new updated version `v2.0` included `TensorFlow v2.x` support, tested on both TensorFlow `v2.1.0` and `v2.2.0`. You can download the previous version from **[`here`](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/releases/tag/v1.0)**.

## How to Run the Code  :runner:
To detect the blood cells, simply run the `detect.py` file in the terminal or using an IDE. A step-by-step guideline of how to run the blood cell detection code in your computer is provided in this **[`wiki`](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/wiki/A-Step-by-Step-Guide-of-How-to-Run-the-Code)**.
If you have any trouble running the code and facing any error please feel free to create an **[`issue`](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/issues)** or **[`contact me`](https://amanadhikari45.github.io/#contact)**.

## How to Train on Your Dataset  :bullettrain_side:
A seven-step guideline of how to train on your own dataset is provided in this **[`wiki`](https://github.com/amanadhikari45/Blood-Cell-Classification-CNN/wiki/How-to-Train-on-Your-Dataset)**.

## Blood Cell Detection Output
<p align="center">
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/detection_output.png" width="500">
</p>

## KNN and IOU Based Verification
In some cases, our model predicts the same platelet twice. To solve this problem we propose a k-nearest neighbor (KNN) and intersection over union (IOU) based verification system where we find the nearest platelet of a selected platelet and calculate their overlap. We are allowing only 10% overlap between two platelets. If the overlap is more than that then it will be a spurious prediction and we will ignore the prediction.

| Before Verification  | After Verification  |
|:-:|:-:|
| <p align="center"> <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/before_verification.jpg"> </p>  | <p align="center"> <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/after_verification.jpg"> </p>  |

## Prediction on High-Resolution Image (HRI)
We have used our model to detect and count blood cells from high-resolution blood cell smear images. These test images are of the size of ```3872 x 2592``` way higher than the size of our trained images of ```640 x 480```. So, to match the cell size of our trained images we divide those images into grid cells and run prediction in each grid cell and then combine all the prediction results.

<h3 align="center">Dividing Image into Grid/Patch</h3>
<p align="center">
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/grid_patch.jpg" width="700">
</p>

<h3 align="center">Combined Output</h3>
<p align="center">
  <img src="https://raw.githubusercontent.com/amanadhikari45/Blood-Cell-Classification-CNN/master/assets/combined_output.jpg" width="700">
</p>
