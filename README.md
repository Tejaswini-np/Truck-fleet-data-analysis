
# Risk Factor Analysis of Truck Fleet Data

## Overview

This project analyzes truck fleet data to understand and mitigate risks associated with driving.The analysis aims to provide insights that can help in reducing risks and ensuring compliance with traffic laws.

As the fleet manager of AZ National Trucking (ANT), the primary responsibility is to minimize risks and prevent reckless driving.

## Business Objectives

The project addresses the following business objectives:

* **Geographical Analysis:** Evaluate and compare the risk levels of cities in California to identify the riskiest areas. 
* **Truck Model Analysis:** Assess and compare truck models based on metrics such as average risk factor and the frequency of driving events. 
* **Driving Incident Analysis:** Analyze various factors related to driving incidents to understand their patterns and causes.

## Data

The analysis is based on truck fleet data. Key data columns used in the analysis include:

* `Driver_Average_mileage`
* `Total Miles`
* `Number of Events`
* `Risk Factor`
* `Scaled Risk Factor` (using min-max approach) 

**Note:** Due to data sensitivity and size constraints, the original dataset cannot be included in this repository. However, a sample dataset (`data/sample_truck_data.csv`) with a similar structure is provided for reference.

## Workflow

The analysis workflow involves the following main steps:

1.  **Data Extraction and Loading:** (Scripts for this may be present in `sqoop/`)  Data was extracted from source systems and loaded into a Hadoop cluster using Sqoop.
2.  **Data Processing:** (Scripts may be present in `scripts/`)  Data was processed and transformed as needed for analysis.
3.  **Data Analysis:**
    * Hive was used to structure and manage the data and perform analysis. SQL queries (see `sql/`) were used to derive metrics like risk factors.
    * The `predict_riskfactor_table.sql` script (in `sql/`) creates a table (`predict_riskfactor`) by joining data from `truck_mileage`, `geolocation`, `riskfactor`, and `trucks` tables to calculate key metrics. 
4.  **Visualization:** Tableau was used to create visualizations for understanding the data and presenting the findings. (Tableau files may be in `visualizations/`, or images of visualizations are included in the `README`).

## Key Findings

The analysis revealed several important insights:

* **Truck Model Analysis:**
    * The distribution of different truck models in the fleet was analyzed (see "Count of Models" chart). 
    * The total miles driven by each truck model were compared to understand usage patterns (see "Miles Driven by Truck Models" chart). 
    * Fuel efficiency trends across truck models were examined. 
    * Truck models were ranked based on their risk factor scores (see "Risk Factor by Model" chart). 
* **Geographical Analysis:**
    * The frequency of driving incidents was analyzed to compare cities (see "Chart - Common Driving Events"). 
    * The distribution of lane departure incidents across cities was visualized on a map (see "Geographical Map - Lane Departure Incidents"). 
    * The top 10 riskiest cities were identified based on the "Count of Risk Factor" (see "Top 10 Risky Cities" chart). 
* **Driving Incident Analysis:**
    * The occurrences of different types of driving events were compared (see "Occurrences of Different Events" graph). 

## Files Included

* `README.md`: This file.
* `sql/`
    * `create_predict_riskfactor_table.sql`: SQL script to create the `predict_riskfactor` table.
    * (Other SQL scripts used for analysis)
* `hive/`
    * (Hive scripts for table creation and analysis)
* `sqoop/`
    * (Sqoop scripts for data import, if available)
* `data/`
    * `sample_truck_data.csv`:  A sample of the truck fleet data.
* `visualizations/`
    * (Tableau files or images of visualizations)
        * `truck_model_bubble_chart.png` 
        * `truck_model_miles_driven_bar_chart.png` 
        * `truck_model_risk_factor_bar_chart.png` 
        * `common_driving_events_chart.png` 
        * `lane_departure_incidents_map.png` 
        * `top_10_risky_cities_bar_chart.png` 
        * `driving_events_occurrences_graph.png` 
    * (Other visualization files/images)
* `scripts/`
    * (Python or other scripts for data processing)
* `presentation/`
    * `FINAL BIGDATA GROUP 4 3.pptx`: The project presentation.

## Setup and Installation

To reproduce the analysis (if applicable), you would need the following environment:

* Hadoop cluster
* Hive
* Sqoop
* Tableau (or other visualization tool)
* (Any other relevant software/libraries)

Follow the instructions in the respective software documentation to set up these tools.  The scripts in this repository can then be used to perform the data processing and analysis steps.

## SQL Explanation

The `create_predict_riskfactor_table.sql` script creates the `predict_riskfactor` table, which is central to the analysis.  The table is created by joining several tables (`truck_mileage`, `geolocation`, `riskfactor`, and `trucks`) and includes the following columns:

* `driverid`
* `truckid`
* `riskfactor`
* `events`
* `totmiles`
* `model`
* `max_speed`
* `avg_mileage`

This table consolidates key information needed to analyze the relationship between truck models, driver behavior, and risk factors. 

## Conclusion

This project provides a comprehensive analysis of truck fleet data, delivering insights into geographical risk, truck model performance, and driving incident patterns. The findings can be used to inform strategies for improving fleet safety, reducing risks, and ensuring regulatory compliance. 
