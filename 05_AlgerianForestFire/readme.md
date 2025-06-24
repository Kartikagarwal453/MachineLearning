# Algerian Forest Fire FWI Prediction Web App

## Project Overview
This project is a Flask-based web application that predicts the Fire Weather Index (FWI) for Algerian forests using meteorological and fire-related features. The model is trained on the Algerian Forest Fires dataset, which contains data from two regions in Algeria (Bejaia and Sidi Bel-abbes) collected between June and September 2012. The app allows users to input relevant features and receive a prediction for the FWI, which is an important indicator for forest fire risk.

## Dataset
- **Source:** Algerian Forest Fires Dataset (2012)
- **Regions:** Bejaia (northeast Algeria) and Sidi Bel-abbes (northwest Algeria)
- **Period:** June 2012 to September 2012
- **Instances:** 244 (122 per region)
- **Attributes:** 11 features + 1 output (class)
- **Classes:** Fire (138), Not Fire (106)

### Features Used
The model uses the following input features:
- **Temperature:** Noon temperature (°C)
- **RH:** Relative Humidity (%)
- **Ws:** Wind speed (km/h)
- **Rain:** Total daily rainfall (mm)
- **FFMC:** Fine Fuel Moisture Code (FWI system)
- **DMC:** Duff Moisture Code (FWI system)
- **ISI:** Initial Spread Index (FWI system)
- **Classes:** Encoded as 1 (Fire) or 0 (Not Fire)
- **Region:** 0 (Bejaia), 1 (Sidi Bel-abbes)

> **Note:** The model does not use all original dataset columns. Only the above features are required for prediction.

## Model
- **Type:** Ridge Regression
- **Preprocessing:** StandardScaler for feature scaling
- **Performance:**
    - Mean Absolute Error (MAE): ~0.56
    - R² Score: ~0.98 (on test set)
- **Artifacts:**
    - `models/ridge.pkl` (trained model)
    - `models/scaler.pkl` (feature scaler)

## App Structure
- `application.py`: Main Flask app
- `models/`: Contains trained model and scaler
- `templates/`: HTML templates for the web interface
- `notebooks/`: Data analysis, model training, and datasets

## Setup & Installation
1. **Clone the repository:**
   ```bash
   git clone <repo-url>
   cd 05_AlgerianForestFire
   ```
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Ensure model files are present:**
   - `models/ridge.pkl`
   - `models/scaler.pkl`
   (If not, retrain using the provided notebooks.)
4. **Run the app:**
   ```bash
   python application.py
   ```
5. **Access the app:**
   - Open your browser and go to [http://127.0.0.1:5000](http://127.0.0.1:5000)

## Usage
1. Go to the `/predictdata` page or click the prediction link on the home page.
2. Enter the following features:
   - Temperature
   - RH (Relative Humidity)
   - Ws (Wind speed)
   - Rain
   - FFMC
   - DMC
   - ISI
   - Classes (1 for Fire, 0 for Not Fire)
   - Region (0 for Bejaia, 1 for Sidi Bel-abbes)
3. Click **Predict** to get the FWI prediction.

## Example
| Temperature | RH | Ws | Rain | FFMC | DMC | ISI | Classes | Region |
|-------------|----|----|------|------|-----|-----|---------|--------|
| 29          | 57 | 18 | 0.0  | 65.7 | 3.4 | 1.3 | 0       | 0      |

## References
- [UCI Machine Learning Repository: Algerian Forest Fires Dataset](https://archive.ics.uci.edu/ml/datasets/Algerian+Forest+Fires+Dataset+)

## License
This project is for educational and research purposes only.
