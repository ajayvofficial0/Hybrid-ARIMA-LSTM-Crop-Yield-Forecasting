# Hybrid-ARIMA-LSTM-Crop-Yield-Forecasting
Time-series model: ARIMA trends + LSTM residuals for crop yield

This repository contains the code, data, and documentation for a hybrid time-series forecasting model that combines ARIMA and LSTM to predict agricultural crop yields. The project was developed as part of the Department of Computer Science and Engineering (Artificial Intelligence and Machine Learning) at Dayananda Sagar University. 

---

## Table of Contents

1. [Overview](#overview)
2. [Repository Structure](#repository-structure)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Methodology](#methodology)
6. [Results](#results)
7. [Project Report](#project-report)
8. [Contributing](#contributing)
9. [License](#license)

---

## Overview

Accurate crop yield forecasting is critical for food security, pricing policy, and agricultural planning. This project implements a hybrid approach that leverages ARIMA to model linear trends and seasonality, and LSTM to capture nonlinear patterns in the residual errors, resulting in improved forecasting performance compared to standalone models.

---

## Repository Structure

```
├── data/                   # Raw and processed time-series datasets
├──LSTM_ARIMA.ipynb         # End-to-end hybrid model implementation
├── XAI_REPORT.docx         # Detailed project report 
├── requirements.txt        # Python dependencies
└── README.md               # Project overview and instructions
```

---

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/hybrid-arima-lstm.git
   cd hybrid-arima-lstm
   ```
2. Create and activate a virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # macOS/Linux
   venv\Scripts\activate    # Windows
   ```
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

1. **Prepare data** in `data/` directory, ensuring a CSV or similar with yearly crop yield values.
2. **Run the notebook** for exploratory analysis and model training:

   ```bash
   jupyter notebook notebooks/LSTM_ARIMA.ipynb
   ```
3. **Execute scripts** for modular runs:

   ```bash
   # ARIMA forecasting only
   python src/arima_model.py --input data/crop_yield.csv --output results/arima_preds.csv

   # LSTM residual modeling only
   python src/lstm_model.py --residuals results/arima_residuals.csv --output results/lstm_residual_preds.csv

   # Hybrid forecasting
   python src/hybrid_model.py --input data/crop_yield.csv --output results/hybrid_forecast.csv
   ```
4. **Visualize results** by opening the generated plots or loading them in the notebook.

---

## Methodology

1. **Data Preparation**: Clean and transform raw yield data into a univariate time series.
2. **ARIMA Modeling**: Identify optimal (p, d, q) parameters via ACF/PACF and AIC, train ARIMA, and extract residuals.
3. **LSTM Modeling**: Normalize residuals, structure into sequences with a look-back window, and train an LSTM network to predict future residuals.
4. **Hybrid Forecasting**: Sum ARIMA forecasts and LSTM-predicted residuals to produce the final yield prediction.
5. **Evaluation**: Compute MAE, MSE, RMSE, MAPE, and R² for ARIMA, LSTM, and hybrid models.

---

## Results

Key evaluation metrics (example values):

* **ARIMA**: MAE=11.08, RMSE=15.61, MAPE=64.83%, R²=0.24
* **LSTM Residual**: MAE=11.75, RMSE=16.02, MAPE=136.73%, R²=-0.04
* **Hybrid**: MAE=11.75, RMSE=16.02, MAPE=70.15%

Plots demonstrating model predictions vs. actual yields are available in the notebook.

---

## Project Report

A detailed report outlining the project background, literature review, methodology, experiments, and conclusions is available at `report/XAI_REPORT.docx` 

---

## Contributing

Contributions are welcome! Please fork the repository, create a feature branch, and submit a pull request describing your changes.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
