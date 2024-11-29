
# Road Safety Analysis

This project aims to **identify the severity of road accidents** based on given crash data. By analyzing the data, we strive to **minimize accident rates** and **maximize public safety** by providing insights and actionable recommendations.

---

## Dataset Description

The dataset, **`crash_data_queensland_1_crash_locations.csv`**, provides detailed information on road accidents in Queensland. Below is the structure of the dataset:

| **Column Name**                 | **Description**                                                                 |
|---------------------------------|---------------------------------------------------------------------------------|
| `Crash_Ref_Number`              | Unique identifier for each crash.                                               |
| `Crash_Severity`                | The severity of the crash (target variable). Categories include: `Minor injury`, `Fatal`, `Property damage only`, `Hospitalisation`, `Medical treatment`. |
| `Crash_Year`                    | Year of the crash.                                                              |
| `Crash_Month`                   | Month of the crash.                                                             |
| `Crash_Day_Of_Week`             | Day of the week when the crash occurred.                                         |
| `Crash_Hour`                    | Hour of the day when the crash occurred.                                        |
| `Crash_Nature`                  | Nature of the crash (e.g., `Angle`, `Rear-end`).                                |
| `Crash_Type`                    | Type of crash (e.g., single-vehicle, multi-vehicle).                            |
| `Crash_Latitude` and `Longitude`| Geographical location of the crash.                                             |
| `Crash_Street`                  | Name of the street where the crash occurred.                                    |
| `Crash_Speed_Limit`             | Speed limit in the area of the crash.                                           |
| `Crash_Road_Surface_Condition`  | Surface condition of the road at the time of the crash.                         |
| `Crash_Atmospheric_Condition`   | Weather conditions during the crash.                                            |
| `Count_Casualty_*`              | Number of casualties in different severity categories (e.g., fatalities, hospitalizations). |
| `Count_Unit_*`                  | Number of vehicles and pedestrians involved.                                    |

---

## Project Overview

- **Target Variable**: `Crash_Severity` (categorical).
- **Objective**: Analyze crash data to predict accident severity, identify patterns, and derive actionable insights for improving public safety.

---

## Exploratory Data Analysis (EDA)

EDA was conducted using **`pandas`**, **`matplotlib`**, and **`sweetviz`**. Key findings include:

### Summary Statistics

1. **Total Accidents**: 374,214  
2. **Total Injuries**: 287,678  
3. **Property Damage Only**: 86,536 cases  
**Sweetviz Analysis**: Comprehensive visual report of the dataset is stored in [**sales EDA.html**](./Sales%20EDA.html).  

---

### Insights from EDA

#### Crash Severity Distribution

- Most crashes resulted in **medical treatment** or **hospitalization**.  
- Fatalities accounted for only **0.901%** of crashes.  
- **Visualization**: A histogram and pie chart show the frequency of severity levels.

#### Year-wise Accident Trends

- Accident rates declined in recent years.  
- The highest accident rates occurred between **2000 and 2010**, averaging 22,508 accidents annually.  
- **Visualization**: Line graph illustrating trends.

#### Time Distribution

- Accidents occurred evenly across months.  
- The majority of accidents occurred between **3 PM and 5 PM**, averaging **30,330 accidents**.  
- **Visualization**: Time-series and pie charts.

#### Street-wise Accident Distribution

- **Top Streets**: Bruce Highway (highest), Pacific Highway (second highest).  
- Focus on improving safety measures on these high-risk roads.

#### Nature of Crashes

- **Top Three Crash Natures**:  
  - **Angle Accidents**: 111,049 cases.  
  - **Rear-End Collisions**: 92,892 cases.  
  - **Hit Object**: 81,644 cases.  
- **Visualization**: Bar chart comparing crash nature frequencies.

#### Lighting and Weather Conditions

- Most accidents occurred during the day under clear weather conditions.  
- **Visualization**: Distribution charts of lighting and atmospheric conditions.

#### Speed Limit Impact

- Majority of crashes occurred at a speed limit of **60 km/h**.  
- **Visualization**: Bar chart of accidents by speed limit.

#### Lockdown Impact Analysis

- Analyzed crashes during the lockdown period (2020-01-01 to 2021-04-01).  
- **Findings**: Significant reduction in both accident frequency and severity during the lockdown compared to pre- and post-lockdown periods.  
- **Visualization**: Bar charts comparing periods.

#### Spatial Characteristics

- A **heatmap** was created to analyze the spatial distribution of accidents based on latitude and longitude.

#### Pedestrian Crashes

- Analyzed crashes involving pedestrians by roadway features, time, and age groups.  
- Suggested measures include enhancing street lighting, increasing pedestrian safety education, and implementing traffic calming measures.  
- **Visualization**: Multiple bar charts and distribution graphs.

---

## Data Preprocessing

### Handling Missing Values

- Missing values were replaced using the **KNN Imputer**.

### Feature Selection

- Dropped columns with:
  - **Low Correlation** (< 0.15) with the target variable.  
  - **High Variance Inflation Factor (VIF)** (> 5).  

### Dimensionality Reduction

- Highly correlated columns (`Count_Casualty_Total` and `Count_Casualty_MedicallyTreated`) were combined using **PCA**.

### Label Encoding

- Categorical columns were encoded using **LabelEncoder**.

### Feature Scaling

- Numerical columns were scaled between 0 and 1 using a **Standard Scaler**.

---

## Model Building

### Data Splitting

- **Training Set**: 60%  
- **Validation Set**: 20%  
- **Test Set**: 20%  

### Models

#### Logistic Regression

- **Validation Accuracy**: 99.98%  

#### K-Nearest Neighbors (KNN)

- Used the **elbow method** to determine the optimal value of `k`.  
- **Test Accuracy**: 80% at `k=20`.  
- Observations: KNN is sensitive to noise, and crash data is inherently noisy, limiting its performance.

#### Decision Tree

- **Parameters**: `max_depth=10`  
- **Validation Accuracy**: 99.19%  
- **Feature Importance**: Visualized feature contributions to the model.  
- Conducted **hyperparameter tuning** to find the optimal **ccp_alpha** value:  
  - Selected **alpha = 0.0026** for the best trade-off between bias and variance.

#### Random Forest

- **Validation Accuracy**: 97.61%  

---

### Model Selection

The **Decision Tree** was selected as the final model due to its high accuracy and ability to generalize well to unseen data.

---

## Conclusions

1. **Key Observations**:
   - Medical treatment and hospitalization are the most common crash outcomes.  
   - Accidents are more frequent at **intersections** and during **afternoon hours**.  
   - High-risk streets and suburbs were identified for targeted interventions.  

2. **Recommendations**:
   - Enhance street lighting and install traffic calming measures in high-risk areas.  
   - Focus safety campaigns on peak accident times and locations.  
   - Improve pedestrian safety through better infrastructure and education.  

This comprehensive analysis provides valuable insights into road safety, helping authorities prioritize areas for intervention and policy-making.

---

## Tools and Libraries

- **Libraries**: `pandas`, `numpy`, `matplotlib`, `sweetviz`.  
- **Visualization**: Heatmaps, histograms, pie charts, and bar graphs.  
- **Modeling**: Logistic Regression, KNN, Decision Tree, Random Forest.  

---

## Files

- **Dataset**: `crash_data_queensland_1_crash_locations.csv`  
- **EDA Report**: `EDA.html`  

--- 

For further inquiries or collaborations, feel free to connect! 😊 
