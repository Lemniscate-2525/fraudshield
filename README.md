FraudShield — Transaction Risk Engine

FraudShield is an end-to-end machine learning system for detecting fraudulent financial transactions using anomaly detection.
The system learns normal transaction behavior and flags suspicious activity based on reconstruction error.

Problem Statement

Financial institutions face significant losses due to fraudulent transactions. The key challenges are:

Fraud cases are extremely rare (~0.17% of total data)

Missing fraud (False Negative) is costly

Excess alerts (False Positive) degrade customer experience

Highly imbalanced datasets make traditional accuracy unreliable

FraudShield is designed to detect anomalies while maintaining a balance between detection rate and false alarms.

Dataset

Source: European Cardholders Dataset (Public)

Dataset Overview

Feature	Description
Total Transactions	284,807
Fraud Cases	492
Fraud Ratio	0.17%
Features	V1–V28 (PCA anonymized), Time, Amount
Target	Class (0 = Normal, 1 = Fraud)
Approach

FraudShield uses Unsupervised Anomaly Detection with Autoencoders.

Pipeline

Data preprocessing and normalization

Train Autoencoder only on normal transactions

Learn compressed representation of legitimate behavior

Calculate reconstruction error

If error > threshold → Flag as fraud

Model Architecture

Input: 30 features

Encoder: Dense layers (dimensionality reduction)

Latent space representation

Decoder: Reconstruction layers

Loss Function: Mean Squared Error (MSE)

Framework: TensorFlow / Keras

Evaluation Metrics

Due to extreme class imbalance, accuracy is not meaningful.

Primary Metrics

Precision

Recall

F1 Score

ROC-AUC

Confusion Matrix

Reconstruction Error Distribution

Objective:
Maximize fraud detection while controlling false positives.

Threshold-Based Risk Control

FraudShield supports adjustable decision thresholds:

Threshold	Effect
Lower	Higher fraud detection, more alerts
Higher	Fewer alerts, risk of missed fraud

This allows deployment based on business risk tolerance.

Project Structure
fraudshield/
│
├── data/                  # Dataset
├── logs/                  # Training logs
├── fraud_detection.ipynb  # End-to-end pipeline
├── model.h5               # Trained model
├── README.md
└── requirements.txt

How to Run
git clone https://github.com/Lemniscate-2525/fraudshield.git
cd fraudshield
pip install -r requirements.txt
jupyter notebook fraud_detection.ipynb

Key Features

Handles extreme class imbalance

Unsupervised anomaly detection

Threshold-based fraud scoring

End-to-end ML workflow

Saved production model artifact

Future Improvements

Real-time inference API (FastAPI/Flask)

Model monitoring & drift detection

Ensemble anomaly detection

Streaming transaction scoring

Use Cases

Banking fraud detection

Payment gateway monitoring

FinTech risk analytics

Transaction risk scoring systems

Author

Akshat Mishra
GitHub: https://github.com/Lemniscate-2525
