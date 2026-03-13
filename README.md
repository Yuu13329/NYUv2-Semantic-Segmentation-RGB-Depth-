# NYUv2 Semantic Segmentation with RGB-D UNet

Author: Yuu (2025)

This repository implements semantic segmentation on the NYUv2 dataset using a UNet architecture with RGB and Depth input.

---

## Overview

- Model: UNet
- Input: 4 channels (RGB + Depth)
- Resolution: 256 × 256
- Loss: CrossEntropyLoss + DiceLoss
- Scheduler: CosineAnnealingLR
- Mixed Precision (AMP)
- Test Time Augmentation (Horizontal Flip)

---

## Key Design Decisions

### Unified Resolution
All RGB images, depth maps, and labels are resized to 256×256.  
Label resizing uses NEAREST interpolation to prevent class index corruption.

### RGB-D Fusion
Depth is concatenated as a fourth channel (no handcrafted fusion).  
The network learns geometric representations directly.

### Loss Design
- CrossEntropyLoss for pixel-wise classification
- DiceLoss for class imbalance robustness
- ignore_index=255 excluded from loss

### Training Stabilization
- Mixed Precision (AMP)
- Cosine Annealing scheduler
- Best model saved by validation mIoU

### Inference Enhancement
Horizontal flip Test Time Augmentation (TTA)

---

## Results

- Best validation mIoU: ~0.31  
- Final TTA mIoU: 0.404

---

## Repository Structure

    nyuv2-semantic-segmentation-rgbd/
    ├── notebooks/
    │   └── NYUv2_Yuu.ipynb
    ├── models/
    │   └── best_model.pth
    ├── outputs/
    │   └── submission.npy
    ├── README.md
    └── .gitignore

---

## Dataset Structure (not included)

    data/
    ├── train/
    │   ├── image/
    │   ├── depth/
    │   └── label/
    └── test/
        ├── image/
        └── depth/

---

## How to Run

1. Download NYUv2 dataset separately.
2. Place dataset under ./data following the structure above.
3. Open notebook and run sequentially.

---

## Note

Dataset is not included due to size and license restrictions.
Pretrained model (≈30MB) is included.
