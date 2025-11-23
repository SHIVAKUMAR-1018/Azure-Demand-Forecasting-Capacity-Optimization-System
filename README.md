# Azure based Demand Forecasting and Capacity Optimization System
Architecture:

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/925b2940-6764-44e9-ac4b-b165a4c25048" />

Demo Video:




https://github.com/user-attachments/assets/612d3af2-96f6-4537-bfa7-b45d8b06aeef




This project implements an end-to-end cloud-based forecasting system designed to predict Azure Compute and Storage demand. The workflow integrates multi-cloud data ingestion, scalable storage, advanced feature engineering, machine learning model training, and Power BI–based visualization to support Azure’s capacity planning and supply chain decision-making.
<img width="1000" height="342" alt="image" src="https://github.com/user-attachments/assets/64ef7ff5-cff4-4b21-813b-b647acbd11e2" />



*1. Data Sources*
   
The solution brings together data from three major platforms:
- Snowflake DB – provides structured enterprise usage and infrastructure data.
- Google Cloud Platform (GCP) – supplies external cloud usage signals and demand indicators.
- Render API – provides API-level real-time consumption metrics.
These diverse sources create a rich dataset combining internal and external demand drivers.

<img width="1000" height="342" alt="image" src="https://github.com/user-attachments/assets/6e947ad8-d2bb-4d07-bed2-3da01e5ff3e1" />

*2. Data Ingestion Layer*
   
All incoming data is ingested through:

✔ Azure Data Factory (ADF)
+ Automates ingestion workflows
+ Connects securely to Snowflake, GCP, and API endpoints
+ Handles scheduling, pipelines, and logging

✔ Azure Data Lake Storage (ADLS)
+ Acts as the centralized raw data storage location
+ Stores data in hierarchical folders for easy integration with Databricks
This ensures scalable, fault-tolerant data handling capable of growing with Azure’s infrastructure signals.

<img width="1000" height="342" alt="image" src="https://github.com/user-attachments/assets/adca9e84-ada0-4c1e-a29d-d2a84924e34e" />


*3. Data Processing Layer (Azure Databricks)*

Azure Databricks is the core data processing and ML environment in this architecture.

✔ Bronze Layer (Raw Data)
+ Stores unprocessed data exactly as received
+ Maintains full data lineage and fidelity

✔ Silver Layer (Clean + Enriched Data)
+ Data cleaning applied
+ Feature engineering performed (lags, moving averages, seasonality, growth, economic indicators, etc.)
+ Time-series alignment and normalization

✔ Gold Layer (Model-Ready Data)
+ Final curated dataset
+ Used for machine learning and dashboard consumption

This multi-layered Lakehouse approach ensures clean, high-quality, reliable input for modeling.

<img width="600" height="442" alt="image" src="https://github.com/user-attachments/assets/ef219e2b-e8fe-44e7-abfb-7310815ae837" />

*4. Machine Learning Model Training*

The Model Training block uses Databricks ML runtime to build multiple forecasting models:
+ Random Forest
+ XGBoost Regressor
+ Prophet
+ ARIMA (Auto-ARIMA)

Each model is trained on engineered features from the Silver/Gold layers.

Model	Accuracy-
Random Forest: 	97.69% (Best),
      XGBoost:    97.47%,
        ARIMA:    84.2%,
      Prophet: 	84.19%

Random Forest performed the best due to its ability to learn complex patterns from multiple correlated signals.

The final outputs include:
+ Predicted Compute demand
+ Predicted Storage demand
+ Weekly and monthly trend insights
+ Model performance metrics (MAE, RMSE, SMAPE)

*5. Visualization Layer (Power BI)*

The final forecasts and performance metrics are published to Power BI, enabling:
+ Real-time interactive dashboards
+ Demand trend reports
+ Regional and service-level breakdowns
+ Capacity planning insights
+ Model accuracy monitoring
<img width="648" height="367" alt="image" src="https://github.com/user-attachments/assets/c94f2be6-1315-44ef-adda-bae07297d2ad" />
<img width="654" height="362" alt="image" src="https://github.com/user-attachments/assets/3a80e199-3903-4f80-a6d6-224539b4f87c" />
<img width="650" height="363" alt="image" src="https://github.com/user-attachments/assets/71e3c863-215c-4786-8e36-87d2fefd11fa" />


The dashboard is visible in this link: https://app.powerbi.com/view?r=eyJrIjoiOGYxYTA5NWMtZTg3NC00Nzk4LThjZjMtNDVlMmE2OTc1ZmI2IiwidCI6IjE1YzM0OWUxLTBjNTUtNDYwOS1iMzNhLWM2MjJkOWU2NjRlYSJ9

*Summary* 

This project delivers an integrated cloud-based forecasting system that ingests multi-cloud data from Snowflake, GCP, and API sources into Azure storage via ADF, processes it through a Databricks Lakehouse (Bronze-Silver-Gold layers), trains multiple ML models to predict Azure Compute & Storage demand, and visualizes the insights in Power BI.
Random Forest delivered the best forecast accuracy (97.69%), enabling Azure to optimize capacity planning and reduce infrastructure cost inefficiencies.
