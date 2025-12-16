# 🧎🏽‍♂️**Postura Posture Predictor** 

We conducted 10-minute trials with 14 participants to obtain data for model training. Each trial consisted of 30 second rounds in one of three positions: **neutral**, **upright**, and **slouch**. An additional category, **shifting**, was labelled as participants shifted from one position to another. The amount of data points per trial ranges from 4,100 ~ 4,300, providing almost 60,000 total data points in the final dataset. The following section details dataset specifics.

# 📊 **Dataset** 

* **Source:** Postura
* **Size:** ~59,106 collected data points (cleaned dataset)
* **Features:** 63 Arduino sensor readings, total force, and health attributes - height and weight.
* **Target**: `bin_label`
  * 0 = Neutral, Upright, or Shifting
  * 1 = Slouch

---

### Features List:

* total_force
* sensor_0
...
* sensor_63
* height_cm
* weight_kg
  
📎[View processed dataset]
()

---
## 🧠 XG-Boost Architecture

| Layer Type     | Details                                         |
| -------------- | ----------------------------------------------- |
| Input Layer    | Matches one-hot encoded input                   |
| Hidden Layers  | 10 hidden layers, 30 neurons each               |
| Activation     | ReLU (hidden), Sigmoid (output)                 |
| Regularization | L1 and L2, both set to `0.001`                  |
| Optimizer      | SGD with learning rate `0.01`, momentum `0.9`   |
| Training       | 50 epochs, batch size `32`, with early stopping |

The ANN is capable of learning both **linear** and **non-linear** relationships between features and diabetes outcome.

---

## ✅ Performance Summary

As part of this project, we trained and evaluated **8 different models**, including:

* **Logistic Regression (L2-regularized)**
* **Random Forest**
* **XGBoost**
* **LightGBM**
* **Bayesian Network**
* **Multiple ANN variants (ANN A, B, C, etc.)**

After extensive testing on consistent **metrics** — accuracy, precision, recall, F1 score, false negative rate — we selected **ANN Model A** as the **best overall model**:

* **Highest test accuracy**
* **Lowest false negative rate** — critical for medical applications
* **Strong precision and recall balance**
* **Robust generalization** to unseen test data

---



