Air-Quality-Fabric

Project Overview
Architected a production-ready Real-Time Intelligence solution using Microsoft Fabric to monitor and analyse global air quality telemetry by integrating with the Open AQ API. The system tracks hazardous pollutants—specifically PM2.5 and PM10—to provide actionable insights for urban health and environmental policy.
________________________________________
Technical Stack
Category	Technology
Platform	Microsoft Fabric (Real-Time Intelligence)
Ingestion	PySpark (Notebooks), Eventstreams (Kafka Protocol)
Database	Eventhouse (KQL Database / Kusto Query Language)
Orchestration	Fabric Data Pipelines (Automated Daily Scheduling)
Visualization	Power BI (Import Mode, Star Schema)
________________________________________
Data Engineering Architecture (Medallion Pattern)
1. Bronze Layer (Raw Ingestion)
	Developed a PySpark ingestion engine to fetch real-time JSON payloads from Open AQ APIs. 
	Utilised Fabric Eventstream as a high-throughput gateway, leveraging the Kafka protocol to flush data into a KQL Database with near-zero latency. 
________________________________________
2. Silver Layer (Transformation & Feature Engineering)
	Implemented KQL scripts to clean telemetry and perform complex feature engineering. 
        Extracted hour, day, and month metrics from UTC timestamps to enable time-series analysis. 
        Programmed a classification engine to categorise air quality (e.g., Good, Unhealthy) based on concentration thresholds. 
________________________________________
3. Gold Layer (Advanced Analytics & Curated Metrics)
	Engineered curated fact tables,fact_sensor_daily ,fact_sensor_calc.
	Developed KQL scripts to calculate 7-day moving averages to smoothen data noise and identify long-term trends. 
	Automated the calculation of daily change metrics to track pollutant fluctuations compared to previous 24-hour cycles. 
________________________________________
Key Metrics & KPIs
	PM2.5 Target: Monitored against a global health target of <12 μg/m³ 
	Hazardous Thresholds: Identified spikes breaching the 500 AQI hazardous limit. 
	7-Day Smoothing: Reduced data volatility through moving average computations to provide reliable trends for policy simulation. 
________________________________________
Visualization & Reporting:
	Visualised pollution hotspots using latitude and longitude markers on a map visual. 
	Built real-time indicators to track current pollutant averages against minimum, maximum, and target thresholds. 
	Configured the semantic model to refresh daily at 14:00, following the completion of the ETL pipeline at 11:30.

