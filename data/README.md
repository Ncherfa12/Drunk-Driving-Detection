# Drunk Driving Detection Dataset

## Table of Contents
1. [Introduction](#introduction)
2. [Dataset Overview](#dataset-overview)
3. [Data Structure](#data-structure)
4. [Data Exploration](#data-exploration)
5. [Data Cleaning](#data-cleaning)
6. [Feature Engineering](#feature-engineering)
7. [Statistical Summary](#statistical-summary)
8. [Data Sensitivity and Handling](#data-sensitivity-and-handling)
9. [References](#references)

## Introduction
This project utilizes a dataset from the Virginia Tech Transportation Institute (VTTI) to study driving behaviors that may indicate alcohol impairment. The dataset consists of high-frequency time-series data collected from real-world driving sessions. This README focuses on the raw data description, the exploration process, and the feature engineering techniques used.

## Dataset Overview
The dataset includes two main categories:

- **Identified Dataset**:
  - Contains trips where alcohol impairment was detected.
  - Data from `220` participants, each with `1 to 3` trips.
  - Total rows: `4,172,516`.

- **Unknown Dataset**:
  - Contains trips with no identified alcohol impairment.
  - Data from the same `220` participants, each with `9 to 12` trips.
  - Total rows: `21,453,929`.

## Data Structure
The dataset includes the following raw variables:

### Kinematic Data
- **`vtti.accel_x`**: Longitudinal acceleration (m/s²).
- **`vtti.accel_y`**: Lateral acceleration (m/s²).
- **`vtti.accel_z`**: Vertical acceleration (m/s²).
- **`vtti.gyro_x`**: Angular velocity in the x-axis (deg/s).
- **`vtti.gyro_y`**: Angular velocity in the y-axis (deg/s).
- **`vtti.gyro_z`**: Angular velocity in the z-axis (deg/s).
- **`vtti.speed_gps`**: Vehicle speed from GPS (km/h).

### Lane Data
- **`vtti.lane_distance_off_center`**: Distance from the lane center (cm).
- **`vtti.lane_width`**: Lane width (cm).

### Steering and Pedal Data
- **`vtti.steering_wheel_position`**: Steering wheel angle (degrees).
- **`vtti.pedal_gas_position`**: Gas pedal position (0-100%).
- **`vtti.pedal_brake_state`**: Brake state (0: not pressed, 1: pressed).

## Data Exploration
The exploration process included the following steps:

1. **Descriptive Statistics**:
   - Calculated summary statistics (mean, standard deviation, min, max) for each variable.
   - Analyzed missing values using `isnull()`.

2. **Outlier Detection**:
   - Plotted histograms and box plots for key variables to identify outliers.

3. **Basic Correlation Check**:
   - Generated preliminary correlation matrices for kinematic variables.

## Data Cleaning
Data cleaning steps included:

1. **Merging Files**:
   - Aggregated CSV files for both identified and unknown datasets.

2. **Duplicate Removal**:
   - Removed duplicates based on `timestamp`.

3. **Handling Missing Values**:
   - Used forward-fill and backward-fill methods.
   - Interpolated missing values in GPS speed.

4. **Outlier Filtering**:
   - Removed extreme values in GPS speed (filtered above `200 km/h` or below `1 km/h`).

5. **Normalization**:
   - Standardized kinematic variables using min-max scaling.

## Feature Engineering
The following features were engineered:

1. **Kinematic Features**:
   - **`accel_magnitude`**: Combined magnitude of acceleration.
   - **`gyro_magnitude`**: Combined magnitude of gyroscope readings.

2. **Lane Features**:
   - **`avg_abs_distance_from_center`**: Rolling average of absolute distance from the lane center.

3. **Steering Features**:
   - **`steering_change`**: Change in steering wheel position.
   - **`steering_rate`**: Rate of change of the steering wheel angle.

4. **Pedal Features**:
   - **`brake_gas_interaction`**: Indicator of simultaneous gas and brake usage.
   - **`brake_duration`**: Total duration of brake engagement.

## Statistical Summary
Here is the detailed summary of some key statistics for both identified and unknown datasets, focusing on the most relevant variables:

### Identified Dataset
| Variable                  | Mean   | Std Dev | Min   | 25%   | 50%   | 75%   | Max   |
|---------------------------|--------|---------|-------|-------|-------|-------|-------|
| Acceleration X (m/s²)     | 0.0098 | 0.078   | -0.79 | -0.02 | 0.005 | 0.049 | 0.38  |
| Gyroscope Y (deg/s)       | -0.19  | 0.98    | -12.0 | -0.65 | 0.0   | 0.0   | 19.19 |
| GPS Speed (km/h)          | 40.56  | 34.73   | 0.0   | 1.71  | 36.44 | 65.28 | 114.63|
| Brake State               | 0.30   | 0.46    | 0.0   | 0.0   | 0.0   | 1.0   | 1.0   |

### Unknown Dataset
| Variable                  | Mean   | Std Dev | Min   | 25%   | 50%   | 75%   | Max   |
|---------------------------|--------|---------|-------|-------|-------|-------|-------|
| Acceleration X (m/s²)     | 0.0067 | 0.053   | -0.69 | -0.014| 0.008 | 0.029 | 0.44  |
| Gyroscope Y (deg/s)       | -0.24  | 0.77    | -14.63| -0.65 | 0.0   | 0.0   | 19.84 |
| GPS Speed (km/h)          | 72.2   | 40.7    | 0.0   | 38.96 | 83.3  | 108.87| 126.81|
| Brake State               | 0.13   | 0.34    | 0.0   | 0.0   | 0.0   | 0.0   | 1.0   |

## Data Sensitivity and Handling
The dataset includes sensitive information from real-world driving:

- **Access Control**: Data is stored on encrypted drives with restricted access.
- **Anonymization**: All participant identifiers have been anonymized.
- **No External Sharing**: The dataset cannot be uploaded to public platforms.

## References
1. Li, Z., Jin, X., & Zhao, X. (2015). Drunk driving detection based on Multivariate Time Series.
2. Harkous, H., & Artail, H. (2019). Machine learning methods for detecting impaired driving.
3. Dai, J., Teng, J., Bai, X., Shen, Z., & Xuan, D. (2010). Mobile phone-based detection of impaired driving.

