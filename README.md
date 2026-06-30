# Brain MRI Modality Translation Using CycleGAN

This project implements a **CycleGAN** (Cycle-Consistent Generative Adversarial Network) for translating brain MRI scans between **T1 and T2 modalities** without requiring paired training data. Since acquiring perfectly aligned T1-T2 image pairs is often impractical in clinical settings, this unpaired image-to-image translation approach offers a practical alternative for cross-modality synthesis in medical imaging.

## Overview

The model learns bidirectional mappings (T1 → T2 and T2 → T1) using two generator-discriminator pairs trained jointly with cycle-consistency loss, ensuring that an image translated to the other modality and back reconstructs the original.

## Architecture

- **Generators:** Dual U-Net architectures with skip connections for preserving spatial detail
- **Normalization:** Instance normalization for stable training on grayscale medical images
- **Discriminators:** PatchGAN discriminators for realistic local texture evaluation
- **Loss functions:** Adversarial loss + cycle-consistency loss + identity loss to maintain anatomical structure across translations

## Dataset

- Brain MRI scans in T1 and T2 modalities
- Images resized to 64×64 grayscale and normalized to [-1, 1]

## Training

- Framework: TensorFlow / Keras
- Epochs: 300
- Optimizer: Adam (lr=2e-4, β1=0.5)
- Checkpointing implemented for training resumption

## Tech Stack

Python, TensorFlow, Keras, NumPy, scikit-image, Matplotlib, imageio

## Results

Generated image samples are saved per epoch to visualize translation quality over training, with an animated GIF compiled to show progressive improvement.
