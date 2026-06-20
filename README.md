Bengaluru House Price Prediction
## Overview
Machine learning project to predict house prices in Bengaluru based on features like location, total sqft, BHK, and bathrooms.

## Dataset
- **File**: `bengaluru_house_prices.csv`
- **Source**: Kaggle Bengaluru House Price Dataset
- **Features**: location, size, total_sqft, bath, price
- **Size**: ~13,000+ records

## Tech Stack
- Python, Pandas, NumPy
- Scikit-learn, Matplotlib, Seaborn
- Linear Regression, Lasso, Decision Tree

## Project Workflow
1. Data Cleaning - Handling null values, outliers, feature engineering
2. Exploratory Data Analysis - Price vs location, BHK trends
3. Model Building - Training regression models and comparing accuracy
4. Model Deployment - Flask/Streamlit web app for price prediction

## Demo
Video walkthrough: `house price prediction.mp4`

## How to Run
1. Clone repo: `git clone https://github.com/Ashish304544/house-price-prediction-.git`
2. Install dependencies: `pip install -r requirements.txt`
3. Run notebook: `jupyter notebook Bengaluru_Price_Prediction.ipynb`

## Results
Achieved ~85% accuracy using Linear Regression after feature engineering and outlier removal.

## Future Scope
- Add more cities
- Use advanced models like XGBoost
- Deploy on AWS/Heroku
