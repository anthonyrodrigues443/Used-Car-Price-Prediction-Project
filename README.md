# Car Price Prediction Web Application

[![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![Flask](https://img.shields.io/badge/Flask-2.0+-green.svg)](https://flask.palletsprojects.com/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-0.24+-red.svg)](https://scikit-learn.org/)

## Overview
A machine learning web application that predicts car prices based on various features like manufacturer, model year, mileage, and other specifications. The project uses Random Forest Regression for predictions and Flask for the web interface.<br>
<img src="https://github.com/Sharkytony/Used-Car-Price-Prediction-Project/blob/main/web_page_images/web_1.png" width=400px><img src="https://github.com/Sharkytony/Used-Car-Price-Prediction-Project/blob/main/web_page_images/web_2.png" width=400px><img src="https://github.com/Sharkytony/Used-Car-Price-Prediction-Project/blob/main/web_page_images/web_3.png" width=400px><img src="https://github.com/Sharkytony/Used-Car-Price-Prediction-Project/blob/main/web_page_images/web_op.png" width=400px>
## Project Structure
```
Used-Car-Price-Prediction-Project/
├── main.ipynb                 # EDA and Model Building Notebook
├── app.py                     # Flask application
├── pipeline.py                # Data preprocessing pipeline
├── requirements.txt           # Project dependencies
├── model/
│   └── rforest_model.pkl     # Trained Random Forest model
├── feature_encoders/         # Saved feature encoders
│   ├── cat_encoder.pkl
│   ├── color_encoder.pkl
│   ├── dw_encoder.pkl
│   ├── fuel_encoder.pkl
│   ├── gbt_encoder.pkl
│   └── man_encoder.pkl
├── scaler/
│   └── scaler.pkl           # Feature scaler
└── templates/
    ├── index.html           # Input form template
    └── predictions.html     # Results display template
```

## Features
- Comprehensive data preprocessing pipeline
- Support for various car specifications:
  - Manufacturer and Model
  - Production Year
  - Category (Sedan, SUV, etc.)
  - Engine Specifications (Volume, Turbo)
  - Interior Features (Leather, Airbags)
  - Technical Specifications (Gear Box, Drive Wheels)
- Automatic handling of missing values
- Feature encoding for categorical variables
- Data scaling for numerical features
- Web interface for easy predictions

## Installation

```bash
# Clone the repository
git clone https://github.com/Sharkytony/Used-Car-Price-Prediction-Project.git
cd Used-Car-Price-Prediction-Project

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Usage

1. Start the Flask application:
```bash
python app.py
```

2. Open your web browser and navigate to `http://localhost:5000`

3. Enter the car specifications in the form

4. Click "Predict" to get the estimated car price

## Data Preprocessing Pipeline

The project includes a robust data preprocessing pipeline that handles:

1. Missing Value Treatment
2. Feature Engineering:
   - Car Age Calculation
   - Turbo Engine Detection
   - Mileage Standardization
3. Categorical Encoding:
   - Manufacturer Categories
   - Car Categories
   - Fuel Types
   - Color Schemes
4. Feature Scaling

Example usage of the pipeline:

```python
import pipeline

# Create input DataFrame
input_df = pipeline.create_df(np.nan, new_input['Levy'], new_input['Manufacturer'], np.nan, 
new_input['Prod. year'], new_input['Category'],new_input['Leather interior'],
 new_input['Fuel type'], new_input['Engine volume'] , new_input['Mileage'],
 new_input['Cylinders'],new_input['Gear box type'], new_input['Drive wheels'],
 np.nan, new_input['Wheel'], new_input['Color'], new_input['Airbags'])

# Process data
input_processed_df = pipeline.entire_pipeline(input_df, man_encoder, cat_encoder,fuel_encoder, 
gbt_encoder, dw_encoder,color_encoder, scaler)

# Prediction
pred_price = loaded_model.predict(input_processed_df)

```

## Model Details

The project uses a Random Forest Regression model trained on historical car price data. Key features of the model:

- Algorithm: Random Forest Regressor
- Input Features: 17 processed features
- Target Variable: Car Price
- Encoding: One-Hot Encoding for categorical variables
- Scaling: Standard Scaler for numerical features

<img src="https://github.com/Sharkytony/Used-Car-Price-Prediction-Project/blob/main/feature_importances.png">

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
