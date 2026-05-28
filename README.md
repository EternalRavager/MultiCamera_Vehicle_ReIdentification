# 🕵️ The Digital Detective: Multi-Camera Vehicle Tracking

## 📌 Project Overview
This project is an automated Multi-Target Multi-Camera (MTMC) tracking system. It utilizes a Deep Learning pipeline to act as an autonomous security agent, capable of processing multi-camera video streams, instantly reading license plates, and tracking a specific vehicle's journey across disparate camera nodes.

## ⚙️ The Architecture (The Pipeline)
The system is divided into three functional modules:
1. **The Eyes (Detector):** A fine-tuned **YOLOv8** model that scans video frames to localize vehicles and draw bounding boxes around license plates.
2. **The Brain (Reader):** An **EasyOCR** pipeline that dynamically crops the detected plates, applies OpenCV bilateral filtering, and extracts alphanumeric sequences.
3. **The Memory (Tracking Logic):** A centralized **SQLite** state matrix that logs plate strings, timestamps, and Camera IDs. A temporal debouncing algorithm filters out duplicate reads, allowing for chronological tracking of a vehicle across multiple cameras.

## 📂 Repository Structure
* `license.ipynb` - Establishes the Google Drive architecture and securely downloads the Kaggle dataset.
* `01_yolo_training.ipynb` - The YOLOv8n training pipeline (50 epochs) with a smart-resume engine.
* `02_ocr_testing.ipynb` - The OpenCV preprocessing and EasyOCR extraction logic.
* `04_main_pipeline.ipynb` - The master executable that merges YOLO, EasyOCR, and the SQLite database to process video streams.
* `best.pt` - Our custom-trained YOLOv8 license plate detection weights.

## 🚀 How to Run
1. Upload the notebooks to Google Colab.
2. Run `license.ipynb` to set up your dataset.
3. Skip the training phase by directly loading the provided `best.pt` weights.
4. Run `04_main_pipeline.ipynb` on the provided test video to see the real-time detection and database logging.

## 👥 Authors
* Tejasveer Singh
* Abhishek Kumar
*(Computer Science Engineering, AI/ML - MIT Manipal)*
