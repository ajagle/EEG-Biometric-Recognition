# EEG-Biometric-Recognition
A Biometric Person Recognition System based on Brainwave (EEG) signals, developed as part of an MSc Data Science dissertation.  
This project explores EEG-based biometrics for reliable individual identification using machine learning techniques and session-disjoint validation.

---

## 🧩 Project Overview
This repository implements a **biometric person recognition system** using **Electroencephalogram (EEG)** signals.  
The system extracts EEG-based spectral features (absolute and relative band power) and trains classifiers to identify individuals based on their brainwave patterns.

The project focuses on improving **cross-session generalization**, ensuring that the model performs well not only within a recording session but also across different days and recording sessions — a critical factor for real-world biometric reliability.

---

## 🎯 Objectives
- Develop a person identification system using EEG data.  
- Extract meaningful spectral features from EEG signals.  
- Evaluate traditional machine learning models (SVM, Random Forest).  
- Compare session-overlapping and session-independent evaluations.  
- Demonstrate robustness and generalization across EEG sessions.

---

## 📚 Datasets
### 1. **Kaggle EEG Dataset**
- 36 subjects, single-session recordings.
- Used for initial model training and validation.
- Source: [Kaggle EEG Dataset](https://www.kaggle.com/)

### 2. **PhysioNet EEG Motor Movement/Imagery Dataset**
- 109 subjects with multiple sessions.
- Multi-task EEG dataset allowing session-disjoint testing.
- Source: [PhysioNet EEG Dataset](https://physionet.org/content/eegmmidb/1.0.0/)

---

## ⚙️ Methodology

### 1. **Preprocessing**
- Band-pass filtering and noise reduction.
- Data segmentation into **5-second overlapping windows**.
- Feature extraction from **19 EEG channels**.

### 2. **Feature Extraction**
- Absolute and relative band power across standard EEG bands:
  - Delta (0.5–4 Hz)
  - Theta (4–8 Hz)
  - Alpha (8–13 Hz)
  - Beta (13–30 Hz)
  - Gamma (30–50 Hz)

### 3. **Classification Models**
- **Support Vector Machine (SVM)** with RBF kernel  
- **Random Forest Classifier**

### 4. **Evaluation Protocols**
Six evaluation strategies were implemented to measure generalization:
1. Random k-Fold Cross-Validation  
2. 60/20/20 Train-Validation-Test Split  
3. Cross-Validation by Session  
4. Leave-One-Subject-Out (LOSO)  
5. Hybrid Session-Subject Split  
6. Randomized-Label Control Test (sanity check)

---

## 📁 Repository Structure
EEG-Biometric-Recognition/
│
├── 1_Preprocessing.ipynb
├── 2_Feature_Extraction.ipynb
├── 3_Model_Training.ipynb
├── 4_Validation_Protocols.ipynb
├── 5_Session_Disjoint.ipynb ← Final session-aware evaluation
│
├── /data/
│ ├── kaggle_eeg/
│ ├── physionet_eeg/
│
├── /results/
│ ├── accuracy_reports.csv
│ ├── confusion_matrix.png

##📊 Results Summary
| Evaluation Protocol             | Dataset                  | Accuracy (%) |
| ------------------------------- | ------------------------ | ------------ |
| Random k-Fold CV                | Kaggle EEG (36 subjects) | 98.7         |
| Train/Val/Test Split (60/20/20) | Kaggle EEG               | 98.1         |
| Random k-Fold (Window-level)    | PhysioNet                | 97.6         |
| Session-Disjoint Split          | PhysioNet                | **92.3**     |
| Leave-One-Session-Out (LOSO)    | PhysioNet                | 91.8         |

##🔮 Future Work
1. Integrate deep learning (CNN/LSTM) models for automated feature extraction.
2. Explore adversarial or transfer learning for session-invariant representations.
3. Deploy in real-time BCI (Brain-Computer Interface) scenarios.
4. Expand dataset size for better long-term generalization.
