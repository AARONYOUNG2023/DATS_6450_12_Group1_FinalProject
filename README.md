# DATS_6450_12_Group1_FinalProject

# Introduction

The goal of this project is to analyze and predict ride-sharing prices for Uber and Lyft in Boston, Massachusetts, leveraging the power of cloud computing with AWS. By exploring patterns in pricing and identifying key factors influencing these fluctuations, we aim to provide insights into ride-sharing dynamics and develop a predictive model for price forecasting.

To achieve this, we utilized a dataset comprising 693,071 observations and 57 variables sourced from Kaggle, containing information such as ride distance, surge pricing, and weather conditions. AWS services formed the backbone of our project, enabling efficient data handling, processing, modeling, and visualization.

## Model Results:
We evaluated three models for predicting ride-sharing prices, with the following results:
- **Linear Regression**:
  - R² Score: 0.89
  - Mean Squared Error (MSE): 9.34
- **Principal Component Regression (PCR)**:
  - R² Score: 0.42
  - Mean Squared Error (MSE): 50.62
- **Decision Tree**:
  - R² Score: 0.90
  - Mean Squared Error (MSE): 8.72

The Decision Tree model demonstrated the best performance in terms of predictive accuracy, capturing non-linear relationships in the data effectively.

## AWS Usage:
- **Amazon S3**: Stored raw ride and weather data, along with processed datasets, ensuring scalable and secure data storage.
- **AWS Glue**: Preprocessed and cleaned the data, handling null values, extracting relevant features, and integrating ride data with weather attributes.
- **Amazon SageMaker**: Facilitated the training and deployment of machine learning models, leveraging its robust infrastructure to predict ride prices accurately.
- **Amazon RDS**: Stored prediction results and analysis outputs for easy querying and integration with other tools.
- **Amazon QuickSight**: Provided dynamic visualizations and dashboards, presenting insights on price trends, factors affecting pricing, and model performance.

This comprehensive pipeline not only enabled efficient data processing but also allowed for seamless integration and analysis, ultimately offering an in-depth understanding of ride-sharing pricing strategies. The outcomes of this project include a functional price prediction model and actionable insights for both ride-sharing companies and consumers.
