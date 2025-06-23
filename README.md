# MedSAM-2 for Brain Tumor Segmentation (BRATS 2019)

This repository contains the implementation of **MedSAM-2** for 3D brain tumor segmentation on the BRATS 2019 dataset.

## 📌 Overview
- Implements MedSAM-2's tracking-based segmentation approach
- Processes multi-modal MRI scans (T1, T1Gd, T2, FLAIR)
- Evaluates on three tumor subregions: ET, TC, WT
- Includes quantitative metrics (Dice, IoU) and visualization

## 🚀 Quick Start

### 1. Install Dependencies
pip install torch torchvision SimpleITK numpy opencv-python matplotlib scikit-learn

## 2. Download BRATS 2019 Dataset
python
# Run in Colab/Kaggle
!kaggle datasets download -d awsaf49/brats2019-dataset
!unzip brats2019-dataset.zip -d data/

## 3. Run Inference
from medsam_inference import MedSAM2Inference

# Initialize model
model = MedSAM2Inference(ckpt_path="medsam2_vit_b.pth")

# Load sample volume
- volume_path = "data/BraTS19_2013_2_1_flair.nii.gz"
- volume = load_nii(volume_path)  # (H, W, D)

# Run one-prompt segmentation
- prompt = [x=120, y=150]  # Example prompt coordinate
- mask_3d = model.segment_volume(volume, prompt)  # (H, W, D)

## License:
- MIT License
