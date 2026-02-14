
---

# Customer Attrition Prediction using PyTorch

## 📌 Overview

This project implements a **Binary Classification Neural Network** using **PyTorch** to predict customer attrition (churn).

The model predicts whether a customer will:

* `0` → Stay
* `1` → Leave

The dataset used is balanced, and the model is trained using `BCEWithLogitsLoss` for numerical stability.

---

## 🧠 Model Architecture

The neural network consists of:

* Input Layer
* Fully Connected Hidden Layers with ReLU activation
* Output Layer (1 neuron – raw logits)

Final layer does **NOT** use Sigmoid because:

```
BCEWithLogitsLoss = Sigmoid + Binary Cross Entropy (combined internally)
```

---

## ⚙️ Tech Stack

* Python
* PyTorch
* NumPy
* Pandas
* Scikit-Learn (for evaluation metrics)

---

## 📂 Project Workflow

### 1️⃣ Data Preprocessing

* Handling missing values
* Encoding categorical variables
* Feature scaling using `StandardScaler`
* Train/Test split

### 2️⃣ Model Training

* Loss Function: `nn.BCEWithLogitsLoss()`
* Optimizer: Adam
* Epochs: 1000
* Evaluation done using `torch.inference_mode()`

### 3️⃣ Evaluation Metrics

After converting logits to probabilities using:

```python
probs = torch.sigmoid(logits)
y_preds = (probs > 0.5).float()
```

The following metrics are computed:

* Accuracy
* Precision
* Recall
* F1 Score

---

## 📊 Training Results

Example output:

```
Epoch 900
Training Loss: 0.372
Testing Loss:  0.421
```

Model shows stable convergence with minimal overfitting.

---

## 🚀 How to Run

1. Clone the repository

```
git clone <your-repo-url>
```

2. Install dependencies

```
pip install torch numpy pandas scikit-learn
```

3. Run the training script

```
python train.py
```

---

## 🔎 Key Learning Points

* Proper usage of `BCEWithLogitsLoss`
* Importance of matching tensor shapes `[N,1]`
* Difference between logits and probabilities
* Correct evaluation workflow
* How to compute classification metrics

---

## 📈 Future Improvements

* Add Dropout for regularization
* Implement Early Stopping
* Add ROC-AUC metric
* Convert to FastAPI deployment
* Hyperparameter tuning

---

