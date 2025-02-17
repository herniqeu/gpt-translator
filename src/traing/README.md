# Portuguese-English NMT Training Performance Analysis: CPU vs GPU Implementation

## Hardware Configurations
### CPU Implementation
- Hardware: Single CPU (specs not provided)
- Runtime: >3 hours
- Epochs completed: 3

### GPU Implementation
- Hardware: 8x NVIDIA H100 GPUs
- Runtime: ~2 hours
- Epochs completed: 20

## Performance Metrics Comparison

### Training Speed
| Metric           | CPU Implementation | GPU Implementation |
|-----------------|-------------------|-------------------|
| Time per epoch  | ~60 minutes       | ~6 minutes        |
| Steps per second| ~11s/step         | ~470ms/step      |
| Batch processing| 810/810 batches   | 810/810 batches  |

### Training Progress

#### CPU Implementation (3 epochs)
```
Epoch 1: loss: 7.6928 - masked_accuracy: 0.0986 - val_loss: 4.9179 - val_masked_accuracy: 0.2660
Epoch 2: loss: 4.6064 - masked_accuracy: 0.3005 - val_loss: 3.9365 - val_masked_accuracy: 0.3717
Epoch 3: loss: 3.7789 - masked_accuracy: 0.3901 [Incomplete training]
```

#### GPU Implementation (selected epochs)
```
Epoch 1: loss: 7.6917 - masked_accuracy: 0.0883 - val_loss: 4.8816 - val_masked_accuracy: 0.2729
Epoch 2: loss: 4.5777 - masked_accuracy: 0.3045 - val_loss: 3.8962 - val_masked_accuracy: 0.3786
...
Epoch 19: loss: 0.6697 - masked_accuracy: 0.8274 - val_loss: 2.7767 - val_masked_accuracy: 0.5729
Epoch 20: loss: 0.6082 - masked_accuracy: 0.8417 - val_loss: 2.8805 - val_masked_accuracy: 0.5616
```

## Key Observations

1. **Processing Speed**
   - GPU implementation is approximately 23x faster per step (470ms vs 11s)
   - Enables processing of significantly more epochs in less total time
   - Consistent step times throughout training on GPU

2. **Training Progress**
   - Both implementations show similar early-epoch performance
   - Initial convergence patterns are comparable
   - GPU implementation achieves significantly better final results due to completed training
   - Final accuracy reaches 84.17% (training) and 56.16% (validation)

3. **Resource Utilization**
   - CPU implementation is resource-constrained, limiting training to 3 epochs
   - GPU implementation efficiently utilizes parallel processing
   - H100s enable full training completion with 20 epochs

4. **Cost-Benefit Analysis**
   - Despite higher hardware costs, GPU implementation provides:
     - Better model convergence
     - More comprehensive training
     - Faster iteration cycles for experimentation
     - Higher final model quality

5. **Practical Implications**
   - GPU setup enables rapid prototyping and experimentation
   - CPU implementation might be suitable for small-scale testing only
   - Full training on CPU would require approximately 20 hours for comparable epochs
   - GPU implementation allows for more hyperparameter tuning in the same timeframe

## Conclusion
The GPU implementation demonstrates substantial advantages in both training speed and final model quality. While the CPU implementation shows similar early-epoch patterns, the ability to complete full training with 20 epochs in less time makes the GPU setup significantly more practical for production-level model development. The final model achieves considerably better accuracy metrics, justified by the investment in GPU infrastructure.