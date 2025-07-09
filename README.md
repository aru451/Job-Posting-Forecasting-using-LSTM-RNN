# Job Posting Volume Forecasting Using Stacked LSTM

## Overview
This project focuses on analyzing and forecasting daily job posting volumes using a Stacked LSTM (Long Short-Term Memory) model. The goal is to understand job market trends and predict future job postings based on historical patterns.

## Steps Involved
### 1. Data Collection
The job posting data used in this project comes from real-world sources such as websites like Indeed or publicly available datasets on Kaggle. The data includes important fields such as the date when a job was posted, the job title, and the location. The primary objective in this step is to extract and count how many job postings appear on each day based on the Date column.

### 2. Data Preprocessing
First, the text-based date information like "Posted 10 days ago" is converted into actual calendar dates. After that, the data is grouped by these dates to count the number of job postings for each day. To ensure that no date is missing, the time series is resampled to include every day and any missing dates are filled with zeros. Finally, the job posting counts are scaled to a range between 0 and 1 using MinMaxScaler, which prepares the data for training the LSTM model.

### 3. Splitting the Dataset
The full dataset is divided into two parts: 80% for training the model and 20% for testing its performance. This split allows the model to learn patterns from the majority of the data while still being tested on unseen data to check how well it performs.

### 4. Preparing Sequences for LSTM
A fixed-length sliding window, such as 7 days, is used to create sequences of past data that the model can learn from. These sequences allow the model to predict the next day’s job posting count based on the previous days. The data is then reshaped into three dimensions — samples, time steps, and features — which is the format expected by LSTM models.

### 5. Building the Model
A stacked LSTM model is built using two LSTM layers. Each LSTM layer has 64 units, and dropout layers are added between them to reduce overfitting. At the end, a Dense layer is used to output a single predicted value. This model is constructed using Keras and follows a sequential architecture.

### 6. Training the Model
The model is compiled using the Adam optimizer and the mean squared error (MSE) loss function. It is then trained on the training data for 30 epochs using a small batch size, which is more suitable for smaller datasets.

### 7. Making Predictions
Once the model is trained, it is used to predict job posting counts for both the test set and the next 30 days into the future. These predicted values are then converted back to the original scale so that they can be interpreted and compared with the actual job posting numbers.

### 8. Model Evaluation
To measure how well the model performs, the Root Mean Squared Error (RMSE) is calculated. This metric helps understand the average error in the predictions. A lower RMSE value indicates better model accuracy.

### 9. Visualizing the Results
The predicted values and actual values are plotted on a graph to visually assess the model’s performance. Additionally, the 30-day forecast is shown alongside the historical data to provide an overall view of how the job posting trend may change in the near future.

### 10. Forecasting Future Job Postings
To predict job postings for the next 30 days, the model uses the most recent data and then feeds its own predictions back into itself to generate each new forecast. This process continues step-by-step and helps estimate how the volume of job postings may rise or fall over the upcoming month.

## Conclusion
This project demonstrates how a stacked LSTM model can be applied to forecast job posting trends using time series data. It includes steps from data cleaning and preparation to model building and forecasting. The same approach can be used for different job categories, locations, or even other types of time-based data, and it offers useful insights for hiring strategies, job market research, or business planning.

