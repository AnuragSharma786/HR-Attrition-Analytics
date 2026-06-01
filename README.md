# End-to-End HR Attrition Analytics: ETL Pipeline & Executive Dashboard

## 📌 Project Overview
This project is a complete end-to-end data analytics solution designed to identify the root causes of employee attrition at Elevate Labs. I built a custom ETL pipeline to process raw HR data, loaded it into a MySQL database, executed complex SQL queries to extract business insights, and visualized the findings in an interactive Power BI executive dashboard.

---

## ⚙️ Architecture & Tech Stack
* **Database:** MySQL
* **ETL & Analysis:** Python (Pandas, SQLAlchemy, PyMySQL)
* **Visualization:** Power BI (DAX, Data Modeling)

---

## 🚀 Step 1: The ETL Pipeline (MySQL Integration)
To ensure the data was structured for scalable analysis, I built an automated ETL (Extract, Transform, Load) pipeline using Python.

* **Extract:** Ingested the raw HR dataset containing 35+ columns of employee metrics (demographics, performance ratings, salary hikes, and tenure).
* **Transform:** Cleaned the data using Pandas. Mapped categorical text values (e.g., "Yes"/"No") to binary integers (1/0) for mathematical aggregation, handled null values, and engineered new features like `Burnout Category`.
* **Load:** Used Python's `SQLAlchemy` engine to establish a direct connection to a local **MySQL** database and loaded the cleaned dataframe into an active SQL table (`employees_data`) for querying.

---

## 🔍 Step 2: SQL Data Modeling & Discovery
Instead of relying on basic visualization filters, I used advanced SQL queries directly against the MySQL database to isolate high-risk employee cohorts. 

Key SQL techniques utilized:
* **Complex Aggregations:** Used `GROUP BY` and `AVG()` to calculate department-level salary trends.
* **Conditional Logic:** Built custom `CASE WHEN` statements to segment employees into distinct risk buckets (e.g., `OverTime = 'Yes' AND PercentSalaryHike <= 14`).
* **Dynamic Calculations:** Calculated exact attrition percentages across various departments and performance brackets using embedded division and `COUNT()` logic.

---

## 📊 Step 3: Key Business Insights Discovered
The SQL and Python analysis revealed that Elevate Labs is not losing underperformers; it is actively burning out its most elite talent.

1. **The "High Effort, Low Reward" Trap:** I isolated a high-risk group in the Sales department working consistent overtime but receiving sub-14% raises. This specific group is experiencing a catastrophic **40%+ attrition spike**.
2. **Top Performer Flight Risk:** "Outstanding" employees (Performance Rating 4) who reported a poor Work-Life Balance are quitting at a rate of **~36%**, nearly triple the rate of those with a healthy balance.
3. **The Loyalty Penalty:** A time-series analysis revealed an inverse relationship between an employee’s tenure and their average percentage salary hike, mathematically proving that long-term loyalty is currently disincentivized.

---

## 📈 Step 4: Power BI Executive Dashboard
To present these findings to the Elevate Labs leadership team, I connected Power BI directly to the cleaned dataset and built a highly focused, interactive scorecard.

**Dashboard Features:**
* **DAX Engineering:** Created dynamic, fail-safe measures using `CALCULATE` and `DIVIDE` to establish a live baseline `Company Attrition Rate (16.1%)` that automatically recalculates based on slicer selection.
* **Burnout Heatmap:** Built a custom Matrix visual with conditional formatting to instantly draw executive attention to the highest-risk intersections of Performance and Work-Life Balance.
* **Loyalty Penalty Combo Chart:** Designed a dual-axis line/bar chart forcing a visual comparison between employee headcount (grey background bars) and the declining salary hike average (bold red trendline).
* **Strategic Color Psychology:** Stripped away default color palettes, utilizing a strict neutral grey/blue aesthetic while reserving bold red exclusively for critical flight-risk metrics.

---

## 📸 Dashboard Preview
<img width="1415" height="796" alt="image" src="https://github.com/user-attachments/assets/1424a86f-2ba4-40af-891f-5d2e595cc324" />

## 📂 Repository Navigation
* `/scripts`: Contains the Python ETL scripts and the `.sql` query files.
* `/data`: Contains the data dictionary and database schema context.
* `/dashboard`: Contains the `.pbix` Power BI file and static PDF exports for quick viewing.
