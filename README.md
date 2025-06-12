📡 Model-Based Deep Learning for Model Order Selection

This repository presents a hybrid model-based deep learning approach for model order selection, developed as part of the Model-Based Deep Learning (MBDL) course project at Ben-Gurion University.

Our approach enhances classical hypothesis testing (e.g., MDL criterion) with learned representations to improve performance in challenging settings such as coherent sources, low SNR, and short observation durations.

📖 Overview

🎯 Goal

Accurately estimate the number of signal sources impinging on an array of antennas using both classic statistical methods and deep learning.

🔍 Classical Limitation

Methods like MDL and AIC degrade in practical scenarios:

When sources are coherent (e.g., highly correlated)

Under low SNR or few snapshots

💡 Our Contribution

We propose a deep-learning-enhanced architecture that:

Computes both the empirical autocorrelation and sample covariance

Maps the autocorrelation through a CNN autoencoder to learn a surrogate covariance

Combines the learned and classic covariances into a hybrid matrix

Passes this to an MDL test followed by an MLP classifier for robust source count prediction

🖥️ System Architecture



Pipeline:

Input Signal $x(t)$

Compute:

Empirical autocorrelation $\hat{R}_X[\tau]$

Sample covariance $R_X$

CNN autoencoder processes $\hat{R}_X[\tau]$ to produce $\hat{R}(X;\theta)$

Merge via $\tilde{R}_X = \lambda \cdot \hat{R}(X;\theta) + (1 - \lambda) \cdot R_X$

MDL test produces a test vector

MLP predicts the number of sources

📊 Results Overview

We evaluated performance across:

SNR levels (fixed $T$)

Snapshot counts (fixed SNR)

Both coherent and non-coherent source scenarios

Key Findings:

Our MBDL model consistently outperforms classical MDL, especially under coherence

Generalized models trained on a single SNR or $T$ generalize well across varying test conditions

🛠️ Implementation Details

Dataset: $|\mathcal{D}| = 3000$ samples

Loss: Cross-Entropy (with weighted labels for balance)

Optimizer: Adam

Learning Rate: $10^{-4}$

Batch Size: 64

Epochs: 100

📚 References

Arad Gast et al., "Near Field Localization via AI-Aided Subspace Methods", 2025.

Julian Merkofer et al., "Deep Augmented MUSIC Algorithm for Data-Driven DoA Estimation", ICASSP 2022.

👥 Contributors

Aviv Ben Ari

Dor Patel

For questions, issues, or access to trained models, feel free to contact us or open an issue. Contributions are welcome! 🚀

