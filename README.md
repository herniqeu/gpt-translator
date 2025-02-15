# Portuguese-English Neural Machine Translation

## Overview
Implementation of a Transformer-based Neural Machine Translation (NMT) model for Portuguese to English translation using TensorFlow. The model follows the architecture described in "Attention Is All You Need" paper, with modifications for the specific language pair.

## Architecture
- **Model Type**: Transformer
- **Encoder Layers**: 4
- **Decoder Layers**: 4
- **Attention Heads**: 8
- **Model Dimension (d_model)**: 128
- **Feed Forward Network Size**: 512
- **Dropout Rate**: 0.1

## Training Details
- **Hardware**: 8x NVIDIA H100 GPUs
- **Dataset**: TED Talks PT-EN from TensorFlow Datasets
  - Training: ~50k sentence pairs
  - Validation: ~1k sentence pairs
  - Test: ~1k sentence pairs
- **Batch Size**: 64
- **Maximum Tokens**: 128
- **Training Time**: 20 epochs
- **Optimizer**: Adam with custom learning rate schedule
- **Learning Rate**: Custom schedule with warmup steps

## Data Processing
- Tokenization using TensorFlow Text
- Maximum sequence length: 128 tokens
- Dynamic batching with padding
- Token masking for efficient training

## Project Structure
```
├── transformer_pt_en.py     # Main training script
├── translator/             # Saved model directory
├── evaluation/            # Evaluation scripts and results
└── README.md             # This file
```