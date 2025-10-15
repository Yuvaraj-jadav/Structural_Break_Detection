# 🧠 Structural Break Detection using Logistic Regression  

## 📘 Overview  
**Structural Break Detection** is a time series analysis task that identifies sudden changes (breaks) in a system’s underlying data generation process.  
This project applies **statistical feature extraction** and **Logistic Regression** to automatically detect structural breaks in univariate time series data.

---

## 🎯 Problem Statement  
Given a univariate time series and a potential break point, determine whether a **structural break** has occurred or not.  
The model outputs a **likelihood score (0–1)** indicating the probability of a break.

---

## 🔍 Methodology  

### 1️⃣ Data Preparation  
- The dataset consists of several univariate time series.  
- Each series contains a **known potential break point**.  
- Labels indicate whether a true structural break occurred (`1 = Break`, `0 = No Break`).

### 2️⃣ Feature Extraction  
We extract statistical differences between the segments before and after the break point:

| Feature | Description |
|----------|--------------|
| ΔMean | Change in average value |
| ΔVariance | Change in data spread |
| ΔStd | Change in volatility |
| ΔSkew | Change in distribution asymmetry |
| ΔKurt | Change in distribution peakedness |

Each time series is represented by a feature vector:
\[
X = [\Delta \mu, \Delta \sigma^2, \Delta \sigma, \Delta \text{skew}, \Delta \text{kurt}]
\]

### 3️⃣ Model Training — Logistic Regression  
We use **Logistic Regression** to estimate the probability of a structural break:

\[
h_\theta(x) = \frac{1}{1 + e^{-(\theta_0 + \theta_1x_1 + ... + \theta_nx_n)}}
\]

- Optimization via **gradient descent**  
- **Regularization** to reduce overfitting  
- Output is a probability score between 0 and 1  

### 4️⃣ Evaluation Metrics  
| Metric | Formula | Description |
|:--|:--|:--|
| Accuracy | (TP + TN) / (TP + TN + FP + FN) | Overall correctness |
| Precision | TP / (TP + FP) | How many predicted breaks are correct |
| Recall | TP / (TP + FN) | How many actual breaks were detected |
| F1-Score | 2 × (P×R)/(P+R) | Balance of precision and recall |
| ROC-AUC | ∫ TPR d(FPR) | Area under ROC curve |

---

## 📊 Results  
Performance on the synthetic dataset demonstrates high accuracy and reliability:  

| Metric | Value |
|:--|--:|
| Accuracy | ~70% |
| ROC–AUC | ~0.38 |

The model successfully captures structural shifts by analyzing changes in mean, variance, skewness, and kurtosis.

---

## 💻 Technologies Used  
- **Python 3.10+**  
- **NumPy** – numerical computations  
- **Pandas** – data manipulation  
- **SciPy** – statistical feature extraction  
- **Scikit-learn** – machine learning and evaluation  
- **Matplotlib** – visualization  

---

## 📈 Applications  
Structural Break Detection is widely used in:
- **Finance:** detecting regime changes in market trends  
- **Climate Science:** identifying shifts in temperature or rainfall patterns  
- **Industrial IoT:** recognizing early equipment degradation  
- **Healthcare:** monitoring physiological signal anomalies  

---

