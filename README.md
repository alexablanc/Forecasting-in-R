# Forecasting Sales Using Prophet in R

## 🧠 Objective
This project forecasts weekly sales using Facebook Prophet, with attention to seasonality, holidays (e.g., Super Bowl), and known anomalies.

## 📊 Dataset
Simulated data representing weekly sales (not shared due to confidentiality). Date column is `ds`, target column is `y`.

## ⚙️ Key Features
- Time series forecasting with Prophet
- Outlier removal for known disruption periods
- Custom holiday inclusion (Super Bowl)
- Parameter tuning for seasonality
- Model evaluation with visualizations

## 📁 Files
- `Sales_Projections.R`: R script with forecasting logic
- `README.md`: Project overview

## 🧩 Next Steps
- Add cross-validation
- Include prediction interval plots
- Deploy as a Shiny app (optional)

## 🔍 Output Chart
The chart below compares actual desk sales (2020) to historical averages and projected 2021 sales using Prophet's seasonality modeling.

📌 **Interactive Tool**:  
The original output was part of a forecasting tool built in Excel, where users could:
- Select the starting week for a projection drop
- Choose the percentage decrease
- Reset or change assumptions interactively

This allowed business users to model different sales decline scenarios and adjust forecasts accordingly.
<img width="1281" height="526" alt="ForecastResults" src="https://github.com/user-attachments/assets/9e2d66b1-ba24-4c1b-92c3-96a926af29bf" />

## 📬 Contact
alexablanc@github | [LinkedIn](your-link)
