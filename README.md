# Lightweight Deep Learning for Small Object Detection in Aerial Imagery

An end-to-end computer vision pipeline tailored for small object detection in high-resolution aerial and satellite imagery using an optimized **YOLOv7-tiny** model, benchmarked for edge deployment on platforms like the **NVIDIA Jetson Nano**.

---

## 📌 Key Highlights & Results

- **Dataset:** Preprocessed satellite imagery from the **xView** dataset across overhead target categories.
- **Accuracy:** Achieved **0.62 mAP** on small objects (84% Precision, 76% Recall, 0.79 F1-score).
- **Compression:** **64.2% reduction in model size** (12 MB down to 4.3 MB) via L1-norm channel pruning and INT8 post-training quantization.
- **Latency & Throughput:** Inference latency reduced from **23 ms to 14 ms per frame**, boosting inference speed from **~43 FPS to ~70 FPS** on edge hardware with less than a 2% accuracy trade-off.

---

## 📊 Benchmark Comparison

| Metric | Baseline YOLOv7-tiny | Optimized (Pruned + INT8 Quantized) | Improvement |
| :--- | :--- | :--- | :--- |
| **Model Size** | 12 MB | **4.3 MB** | **-64.2%** |
| **Latency (Inference)** | 23 ms / frame | **14 ms / frame** | **-39.1%** |
| **FPS (Edge GPU)** | ~43 FPS | **~70 FPS** | **+62.8%** |
| **Detection Performance** | Baseline mAP | **0.62 mAP** | <2% trade-off |

---

## 🛠️ Pipeline & Architecture

1. **Preprocessing & Augmentation:**
   - Extraction of bounding boxes from aerial `.tif` tiles using `.geojson` metadata.
   - Spatial augmentations: random rotation, horizontal/vertical flips, and brightness perturbation.
   - Dataset split: 70% Train, 20% Validation, 10% Test.

2. **Model Architecture:**
   - YOLOv7-tiny backbone with extended convolutional blocks (CBS) and multi-scale detection heads.
   - Loss functions: CIoU for bounding-box regression and BCE for multi-label classification.
   - Optimizer: SGD with momentum and cosine annealing learning rate schedule.

3. **Compression & Edge Deployment:**
   - **Pruning:** Low L1-norm magnitude channel pruning to reduce parameter redundancy.
   - **Quantization:** Weight conversion from FP32 to INT8 precision via TensorRT / PyTorch APIs for deployment on NVIDIA Jetson.

---

## 📂 Project Structure
```text
├── assets/          # Detection output samples and visuals
├── data/            # Dataset configuration and labels
├── src/             # Preprocessing, pruning, and quantization scripts
├── notebooks/       # Inference demonstration notebooks
├── requirements.txt # Python dependencies
└── README.md

## 📄 Project Documentation & Presentations

- **Final Technical Report:** [View Report PDF](./docs/UAV_Small_Object_Detection_Report.pdf)
- **Project Presentation:** [View Slide Deck](./docs/UAV_Small_Object_Detection_Presentation.pdf)
- **Institutional Certification:** [View Certificate](./docs/Project_Completion_Certificate.pdf)

