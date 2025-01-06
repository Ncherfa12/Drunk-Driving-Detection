# Drunk Driving Detection Using Vehicle Kinematics

⚠️ Important Note:

Due to the sensitive nature of the data used in this project and strict privacy agreements (with Virginia Tech Transportation Insitute: https://www.vtti.vt.edu/), the raw datasets are not included in this repository. Additionally, this repository contains only a simplified version of the codebase. Certain components and full implementations have been omitted to comply with data protection and confidentiality requirements.

Why This Matters:
While the provided code and documentation showcase the general methodology and approach, they are intended as a proof of concept. The missing portions involve the raw data itself and the preprocessing steps and specific model configurations that cannot be shared publicly due to contractual obligations.

How to Use This Repository:

The current content still provides an overview of the problem-solving approach, feature engineering, and high-level analysis techniques used.

## Project Overview
This project investigates the detection of impaired driving using vehicle kinematics data. The analysis leverages a dataset from the Virginia Tech Transportation Institute (VTTI), comparing trips identified as alcohol-influenced against trips with unknown alcohol levels. The objective is to uncover kinematic patterns indicative of impaired driving, utilizing both machine learning and deep learning techniques.

## Repository Structure

- **Drunk-Driving-Detection/**
  - `README.md`: Main project description and overview
  - `LICENSE`: License file (e.g., MIT License)
  - **code/**: Main directory for all code and Jupyter notebooks
    - **Data_Exploration/**
      - `Data_exploration.ipynb`: Data exploration and visualization notebook
    - **Ensemble_Techniques/**
      - `LightGBM.ipynb`: LightGBM model implementation
      - `RandomForest.ipynb`: Random Forest model
      - `XG_GradientBoost.ipynb`: XGBoost model
    - **Neural_Networks/**
      - `CNN_1D.ipynb`: 1D Convolutional Neural Network
      - `RNN_Bi.ipynb`: Bidirectional RNN
      - `RNN_LSTM.ipynb`: LSTM-based Recurrent Neural Network
      - `ScikitMLP_Classifier.ipynb`: Multi-layer Perceptron classifier using Scikit-learn
  - **results/**: Directory for analysis results and visualizations
  - **data/**: Data description (no raw data files included)


## Methodologies
This project utilizes a combination of machine learning and deep learning techniques for time-series analysis of vehicle kinematics data.

- **Programming Language**: Python, using Jupyter Notebooks for modular analysis.
- **Libraries Used**:
  - Data Analysis: Pandas, NumPy
  - Machine Learning: Scikit-Learn (Random Forest, XGBoost, LightGBM, CatBoost)
  - Deep Learning: TensorFlow, Keras (RNN, LSTM, 1D CNN)
  - Visualization: Matplotlib, Seaborn

### Models Employed:
1. **Ensemble Models**:
   - Random Forest
   - XGBoost
   - LightGBM
   - CatBoost
2. **Deep Learning Models**:
   - MLP Classifier
   - Recurrent Neural Networks (RNN LSTM, BI)
   - 1D Convolutional Neural Networks (1D CNN)

## Data Summary
The dataset consists of time-series kinematic data with 19 variables collected from 220 anonymous participants. The data is structured as follows:

- **Identified Data**: Contains 1-3 trips per participant, with a total of 4.17 million rows.
- **Unknown Data**: Contains 9-12 trips per participant, with a total of 21.45 million rows.

Due to the sensitive nature of the dataset, raw data files are not included in this repository. Instead, a comprehensive description of the dataset attributes and summary statistics are provided in the `data_description.md` file.

## Feature Engineering
The following key features were engineered for the analysis:

- **Brake Frequency**: Number of braking events within a 10-second window.
- **Lateral Velocity**: Measures changes in the vehicle's lateral position.
- **Lateral Acceleration**: Calculates the rate of change of lateral velocity.
- **Average Distance from Center**: Determines the vehicle’s deviation from the lane center.

These features were selected based on statistical analysis and correlation with impaired driving patterns.

## Model Performance
The performance of various models was evaluated based on training and test accuracy, precision, recall, and F1 scores. See some results below:

| Model                  | Training Accuracy | Test Accuracy | Precision | Recall | F1 Score |
|------------------------|-------------------|---------------|-----------|--------|----------|
| Random Forest          | 0.99              | 0.82          | 0.83      | 0.81   | 0.82     |
| XGBoost                | 0.84              | 0.82          | 0.83      | 0.80   | 0.81     |
| RNN LSTM               | 0.72              | 0.77          | 0.77      | 0.73   | 0.75     |
| 1D CNN                 | 0.78              | 0.77          | 0.77      | 0.77   | 0.77     |

The ensemble models, particularly Random Forest and XGBoost, outperformed the deep learning models. The results indicate that kinematic features such as lateral acceleration and brake frequency are strong indicators of impaired driving.

## Future Work
Potential areas for future research and improvement include:

1. Using longer, continuous driving trips to capture better temporal patterns.
2. Exploring advanced models such as transformers for time-series analysis.
3. Integrating additional data sources (e.g., behavioral indicators) for a more comprehensive analysis.
4. Deploying the model in real-world scenarios for further validation and feedback.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact
For questions or collaboration opportunities, please connect via [LinkedIn](https://www.linkedin.com/in/nadhir-cherfaoui/).
