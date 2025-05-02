
# Human Motion Synthesis using Attention-based Autoencoder

This repository presents the implementation of our research paper "Human Motion Synthesis using Attention-based Autoencoder". The project aims to generate and forecast human motion sequences using an attention-enhanced autoencoder architecture trained on 3D motion capture data.

## Abstract

Human motion synthesis is a key task in computer vision with applications in animation, gaming, robotics, and AR/VR. Our work introduces a novel attention-based autoencoder architecture that models long-term dependencies in motion sequences better than traditional RNNs or plain transformers. We evaluate the model on the Human3.6M dataset and compare it with multiple baselines.

## Model Architecture

### Overview

Our Attention-based Autoencoder consists of the following components:
1. Encoder: Compresses motion sequences into latent representations using stacked GRU layers.
2. Attention Mechanism: Introduced between encoder and decoder to capture long-range temporal dependencies.
3. Decoder: Reconstructs future motion frames from the latent space.

### Components

- Input: 3D joint positions across T timesteps (shape: T x J x 3)
- Encoder: GRU/Transformer-based temporal encoder that outputs latent embedding Z
- Attention Layer: Scaled Dot-Product Attention across time
- Decoder: Auto-regressive GRU or MLP to predict future motion
- Loss: Mean Squared Error (MSE) with optional NPSS or bone-length regularization



## Installation

1. Clone the repository

```
git clone https://github.com/yourusername/human-motion-attention-autoencoder.git
cd human-motion-attention-autoencoder
```

2. Install dependencies

```
pip install -r requirements.txt
```

## Dataset

We use the Human3.6M dataset. To prepare:

1. Download the dataset from http://vision.imar.ro/human3.6m/description.php
2. Place the downloaded files under `data/raw`
3. Preprocess with:

```
python scripts/preprocess.py --input data/raw --output data/processed
```

## Training

Run the training script with:

```
python scripts/train.py --config configs/autoencoder_config.yaml
```

Common options:
- `--model`: Model type (`gru`, `lstm`, `transformer`, `autoencoder`)
- `--epochs`: Number of training epochs
- `--batch_size`: Training batch size

## Evaluation

Evaluate a trained model using:

```
python scripts/evaluate.py --checkpoint models/best_model.pth
```

Metrics used:
- MPJPE: Mean Per Joint Position Error
- NPSS: Normalized Power Spectrum Similarity



## Authors and Contact

- Ibram Abdelmalak*
- Fatima-Zahra El Yedmani*
- Simran Kaur*
- Sameer Sadruddin*
- Syed Wasif Murtaza Jafri*



## Future Work

- Multimodal human motion synthesis
- Generalization to unseen actions
- Pure transformer-based architectures without recurrence
