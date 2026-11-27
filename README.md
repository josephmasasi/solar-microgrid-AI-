# Edge-AI Deep Learning for Solar Micro-Grid Predictive Degradation ☀️

An AI-powered predictive maintenance system that uses deep learning to estimate battery failure risk in solar microgrids. The system analyzes battery, photovoltaic, inverter, electrical load, and environmental sensor measurements to identify potential battery failure conditions within the next 30 days.

## 1. Project Overview

Solar microgrids are essential for providing reliable electricity, particularly in areas with limited access to conventional power infrastructure.

Battery degradation and unexpected battery failures can interrupt power supply, increase maintenance costs, and reduce system reliability.

Traditional monitoring approaches often rely on existing measurements and threshold-based alerts. This project explores the application of deep learning to predict potential battery failure conditions before they occur.

The proposed system processes multiple operational parameters and estimates the probability of battery failure within a 30-day prediction window.

## 2. Problem Statement

Unexpected battery degradation and failure can negatively affect the reliability and efficiency of solar microgrid systems.

Monitoring individual sensor measurements may not adequately capture complex relationships between battery health, electrical performance, environmental conditions, and energy consumption.

There is therefore a need for an intelligent predictive approach capable of analyzing multiple operational parameters simultaneously and identifying potential battery failure risks in advance.

## 3. Project Objectives

- Develop a deep learning model for predicting battery failure risk.
- Analyze battery health, solar panel, inverter, electrical load, and environmental parameters.
- Apply data preprocessing and feature scaling techniques.
- Estimate battery failure probability within a 30-day prediction period.
- Develop a web-based interface for uploading sensor data and displaying predictions.

## 4. Proposed System

The system follows a machine-learning prediction workflow:

1. Sensor data is provided through a CSV file.
2. The application validates the required input features.
3. The input data is arranged according to the model's expected feature order.
4. The trained scaler preprocesses the input measurements.
5. The deep learning model generates a battery failure probability.
6. The probability is evaluated against a 50% classification threshold.
7. The application displays the prediction result.

### System Architecture

```text
       SENSOR DATA
            |
            v
      CSV UPLOAD
            |
            v
    FEATURE VALIDATION
            |
            v
      DATA SCALING
        (scaler.pkl)
            |
            v
     DEEP LEARNING MODEL
      (best_model.keras)
            |
            v
   FAILURE PROBABILITY
            |
            v
     CLASSIFICATION
       Threshold 0.5
            |
       +----+----+
       |         |
       v         v
   HIGH RISK   LOWER RISK
       |         |
       v         v
    FAILURE    HEALTHY
     ALERT     STATUS
```

## 5. Dataset Description

The project uses synthetic solar microgrid operational data developed for model training and experimentation.

The dataset covers multiple categories of operational parameters:

| Feature Category | Examples |
|---|---|
| Battery parameters | State of health, state of charge, internal resistance, battery age |
| Solar PV parameters | Irradiance, PV power, panel temperature, efficiency |
| Inverter parameters | Inverter efficiency, output voltage, frequency |
| Electrical load | Load power, peak load, energy consumption |
| Environmental parameters | Temperature, humidity, rainfall, wind speed |
| System events | Voltage sags, voltage swells, previous blackouts |

The modelling workflow used approximately 150,000 synthetic observations and 75 generated variables, with the application selecting the required model input features.

### Prediction Target

`alert_battery_30d`

This target represents whether a battery failure alert is expected within the next 30 days.

## 6. Deep Learning Model

The project implements a Deep Neural Network using TensorFlow and Keras.

The trained model is saved as:

`best_model.keras`

The model receives preprocessed sensor measurements and produces a probability between 0 and 1.

### Prediction Logic

The application uses a classification threshold of 0.5:

- Probability ≥ 0.50: Battery failure risk detected.
- Probability < 0.50: Lower predicted battery failure risk.

The preprocessing scaler is saved separately as `scaler.pkl` to ensure uploaded data undergoes the same scaling process expected by the trained model.

## 7. Model Evaluation

The reported experimental evaluation produced the following results:

| Metric | Result |
|---|---:|
| Accuracy | 86% |
| Recall | 60% |
| True Negatives | 21,636 |
| False Positives | 1,256 |
| False Negatives | 2,850 |
| True Positives | 4,258 |

The model achieved approximately 86% accuracy and 60% recall on the reported evaluation dataset.

Recall is particularly important in predictive maintenance because missed battery failure cases can result in unexpected system interruptions.

**Note:** These are experimental results obtained using synthetic data. Performance on real solar microgrid installations requires further validation using actual operational sensor data.

## 8. Application Features

- CSV-based sensor data upload.
- Automatic validation of required input features.
- Data preprocessing using a saved scaler.
- Deep learning-based battery failure probability estimation.
- Risk classification using a predefined threshold.
- Display of prediction results through a Streamlit interface.

## 9. Technologies Used

| Technology | Application |
|---|---|
| Python | Core programming language |
| TensorFlow / Keras | Deep learning model |
| Pandas | Data processing |
| Joblib | Loading preprocessing scaler |
| Scikit-learn | Data preprocessing |
| Streamlit | Interactive web application |
| NumPy | Numerical computing |

## 10. Project Structure

```text
Solar_Microgrid_AI/
│
├── app.py
├── best_model.keras
├── scaler.pkl
├── failure_risk_battery.csv
├── healthy_battery.csv
├── README.md
└── .gitignore
```

## 11. Installation and Setup

### Prerequisites

- Python 3.10 or another version compatible with the project's TensorFlow dependencies.
- pip package manager.

### Step 1: Clone the Repository

```bash
git clone https://github.com/josephmasasi/solar-microgrid-AI-.git
```

### Step 2: Navigate to the Project

```bash
cd Solar_Microgrid_AI
```

### Step 3: Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```powershell
venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
pip install streamlit pandas tensorflow joblib scikit-learn numpy
```

### Step 5: Run the Application

```bash
streamlit run app.py
```

The application will open in your browser.

## 12. How to Use the System

1. Launch the Streamlit application.
2. Prepare a CSV file containing the required sensor features.
3. Upload the CSV file using the upload interface.
4. The application validates the uploaded data.
5. The trained model processes the sensor measurements.
6. View the predicted battery failure probability and risk classification.

Two sample CSV files are included:

- `healthy_battery.csv`
- `failure_risk_battery.csv`

These can be used to explore the application's input workflow.

## 13. Limitations and Future Improvements

Potential future improvements include:

- Validation using real-world solar microgrid operational datasets.
- Deployment on resource-constrained edge computing devices.
- Integration with live IoT sensor data.
- Improved detection of early battery degradation patterns.
- Model explainability to identify the sensor parameters contributing to failure predictions.
- Dynamic maintenance recommendations based on predicted risk.
- Calibration of predicted probabilities and confidence reporting.

## 14. Repository

**GitHub:** https://github.com/josephmasasi/solar-microgrid-AI-

## 15. Author

**Joseph Cletus Masasi**

Computer Engineering | Artificial Intelligence | Machine Learning | Cybersecurity

GitHub: https://github.com/josephmasasi

---

*An academic and experimental project exploring the application of deep learning to predictive maintenance in solar microgrid systems.*
