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

This target represents whether a battery failure alert is expected within