# AVISHKAAR-Season-2

A deep learning project for medical image segmentation using PyTorch and MONAI framework. This project implements a 3D UNet architecture for organ and tumor segmentation from medical imaging data.

## Project Overview

This repository contains code for training and evaluating a 3D UNet model for medical image segmentation. The project is specifically designed to work with medical imaging datasets (NIfTI format) and includes preprocessing, training, and visualization capabilities.

## Requirements

```text
matplotlib
numpy
tqdm
glob2
dicom2nifti
pytest-shutil
nibabel
pytorch
monai
```

## Project Structure

- `preprocess.py`: Contains data preprocessing pipeline including:
  - Loading NIfTI files
  - Data transformations (spacing, orientation, intensity scaling)
  - Dataset and DataLoader creation
  - Cache management for faster training

- `utilities.py`: Contains utility functions for:
  - Dice metric calculation
  - Weight calculation for loss functions
  - Training loop implementation
  - Patient data visualization
  - Pixel statistics calculation

- `train.py`: Main training script that:
  - Initializes the 3D UNet model
  - Sets up loss functions and optimizer
  - Runs the training loop

- `apple_mps_test.py`: Script to test MPS (Metal Performance Shaders) availability for MacOS users

## Model Architecture

The project uses a 3D UNet architecture with the following specifications:
- Input channels: 1
- Output channels: 2
- Feature channels: (16, 32, 64, 128, 256)
- Stride values: (2, 2, 2, 2)
- Residual units: 2
- Batch normalization

## Usage

1. Prepare your data in the following structure:
```
data_dir/
├── TrainVolumes/
│   └── *.nii.gz
├── TrainSegmentation/
│   └── *.nii.gz
├── TestVolumes/
│   └── *.nii.gz
└── TestSegmentation/
    └── *.nii.gz
```

2. Update the data paths in `train.py`:
```python
data_dir = 'path/to/your/data'
model_dir = 'path/to/save/results'
```

3. Run the training:
```bash
python train.py
```

## Features

- **Data Preprocessing**:
  - Automatic loading and preprocessing of NIfTI files
  - Configurable preprocessing parameters
  - Data augmentation and normalization
  - Caching support for improved performance

- **Training**:
  - Dice loss and Dice-CE loss support
  - Progress monitoring with metrics
  - Best model checkpoint saving
  - Support for both CPU and CUDA training
  - MacOS MPS support check

- **Visualization**:
  - Training and validation metrics plotting
  - Slice-by-slice visualization of volumes and segmentations
  - Patient data inspection capabilities

## GPU Support

The project supports:
- CUDA devices (NVIDIA GPUs)
- MPS (Apple Silicon Macs)
- CPU training (fallback)

## License

[Include your license information here]

## Contributing

[Include contribution guidelines here]

## Contact

[Include your contact information here]
