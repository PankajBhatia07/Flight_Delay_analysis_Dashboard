# ✈️ Flight Delay Analysis & Operational Insights

## 📌 Project Overview

This project analyzes flight delay data to identify patterns and
operational insights related to airlines, airports, months, days of the
week, and arrival delays.

The project uses **Python, Pandas, NumPy, Matplotlib, and Seaborn** to
clean, analyze, visualize, and communicate flight-delay information
through a business-friendly dashboard.

> 🎯 **Goal:** Understand where and when flight delays are more severe
> and present the findings clearly through data visualization.

------------------------------------------------------------------------

## 📊 Key Business Questions

-   ✈️ Which airline has the highest average delay?
-   📅 Which month has higher average delays?
-   🛫 Which airport has higher average delays?
-   🗓️ Which day of the week has higher delays?
-   📈 How are arrival delays distributed?
-   🔎 What patterns can be identified from the flight-delay data?

------------------------------------------------------------------------

## 🛠️ Tools & Technologies

  Tool                  Purpose
  --------------------- -------------------------------------
  🐍 Python             Data analysis and programming
  🐼 Pandas             Data cleaning and manipulation
  🔢 NumPy              Numerical operations
  📊 Matplotlib         Data visualization
  🎨 Seaborn            Statistical visualization
  📓 Jupyter Notebook   Analysis environment
  💻 VS Code            Development environment
  🔗 Git & GitHub       Version control and project sharing

------------------------------------------------------------------------

## 📂 Project Structure

``` text
Flight_Delay_Analysis/
│
├── 📄 Flight_Analysis.csv
├── 📓 Flight_Project.ipynb
└── 📖 README.md
```

------------------------------------------------------------------------

## 🔄 Project Workflow

``` text
📥 Data Collection
       ↓
🔍 Data Understanding
       ↓
🧹 Data Cleaning
       ↓
❌ Missing Value Analysis
       ↓
🔁 Duplicate Analysis
       ↓
📊 Exploratory Data Analysis
       ↓
✈️ Airline Analysis
       ↓
🛫 Airport Analysis
       ↓
📅 Month & Day Analysis
       ↓
📈 Delay Distribution
       ↓
📊 Dashboard
       ↓
💡 Business Insights
```

------------------------------------------------------------------------

## 🧹 Data Preparation

The dataset was inspected and prepared using Python.

### Main activities

-   Checking dataset shape and columns
-   Checking data types
-   Checking missing values
-   Checking duplicate records
-   Checking unique values
-   Creating a delayed-flight indicator
-   Grouping data by airline, airport, month, and day
-   Calculating average arrival delay
-   Preparing data for visualization

### Delayed Flight Definition

``` python
df["IS_DELAYED"] = (df["ARRIVAL_DELAY"] >= 15).astype(int)
```

A flight with an arrival delay of **15 minutes or more** is treated as
delayed.

------------------------------------------------------------------------

## 📊 Analysis Performed

### ✈️ 1. Airline Analysis

The project calculates the average arrival delay for each airline.

``` python
airline_analysis = (
    df.groupby("AIRLINE")["ARRIVAL_DELAY"]
      .mean()
      .sort_values(ascending=False)
)
```

📌 **Finding:** F9 has the highest average arrival delay in the current
dataset, at approximately **69.46 minutes**.

------------------------------------------------------------------------

### 📅 2. Month Analysis

Average arrival delay is calculated for each available month.

``` python
month_analysis = (
    df.groupby("MONTH")["ARRIVAL_DELAY"]
      .mean()
      .sort_index()
)
```

This helps identify whether delay severity changes across months.

------------------------------------------------------------------------

### 🛫 3. Airport Analysis

Origin airports are compared using average arrival delay.

``` python
airport_analysis = df.groupby("ORIGIN_AIRPORT").agg(
    Total_Flights=("ORIGIN_AIRPORT", "size"),
    Average_Delay=("ARRIVAL_DELAY", "mean")
)
```

A minimum flight-count threshold of **100 flights** is used to reduce
misleading results from airports with very few observations.

📌 **Finding:** Among airports meeting the minimum-volume condition, COS
has the highest average delay in the current dataset.

