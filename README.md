# NYUv2 Semantic Segmentation (RGB + Depth)

## Overview
This project implements semantic segmentation on NYUv2 dataset using UNet with RGB and Depth input.

## Model
- Input: 4 channels (RGB + Depth)
- Resolution: 256x256
- Loss: CrossEntropy + DiceLoss
- Ignore index applied
- AMP enabled
- Best model selected by validation mIoU
- TTA (horizontal flip)

## Result
Validation mIoU: ~0.31  
Final submission (with TTA): 0.404

## Key Design Decisions
- Unified spatial resolution
- NEAREST interpolation for labels
- Combined CE + Dice for class imbalance
- Simple channel concatenation for RGB + Depth

## How to Run
1. Download NYUv2 dataset
2. Set DATA_ROOT path
3. Run notebook

## Pretrained Model
Best model (mIoU=0.404 with TTA) is included as best_model.pth
