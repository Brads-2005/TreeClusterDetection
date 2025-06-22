project:
  name: 🌲 Generalized Tree Cluster Detection
  author: Radha Agarwal
  description: >
    A tree cluster segmentation pipeline using high-resolution RGB aerial imagery.
    Trained on the public OAM-TCD dataset with instance-level masks for trees and clusters,
    using a PyTorch Mask R-CNN model with a partially frozen backbone.

dataset:
  name: 📊 OAM-TCD
  source: https://huggingface.co/datasets/restor/tcd
  format: RGB GeoTIFF (2048x2048 px) + instance masks
  resolution: 10 cm/px
  annotation_type: Instance segmentation
  details: >
    Contains ~280,000 individual trees and ~56,000 tree clusters.
    Designed for training both semantic and instance segmentation models.

model:
  name: 🛠️ Mask R-CNN
  framework: PyTorch
  architecture: maskrcnn_resnet50_fpn
  pretrained: false
  num_classes: 2
  backbone:
    frozen_layers: all_except_layer4
  device: cuda_or_cpu

results:
  -  Successfully segmented tree clusters in aerial RGB imagery
  -  Freezing early backbone layers helped reduce overfitting

future_work:
  -  Add multi-class segmentation (individual trees + clusters)
  -  Integrate LiDAR/hyperspectral features
  -  Apply model to UAV-based real-time data streams
