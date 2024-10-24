# Electricity Price Forecasting with AR(1) and Neural Networks

## Overview
This project aims to forecast electricity prices using historical data from the GEFCom dataset. We employ autoregressive models (AR(1)) and artificial neural networks (NN) to generate predictions. The project explores various configurations of neural networks to optimize their performance.

## Dataset
The dataset used for this analysis is `GEFCOM.txt`, which contains the following columns:
- `date`: The date of the observation.
- `hour`: The hour of the day (0-23).
- `price`: The electricity price.
- `sysload`: The system load.
- `zoneload`: The zonal load.
- `dotw`: Day of the week.

## Forecasting Models
### 1. AR(1) Model
The first step involves implementing an AR(1) model for forecasting:
- **Joint Estimation**: The model is fitted jointly across all hours of the day.
- **Separate Estimation**: The model is also fitted separately for each hour.

Both variants are evaluated using Mean Absolute Error (MAE) as the performance metric. 

### 2. Neural Network Models
To enhance the forecasting capabilities, we recreate the joint AR(1) model using a neural network:

#### 2.1. Basic Neural Network
- The first neural network (NN) model consists of an input layer followed by an output layer with no hidden layers. This simple architecture serves as a baseline.
- The model is trained on the data with a specified number of epochs and batch size, and performance is evaluated based on MAE.

#### 2.2. Improved Neural Network
- The second NN model incorporates a batch normalization layer and a hidden layer with ELU activation. 
- The addition of layers allows the model to capture more complex relationships in the data, although it may not always lead to better performance due to limited data.

#### 2.3. Multi-Output Neural Network
- The third NN model extends the architecture to have 24 outputs, one for each hour of the day. 
- This model requires increased input dimensions to include data for all hours and is designed to address the challenge of data scarcity.

### 3. Hyperparameter Optimization
Hyperparameter optimization is performed using the Optuna library to identify the optimal number of neurons and activation functions for the NN model. The optimization process includes:
- Defining an objective function that evaluates the model's performance.
- Running the optimization study across a specified number of trials to find the best hyperparameters.
- Training the final model using the optimized parameters and validating its performance on a separate validation dataset.

## Conclusion
This project demonstrates the effectiveness of both AR(1) models and neural networks in forecasting electricity prices. Through iterative improvements and hyperparameter optimization, we strive to enhance prediction accuracy while acknowledging the limitations posed by the dataset.

## Requirements
To run this project, ensure you have the following Python libraries installed:
- `numpy`
- `pandas`
- `matplotlib`
- `tensorflow`
- `optuna`

## Usage
Follow the provided Jupyter Notebook to execute the code and replicate the forecasting process. Modify the model parameters and data processing steps as needed to explore further enhancements in forecasting performance.

## Acknowledgments
The dataset used in this project is sourced from GEFCom. Special thanks to the contributors who provided the necessary frameworks and libraries for data analysis and modeling.
