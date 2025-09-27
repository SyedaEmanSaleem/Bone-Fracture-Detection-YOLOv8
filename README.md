# 🦴 Bone Fracture Detection using YOLOv8

This repository contains code and experiments for detecting **bone fractures in X-ray images** using the **Ultralytics YOLOv8** object detection model. The project involves training, validation, and inference on a custom bone fracture dataset.

---

## 📌 Project Overview

Bone fracture detection in medical imaging is a challenging task requiring high precision. This project leverages the **YOLOv8n (nano)** model for efficient training and inference.

* **Framework**: [Ultralytics YOLOv8](https://docs.ultralytics.com)
* **Dataset**: Custom-labeled bone fracture X-ray images (`data.yaml`)
* **Hardware Used**: NVIDIA RTX 3090 (24 GB VRAM)
* **Objective**: Train and validate a model capable of localizing fractures with high accuracy.

---

## 🚀 Features

✔️ Custom dataset training with YOLOv8
✔️ Early stopping to prevent overfitting
✔️ Inference on medical X-ray images
✔️ High accuracy detection (mAP@50 ≈ **0.995**, mAP@50-95 ≈ **0.987**)
✔️ Image format conversion (`.jfif → .jpg`) for compatibility

---

## 📂 Repository Structure

```
├── Bone_Fracture_Dataset.ipynb   # Main notebook with training & inference
├── data.yaml                     # Dataset configuration (train/val/test paths)
├── README.md
├── best.pt
└── result.csv                   
```

---

## ⚙️ Installation

```bash
# Clone the repo
git clone https://github.com/your-username/bone-fracture-detection.git
cd bone-fracture-detection

# Install dependencies
pip install ultralytics pillow
```

---

## 🏋️ Training

To train the YOLOv8 model on the dataset:

```bash
yolo detect train \
  data="data.yaml" \
  model=yolov8n.pt \
  epochs=100 \
  imgsz=954 \
  batch=32 \
  name="bonefracture_train" \
  lr0=0.001 lrf=0.01 patience=20
```

---

## 📊 Training Results

* **Best epoch**: 51
* **Precision (P)**: 0.997
* **Recall (R)**: 1.0
* **mAP@50**: 0.995
* **mAP@50-95**: 0.987

Training was stopped early due to **early stopping** after 71 epochs.

---

## 🔍 Inference

```python
from ultralytics import YOLO

# Load trained model
model = YOLO("runs/detect/bonefracture_train10/weights/best.pt")

# Run inference on test images
results = model("Bone-Fracture-1/test/images")
results[0].show()
```

---

## 📈 Model Performance

| Metric        | Score |
| ------------- | ----- |
| Precision (P) | 0.997 |
| Recall (R)    | 1.000 |
| mAP@50        | 0.995 |
| mAP@50-95     | 0.987 |

---

## 📌 Future Improvements

* Experiment with **YOLOv8m/l** for higher accuracy.
* Add **Grad-CAM visualization** for interpretability.
* Expand dataset with more diverse fracture cases.

---

## 🙌 Acknowledgements

* [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
* Medical imaging dataset contributors


