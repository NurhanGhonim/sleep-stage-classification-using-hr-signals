# Heart Rate Based Sleep Stage Classification

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)
[![MNE](https://img.shields.io/badge/MNE-Python-007ACC.svg)](https://mne.tools/)

A deep learning pipeline for **automatic sleep stage classification** using only **Heart Rate (HR)** signal from the MESA dataset.

---

## 📋 Project Overview

This project classifies sleep stages (Wake, N1, N2, N3, REM) using **Heart Rate variability features** extracted from EDF files. It combines traditional feature engineering with a Bidirectional GRU model, achieving robust performance despite using only one physiological channel.

### Key Features
- Full data preprocessing pipeline (EDF + XML annotations)
- Hand-crafted HRV feature extraction
- Sequence modeling with Bidirectional GRU
- Class weighting to handle severe class imbalance (especially N1)
- Professional logging and visualization
- Ready for GitHub and further research

---

##  Project Structure

```bash
mesa-hr-sleep-staging/
├── main.py                     # Main script (run this)
├── best_sleep_model.keras      # Best saved model
├── requirements.txt
├── README.md
├── results/
│   ├── confusion_matrix.png
│   └── training_curves.png
└── Dataset/                    # (Not included - add your own)
    ├── signals/
    └── annotations/

```
Installation

Clone the repository:

```Bash
git clone https://github.com/NurhanGhonim/sleep-stage-classification-using-hr-signals.git
cd mesa-hr-sleep-staging
```

Install dependencies:
```bash
Bashpip install -r requirements.txt
```

 Requirements
 ```txt
txttensorflow>=2.10.0
mne>=1.0.0
numpy
pandas
scikit-learn
matplotlib
seaborn
```

## How to Run
```bash
Bashpython main.py
```
The script will:

Load and parse EDF + XML files
Extract HR epochs and features
Train the Bidirectional GRU model
Evaluate and generate plots

## Dataset

Dataset: MESA (Multi-Ethnic Study of Atherosclerosis) Sleep Dataset
Signal Used: Heart Rate (HR) only
Annotation: XML scored events
Epoch Length: 30 seconds
Classes: Wake (0), N1 (1), N2 (2), N3 (3), REM (4)


## Model Architecture

Input: Sequence of 15 hand-crafted HRV features
Architecture: Bidirectional GRU (160 → 80)
Regularization: Dropout + L2 + Batch Normalization
Optimizer: Adam (lr=0.0015) with gradient clipping


 ## Results
(Add your best results here after training)
Example:

Test Accuracy: 82.4%
Macro F1-Score: 0.78


## Future Improvements

Add more HRV features (Frequency domain, Poincaré plot, etc.)
Patient-wise cross-validation
Transformer or Temporal Convolutional Network (TCN)
Real-time inference support
Integration with wearable devices
Add another signal/signals


## License
This project is licensed under the MIT License — see the LICENSE file for details.

## Acknowledgments

MESA Study researchers and data providers
MNE-Python team
TensorFlow community


## Contact
Nurhan Ghonim

GitHub: @NurhanGhonim
