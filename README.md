# Air-Quality-Fabric

Project Overview:
        Architected a production-ready Real-Time Intelligence solution using Microsoft Fabric to monitor and analyse global air quality telemetry
        by integrating with the Open AQ API, the system tracks hazardous pollutants—specifically PM2.5 and PM10—to provide actionable insights for urban                   health and environmental policy
-------------------------------------------------------------------------------------
Technical Stack:
         Platform: Microsoft Fabric (Real-Time Intelligence)
         Ingestion: PySpark (Notebooks), Eventstreams (Kafka Protocol)
         Database: Eventhouse (KQL Database / Kusto Query Language)
         Orchestration: Fabric Data Pipelines (Automated daily scheduling)
         Visualization: Power BI (Import Mode, Star Schema)
------------------------------------------------------------------
Data Engineering Architecture (Medallion Pattern)
     1. Bronze Layer (Raw Ingestion)
        Developed a PySpark ingestion engine to fetch real-time JSON payloads from Open AQ        APIs.
        Utilised Fabric Eventstream as a high-throughput gateway, leveraging the Kafka protocol to flush data into a KQL Database with near-zero latency.
     2. Silver Layer (Transformation & Feature Engineering)
        Implemented KQL scripts to clean telemetry and perform complex feature engineering.
        Temporal Enrichment: Extracted hour, day, and month metrics from UTC timestamps to enable time-series analysis.
        Conditional Logic: Programmed a classification engine to categorise air quality (e.g., "Good", "Unhealthy") based on concentration thresholds.
     3. Gold Layer (Advanced Analytics & Curated Metrics)
        Engineered curated fact tables (fact_sensor_daily and fact_sensor_calc) to support stable reporting.
        Pre-computed Metrics: Developed KQL scripts to calculate 7-day moving averages to smoothen data noise and identify long-term trends.
        Delta Analysis: Automated the calculation of daily change metrics to track pollutant fluctuations compared to previous 24-hour cycles.
------------------------------------------------------------------------------------------------------------------------------------------------
Key Metrics & KPIs:
PM2.5 Target: Monitored against a global health target of <12 μg/m³.
Hazardous Thresholds: Identified spikes breaching the 500 AQI hazardous limit.
7-Day Smoothing: Reduced data volatility through moving average computations to provide reliable trends for policy simulation.
-------------------------------------------------------------------------------------------------------------------------------------------------
Visualization & Reporting:
Geospatial Analysis: Visualised pollution hotspots using latitude and longitude markers on a map visual.
Gauge Visuals: Built real-time indicators to track current pollutant averages against minimum, maximum, and target thresholds.
Automated Refresh: Configured the semantic model to refresh daily at 14:00, following the completion of the ETL pipeline at 11:30.


