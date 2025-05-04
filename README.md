**Project Title: Brain Tumor Segmentation**

![Python Version](https://img.shields.io/badge/python-3.8%2B-blue) 

---

## 📖 Introduction

A deep-learning pipeline for **brain tumor segmentation** on the BraTS dataset. We segment three tumor sub-regions:

* **Whole Tumor (WT)**
* **Tumor Core (TC)**
* **Enhancing Tumor (ET)**

Format of photos used: T1, T1Gd, T2, FLAIR.

---

## 🏗️ Architecture

![Architecture Diagram](assets/3D-U-Net-architecture-diagram.png)

We employ a 3D U-Net (UNet3D) architecture for volumetric brain tumor segmentation. This model processes the full 3D MRI volumes directly, preserving spatial context across slices. Key components:

1. **Encoder**: Four 3D convolutional downsampling blocks (Conv3D → ReLU → MaxPool3D)
2. **Bottleneck**: Dilated 3D convolution layers for capturing multi-scale context
3. **Decoder**: Four 3D upsampling blocks with skip-connections to recover spatial resolution
4. **Attention Gates**: Integrated on skip paths to refine feature selection and suppress irrelevant activations

---

## 🛠️ Setup & Installation

**Prerequisites**

```bash
python >=3.8
pip install -r requirements.txt
```

**Data**

Download BraTS 2020 dataset from \[[kaggle website](https://www.kaggle.com/datasets/awsaf49/brats20-dataset-training-validation)].

---

## 📊 Benchmarks & Metrics

![Benchmark comparison](assets/bemchmark_comparison.png)
![Dice vs. Epoch](assets/dice_curve.png)
![IOU vs. Epoch](assets/iou_curve.png)
![Loss vs. Epoch](assets/loss_curve.png)
![Precision vs. Epoch](assets/precision_curve.png)
![Sensitivity vs. Epoch](assets/sensitivity_curve.png)
![Specificity vs. Epoch](assets/specificity_curve.png)

---

## ⏱️ Runtime & Resources

* **GPU**: NVIDIA Tesla V100, 16 GB VRAM
* **Training time**: \~2 hours / epoch
* **Inference speed**: \~0.5 sec / volume on GPU

---

## 🗂️ Repository Structure

```
├── assets/               # figures, diagrams, sample outputs
├── data/                 # raw & preprocessed data
├── src/                  # training, evaluation scripts
├── notebooks/            # exploratory analysis
├── results/              # trained models, logs, predictions
├── requirements.txt
└── README.md
```

---

## 📝 License

This project is released under the **MIT License**.

---

## 🤝 Contributing & Contact

* **Author**: Your Name ([email@example.com](mailto:email@example.com))
* **Acknowledgements**: Thanks to the MICCAI BraTS organizers and the research community.

Feel free to open issues or PRs for improvements!
