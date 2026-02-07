# FraudShield — Transaction Risk Engine

**FraudShield** is an end-to-end machine learning system for detecting fraudulent financial transactions using anomaly detection techniques.  
The system learns normal transaction behavior and flags suspicious activity based on reconstruction error.

---

## Business Problem

Financial institutions lose billions annually due to fraudulent transactions. The core challenges include:

- Fraud cases are extremely rare (**~0.17% of total data**)
- Missing fraud (**False Negatives**) results in financial loss
- Excess alerts (**False Positives**) impact customer experience
- Highly imbalanced data makes **accuracy an unreliable metric**

FraudShield focuses on **detecting rare anomalies while maintaining operational efficiency**.

---

## Dataset

**Source:** European Cardholder Transactions Dataset

| Attribute | Value |
|----------|------|
| Total Transactions | 284,807 |
| Fraud Cases | 492 |
| Fraud Ratio | 0.17% |
| Features | V1–V28 (PCA anonymized), Time, Amount |
| Target | Class (0 = Normal, 1 = Fraud) |

Dataset Download:
https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

Download the dataset and place it inside the /data directory before running the notebook.


---

## Approach

FraudShield uses **Unsupervised Anomaly Detection** via an Autoencoder.

### Pipeline

1. Data preprocessing and normalization  
2. Train model **only on normal transactions**  
3. Learn compressed representation of legitimate behavior  
4. Compute **reconstruction error**  
5. Apply threshold to classify anomalies  


---

## Model Architecture

- Input: 30 features  
- Encoder: Dense layers (dimensionality reduction)  
- Latent representation  
- Decoder: Reconstruction layers  
- Loss Function: **Mean Squared Error (MSE)**  
- Framework: **TensorFlow / Keras**

---

## Evaluation Metrics

Due to extreme class imbalance, accuracy is not meaningful.

**Primary Metrics**

- Precision  
- Recall  
- F1 Score  
- ROC-AUC  
- Confusion Matrix  

**Objective:**  
Maximize fraud detection while controlling false positives.

---

## Threshold-Based Risk Control

| Threshold | Effect |
|----------|--------|
| Lower | Higher fraud detection, more false positives |
| Higher | Fewer alerts, risk of missed fraud |

This allows deployment based on business risk tolerance.

---

## Project Structure

fraudshield/
│
├── data/
├── logs/
├── fraud_detection.ipynb
├── model.h5
├── README.md
└── requirements.txt


---

## How to Run

```bash
git clone https://github.com/Lemniscate-2525/fraudshield.git
cd fraudshield
pip install -r requirements.txt
jupyter notebook fraud_detection.ipynb

