# NASA Turbofan Engine Sensor Analysis

## Project Overview

This project analyzes sensor data from simulated turbofan engines to investigate how sensor behavior changes throughout an engine's operating life.

The goal is to identify sensors that show consistent changes as engines approach the end of their useful life and determine which sensors may be useful for monitoring engine degradation.

The project uses Python-based data analytics techniques including data cleaning, statistical analysis, correlation analysis, normalization, trend analysis, and data visualization.

No machine learning is used in this project. The analysis focuses on understanding the engineering data and identifying potential degradation indicators.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Engineering Question](#engineering-question)
- [Objectives](#objectives)
- [Dataset](#dataset)
- [Tools & Technologies](#tools--technologies)
- [Methodology](#methodology)
- [Key Results](#key-results)
- [Sensor Behavior Near End of Engine Life](#sensor-behavior-near-end-of-engine-life)
- [Late-Life Trend Analysis](#late-life-trend-analysis)
- [Operating Condition Analysis](#operating-condition-analysis)
- [Visualizations](#visualizations)
- [Engineering Interpretation](#engineering-interpretation)
- [Limitations](#limitations)
- [Future Work](#future-work)
- [Project Structure](#project-structure)
- [Conclusion](#conclusion)
- [References](#references)

## Engineering Question

> Which engine sensors consistently change as engines approach the end of their operating life, and which sensors provide the strongest evidence of potential engine degradation?

---

## Objectives

- Clean and organize turbofan engine sensor data.
- Explore sensor behavior throughout engine life.
- Analyze sensor variability.
- Identify sensors with meaningful changes over engine life.
- Determine whether sensor trends are consistent across multiple engines.
- Analyze relationships between sensors and normalized engine life.
- Investigate whether operating conditions influence sensor behavior.
- Analyze sensor behavior during the later stages of engine life.
- Identify potential sensors for engine degradation monitoring.
- Communicate findings using engineering plots and statistical analysis.

---

## Dataset

The project uses the NASA turbofan engine degradation dataset from the NASA Prognostics Center of Excellence.

The dataset contains simulated turbofan engines operating under different conditions until failure.

### Dataset Summary

- **100 engines**
- **20,631 observations**
- **21 sensor measurements**
- **3 operating settings**
- Engine ID
- Operating cycle

Each row represents a measurement taken from an engine during a specific operating cycle.

---

## Tools & Technologies

- Python
- pandas
- NumPy
- Matplotlib
- Jupyter Notebook
- Git
- GitHub

### Skills Demonstrated

- Data cleaning
- Exploratory data analysis
- Descriptive statistics
- Standard deviation analysis
- Correlation analysis
- Data aggregation
- Normalization
- Linear trend analysis
- Slope analysis
- Engineering data visualization
- Engineering interpretation

---

## Methodology

### 1. Data Loading & Organization
- Loaded the NASA C-MAPSS FD001 turbofan engine dataset using Python and pandas.
- Added descriptive column names for engine ID, operating cycle, operating settings, and sensor measurements.
- Verified dataset dimensions, data types, missing values, and number of unique engines.

### 2. Initial Dataset Exploration
- Examined engine operating cycles to understand differences in engine lifetime.
- Calculated descriptive statistics for engine life.
- Reviewed sensor ranges and variability to identify potentially useful degradation indicators.

### 3. Engine Life Normalization
- Calculated the maximum operating cycle for each engine.
- Normalized each engine's cycle count to a percentage of its total operating life.
- Used normalized engine life to compare sensor behavior across engines with different lifetimes.

### 4. Sensor Variability Analysis
- Calculated the standard deviation of each sensor.
- Compared sensor variability and visual trends across multiple engines.
- Identified sensors showing consistent changes versus sensors with inconsistent behavior.

### 5. Candidate Sensor Selection
- Selected sensors showing the strongest potential relationship with engine degradation based on variability, correlation, and visual trends.
- Initial candidates included Sensors 4, 7, 11, 12, and 15.

### 6. Cross-Engine Validation
- Calculated correlations between candidate sensors and normalized engine life for individual engines.
- Compared results across engines to determine whether sensor trends were consistent.
- Evaluated the percentage of engines showing the expected direction of change.

### 7. Correlation With Engine Life
- Calculated correlations between sensor measurements and normalized engine life.
- Used correlation strength and direction to identify sensors with potential degradation-related behavior.

### 8. Sensor Behavior Across Engine Life
- Divided normalized engine life into four stages:
  - 0–25%
  - 25–50%
  - 50–75%
  - 75–100%
- Calculated average sensor values within each stage.
- Compared trends and changes in slope between different stages of engine life.

### 9. Late-Life Slope Analysis
- Calculated sensor slopes during later portions of engine life.
- Compared slope changes between consecutive life stages to determine whether sensor trends became more pronounced near the end of engine life.

### 10. Operating Condition Analysis
- Examined the three operating settings and their variability.
- Calculated correlations between operating settings and the selected candidate sensors.
- Evaluated whether observed sensor trends could be strongly explained by changes in operating conditions.

### 11. Engineering Interpretation
- Combined statistical results, cross-engine consistency, correlation analysis, and visual trends.
- Identified Sensors 4, 7, 11, 12, and 15 as the strongest candidates for further degradation analysis.
- Interpreted these sensors as potential degradation indicators rather than definitive failure predictors.
---

## Key Results

The analysis identified five sensors that consistently exhibited relationships with normalized engine life:

| Sensor | Mean Within-Engine Correlation | Expected Direction | Engines Showing Expected Direction |
|---|---:|---|---:|
| Sensor 11 | 0.811 | Increasing | 100% |
| Sensor 12 | -0.790 | Decreasing | 100% |
| Sensor 4 | 0.782 | Increasing | 100% |
| Sensor 7 | -0.762 | Decreasing | 100% |
| Sensor 15 | 0.725 | Increasing | 100% |

### Main Findings

- **Sensors 4, 11, and 15** showed increasing behavior as normalized engine life progressed.
- **Sensors 7 and 12** showed decreasing behavior as normalized engine life progressed.
- All five candidate sensors showed the expected direction across **100% of the engines analyzed**.
- Sensor behavior generally became more pronounced during the later stages of engine life.
- Sensors 4, 7, 11, 12, and 15 were identified as promising candidates for further degradation analysis.
- The candidate sensors showed very weak linear correlations with the measured operating settings.

---

## Sensor Behavior Near End of Engine Life

The candidate sensors displayed different directional trends but similar changes in behavior as engines approached the end of their operating lives.

### Increasing Sensors: 4, 11, and 15

These sensors generally:

- Remained relatively stable around an average value during the earlier portion of engine life.
- Began showing a slight increase around approximately 40–60% of normalized engine life.
- Displayed a more pronounced increase after approximately 60% of normalized engine life.

### Decreasing Sensors: 7 and 12

These sensors generally:

- Remained relatively stable during the early portion of engine life.
- Began showing a small decrease around approximately 40–60% of normalized engine life.
- Displayed a stronger downward trend after approximately 60% of normalized engine life.

The similar timing of these changes suggests that the candidate sensors may contain useful information about degradation progression, particularly during the later stages of engine operation.

---

## Late-Life Trend Analysis

The late-life analysis was used to quantify changes in sensor behavior rather than relying only on visual observations.

The results showed that:

- **Sensor 4** exhibited the largest positive change in late-life slope.
- **Sensors 7 and 12** showed increasingly negative behavior during later engine-life intervals.
- **Sensors 11 and 15** also showed positive late-life changes, although their measured slope changes were smaller than Sensor 4.

This supports the observation that sensor behavior becomes more pronounced as engines approach the end of their simulated operating lives.

---

## Operating Condition Analysis

The relationship between the candidate sensors and the measured operating settings was also investigated.

The calculated correlations were close to zero:

| Operating Setting | Sensor 4 | Sensor 7 | Sensor 11 | Sensor 12 | Sensor 15 |
|---|---:|---:|---:|---:|---:|
| Setting 1 | 0.010 | -0.009 | 0.012 | -0.001 | 0.008 |
| Setting 2 | 0.015 | -0.017 | 0.012 | -0.011 | 0.014 |
| Setting 3 | N/A | N/A | N/A | N/A | N/A |

Setting 3 was constant throughout the FD001 dataset, so a correlation could not be calculated.

The very small correlations between the candidate sensors and Settings 1 and 2 indicate that there were no strong linear relationships between these measured operating settings and the selected sensor trends.

However, weak correlation does not prove that operating conditions have no influence on sensor behavior.

---

## Visualizations

The analysis includes visualizations showing:

- Engine operating life
- Individual engine sensor trends
- Sensor behavior across multiple engines
- Sensor variability
- Sensor correlations
- Normalized engine life
- Operating settings
- Sensor behavior by life stage
- Late-life sensor slopes
- Candidate sensor comparisons


---

## Engineering Interpretation

The analysis indicates that Sensors **4, 7, 11, 12, and 15** demonstrate consistent relationships with normalized engine life across the simulated engines.

The increasing behavior of Sensors 4, 11, and 15 and the decreasing behavior of Sensors 7 and 12 were observed consistently across the engines analyzed.

The trends also became more pronounced during the later stages of engine life, particularly after approximately 60% of normalized engine life.

These characteristics make the five sensors promising candidates for further investigation in predictive maintenance and engine degradation monitoring applications.

However, the results should be interpreted as evidence of **potential degradation-related behavior**, rather than direct proof that these sensors independently measure physical component degradation.

---

## Limitations

Several limitations should be considered when interpreting the results:

- The dataset consists of simulated turbofan engine data rather than measurements from physical engines.
- The analysis focuses on the FD001 dataset and therefore does not represent all C-MAPSS operating conditions and fault modes.
- Correlation does not establish causation.
- The analysis identifies potential degradation indicators but does not predict the exact failure point.
- No machine learning or Remaining Useful Life (RUL) prediction model was developed.
- The analysis primarily evaluates individual sensor behavior rather than combinations of multiple sensors.
- Additional datasets and real-world engine data would be needed to determine whether the observed relationships generalize to other operating conditions.

---

## Future Work

Potential extensions of this project include:

### Predictive Maintenance

- Develop a Remaining Useful Life (RUL) prediction model.
- Apply machine learning techniques to predict engine degradation.
- Develop automated degradation detection methods.

### Sensor Analysis

- Investigate combinations of multiple sensors.
- Perform feature engineering using sensor measurements.
- Investigate nonlinear relationships between sensors and engine life.
- Develop quantitative degradation thresholds.

### Dataset Expansion

- Compare sensor behavior across FD001–FD004.
- Analyze datasets with multiple operating conditions and fault modes.
- Validate candidate sensors using unseen test-engine data.

### Engineering Applications

- Develop an automated sensor health monitoring system.
- Build a dashboard for monitoring engine degradation.
- Investigate how identified sensor trends relate to specific engine components.
- Evaluate whether sensor trends can support predictive maintenance decisions.

---

## Project Structure


NASA-Turbofan-Sensor-Analysis/
│
├── data/
│   └── raw/
│       └── train_FD001.txt
│
├── notebooks/
│   └── 01_NASA_Data_Exploratioj.ipynb
│
├── figures/
│   ├── 01-engine_lifetime_histogram.png
│   └── ...
│
├── README.md
│
└── requirements.txt




## Conclusion

This project used statistical and engineering data analysis techniques to investigate sensor behavior throughout the operating life of 100 simulated turbofan engines.

From **20,631 observations across 100 engines**, five sensors — **4, 7, 11, 12, and 15** — were identified as strong candidates for further degradation analysis.

Sensors 4, 11, and 15 generally increased with normalized engine life, while Sensors 7 and 12 generally decreased. All five sensors demonstrated the expected direction of change across **100% of the engines analyzed**.

The trends also became more pronounced during the later stages of engine life, suggesting that these sensors may contain useful information for monitoring degradation progression.

This analysis provides a foundation for future work involving predictive maintenance, automated degradation detection, sensor fusion, and Remaining Useful Life prediction.

---

## References

- NASA Prognostics Center of Excellence
- NASA C-MAPSS Turbofan Engine Degradation Simulation Dataset





[def]: #references
