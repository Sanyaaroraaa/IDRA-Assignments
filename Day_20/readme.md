<div align="center">

# 🌫️ Urban Air Quality Analysis

### IDRA · Final Capstone Project · Project 8

**Exploring air quality patterns and testing AQI prediction across five Indian cities.**

<br>

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge\&logo=pandas\&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Machine%20Learning-F7931E?style=for-the-badge\&logo=scikitlearn\&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge\&logo=jupyter\&logoColor=white)

<br>

**📍 Bangalore · Chennai · Delhi · Kolkata · Mumbai**

</div>

---

## ✨ About the Project

Air quality affects millions of people, but how well can pollutant measurements explain the Air Quality Index?

In this capstone, I explored daily air-quality data from five Indian cities, investigated pollutant patterns, checked the dataset's consistency, and tested regression models to see whether the recorded pollutant values could be used to estimate AQI.

The project also looks at an important part of data science: **what to do when the data does not support the result we expected.**

---

## 📊 Dataset at a Glance

<table>
<tr>
<td align="center" width="25%">

### 18,265

Rows

</td>
<td align="center" width="25%">

### 16

Columns

</td>
<td align="center" width="25%">

### 5

Cities

</td>
<td align="center" width="25%">

### 2015–2024

Time period

</td>
</tr>
</table>

**Dataset file:** `P_8_city_day.csv`

It includes daily measurements for pollutants such as PM2.5, PM10, NO, NO₂, NOx, NH₃, CO, SO₂, O₃, Benzene, Toluene, and Xylene, along with AQI and AQI category information.

---

## 🧭 Project Workflow

|  Step | What I explored                                                                                       |
| :---: | ----------------------------------------------------------------------------------------------------- |
| 🔎 01 | **Data Inspection** — Dataset structure, data types, date coverage, missing values, and duplicates    |
| 🧹 02 | **Preprocessing** — Date and numeric conversions and data validation                                  |
| 📈 03 | **Exploratory Analysis** — Pollutant distributions and AQI patterns across cities and time            |
| 🔗 04 | **Correlation Analysis** — Pearson and Spearman correlations between pollutants and AQI               |
| 🧪 05 | **Statistical Checks** — Distribution tests and comparison of supplied AQI categories with CPCB bands |
| 🤖 06 | **Regression Modelling** — Testing five regression variants against a mean baseline                   |
| 📏 07 | **Evaluation** — Chronological train-test split, error metrics, and overfitting checks                |
| 💡 08 | **Conclusion** — Findings, limitations, and possible future work                                      |

---

## 🛠️ Tech Stack

<div align="center">

| Tool                        | Purpose                                |
| --------------------------- | -------------------------------------- |
| 🐍 **Python**               | Core programming language              |
| 🐼 **Pandas & NumPy**       | Data handling and numerical operations |
| 📊 **Matplotlib & Seaborn** | Data visualisation                     |
| 📐 **SciPy**                | Statistical testing                    |
| 🤖 **Scikit-learn**         | Regression models and evaluation       |
| 📓 **Jupyter Notebook**     | Analysis and experimentation           |

</div>

---

## 🤖 Machine Learning

The project tested whether pollutant measurements could estimate AQI.

### Models and evaluation

* Mean baseline
* Linear Regression
* Random Forest
* Additional feature-based regression variants

The data was split chronologically to evaluate performance on a later time period.

| Dataset split | Years     |
| ------------- | --------- |
| Training      | 2015–2022 |
| Testing       | 2023–2024 |

**Evaluation metrics:** MAE and R².

---

## 📌 Key Findings

<details open>
<summary><b>🔍 Data quality</b></summary>
<br>

* All 16 columns had zero missing values.
* No duplicate rows were found.

</details>

<details open>
<summary><b>🔗 Pollutant relationships</b></summary>
<br>

* Pollutant-AQI correlations were very weak in this dataset.
* The supplied AQI categories matched the CPCB bands for only **16.2%** of records.

</details>

<details open>
<summary><b>🤖 Regression results</b></summary>
<br>

* None of the tested regression models improved on the mean-baseline MAE of **125.14 AQI units**.
* Random Forest achieved a training R² of approximately **0.82**, but its test R² was approximately **−0.02**, indicating poor generalisation.

</details>

<div align="center">

### 💡 Main Takeaway

**The available data did not provide a reliable basis for predicting AQI with the tested regression models.**

</div>

---

## ⚠️ Limitations

* Findings are limited to the dataset used in this project.
* Weak relationships in this file do not mean pollutants are unrelated to AQI in general.
* The regression results show that the tested models did not generalise well to the held-out period.
* Further validation using additional reliable air-quality data would be needed.

---

## 🚀 Future Work

* Validate the findings using additional air-quality datasets.
* Investigate the data quality and AQI calculation methods.
* Explore additional features and alternative modelling approaches.
* Test models on other cities and time periods.

---

## 📓 Explore the Project

<div align="center">

### 💻 Notebook & Code

The notebook contains the complete workflow, from data inspection and visualisation to statistical analysis, modelling, and conclusions.

<br>

<a href="https://github.com/Sanyaaroraaa/IDRA-Assignments">
  <img src="https://img.shields.io/badge/VIEW%20PROJECT%20ON%20GITHUB-181717?style=for-the-badge&logo=github&logoColor=white" alt="View Project on GitHub">
</a>

<br><br>

**[Open the IDRA Assignments Repository](https://github.com/Sanyaaroraaa/IDRA-Assignments)**

</div>

---

<div align="center">

### 🎓 IDRA · Final Capstone Project

*An end-to-end data analysis project focused on exploring the data, testing assumptions, and reporting the findings honestly.*

**Made by Sanya Arora 💙**

</div>
