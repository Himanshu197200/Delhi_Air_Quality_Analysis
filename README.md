# Delhi Air Quality Analysis - Pollution Trends, Prediction & Knowledge Discovery

This repository contains a complete end-to-end analytical pipeline for understanding and predicting Delhi's air quality using data-driven techniques. The project combines EDA, supervised learning, unsupervised learning, and rule mining methods to uncover how pollution behaves, why certain AQI levels occur, and how tomorrow's air quality can be predicted accurately.

## Project Goals
- Analyze long-term pollution trends in Delhi
- Understand seasonal variation & pollutant correlations
- Build interpretable AQI prediction models
- Detect pollution anomalies and natural clusters
- Extract human-readable rules explaining AQI behavior
- Provide a transparent & explainable environmental analytics system

## Dataset Overview
**Location:** Delhi, India  
**Duration:** January 2021 – December 2024  
**Frequency:** Daily observations  
**Records:** ~1460 days

### Measured Pollutants
- PM2.5
- PM10
- NO₂
- SO₂
- CO
- Ozone
- AQI

### Temporal Attributes
- Date, Month, Year
- Season (engineered)
- Holidays indicator

### Target Categories
Good, Satisfactory, Moderate, Poor, Very Poor, Severe

## Notebook 1 — Exploratory Data Analysis (EDA)
A deep exploration of Delhi's air pollution patterns.

###  Key Findings
- PM2.5 & PM10 are the dominant pollutants influencing AQI
- Winter shows severe pollution spikes
- Monsoon significantly improves pollutant levels
- AQI frequently exceeds WHO guidelines
- Correlation heatmaps show strong pollutant co-movement

###  Feature Engineering
- Lag features (1-day, 2-day, 7-day)
- Rolling means (3-day, 7-day)
- Season labels
- Holiday vs working-day pollution comparison

This notebook establishes the scientific foundation for predictive modeling.

## Notebook 2 — PCA + KNN Classification (Baseline Prediction Model)
To handle 40+ engineered features, PCA was applied to reduce dimensionality while preserving maximum variance. The reduced feature space was fed into a KNN classifier.

###  Outcomes
- PCA components optimized for best variance retention
- KNN accuracy ≈ 88–90%
- Good performance on straightforward AQI classes
- Struggles on overlapping categories like Moderate vs Poor

This highlighted the need for stronger nonlinear models.

## Notebook 3 — Random Forest (Primary Prediction Model)
Random Forest was introduced to capture complex pollution behavior.

###  Why It Works Better
- Handles nonlinear relationships
- Learns feature interactions
- Robust to noise & outliers

###  Results
- Accuracy up to 98–99%
- Top predictors include lagged PM2.5, PM10, and rolling averages
- Provides clear feature importance rankings

This became the most reliable forecasting model.

## Notebook 4 — Decision Tree (Interpretability Model)
Focused on explaining why AQI becomes Good, Moderate, Poor, etc.

###  What It Provides
- Transparent, rule-based AQI prediction
- Human-readable threshold splits
- Example: PM2.5 > 150 AND PM10 > 200 → Very Poor/Poor AQI

Although accuracy was high, depth control was used to avoid overfitting.

## Notebook 5 — Clustering & Anomaly Detection

### K-Means Clustering
Identified natural pollution-day groups:
- Clean Days (Monsoon)
- Moderate Days
- Severe Smog (Winter)

### DBSCAN
Detected pollution anomalies such as:
- Diwali firework spikes
- Stubble burning episodes
- Unexpected industrial jumps

This helps in identifying real environmental events.

## Notebook 6 — Apriori Rule Mining (Knowledge Extraction)
Converted pollutant levels into Low/Medium/High categories to discover meaningful rules.

###  Strong Discovered Rules
- {High PM2.5, High PM10} → Severe AQI
- {Low PM2.5, High Ozone} → Good AQI

These rules help environmental agencies interpret pollutant interactions transparently.

## Overall System Architecture
```
EDA 
   ↓
PCA + KNN (Baseline Classifier)
   ↓
Random Forest (Best Predictor)
   ↓
Decision Tree (Explainability)
   ↓
K-Means (Cluster Discovery)
   ↓
DBSCAN (Anomaly Detection)
   ↓
Apriori (Knowledge Mining)
```
This makes the project both predictive and interpretable.

## How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/Himanshu197200/Delhi_Air_Quality_Analysis.git
cd Delhi_Air_Quality_Analysis
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Execute Notebooks in Order
1. `01_Air_Quality_EDA.ipynb`
2. `02_KNN_PCA.ipynb`
3. `03_Random_Forest.ipynb`
4. `04_Decision_Tree.ipynb`
5. `05_Clustering_Anomaly.ipynb`
6. `06_Apriori_Rule_Mining.ipynb`

## Research Paper
The IEEE-style report provides detailed documentation:
- Data processing
- Feature engineering
- Model architectures
- Evaluation
- Pollution insights

Available in: `reports/Delhi_Air_Quality_Analysis_IEEE_Report.pdf`

## Limitations
- No meteorological features (wind, rainfall, humidity)
- Severe AQI class is rare → harder to predict
- Single-city dataset
- Forecast horizon limited to one day

## Future Enhancements
- Integrate meteorological APIs
- Use XGBoost / LightGBM
- Multi-day AQI forecasting
- Deploy as a real-time web dashboard

## Team Members
- Himanshu Mishra
- Subhan Kumar Rai
- Krish Amit Modi

**Team Name:** NAME
