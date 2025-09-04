# Cyber IDS 2018 – Machine Learning Intrusion Detection

This project implements a **machine learning pipeline** for intrusion detection on the [CSE-CIC-IDS2018 dataset](https://www.kaggle.com/datasets/dhoogla/csecicids2018).  
The goal is to build a memory-efficient and well-calibrated classifier capable of detecting a wide range of network attacks with **balanced precision and recall**, despite the extreme class imbalance of the dataset.

---

## Project Highlights

- **Dataset**: [CSE-CIC-IDS2018 on Kaggle](https://www.kaggle.com/datasets/dhoogla/csecicids2018).  
- **Challenges**:
  - Highly imbalanced class distribution (Benign vs. rare attacks like FTP-Bruteforce, SQL Injection).
  - Risk of data leakage (e.g., derived labels like `IsAttack`).
  - Memory constraints (1.3M+ flows).
- **Solutions**:
  - **Numeric-only features** with downcasting to save memory.
  - **Rebalancing**: RandomUnderSampler + targeted SMOTE for small classes.
  - **Classifier**: LightGBM (efficient and robust for large tabular data).
  - **Calibration**:  
    - Prior correction with partial exponent (γ).  
    - Post-processing with thresholds (Benign gate, Infilteration threshold).  
  - **Evaluation**: Classification reports, confusion matrices (counts, recall view, precision view), top confusions.

---

## Results (Key Takeaways)

- **Benign**: Precision & recall ~100% (minimal false alarms).

- **Major attacks (DDoS, DoS, SSH, Bot)**: F1 ~1.00.

- **Medium attacks (Brute Force Web/XSS, SQL Injection)**: F1 between 0.65–0.90 despite small support.

- **Rare attacks (FTP-Bruteforce, SlowHTTPTest)**: F1 low (~0.20) due to <20 samples.

- **Macro-F1 ≈ 0.85** overall — strong performance on an imbalanced real-world dataset.

---

## References
- **Dataset**: [CSE-CIC-IDS2018 on Kaggle](https://www.kaggle.com/datasets/dhoogla/csecicids2018).
- **Original dataset description**: [Canadian Institute for Cybersecurity](https://www.unb.ca/cic/datasets/ids-2018.html?utm_source=chatgpt.com).
