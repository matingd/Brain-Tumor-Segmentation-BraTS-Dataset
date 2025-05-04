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

![Architecture Diagram](assets/architecture.png)

We employ a U-Net based backbone with attention gates to refine segmentation masks. Key components:

1. **Encoder**: 4 downsampling blocks (Conv → ReLU → MaxPool)
2. **Bottleneck**: Dilated conv layers
3. **Decoder**: 4 upsampling blocks + skip-connections
4. **Attention Gates** on skip paths for feature selection

---

## 🛠️ Setup & Installation

**Prerequisites**

```bash
python >=3.8
pip install -r requirements.txt
```

**Data**

1. Download BraTS 2021 dataset from \[MICCAI website].
2. Organize files:

   ```
   data/BraTS2021/
   ├── HGG
   └── LGG
   ```

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
