# Task 9: Neural Networks with TensorFlow/Keras

## Objective
Build and train a feed-forward neural network to predict housing prices using the **California Housing dataset**.  

## Steps
1. **Dataset Loading & Preprocessing**
   - Loaded California Housing dataset from `sklearn.datasets`.
   - Split data into training and testing sets (80/20).
   - Scaled features using `StandardScaler` for faster convergence.

2. **Model Architecture**
   - Input layer: 8 features (housing attributes).
   - Hidden layers:
     - Dense(64, activation="relu")
     - Dense(32, activation="relu")
   - Output layer: Dense(1) for regression.

3. **Model Compilation**
   - Optimizer: Adam (`learning_rate=0.01`)
   - Loss function: Mean Squared Error (MSE)
   - Metric: Mean Absolute Error (MAE)

4. **Training**
   - Trained for 50 epochs with batch size 32.
   - Validation split: 20% of training set.
   - Monitored training vs. validation loss and MAE.

5. **Evaluation**
   - Test MAE computed to assess prediction accuracy.
   - Plotted **Loss (MSE)** and **MAE curves** to check performance trends.

6. **Prediction & Comparison**
   - Predicted house values on test data.
   - Compared actual vs. predicted values using a DataFrame.

## Tools & Libraries
- **Python**
- **TensorFlow / Keras**
- **scikit-learn**
- **pandas**
- **matplotlib**

## Key Insights
- Neural networks can effectively model structured datasets like housing prices.
- Scaling features significantly improves training stability.
- Monitoring loss and MAE curves helps detect overfitting or underfitting.
