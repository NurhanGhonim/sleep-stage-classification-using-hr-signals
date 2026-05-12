# Sleep Stage Classification Using Heart-Related Physiological Signals

## Overview

This project implements a deep learning pipeline for automated sleep stage classification using heart-related physiological signals. The model processes sequential biosignals, extracts physiological features, and classifies sleep into five stages: Wake, N1, N2, N3, and REM.

The system combines physiological feature engineering with sequential neural networks to capture temporal dependencies in sleep dynamics.

---

## Motivation

Sleep is essential for physiological and cognitive health. Traditional sleep staging using polysomnography (PSG) is:

- Expensive
- Clinically complex
- Sensor intensive
- Manually scored

This project explores a wearable-friendly alternative using heart-related signals for scalable sleep monitoring.

---

## Dataset

- Subjects: 10  
- Total epochs: 12,758  
- Epoch duration: 30 seconds  
- Signal length: 7680 samples  

### Class Distribution

- Wake: 5,569  
- N1: 942  
- N2: 4,117  
- N3: 869  
- REM: 1,261  

---

## Key Challenge

The dataset is highly imbalanced, especially in N1 and N3 stages. To address this, class-weighted loss is used to reduce bias toward majority classes and improve minority stage detection.

---

## Methodology

### 1. Signal Processing

- EDF signals processed using MNE
- Sleep annotations extracted from XML files
- Segmentation into 30-second epochs

---

### 2. Feature Engineering

Each epoch is transformed into an 8-dimensional feature vector:

- Mean
- Standard Deviation
- Range
- RMSSD
- MAD
- Energy
- Skewness
- Slope

This reduces noise and improves computational efficiency while preserving physiological meaning.

---

### 3. Sequence Construction

- Sequence length: 15 epochs  
- Temporal context: 7.5 minutes  

Each input represents a sequence of physiological states to capture sleep transitions over time.

---

## Model Architecture

The model is a Bidirectional GRU-based sequential neural network.

### Input Layer
- Shape: (15, 8)

### GRU Layers

- Bidirectional GRU (160 units)
  - return_sequences=True
  - Learns long-term temporal dependencies

- Bidirectional GRU (80 units)
  - Produces compact temporal representation

### Dense Layer
- 160 units
- ReLU activation

### Regularization
- Batch Normalization
- Dropout

### Output Layer
- 5 neurons
- Softmax activation

---

## Model Intuition

The model learns sleep as a temporal process:

- It analyzes sequences of physiological signals
- Captures transitions between sleep stages
- Uses bidirectional context for better temporal understanding
- Outputs probability distribution over sleep stages

---

## Training Configuration

- Loss: Sparse Categorical Crossentropy  
- Optimizer: Adam  
- Gradient clipping: 1.0  
- Class weights: applied  

---

## Evaluation Metrics

- Accuracy  
- Precision  
- Recall  
- F1-score  
- Confusion Matrix  

---

## Key Advantages

- Wearable-compatible design  
- Low-dimensional feature representation  
- Temporal modeling of sleep stages  
- Robust handling of class imbalance  
- Efficient and scalable architecture  

---

## Technologies Used

- Python  
- TensorFlow / Keras  
- MNE  
- NumPy  
- Pandas  
- Scikit-learn  

---

## Conclusion

This project demonstrates that heart-related physiological signals combined with Bidirectional GRU networks can effectively classify sleep stages in a scalable and non-invasive manner.

---

## Future Work

- Multimodal fusion with EEG and respiration  
- Real-time wearable deployment  
- Model compression for edge devices  
- Improved cross-subject generalization  
