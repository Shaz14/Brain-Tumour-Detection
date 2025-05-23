# 🧠 Brain Tumor Detection
### _Author: Shahzeb Abbas_

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![](https://badgen.net/badge/release/1.2.0/green?icon=github)](https://github.com/giuseppebrb/BrainTumorDetection/releases) [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/giuseppebrb/BrainTumorDetection/blob/main/Brain_Tumor_Detector.ipynb)



## About

This project aims to build 3 different models to detect **tumors** in **brain MRIs** (Magnetic Resonance Imaging) of different patients by using computer vision. Each model is trained and validated on one of the 3 possible planes generated by an MRI: **axial**, **coronal** and **sagittal**.

| Axial                                            | Coronal                                        | Sagittal                                          |
| ------------------------------------------------ | ---------------------------------------------- | ------------------------------------------------- |
| ![00022_75.jpg](https://i.imgur.com/BdcTZOO.jpg) | ![59 (8).jpg](https://i.imgur.com/lH96GA2.jpg) | ![00002_166.jpg](https://i.imgur.com/9rCqylE.jpg) |

The outcomes of the models will show a **colored box** around a possible tumor or a structure that may resamble a tumor but it is not (in this case "Not tumor" label will be shown) and the **confidence score** for the detection.

The dataset used in this project has been edited and enlarged starting from this repository on Kaggle: [Brain Tumor Object Detection Dataset](https://www.kaggle.com/datasets/davidbroberts/brain-tumor-object-detection-datasets). In total there are ~1.300 images and labels.

## Tech overview

We won't building the entire Deep Neural Network from scratch, instead we'll perform fine-tuning of the [**YOLOv5**](https://github.com/ultralytics/yolov5) architecture which has been already trained on the **COCO** dataset. This allows us to specialize the model to our specific task of tumor detection. In particular, will be starting from the **YOLOv5m** checkpoint.

A Python environment with [**PyTorch**](https://pytorch.org/get-started/locally/) installed is required to perform both training end/or detection.

## About the repo

You can use the code in this repository in different ways:

1. Train and detect on this **Google Colaboratory** environment [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/giuseppebrb/BrainTumorDetection/blob/main/Brain_Tumor_Detector.ipynb) (TIP: if you select the runtime with GPU, training process will be faster).
2. Train and detect locally by cloning the repository and running this **Jupyter Notebook** file [Brain_Tumor_Detector.ipynb](https://colab.research.google.com/github/giuseppebrb/BrainTumorDetection/blob/main/Brain_Tumor_Detector.ipynb) (training time will be determined by your hardware capacity).
3. **Download** and use the fine-tuned models in the [release](https://github.com/giuseppebrb/BrainTumorDetection/releases) page (see below for further details).

## How to use the models

If you prefer skipping the building process you can download the latest version of models [here](https://github.com/giuseppebrb/BrainTumorDetection/releases).

In order to run one of the models please follow these steps:

**1.** Clone the YOLOv5 repository

```
git clone https://github.com/ultralytics/yolov5.git
```

**2.** Within the folder of the repository just cloned, in the terminal run:

```
pip install -r requirements.txt
```

**3.** Now you are ready to use one of the model. Within the folder of the YOLOv5 Repository you can run in the terminal:

```
python detect.py --weights <DOWNLOADED_MODEL_PATH> --img 640 --conf 0.4 --source <URL_OR_PATH_OF_THE_IMAGE>
```

Examples below show 3 different detections (one per model) on the MRIs of 3 different patients. <br>
A **label** over the bounding box identifies the **class** of the detection ("tumor" / "not tumor") and besides that is displayed a **confidence score** (**0 minimum** - **1 maximum**).
![output](https://i.imgur.com/sk2Vh1s.jpg)
