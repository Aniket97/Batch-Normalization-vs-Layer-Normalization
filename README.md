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

### 1) Training & Validation Loss/Accuracy vs Epoch (combined)

**What:**  
Two subplots (or a combined panel):  
- Training & validation **loss** vs epoch  
- Training & validation **accuracy** vs epoch  
Both include **BN and LN curves** on the same axes.

**Why:**  
Shows convergence speed, stability, and overfitting differences.

**How:**  
- Average across **≥5 seeds**  
- Plot **mean ± 1 std** (shaded region)  
- Mark learning-rate changes  
- Keep identical x-ranges for BN and LN  
- Provide raw (non-smoothed) curves in the supplement

---

### 2) Final Test Performance Across Architectures (bar plot)

**What:**  
A grouped bar plot:  
- Each group = architecture (MLP, CNN, LSTM, Transformer, …)  
- Bars = BN vs LN  
- Y-axis = final test accuracy (or task metric)

**Why:**  
Provides a single-number cross-architecture comparison.

**How:**  
- Report **mean ± std**  
- Add statistical significance markers (paired t-test / Wilcoxon)

---

### 3) Sensitivity to Batch Size (line plot)

**What:**  
- X = batch size (8, 16, 32, 64, 128, …)  
- Y = final validation accuracy  
- Lines = BN vs LN

**Why:**  
Highlights BN’s dependence on batch statistics.

**How:**  
- Points show mean; vertical error bars show std  
- For tiny batches, annotate with “mini-batch too small for BN”

---

### 4) Convergence Speed: Time/Epochs to Reach Threshold

**What:**  
Plot epochs (or wall-clock time) required to reach a target metric (e.g., 80% val accuracy).  
Use a bar plot or CDF.

**Why:**  
Shows the practical training-time advantage/disadvantage of BN vs LN.

**How:**  
- Treat missing targets as **censored**  
- Show them separately (e.g., hatched bars or >max marker)  
- Report **median + IQR**

---

### 5) Batch Statistics Stability (BN) vs Equivalent LN Metric

**What:**  
For a representative channel/unit:  
- Plot per-mini-batch **mean** of activations  
- Plot per-mini-batch **variance**  
Overlay BN vs LN.

**Why:**  
Shows noisy batch-stat fluctuations of BN vs stable per-example LN stats.

**How:**  
- Sample a few channels  
- Plot time-series across batches  
- Add a zoomed-in inset for noisy regions

---

### 6) Variability Across Random Seeds (violin/boxplot)

**What:**  
A violin or boxplot:  
- X = normalization method (BN, LN)  
- Y = final test accuracy across seeds/hyperparameter repeats

**Why:**  
Reveals reproducibility and sensitivity to random factors.

**How:**  
- Use ≥5 seeds (preferably 10)  
- Show median, quartiles, outliers  
- Report effect size and p-value

---

## Quick Implementation Tips (applies to all plots)

- Use paired seeds for fair BN vs LN comparison.  
- Always report **N (seeds)** and include raw values in an appendix table.  
- Use a consistent color scheme and labeling (e.g., BN = blue, LN = orange).  
- Save per-step logs for CI computation and flexible re-plotting.  
- Add brief captions under figures including dataset + hyperparameters (batch size, LR, optimizer).
