# Building-a-Hybrid-Machine-Learning-Model-with-Python

# **Hybrid Stock Price Prediction Model (LSTM + Linear Regression)**

## **📌 Overview**
This project implements a **hybrid machine learning model** combining **LSTM (Long Short-Term Memory)** and **Linear Regression** to predict stock prices (Apple's closing prices). The hybrid approach leverages LSTM for capturing complex temporal patterns and Linear Regression for simpler trends, improving overall prediction accuracy.

---

## **📂 Dataset**
- **File:** `apple_stock_data.csv`  
- **Columns:**  
  - `Date` (datetime index)  
  - `Close` (target variable, scaled between 0 and 1)  
- **Preprocessing:**  
  - Missing values removed.  
  - Lagged features (`Lag_1`, `Lag_2`, `Lag_3`) generated for Linear Regression.  

---

## **⚙️ Model Architecture**
### **1. LSTM Model**
- **Layers:**  
  - Two LSTM layers (50 units each, `return_sequences=True` for the first).  
  - A `Dense(1)` output layer.  
- **Training:**  
  - Optimizer: `Adam`  
  - Loss: `Mean Squared Error (MSE)`  
  - Epochs: `20`  
  - Batch Size: `32`  

### **2. Linear Regression Model**
- **Features:** Past 3 days' closing prices (`Lag_1`, `Lag_2`, `Lag_3`).  
- **Training:** Standard `scikit-learn` implementation.  

### **3. Hybrid Model**
- **Combination:**  
  - **70% LSTM** + **30% Linear Regression** predictions.  
- **Alignment:** Ensures equal-length predictions before blending.  

---

## **🚀 How It Works**
1. **Data Preparation**  
   - Load and preprocess stock data (scaling, lag features).  
   - Split into sequences (`seq_length=60`) for LSTM.  
   - Train-test split (`80-20`).  

2. **Training**  
   - Train LSTM on sequences.  
   - Train Linear Regression on lagged features.  

3. **Predictions**  
   - Generate future predictions (next 10 days).  
   - Inverse-transform scaled predictions to original values.  

4. **Hybrid Blending**  
   - Combine predictions with weighted averaging.  

---

## **📊 Results**
- **Output:** A `DataFrame` showing:  
  - Future dates (next 10 days).  
  - Individual model predictions (LSTM, Linear Regression).  
  - Hybrid model predictions.  

**Example Output:**
```
         Date  LSTM Predictions  Linear Regression Predictions  Hybrid Predictions
0  2025-01-01            150.25                         148.30             149.72
1  2025-01-02            151.80                         149.15             151.06
...
```

---

## **🛠️ Dependencies**
- Python 3.7+  
- Libraries:  
  ```bash
  pandas numpy scikit-learn tensorflow matplotlib
  ```
  Install via:  
  ```bash
  pip install pandas numpy scikit-learn tensorflow matplotlib
  ```

---

## **📝 Usage**
1. **Run the Script**  
   ```bash
   python building_a_hybrid_machine_learning_model_with_python.py
   ```
2. **Customize**  
   - Adjust `seq_length`, weights (`0.7/0.3`), or model architecture.  
   - Replace `apple_stock_data.csv` with your dataset.  

---

## **⚠️ Limitations**
- Stock markets are volatile; long-term predictions may be unreliable.  
- Hybrid weights (`0.7/0.3`) should be validated empirically.  
- Ensure data is up-to-date for real-world use.  

---

## **📜 License**
MIT License. Free for academic and commercial use.  

---

## **📬 Contact**
For questions or improvements, open an issue or reach out to [your email].  

--- 

This **README.md** provides a clear, structured overview of your project. Let me know if you'd like to add more details (e.g., visualizations, performance metrics)! 🚀