------------------------------------------------------------------------

### 🗓️ 4. Day-of-Week Analysis

Average arrival delay is compared across the days of the week.

``` python
day_analysis = (
    df.groupby("DAY_OF_WEEK")["ARRIVAL_DELAY"]
      .mean()
      .sort_index()
)
```

📌 **Finding:** Sunday has the highest average arrival delay in the
current dataset, at approximately **61.91 minutes**.

------------------------------------------------------------------------

### 📈 5. Delay Distribution

A histogram and descriptive statistics are used to understand how delays
are distributed.

``` python
df["ARRIVAL_DELAY"].describe()
```

The distribution is **right-skewed**, with some flights experiencing
very large delays.

------------------------------------------------------------------------

## 📊 Dashboard

The final dashboard combines the major findings into one view.

### Dashboard Includes

-   🔢 Total flights
-   ⏱️ Average arrival delay
-   ✈️ Airline with highest average delay
-   🗓️ Day with highest average delay
-   📊 Average delay by airline
-   📅 Average delay by month
-   🛫 Top airports by average delay
-   🗓️ Average delay by day
-   📈 Distribution of arrival delays

The charts include **data labels on the bars** so values can be read
directly from the dashboard.

------------------------------------------------------------------------

## 💡 Key Insights

Based on the current `Flight_Analysis.csv` dataset:

-   ✈️ **F9** has the highest average arrival delay among airlines:
    approximately **69.46 minutes**.
-   🗓️ **Sunday** has the highest average arrival delay: approximately
    **61.91 minutes**.
-   🛫 **COS** has the highest average delay among airports meeting the
    minimum 100-flight threshold.
-   📈 Arrival delays are **right-skewed**, with a smaller number of
    flights experiencing very large delays.
-   ⏱️ The overall average arrival delay in the dataset is approximately
    **56.78 minutes**.

------------------------------------------------------------------------

## ⚠️ Important Data Note

The current `Flight_Analysis.csv` appears to contain flights that are
already delayed.

Therefore, this project primarily compares **delay severity using
average arrival delay**, rather than comparing the percentage of all
flights that were delayed.

For example:

> ✅ "F9 has the highest average arrival delay."

Instead of:

> ❌ "F9 has the highest overall delay rate."

A full delay-rate analysis would require a dataset containing both
**delayed and non-delayed flights**.

------------------------------------------------------------------------

## 🚀 Future Improvements

-   🤖 Flight delay prediction using Machine Learning
-   📊 Model evaluation
-   🗄️ SQL-based analysis
-   📈 Power BI dashboard
-   🌦️ Weather impact analysis
-   🛣️ Route-level delay analysis
-   ⏰ Departure-time analysis
-   🏢 Airline performance comparison
-   🌐 Deployment as a web application

------------------------------------------------------------------------

## ▶️ How to Run the Project

### 1. Clone the repository

``` bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### 2. Open the project

Open the project folder in **VS Code** or **Jupyter Notebook**.

### 3. Install required libraries

``` bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Run the notebook

Open:

``` text
Flight_Project.ipynb
```

Run the cells from top to bottom.

------------------------------------------------------------------------

## 📌 Skills Demonstrated

-   🐍 Python
-   🐼 Pandas
-   🔢 NumPy
-   📊 Exploratory Data Analysis (EDA)
-   🧹 Data Cleaning
-   📈 Data Visualization
-   📋 Business Problem Solving
-   📊 Dashboard Development
-   💡 Business Insight Generation
-   💻 Git & GitHub

------------------------------------------------------------------------

## 👨‍💻 Author

### **Pankaj Bhatia**

📧 **Email:** <pankajbhatia938@gmail.com>

🔗 **LinkedIn:** [Pankaj
Bhatia](https://www.linkedin.com/in/pankaj-411463302/)

💻 **GitHub:** [Pankaj Bhatia](https://github.com/PankajBhatia07)

------------------------------------------------------------------------

## ⭐ If you find this project useful

Feel free to ⭐ **star the repository** and connect with me on LinkedIn!

------------------------------------------------------------------------

## 📜 License

This project is created for **learning, portfolio, and educational
purposes**.
