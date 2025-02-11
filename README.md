# Destination-Suggestion
## Overview

This file is a Jupyter Notebook developed as part of a university-level AI project at Sharif University of Technology. It focuses on creating an advanced **destination suggestion system** for ride-hailing applications. The system predicts a passenger's possible destinations based on their historical travel data using various machine learning techniques, including **K-Nearest Neighbors (KNN)**, **XGBoost**, and a custom **Neural Network Classifier**.

This project strives to enhance the predictive capabilities of ride-hailing services by addressing the challenge of destination prediction and enabling data-driven improvements in user experience and operational efficiency.

## Project Context

In ride-hailing services such as Uber or Lyft, predicting a passenger’s destination is essential for improving **logistics** and **user experience**. By analyzing travel patterns (e.g., daily routines, frequently visited places), this system can provide intelligent predictions for passengers based on the time of request, day of the week, and their historical data.

## Features and Key Components

1. **Environment**:
   - The code starts by importing all necessary libraries for **data manipulation**, **machine learning**, and **visualization**:
     - Libraries like `pandas`, `numpy`, `matplotlib`, and `torch` are utilized.
     - Data is visualized interactively with `KeplerGl`.

2. **Datasets**:
   - Contains structured travel data stored in JSON format:
     - `Data/output.json`: Historical trip data for training purposes.
     - `Data/output_test.json`: Dedicated test data for evaluating prediction accuracy.
     - Other auxiliary travel data for further testing and handling specific modeling requirements.

3. **Data Preprocessing**:
   - The data is cleaned and processed to extract essential features such as:
     - **Passenger attributes** (e.g., user ID, starting location, start/end time).
     - **Trip attributes** (e.g., day of week, origin/destination details).
   - Preprocessing prepares features for **model compatibility**, ensuring numerical and categorical features are correctly formatted.

4. **Prediction Models**:
   - Three predictive models are implemented in the script to compare performance:
     1. **K-Nearest Neighbors (KNN)**:
        - A classic approach that looks for the most similar historical trips to suggest destinations.
        - The number of neighbors (`K`) determines prediction accuracy.
     2. **XGBoost**:
        - A popular machine-learning model used for classification problems with high accuracy.
        - Handles predictive tasks efficiently while supporting both categorical and numerical features.
     3. **Neural Network Classifier**:
        - A deep learning-based model designed to improve accuracy by learning complex patterns in user travel data.
        - Includes a flexible architecture for training and validation.

5. **KeplerGl Data Visualization**:
   - Visualizes user travel patterns interactively on maps to highlight the geographical context of destinations, origins, and patterns.

6. **Evaluation Metrics**:
   - The predictive models are evaluated based on their **accuracy** on both training and test datasets.
   - **Haversine distance** and similar geographical metrics are used to assess error margins in destination prediction.

## Functions and Classes

1. **NearestNeighbor Class (KNN Implementation)**:
   - **Purpose**: Implements a simple but effective way of predicting destinations based on historical trips.
   - **Core Methods**:
     - `fit` trains the KNN model on `train_X` and `train_y`.
     - `predict` predicts destinations for new trip data.
     - `nearest_points` finds the K closest historical trips for any given query.

2. **Encoder Class (XGBoost Implementation)**:
   - **Purpose**: Streamlines preprocessing and classification using the XGBoost model.
   - **Core Methods**:
     - `preprocess` and `labeling` perform feature encoding and label preparation.
     - `fit` and `predict` train and test the XGBoost model.

3. **Neural Network Builder**:
   - Implements a neural network classifier with PyTorch for destination prediction.
   - Includes data normalization and encoding steps to handle the multi-feature data.

4. **Data Utilities**:
   - Handles JSON-based datasets with utilities for cleaning, filtering, feature extraction, and transformation.

## Data Structure

### Input Data
- **`Data/output.json`**: Contains training data, including fields:
  - `user_id` (user identifier), `origin lat`/`lon` (origin coordinates), `dest lat`/`lon` (destination coordinates), `start_time`, `Day`.

- **`Data/output_test.json`**: The test dataset shares the same structure as the training data.

- **Auxiliary Travel Data**:
  - Includes trip metadata such as duration, end time, and price, for training or additional exploratory purposes.

### Output
- **Predicted Destinations**:
  - KNN, XGBoost, and Neural Network models predict destination coordinates.
- **Visualization**:
  - Interactive results mapped with `KeplerGl`.

## Usage

### Instructions for Running
1. Place all required datasets (`output.json` and `output_test.json`) in the `Data/` directory.
2. Ensure the required dependencies (`pandas`, `numpy`, `matplotlib`, `torch`, `xgboost`, etc.) are installed.
3. Run the script to preprocess the data and train the models.
4. Inspect the performance metrics (accuracy) and visualizations to evaluate model effectiveness.

### Output Files
- The models print their accuracy for **training** and **test datasets** directly to the console.
- Interactive maps showing travel patterns are displayed, offering insight into user habits.
