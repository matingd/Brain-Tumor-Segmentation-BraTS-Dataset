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

Download BraTS 2021 dataset from \[[MICCAI website](https://www.kaggle.com/datasets/awsaf49/brats20-dataset-training-validation)].

---

## 🚀 Usage

**Training**

```bash
python src/train.py \
  --data_dir ./data/BraTS2021 \
  --epochs 100 \
  --batch_size 4 \
  --lr 1e-4
```

**Inference / Evaluation**

```bash
python src/evaluate.py \
  --checkpoint ./results/best_model.pth \
  --output_dir ./results/predictions
```

---

## 📊 Benchmarks & Metrics

| Class                | Dice Score | IoU  |
| -------------------- | ---------- | ---- |
| Whole Tumor (WT)     | 0.89       | 0.82 |
| Tumor Core (TC)      | 0.78       | 0.70 |
| Enhancing Tumor (ET) | 0.71       | 0.60 |

![Dice vs. Epoch](assets/dice_epoch.png)

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
