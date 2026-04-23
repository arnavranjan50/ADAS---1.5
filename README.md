# 🚗 AI-Based Animal Detection & Collision Warning System (ADAS Prototype)

A real-time **vision-based Advanced Driver Assistance System (ADAS)** that detects animals on roads using a **fine-tuned YOLOv8 model** and provides **intelligent brake alerts** to the driver.

---

## 📌 Overview

Animal-vehicle collisions are a serious safety issue, especially in rural and low-visibility conditions.  
This project provides a **software-only solution** that:

- Detects animals in real-time from dashcam video
- Estimates distance using bounding box size
- Applies temporal stability to reduce false alerts
- Activates **night mode enhancement** automatically
- Displays **brake alerts** based on proximity

---

## 🎯 Key Features

✅ Real-time animal detection using YOLOv8  
✅ Distance estimation (bounding box ratio method)  
✅ Smart brake alerts (Monitor / Brake / Hard Brake)  
✅ Night mode using CLAHE (low-light enhancement)  
✅ Temporal filtering (reduces flickering detections)  
✅ Context filtering (avoids posters / fake animals)  
✅ Runs fully in software (no sensors required)

---

## 🧠 How It Works

### 🔁 Pipeline

### 🚦 Alert Logic

| Condition | Output |
|----------|--------|
| No animal | ROAD CLEAR |
| Far animal | MONITOR |
| Close animal | BRAKE |
| Very close | HARD BRAKE |

---

## 🧪 Tech Stack

- Python 3.10+
- OpenCV
- Ultralytics YOLOv8
- PyTorch (CUDA enabled)
- NumPy

---

## 📂 Project Structure
ADAS/
│── dataset/
│ ├── train/
│ ├── valid/
│ └── data.yaml
│
│── runs/
│ └── detect/
│ └── train/
│ └── weights/
│ └── best.pt
│
│── adas_advanced_demo.py
│── train.py
│── requirements.txt
│── README.md

## ⚙️ Installation

### 1. Clone Repository

git clone https://github.com/your-username/ADAS-Animal-Detection.git
cd ADAS-Animal-Detection

pip install -r requirements.txt
pip install ultralytics 

Training the Model

python train.py

Make sure your dataset path in data.yaml is correct.

Run Demo
python adas_advanced_demo.py
Press Q to exit

Works with both:
Video file
Webcam
🌙 Night Mode

Automatically activates when brightness is low.

Uses CLAHE (Contrast Enhancement)
Improves detection in dark scenes
📊 Distance Estimation

Distance is approximated using:

Bounding Box Area / Frame Area

Thresholds:

< 0.05 → Far
0.05 - 0.12 → Close
> 0.12 → Very Close

⚠️ Limitations

Distance is approximate (no depth sensor)
Small or far animals may be missed
Performance depends on dataset quality
Night mode may amplify noise in very dark scenes

🔮 Future Improvements
Depth estimation (MiDaS integration)
Multi-object tracking (DeepSORT)
Edge deployment (TensorRT / ONNX)
Larger dataset for better generalization
Integration with real vehicle braking systems
