# Traditional-Demand-Forecasting-Engine-using-Power-Query-Excel
Automated Demand Forecasting Engine using Power Query &amp; Excel


## Overview

In many companies, forecasting is not about finding the most advanced machine learning model. The bigger challenge is dealing with products that behave very differently from one another.

While working in inventory and category management, I helped develop an automated forecasting framework that assigns different forecasting methods to different types of products. The solution combines **Power Query**, **Excel**, and traditional forecasting techniques to generate monthly forecasts for thousands of SKUs while remaining transparent and easy for planners to maintain.

The goal was to reduce manual forecasting work and improve forecast quality by matching each product with the forecasting approach that best fits its demand pattern.

---

## Business Problem

Applying the same forecasting calculation to every SKU often produces poor results.

A mature product with stable demand behaves very differently from:

* A newly launched product
* A highly seasonal product
* A slow-moving SKU
* A product experiencing rapid growth

Instead of using a one-size-fits-all approach, I designed a segmentation-driven forecasting process that automatically selects the most appropriate forecasting logic for each product category.

---

## Tools Used

* Power Query
* Microsoft Excel
* Statistical Forecasting
* Demand Forecasting
* ABC Analysis
* XYZ Analysis

---

## Data Sources

The forecasting workflow combines multiple data sources:

* 24 months of sales history
* SKU stockout reports
* Product master data
* Product cost information
* Rolling forecast calendar
* Product classification tables

Power Query automates the extraction, transformation, and consolidation of all data sources into a standardized forecasting dataset.

<p align="center">
  <img src="https://raw.githubusercontent.com/Ibarca/Traditional-Demand-Forecasting-Engine-using-Power-Query-Excel/c73a2f9878da8b92d7786aab3bab5baa028b8908/Images/Image%2001.06.26%20at%2017.05.jpeg" width="800">
</p>
---

## Data Preparation

Forecast quality depends heavily on data quality.

Before generating forecasts, the workflow automatically:

* Removes incomplete months
* Removes duplicates and reporting errors
* Excludes discontinued and non-replenishable products
* Detects extreme sales spikes using statistical thresholds
* Excludes periods significantly impacted by stockouts
* Smooths sales history using rolling averages

These preprocessing steps ensure forecasts are based on realistic demand patterns rather than operational anomalies.

---

## Product Segmentation

A key part of the solution is classifying products according to their demand characteristics.

### ABC Analysis

Products are classified based on their contribution to annual COGS:

* **A:** High-value products
* **B:** Medium-value products
* **C:** Low-value products

### XYZ Analysis

Products are segmented according to demand variability:

* **X:** Stable demand
* **Y:** Moderate variability
* **Z:** Highly variable demand

### Lifecycle Classification

Products are classified based on their sales age:

* **NN:** Very new products
* **N:** New products

### Low Seller Classification

Products below a configurable sales threshold receive a dedicated forecasting approach.

### Seasonal Classification

Products with strong seasonal demand patterns are managed separately.

The final classification determines which forecasting method will be applied.

---

## Forecasting Logic

This project intentionally uses **traditional forecasting techniques rather than machine learning**.

The objective was to create a forecasting process that planners can easily understand, validate, and adjust without requiring data science expertise.

### Type A — Seasonal Forecasting (ETS)

Used for products with stable seasonal demand.

Forecasts are generated using Excel's `FORECAST.ETS()` function, which captures recurring seasonal patterns while accounting for long-term trends.

**Best suited for:**

* Stable products
* High-volume products
* Predictable seasonal demand

---

### Type B — Year-over-Year Monthly Average

Used for products with extreme seasonality.

Historical monthly averages from previous years are used as the baseline forecast. Forecasts can then be manually adjusted by planners based on market expectations and upcoming campaigns.

**Best suited for:**

* Highly seasonal products
* Products requiring manual planning oversight

---

### Type C1 — Raw Moving Average

Used for new products with limited sales history.

The forecast is calculated using the average monthly demand from the previous 12 months without applying cleansing or smoothing logic.

**Best suited for:**

* New products
* Products with limited historical data

---

### Type C2 — Cleansed Moving Average

Used for low-volume products.

The forecast is based on the average demand from the previous 12 months after cleansing and smoothing the historical data.

**Best suited for:**

* Low sellers
* Products with noisy demand patterns

---

### Type D — Maximum Historical Demand

Used for very new products showing rapid growth.

The forecast is based on the highest observed monthly sales value to avoid underestimating future demand.

**Best suited for:**

* Very new products
* Fast-growing products
* Products with strong growth momentum

---

## Forecast Consolidation

After forecasts are generated, Power Query consolidates all forecasting outputs into a single planning dataset.

### Final Output Structure

| SKU    | Forecast Month | Forecast Quantity |
| ------ | -------------- | ----------------- |
| 100013 | Jan-2026       | 245               |
| 100013 | Feb-2026       | 268               |
| 100013 | Mar-2026       | 302               |

This dataset can be used directly for:

* Inventory planning
* Replenishment decisions
* Purchase planning
* Supply chain forecasting

---

## Flexibility and Business Control

One of the strengths of the framework is its configurability.

Users can adjust:

* ABC thresholds
* XYZ thresholds
* Low-seller definitions
* Product age criteria
* Forecasting method assignment
* SKU-specific overrides

This allows planners to adapt the forecasting logic as product portfolios and market conditions evolve.

---

## Key Takeaways

This project demonstrates how traditional forecasting techniques, combined with strong product segmentation and automated data preparation, can create a scalable and practical forecasting solution.

Rather than relying on a single forecasting model, the framework applies different forecasting methods based on product behavior, resulting in a more realistic and business-friendly planning process.

---

## Skills Demonstrated

* Demand Forecasting
* Inventory Planning
* Forecast Segmentation
* Power Query
* Excel Forecasting Models
* Data Cleansing
* Time Series Analysis
* ABC Analysis
* XYZ Analysis
* Business Process Automation
* Supply Chain Analytics
