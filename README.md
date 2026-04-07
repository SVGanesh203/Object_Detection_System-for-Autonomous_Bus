# 🚍 Autonomous Smart Bus – Blind Spot Detection System

## 📌 Overview

This project presents a **real-time object detection system** designed for an **Autonomous Smart Bus** to eliminate blind spots and improve road safety.

Using **YOLOv8** and the **BDD100K dataset**, the system detects pedestrians, vehicles, and obstacles from video input and generates **visual alerts** when objects enter critical blind spot regions.

---

## 🎯 Objectives

* Detect objects in real-time using deep learning
* Identify **left and right blind spot zones**
* Generate **alerts for potential collisions**
* Improve safety in urban public transportation systems

---

## 🧠 System Architecture

* **Input:** Camera / Video feed
* **Processing:** YOLOv8 Object Detection
* **Logic:** Blind Spot Region Analysis
* **Output:** Bounding boxes + Alert messages

---

## 📊 Features

✔ Real-time object detection (YOLOv8)
✔ Blind spot detection (left & right zones)
✔ Works on images and videos
✔ Visual alert system
✔ Simulation using real-world bus driving videos

---

## 🛠️ Tech Stack

* Python
* OpenCV
* YOLOv8 (Ultralytics)
* NumPy
* Google Colab

---

## 📂 Dataset

We used the **BDD100K dataset**, which contains diverse driving scenarios including urban traffic, pedestrians, and vehicles.

---

## 🚀 Installation

```bash
pip install ultralytics opencv-python
```

---

## ▶️ Usage

### 1. Load Model

```python
from ultralytics import YOLO
model = YOLO("yolov8n.pt")
```

### 2. Run Detection on Video

```python
import cv2

cap = cv2.VideoCapture("bus_video.mp4")

while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break

    results = model(frame)

    h, w, _ = frame.shape

    for r in results:
        for box in r.boxes:
            x1, y1, x2, y2 = map(int, box.xyxy[0])

            # Blind spot logic
            if x1 > w * 0.7:
                cv2.putText(frame, "RIGHT BLIND SPOT", (50,50),
                            cv2.FONT_HERSHEY_SIMPLEX, 1, (0,0,255), 3)

            if x2 < w * 0.3:
                cv2.putText(frame, "LEFT BLIND SPOT", (50,100),
                            cv2.FONT_HERSHEY_SIMPLEX, 1, (0,0,255), 3)
```

---

## 🎥 Output

The system generates a processed video with:

* Bounding boxes around detected objects
* Labels (person, car, etc.)
* Real-time blind spot alerts

---

## ⚠️ Challenges Faced

* Handling large dataset (BDD100K)
* It takes some time to run large outputs
* I couldn't upload the code with outputs as the size of file has reached ~ 500MB

---

## 💡 Future Improvements

* Distance estimation for objects
* Audio alert system
* Integration with real vehicle sensors
* Deployment on edge devices (Raspberry Pi / Jetson Nano)

---

## 🧠 Conclusion

This project demonstrates how **AI-powered perception systems** can significantly improve safety in autonomous public transportation by addressing blind spot challenges.

---

## 👨‍💻 Authors

* S.V.Ganesh
---

## 📜 License

This project is MIT LISENCE.

