# YOLOv8.ipynb – Training, Retraining, and Visualization Pipeline

This Jupyter Notebook contains a complete pipeline for object detection using the YOLOv8 model. It includes the following key stages:

## 📌 Overview

1. **Model Training**  
   Trains a YOLOv8 model using an annotated dataset in YOLO format. The training is customizable with parameters like image size, epochs, batch size, and more.

2. **Prediction & Auto-Labeling**  
   Runs inference on unlabeled images or video frames to generate predictions. These predictions are optionally used for **auto-labeling** to expand the training set.

3. **Model Retraining**  
   Incorporates the auto-labeled data to retrain and refine the model. This improves performance, especially for underrepresented or initially poorly performing classes.

4. **Video Visualization**  
   Applies the trained model to video input, draws bounding boxes and class labels on each frame, and generates annotated video outputs.

---

## Model Pipeline

![image](https://github.com/user-attachments/assets/c4fff7a4-1b31-4a75-83ae-6d46287ba9bc)


# comparison_two_model.ipynb – Side-by-Side Model Comparison

This notebook enables visual and qualitative comparison between two trained YOLOv8 models by running inference on video input and displaying their predictions frame-by-frame side by side.

---

## 📌 Overview

This notebook performs the following tasks:

1. **Load Two Trained YOLOv8 Models**  
   Retrieves model weights from `runs/train/` directory or other specified paths.

2. **Video Frame Extraction**  
   Reads input video frame by frame using OpenCV.

3. **Inference on Both Models**  
   Each frame is processed by both models to generate predictions (bounding boxes and class labels).

4. **Side-by-Side Visualization**  
   Combines the predictions into a single frame with split view:
   - Left: Predictions from Model A  
   - Right: Predictions from Model B

5. **Output Video Generation**  
   Saves the side-by-side comparison frames into a new video for easy review and presentation.

---

## 🎯 Purpose

- Visually evaluate improvements between two training runs.
- Highlight differences in detection quality, precision, recall, and bounding box accuracy.
- Use as evidence of progress after retraining or hyperparameter tuning.

---

## Comparison Video


https://github.com/user-attachments/assets/a55ba3a7-9189-4f9e-adeb-92a48315bf1b

# live_prediction.ipynb – Real-Time Side-by-Side Model Comparison

This notebook performs real-time inference from a live camera feed using **two different YOLOv8 models**, and displays their predictions side by side for visual comparison.

---

## 📌 Overview

The notebook performs the following steps:

1. **Load Two Trained YOLOv8 Models**  
   Loads `.pt` weights from the `runs/train/` directory or any custom path.

2. **Access Live Camera Feed**  
   Uses OpenCV to access the system's webcam or an external camera device.

3. **Real-Time Inference**  
   Captures frames and runs predictions in parallel using both models.

4. **Side-by-Side Display**  
   Combines the outputs from both models into a split-screen view:
   - Left side shows predictions from Model A
   - Right side shows predictions from Model B

5. **Live Visualization**  
   Displays the combined result in a window for real-time comparison.

---

## 🎯 Purpose

- Visually compare model predictions in real time.
- Observe differences in detection speed, accuracy, and stability.
- Useful for field-testing and deployment validation.

---


# print_metrics.ipynb – Per-Class Metrics Comparison

This notebook is designed to load and display per-class evaluation metrics (such as mAP, precision, recall) for two YOLOv8 models: the baseline model and the retrained model.

---

## 📌 Overview

The notebook performs the following:

1. **Load Evaluation Results**  
   Parses metrics from the following JSON files:
   - `per_class_metrics.json` – Metrics from the original model
   - `per_class_metrics_retrain.json` – Metrics from the retrained model

2. **Display Per-Class Metrics**  
   Compares class-wise performance (e.g., mAP@0.5:0.95, precision, recall) side by side.

3. **Highlight Improvements**  
   Clearly indicates gains or losses in performance after retraining, making it easier to interpret the impact of auto-labeling or model tuning.

4. **(Optional)** Visualize Metrics  
   Optionally, you can plot bar graphs or tables to visualize metric changes for each class.

---

## 🎯 Purpose

- Quantify the improvement of the retrained model compared to the original.
- Support findings from visual comparisons in `comparison_two_model.ipynb`.
- Justify the effectiveness of the automatic labeling and retraining process.

---
