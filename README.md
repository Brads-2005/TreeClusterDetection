

# 🌲 Generalized Tree Cluster Detection
# Author: Radha Agarwal

# 📄 Description
description: >
  This repository implements **tree cluster segmentation** using a Mask R-CNN model trained on the
  [OAM-TCD dataset](https://huggingface.co/datasets/restor/tcd). Unlike crown-specific detection,
  this project focuses on detecting **tree groups** and **dense vegetation clusters** from high-resolution
  RGB aerial imagery.

---

# 📦 Dataset: OAM-TCD (Hugging Face)

dataset:
  name: 📊 OAM-TCD
  source: https://huggingface.co/datasets/restor/tcd
  format: 2048×2048 px RGB **GeoTIFF** tiles
  resolution: 10 cm/pixel
  masks: 
    - ~280,000 individual trees
    - ~56,000 tree clusters
  annotation_type: Instance segmentation
  details: >
    Designed for both **semantic** and **instance segmentation** tasks. The dataset includes
    high-resolution aerial tiles and matching polygonal masks.

---

# 🛠️ Model Configuration

model:
  name: Mask R-CNN
  framework: PyTorch
  architecture: maskrcnn_resnet50_fpn
  pretrained: false
  num_classes: 2
  backbone:
    strategy: Partially frozen (all layers frozen except 'layer4')
  device: CUDA (if available) or CPU

---


# ✅ Results

results:
  - Successfully segmented dense tree clusters from RGB aerial images
  - Freezing backbone layers helped reduce overfitting and GPU usage
  - Achieved clean masks on clustered vegetation without post-processing

---

# 🔭 Future Work

future_work:
  - Extend model for **multi-class segmentation** (individual + grouped trees)
  - Integrate **LiDAR** and **hyperspectral features** for improved accuracy
  -  Adapt pipeline for **UAV-based real-time** tree monitoring systems


