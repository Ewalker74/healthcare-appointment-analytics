# Healthcare Appointment Analytics Project

## Project Overview

This project focuses on building an end-to-end data pipeline using Databricks, SQL and Power BI to analyze healthcare appointment activity.

The goal was to take raw appointment data, clean and transform it, and create a reporting-ready dataset to analyze appointment volume, scheduling lead times, and performance across practices and service lines.

This project processes data through bronze, silver, and gold layers.

**Note:** All data used in this project is synthetic and does not contain actual patient information.

## Tools Used

* Databricks Free Edition
* SQL
* Power BI Desktop

## Data Pipeline Architecture

!\[Data pipeline architecture: Bronze to Silver to Gold to Power BI](pipeline-architecture.png)

## Data Pipeline

### Bronze Layer – Data Profiling

The Bronze layer contains the raw source data. Initial profiling was performed to understand the datasets and identify potential data quality issues.

The appointments dataset contained 12,008 records. Profiling identified eight duplicate appointment IDs, missing values, and inconsistent appointment status and type values.

### Silver Layer – Data Cleaning and Enrichment

The Silver layer focuses on preparing the data for reporting.

* Removed duplicate appointment records.
* Standardized appointment statuses and types.
* Converted blank values to NULL where appropriate.
* Joined appointments to the Practices table to include practice names and service lines.
* Created flags for appointment statuses and new patient appointments.
* Calculated scheduling lead days between the scheduled date and appointment date.

### Gold Layer – Monthly Appointments Mart

The Gold layer contains the final reporting dataset, with appointment data aggregated by month and practice.

The mart includes appointment counts by status, new patient appointments, and scheduling lead-day metrics. Total lead days and valid record counts were retained to allow accurate average calculations in Power BI.

## Data Validation

Data quality checks were performed throughout the pipeline, including record counts, duplicate checks, missing values, and validation of the expected table grain.

The Gold mart was also reconciled against Silver to confirm that appointment counts and lead-day calculations remained consistent after aggregation.

## Power BI Dashboard

The Gold appointments mart was connected to Power BI to create an interactive Appointment Performance dashboard.

The dashboard includes total appointments, completion rate, cancellation rate, no-show rate, new patient rate, and average scheduling lead days.

Additional visuals show appointment volume by service line and monthly performance trends. Users can filter the report by year, month, and service line.

