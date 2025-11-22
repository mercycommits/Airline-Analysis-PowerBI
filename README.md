# ✈️ Flight Performance Analysis — Power BI Case Study

This repository contains a complete end-to-end **Flight Performance Analytics Project**, built using **Power BI**, **clean data modeling (Star Schema)**, and well-structured **DAX measures**.
The goal of the project is to evaluate **flight punctuality**, **delays**, **cancellations**, and **time-of-day performance** across multiple airlines and airports.

This project demonstrates practical BI skills in:

Data cleaning & modeling
Fact–dimension schema design
Creating calculated columns
Writing analytical DAX measures
Designing multi-page interactive dashboards
Documenting a reproducible BI workflow

---

## 📘 Project Overview

Air travel delays affect customer satisfaction, airline operations, and airport planning.
This case study analyzes historical flight performance data to answer key questions:

### **Business Questions**

* Which airports consistently perform best or worst?
* Which airlines have the highest delay rates?
* What hours of the day experience the most delays?
* Are there seasonal or monthly patterns in performance?
* How do delays differ by day of week?
* What is the overall On-Time Performance %?

### **Key Insights Delivered**

* Peak delay hours and their characteristics
* Best/worst performing airlines and airports
* KPI tracking for cancellations, delays, and overall on-time rate
* Seasonal trends across months
* Hourly heatmaps for operational bottleneck analysis

---

## 🧱 Data Model (Star Schema)

The dataset was transformed into a **clean semantic model**:

### **Fact Table**

* `FactFlights` — flight-level records including delays, cancellations, and mappings to dimensions.

### **Dimension Tables**

* `dimAirline` — AirlineID, Airline Name
* `dimAirport` — AirportID, Airport Code
* `dimTime` — HourID, time-of-day categories, hour labels

All calculated columns and DAX measures are documented under `Documentation/`.

---

## 📊 Power BI Report Pages

The Power BI dashboard contains **6 analytical pages**:

1. **Overview Dashboard**

   * High-level KPIs
   * Delay %, On-Time %, Cancellations
   * Trend charts

2. **Airport Performance**

   * Comparison across BWI, DCA, IAD
   * Delay rates by airport

3. **Airline Performance**

   * Airline comparison matrix
   * Delay %, cancellations, avg delay minutes

4. **Time-of-Day Analysis**

   * Delays by hour
   * Hour vs Day-of-Week heatmap
   * KPI: Worst Delay Hour

5. **Monthly Trends**

   * Seasonal patterns
   * Month-over-month delay analysis

6. **Detail / Drill-Down Page**

   * For analysts performing deep dives

---

## 🧮 DAX & Calculated Columns

All formulas are fully documented here:

📄 `/DAX-Measures-and-Calculated-Columns/measures.md`
📄 `/DAX-Measures-and-Calculated-Columns/calculated-columns.md`

This includes:

* Total Flights
* Delay %
* On-Time %
* Worst Hour KPI logic
* HourID mapping
* Sorting columns (MonthNumber, Day-of-Week Number)

---

## 🔁 Reproducibility

Anyone can reproduce this analysis using:

1. Install **Power BI Desktop**
2. Download the `.pbix` file from `/PowerBI/Flight_Report.pbix`
3. Open the report — all relationships, DAX measures, and calculated columns are already embedded
4. Refresh the data if raw files are included

No additional configuration is required.

---

## 🛠 Tools & Technologies

* **Power BI Desktop**
* **DAX**
* **Power Query (M)**
* **Data Modeling (Star Schema)**
* **Visualization Design & UX**

---
