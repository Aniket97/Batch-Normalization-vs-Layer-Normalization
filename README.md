# Batch-Normalization-vs-Layer-Normalization

## Architectures that are compared
- Mulit-Layer Perceptron
- Simple CNN
- LSTM
- GRU
- Transformer
- ResNet-18

## 📊 Plots Used in the BN vs LN Comparison

Below are the 6 key plots included for every architecture.

---

### 1) Training & Validation Loss vs Epoch (Combined)

**What:**  
Two subplots (or a combined panel):  
- Training & validation **loss** vs epoch   

**Why:**  
Shows convergence speed.


### 2) Training & Validation Accuracy vs Epoch (Combined)

**What:**  
Two subplots (or a combined panel):  
- Training & validation **Accuracy** vs epoch   

**Why:**  
Shows convergence speed, stability and overfitting.

---

### 3) Sensitivity to Batch Size (line plot)

**What:**  
- X = batch size (8, 16, 32, 64, 128, …)  
- Y = final validation accuracy  
- Lines = BN vs LN

**Why:**  
Highlights BN’s dependence on batch statistics.

---
### 4) Global Gradient Norm vs Training Step (line plot)

- X: training step / epoch
- Y: global L2 norm of all gradients ( L2 norm of gradient is square_root(sum(square(gradient))) )

**Why:**  
Shows overall gradient stability; BN sometimes causes noisy spikes.

### 5) Layer Gradient Distribution (violin / histogram) at several checkpoints

- X: layer index
- Y: distribution (violin) of gradient values or gradient magnitudes (sample at epoch 1, mid, final)

**Why:** 
Visualizes if gradients are heavy-tailed or centered near zero (vanishing).

---

## Quick Implementation Tips (applies to all plots)

- Use paired seeds for fair BN vs LN comparison.  
- Always report **N (seeds)** and include raw values in an appendix table.  
- Use a consistent color scheme and labeling (e.g., BN = blue, LN = orange).  
- Save per-step logs for CI computation and flexible re-plotting.  
- Add brief captions under figures including dataset + hyperparameters (batch size, LR, optimizer).
