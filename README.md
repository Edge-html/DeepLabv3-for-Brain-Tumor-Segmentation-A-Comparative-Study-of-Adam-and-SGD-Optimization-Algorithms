# DeepLabv3+ for Brain Tumor Segmentation: Optimizer Comparative Study

This repository contains the implementation of a modified DeepLabv3+ architecture designed for semantic segmentation of brain tumors from MRI scans. The project explores the performance impact of different optimization strategies, specifically comparing **Adam** and **Stochastic Gradient Descent (SGD)**.

## Project Overview
Automated delineation of tumor boundaries is critical for clinical treatment planning. This study utilizes a deep learning approach to assist in consistent and timely medical decision-making using the BRISC 2025 dataset.

### Key Features
* **Architecture:** Simplified DeepLabv3+ featuring Atrous Spatial Pyramid Pooling (ASPP) and skip connections.
* **Optimization:** Comparative analysis between Adam (adaptive learning rate) and SGD (momentum-based).
* **Loss Function:** Focal Tversky Loss to address high class imbalance between tumor regions and healthy tissue.
* **Augmentation:** Real-time spatial invariance training using the Albumentations library (flips and rotations).

## Model Architecture
The model uses an encoder-decoder framework:
1.  **Encoder:** Extracts hierarchical features using dilated (atrous) convolutions to expand the receptive field without losing resolution.
2.  **Bottleneck (ASPP):** Processes high-level features through parallel branches with different dilation rates (6, 12) to capture multi-scale context.
3.  **Decoder:** Refines spatial details by concatenating low-level encoder features with upsampled high-level semantic maps.

## Performance Summary
| Metric | Baseline (SGD) | Tuned (Adam) | Improvement |
| :--- | :--- | :--- | :--- |
| **Dice Coefficient** | 0.3254 | 0.7816 | +140% |
| **IoU Score** | 0.1947 | 0.6440 | +230% |
| **Test Loss** | 0.6665 | 0.2805 | -58% |

[cite_start]*Data source: [cite: 263, 508]*

## Dependencies
* TensorFlow / Keras
* NumPy
* Albumentations
* Matplotlib (for visualization)

## How to Use
1.  **Preprocessing:** MRI images are standardized to 256x256 grayscale and normalized to [0, 1].
2.  **Training:** Run the optimization experiment loop to compare Adam ($5\times10^{-5}$) and SGD ($10^{-3}$).
3.  **Evaluation:** Performance is measured using Dice Coefficient and Intersection over Union (IoU) as primary overlap metrics.

## Authors
* Anna Maria Theresa C. Hermoso
* Bea Bianca O. Lastimosa
* Ian Carl P. Solana
* Rhudsel James M. Uy

*Course: CPE194 Special Topics in Computer Engineering, Mapúa Malayan Colleges Mindanao.*
