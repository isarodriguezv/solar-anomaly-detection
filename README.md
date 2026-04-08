# Photovoltaic System Performance Monitoring & Anomaly Detection
This project simulates a real-world photovoltaic monitoring system used to detect performance anomalies and support maintenance decisions.

## Overview

This project focuses on analyzing the operational performance of photovoltaic (PV) systems using real-world data from solar inverters and project-level information.

The objective is to identify abnormal performance patterns and potential maintenance needs through a rule-based analytical approach, without relying on machine learning models.

The solution integrates multiple data sources, applies data cleaning and transformation processes, and generates performance indicators and operational alerts to support decision-making.

## Problem Statement

Photovoltaic systems are highly dependent on external factors such as irradiance and environmental conditions, making it difficult to directly detect failures using raw generation data.

Daily fluctuations in energy production do not necessarily indicate system issues, which can lead to incorrect maintenance decisions if not properly analyzed.

This project addresses the challenge of distinguishing between normal variability and potential performance degradation using available operational data.

## Solution Approach

A rule-based anomaly detection system was developed to evaluate system performance using engineered features derived from operational and project-level data.

Instead of directly predicting failures, the model identifies patterns of abnormal performance that may require further inspection.

Key elements of the approach include:

- Integration of operational and master datasets
- Data cleaning and standardization
- Feature engineering based on photovoltaic performance logic
- Rolling performance metrics to reduce daily noise
- Alert-based classification of system behavior

## Data Architecture

The project follows a medallion architecture:

- **Bronze**: Raw data from inverter systems and project master records  
- **Silver**: Cleaned and standardized datasets  
- **Gold**: Analytical dataset with performance indicators and alerts  

This structure ensures data traceability and separation between raw, processed, and analytical layers.

## Feature Engineering

Several key indicators were developed to evaluate system performance:

- **Theoretical Energy**: Estimated from installed capacity and solar resource (HSP)
- **Real Performance Ratio (PR)**: Measures actual performance vs expected energy
- **Performance Deviation**: Difference between real performance and design expectations (PVsyst)
- **Rolling Performance Metrics (7-day window)**: Smooths short-term variability
- **Daily Variation**: Detects abrupt changes in generation
- **Operational Status Indicators**: Includes inactivity, project state, and maintenance history

## Alert System

Instead of directly classifying failures, the system generates operational alerts:

- **Expected Operation**: Performance aligned with expectations  
- **Possible Degradation**: Moderate and sustained underperformance  
- **Low Performance**: Significant deviation from expected behavior  
- **Critical Alert**: System inactivity or severe anomalies  

Additionally, a **potential soiling alert** was implemented to detect gradual efficiency loss patterns consistent with panel dirt accumulation.

## Limitations

The model does not include external variables such as irradiance or weather conditions, which are key drivers of photovoltaic performance.

As a result, the system does not diagnose root causes directly, but instead identifies anomalous behavior patterns that may require further investigation.

This design decision ensures reliability given the available data.

## Key Learnings

- Real-world data often contains inconsistencies that must be carefully handled  
- Data integration requires aligning identifiers across multiple sources  
- Not all problems require machine learning; rule-based systems can be effective when grounded in domain knowledge  
- Understanding the business and physical context is critical for building meaningful analytics solutions  

## Technologies Used

- Python (Pandas, NumPy)
- Data cleaning and transformation techniques
- Jupyter Notebooks
- Analytical feature engineering

## Conclusion

This project demonstrates how to transform raw operational data into actionable insights using a structured analytical approach.

By combining data engineering, domain knowledge, and feature engineering, it is possible to detect meaningful performance patterns even without advanced machine learning models.
