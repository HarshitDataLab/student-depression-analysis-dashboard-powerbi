# Repository Configurations

* **Repository Name:** student-depression-analytics
* **Short Description:** A 3-page Power BI dashboard analyzing academic pressure, lifestyle habits, and depression rates across 27K+ students.

---

# README.md

# Student Mental Health Analytics Dashboard

A professional 3-page **Power BI Dashboard** analyzing the physiological, academic, and environmental drivers of stress and depression across **27,901 students**. 

This repository contains the interactive report designed to isolate high-risk groups, track academic performance correlations, and map lifestyle compounding factors for educational institutions and mental health advocates.

---

## 📊 Dashboard Architecture

The dashboard is logically segmented across three analytical pages to simplify complex data storytelling:

### 1. Student Mental Health Overview
* **Executive Summary:** Quick-glance KPI blocks tracking **Total Students Surveyed**, **Overall Depression Rate (58.55%)**, and **Suicidal Ideation Rate (63.28%)**.
* **Workload & Demographics:** Aggregated tracking of average study hours, age distributions, and high-level behavioral stress filters.

### 2. Academic & Demographic Insights
* **CGPA Trend Analytics:** A clean, segmented line chart tracking depression rates against structural academic brackets (*9.0+ Excellent, 8.0–8.9 Very Good, etc.*).
* **Workload Imbalances:** Clustered column charts contrasting absolute student numbers across levels of academic pressure (Scale 1–5) and current diagnostic status.
* **Geographic Distribution:** Bar chart segmentation isolating the top 10 urban centers with the highest density of reported student depression cases.

### 3. Lifestyle & Environmental Stressors
* **Lifestyle Overlap Heatmap:** A conditional-formatted matrix grid highlighting the exact intersection points of sleep deprivation (*e.g., <5 hours*) and dietary habits (*Healthy, Moderate, Unhealthy*).
* **Genetic Risk Profiling:** A 100% stacked percentage chart visually proving the correlation between a student's family history of mental illness and their diagnostic outcome.
* **Scatter Plot Correlatives:** Dynamic multi-variable plot tracking individual student workloads against a cumulative **Total Stress Index**.

---

## 🛠️ Data Engineering & DAX Calculations

To facilitate meaningful aggregations and smooth out visualization noise, the raw dataset was transformed using custom **Data Analysis Expressions (DAX)** columns and measures:

### Dynamic Segmentation Column
```dax
```
CGPA Range = 
SWITCH(
    TRUE(),
    'Student Depression'[CGPA] >= 9.0, "1. 9.0+ Excellent",
    'Student Depression'[CGPA] >= 8.0, "2. 8.0 - 8.9 Very Good",
    'Student Depression'[CGPA] >= 7.0, "3. 7.0 - 7.9 Good",
    'Student Depression'[CGPA] >= 5.0, "4. 5.0 - 6.9 Average",
    "5. Below 5.0"
)

### Analytical Health Metrics
``
Depression Rate = 
DIVIDE(
    CALCULATE(COUNT('Student Depression'[id]), 'Student Depression'[Depression Status] = "Depressed"),
    COUNT('Student Depression'[id]),
    0
)

Total Stress Score = 
'Student Depression'[Academic Pressure] + 'Student Depression'[Financial Stress] + 'Student Depression'[Work Pressure]
