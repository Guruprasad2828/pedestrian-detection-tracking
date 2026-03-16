# Pedestrian Detection and Tracking using Faster R-CNN and SORT

## Overview

This project implements a pedestrian detection and tracking pipeline using deep learning and classical tracking algorithms. The system detects pedestrians in video frames using Faster R-CNN with a ResNet-50 + Feature Pyramid Network (FPN) backbone and tracks them across frames using the SORT (Simple Online Realtime Tracking) algorithm.

The detector identifies pedestrians in each frame, and the tracker assigns consistent IDs to each detected person as they move through the scene. This allows the system to follow multiple pedestrians across time and visualize their trajectories in video sequences.

The project demonstrates how object detection models and tracking algorithms can be integrated into a complete computer vision pipeline for analyzing dynamic scenes.

---

## Key Features

- Pedestrian detection using Faster R-CNN
- ResNet-50 + Feature Pyramid Network backbone
- Multi-object tracking using SORT
- Motion prediction using Kalman Filter
- Detection-to-track assignment using Hungarian Algorithm
- Identity tracking across frames
- Visualization of bounding boxes, track IDs, detection count, and FPS

---

## Pipeline Overview

The complete pipeline processes video frames sequentially:

1. Frame Input  
   Video frames are loaded from the MOT17 dataset.

2. Pedestrian Detection  
   Faster R-CNN detects pedestrians and outputs bounding boxes with confidence scores.

3. Detection Filtering  
   Predictions below the confidence threshold are removed.

4. Tracking with SORT  
   The SORT tracker:
   - Predicts object motion using a Kalman Filter
   - Matches detections to existing tracks using the Hungarian Algorithm
   - Uses Intersection over Union (IoU) for similarity measurement

5. Track Management  
   - Matched tracks are updated  
   - New detections create new tracks  
   - Lost tracks are removed after a set number of frames

6. Visualization  
   Bounding boxes, unique IDs, and runtime statistics are drawn on each frame.

---

## Dataset

This project uses the MOT17 (Multiple Object Tracking) Benchmark Dataset.

Dataset features:
- Real-world pedestrian scenes
- Multiple people per frame
- Bounding box annotations
- Identity labels across frames

Dataset Link:

https://motchallenge.net/data/MOT17/

---

## Technologies Used

- Python
- PyTorch
- Torchvision
- OpenCV
- NumPy
- SciPy
- FilterPy
- Matplotlib

---

## Evaluation Metrics

The detection model is evaluated using standard object detection metrics:

- Precision – proportion of correct detections
- Recall – proportion of pedestrians detected
- F1 Score – balance between precision and recall
- mAP (Mean Average Precision) – detection performance across thresholds

---

## Results

The system detects pedestrians in video frames and assigns consistent track IDs across frames using the SORT tracker. The output video visualizes tracked pedestrians with bounding boxes and identity numbers along with runtime statistics.

Example output includes:
- Pedestrian bounding boxes
- Unique tracking IDs
- Frame processing speed (FPS)
- Detection count
- Active track count

---

## Possible improvements include:

- Integrating DeepSORT for appearance-based tracking
- Improving detection accuracy using newer detectors such as YOLOv8 or DETR
- Adding trajectory visualization
- Evaluating tracking performance using MOTA, MOTP, and IDF1 metrics
- Optimizing the system for real-time performance


