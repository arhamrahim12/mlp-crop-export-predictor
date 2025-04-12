# mlp-crop-export-predictor
Multilayer Perceptron-based model to forecast crop export values for countries and regions three years into the future. Uses feature selection, scaling, and MSE loss for regression. Includes model tuning, overfitting prevention, and performance evaluation using R², MSE, and MAE metrics.

## 📌 Project Objective

- Predict future export values based on past data using MLP
- Evaluate performance using R², MSE, and MAE
- Prevent overfitting using regularization, early stopping, and feature selection

## 🧠 Model Summary

- Model: `MLPRegressor` from Scikit-learn
- Output: Single neuron for continuous value prediction
- Hidden layers: Tuned using randomized search
- Activation: ReLU (hidden layers), Linear (output)
- Loss function: Mean Squared Error (MSE)
- Optimization: Adam optimizer
- Overfitting control: L2 regularization, early stopping, cross-validation

## 🔍 Features

15 selected features using Recursive Feature Elimination (RFE) based on relevance to crop exports, including:
- Emissions (CH₄, N₂O, CO₂)
- Export/Import quantities
- Agricultural value
- Losses and other non-food usage
- Environmental indicators

## ⚙️ Preprocessing Steps

- Data filtered by country or region
- Label derived by shifting 'Export Value' by 3 years
- StandardScaler used for normalization
- Feature selection using RFE
- 80/20 train-test split

## 📁 Repository Structure

├── report.pdf # Main report (Part A) ├── code.pdf # Code (Part B) ├── predictions.csv # Model outputs (Part C) ├── README.md

markdown
Copy code

## 📊 Performance

Best region test R²: 0.949 (Africa)  
Best country test R²: 0.885 (Afghanistan)  
Average R² for regions: 0.785  
Average R² for countries: 0.588  

## 📂 Dataset Content

The dataset includes 13 CSV files, each representing a variable category:

1. **Consumer Prices** – Food price index, inflation, country, month, year  
2. **Crops Production** – Crop yields by country and year  
3. **Emissions** – CH₄, N₂O, CO₂ by crop and soil types  
4. **Employment** – Agricultural employment and work hours  
5. **Exchange Rate** – Currency and USD conversion rates  
6. **Fertilizers Use** – Types and amount used in agriculture  
7. **Food Balances** – Export/import quantities, losses, other uses  
8. **Food Security** – Indicators like irrigation, anaemia, protein supply  
9. **Food Trade** – Export/import values  
10. **FDI** – Inflows/outflows in agriculture and food sectors  
11. **Land Temperature** – Monthly temperature changes  
12. **Land Use** – Land categories and usage types  
13. **Pesticides Use** – Use per cropland area and production value  

Each file includes "Country" and "Year" as common keys. For variable definitions, see [FAOSTAT Glossary](https://www.fao.org/faostat/en/#definitions).
