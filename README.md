Hybrid Stock Price Prediction Model (LSTM + Linear Regression)

Overview
This project implements a hybrid machine learning model combining LSTM (Long Short-Term Memory) and Linear Regression to predict stock closing prices. The model leverages LSTM's ability to capture complex temporal patterns and Linear Regression's simplicity for trend analysis, resulting in improved prediction accuracy compared to using either model alone.

Dataset
File: apple_stock_data.csv

Format: CSV with columns:

Date (converted to datetime index)

Close (target variable, normalized to [0,1] range)

Preprocessing:

Missing values removed

Created 3 lagged features (Lag_1, Lag_2, Lag_3) for Linear Regression

Sequences of 60 days prepared for LSTM training

Model Architecture
LSTM Model
Two LSTM layers (50 units each)

Dense output layer (1 unit)

Optimizer: Adam

Loss Function: Mean Squared Error

Training: 20 epochs with batch size 32

Linear Regression Model
Trained on 3-day lagged features

Standard scikit-learn implementation

Hybrid Combination
Final predictions weighted as:

70% from LSTM

30% from Linear Regression

Implementation
Data Preparation

Load and normalize stock data

Generate training sequences (60 days)

Create lagged features

Split data (80% training, 20% testing)

Model Training

Train LSTM on sequential data

Train Linear Regression on lagged features

Prediction

Generate 10-day forecasts

Combine predictions using hybrid weighting

Inverse-transform to original price scale

Results
The script outputs a DataFrame comparing predictions from:

LSTM model

Linear Regression model

Hybrid model

Example output structure:

Date                LSTM    Linear Regression    Hybrid
2025-01-01        150.25            148.30      149.72
2025-01-02        151.80            149.15      151.06
...
Requirements
Python 3.7+

Required packages:

pandas

numpy

scikit-learn

tensorflow

matplotlib

Install with:

bash
pip install pandas numpy scikit-learn tensorflow matplotlib
Usage
Place your stock data in CSV format (matching the expected structure)

Run the script:

bash
python building_a_hybrid_machine_learning_model_with_python.py
Customization Options
Adjust sequence length (default: 60 days)

Modify hybrid weighting (default: 70/30 split)

Change model architecture parameters

Extend forecast horizon

Limitations
Financial markets contain inherent unpredictability

Model performance depends on quality and relevance of historical data

Long-term forecasts become increasingly uncertain

Default parameters may need tuning for different datasets

License
MIT License. Permission is granted for both academic and commercial use, with attribution.

Contact

