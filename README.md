# Latent Mutual Information (LMI) on 3k PBMC scRNA-seq

This repository implements an information-theoretic pipeline to explore high-dimensional dependencies in single-cell transcriptomic data using the **Latent Mutual Information (LMI)** framework, inspired by the paper:

**"Approximating mutual information of high-dimensional variables using learned representations"**  
by *Gokul Gowri et al.* ([arXiv:2409.02732](https://arxiv.org/abs/2409.02732))

---

## 🔬 Objective

To test the capacity of LMI to capture and reveal biologically meaningful transitions and dependencies in the **3k PBMC** dataset by estimating **mutual information (MI)** between compressed latent representations.

---

## 🧠 What is LMI?

Latent Mutual Information (LMI) is a theoretically-grounded neural architecture designed to approximate the mutual information (MI) between high-dimensional variables by learning compressed, low-dimensional representations that preserve dependency structure.

### Key components:
- Neural encoders learn latent projections of high-dimensional inputs.
- A non-parametric MI estimator (e.g. Kraskov–Stögbauer–Grassberger, KSG) quantifies MI in the latent space.
- The architecture avoids autoencoders or contrastive learning, instead emphasizing interpretability and theoretical consistency.

---

## 🧪 Dataset

- **3k PBMC (Peripheral Blood Mononuclear Cells)** from 10x Genomics.
- Preprocessed using standard scRNA-seq pipelines (e.g. Scanpy or Seurat).
- Optionally, the UMAP or PHATE manifold is used for entropy smoothing and visualization.

---

## 🔁 Pipeline Overview

1. **Data Preprocessing**  
   Filter and normalize the scRNA-seq data (log1p, HVG selection).

2. **Latent Representation Learning**  
   Train simple neural networks (MLPs) to encode cell states into low-dimensional latent vectors.

3. **Mutual Information Estimation**  
   Use the KSG estimator on the latent embeddings to approximate MI between:
   - Different cell types
   - Pseudotime segments
   - Cluster transitions

4. **Smoothing and Visualization**  
   Apply spatial smoothing to entropy and MI estimates along the learned manifold. Visualize where information flow or dependency structure changes.

---

## 📦 Dependencies

- `numpy`, `scipy`
- `scikit-learn`
- `scanpy`
- `pynndescent`, `umap-learn`
- `torch` or `tensorflow` (for encoder networks)
- `pyitlib` (optional, for MI estimation)

---

## 📈 Output

- Mutual Information dynamics across cell states.
- Heatmaps of MI along pseudotime or cell clusters.
- Manifold plots highlighting information-rich regions (e.g., transitions, bifurcations).

---

## 📚 References

- Gokul Gowri et al. *Approximating Mutual Information of High-Dimensional Variables Using Learned Representations*. arXiv:2409.02732
- Kraskov, Stögbauer & Grassberger. *Estimating mutual information*. Phys. Rev. E 2004.

---

## ✨ Future Work

- Apply LMI to trajectory inference or RNA velocity-based representations.
- Compare with contrastive MI estimators (e.g., InfoNCE, MINE).
- Extend to multi-omics integration.

