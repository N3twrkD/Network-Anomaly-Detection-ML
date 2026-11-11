# Network Anomaly Detection Using Machine Learning & Deep Learning

## Project Overview

This project explores unsupervised Machine Learning and Deep Learning techniques to identify anomalous network traffic and detect potential cyber attacks.

Using the UNSW-NB15 network traffic dataset, the project trains models using normal network traffic and evaluates their ability to identify malicious or abnormal connections.

Two anomaly detection approaches are implemented and compared:

- **Isolation Forest** – An unsupervised machine learning algorithm that identifies anomalies by isolating unusual data points.
- **Autoencoder** – A neural network trained to reconstruct normal network traffic. Higher reconstruction errors indicate potentially anomalous traffic.

The objective is to compare both approaches and understand their effectiveness in identifying abnormal network behaviour without using attack labels during model training.

## Technologies Used

- Python
- Pandas & NumPy
- Scikit-learn
- TensorFlow / Keras
- Matplotlib & Seaborn
- Google Colab

## Dataset

The project uses the **UNSW-NB15 dataset**, developed by the Australian Centre for Cyber Security.

The dataset contains normal network traffic and nine attack categories:

- Fuzzers
- Analysis
- Backdoors
- DoS
- Exploits
- Generic
- Reconnaissance
- Shellcode
- Worms

Dataset source: [UNSW-NB15 Dataset – Official Research Source](https://research.unsw.edu.au/projects/unsw-nb15-dataset)

The notebook downloads the training and testing CSV files automatically from a public GitHub mirror.

## Project Workflow

### 1. Data Collection
- Download the UNSW-NB15 training and testing datasets.
- Combine both datasets into a single DataFrame.
- Remove the identifier column.
- Analyse normal and attack traffic distribution.

### 2. Data Preparation
- Remove duplicate records.
- Separate normal traffic from attack traffic.
- Allocate 70% of normal traffic for model training.
- Use the remaining 30% of normal traffic together with all attack traffic for evaluation.

An important aspect of this project is that **only normal network traffic is used during model training**.

### 3. Feature Engineering & Preprocessing
- Separate numerical and categorical features.
- Apply StandardScaler to numerical features.
- Apply One-Hot Encoding to categorical features.
- Fit the preprocessing pipeline using normal training data only.
- Transform the evaluation dataset using the same preprocessing pipeline.

### 4. Isolation Forest
- Implement an Isolation Forest model.
- Configure 200 estimators.
- Train using normal network traffic only.
- Generate anomaly scores for the evaluation dataset.
- Identify unusual network connections based on anomaly scores.

### 5. Deep Learning – Autoencoder
- Build a neural network using TensorFlow/Keras.
- Implement an encoder-decoder architecture.
- Train the model to reconstruct normal network traffic.
- Use Mean Squared Error (MSE) as the reconstruction loss.
- Apply early stopping to help prevent overfitting.
- Calculate reconstruction errors to identify potential anomalies.

### 6. Anomaly Detection & Threshold Selection

Both models generate anomaly scores to identify unusual network activity.

A threshold is selected using the 95th percentile of anomaly scores calculated from normal training traffic.

Connections exceeding the selected threshold are classified as potential anomalies.

### 7. Model Evaluation & Comparison

Both approaches are evaluated using:

- True Positive Rate (TPR / Recall)
- False Positive Rate (FPR)
- Precision
- F1-score
- Accuracy
- ROC Curve and AUC
- Precision-Recall Curve
- Confusion Matrix

A final comparison table and visualisation are generated to assess the performance of Isolation Forest and Autoencoder.

## How to Run

The notebook is designed to run in **Google Colab**.

1. Open the notebook in Google Colab.
2. Select Runtime → Change runtime type.
3. Select GPU (optional, recommended for Autoencoder training).
4. Run all cells from top to bottom.

The notebook automatically downloads the dataset from a public GitHub mirror. No manual dataset upload is required.

If the GitHub mirror becomes unavailable, the official UNSW-NB15 training and testing CSV files can be downloaded and uploaded manually.

## Repository Structure

```text
Network-Anomaly-Detection/
│
├── 3_Anomaly_Detection.ipynb
└── README.md
```

## Learning Outcomes

This project demonstrates practical implementation of:

- Network anomaly detection.
- Unsupervised Machine Learning.
- Network traffic analysis.
- Isolation Forest classification.
- Deep Learning using Autoencoders.
- Numerical feature scaling and categorical encoding.
- Anomaly scoring and threshold selection.
- Model evaluation using cybersecurity metrics.
- Comparative analysis of traditional ML and Deep Learning techniques.

## Disclaimer

This project is developed for educational and research purposes as part of cybersecurity studies. The models demonstrate anomaly detection techniques using a publicly available network traffic dataset. They are not intended to replace production-grade Network Intrusion Detection Systems (NIDS).

---

**Project Area:** Cybersecurity | Network Security | Anomaly Detection | Unsupervised Machine Learning | Deep Learning
