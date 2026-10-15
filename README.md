# Customer Shopping Behavior Analysis

## 1. Project Overview

This project focuses on analyzing customer shopping behavior to understand purchasing patterns, customer preferences, spending habits, and subscription trends.

The project follows an end-to-end data analytics workflow using Python for data exploration and cleaning, PostgreSQL for SQL-based analysis, and Power BI for interactive data visualization.

The objective is to transform raw customer shopping data into meaningful insights that can support data-driven business decisions.

### Project Objectives
- Explore and understand customer shopping data.
- Identify and handle missing values and data quality issues.
- Perform data cleaning and feature engineering using Python.
- Analyze customer behavior using SQL queries in PostgreSQL.
- Build an interactive Power BI dashboard.
- Identify trends in revenue, purchasing behavior, product categories, and customer subscriptions.

## 2. Dataset

**Dataset:** Customer Shopping Behavior Dataset

**File:** `customer_behavior_dataset.xlsx`

**Format:** Excel

**Dataset Size:** 3,900 rows and 18 columns

The dataset contains customer demographic information, product details, purchase amounts, shipping preferences, discount usage, review ratings, subscription status, and purchasing frequency.

### Key Features

| Column | Description |
|---|---|
| Customer ID | Unique customer identifier |
| Age | Age of the customer |
| Gender | Customer gender |
| Item Purchased | Product purchased |
| Category | Product category |
| Purchase Amount (USD) | Amount spent on the purchase |
| Location | Customer location |
| Size | Product size |
| Color | Product color |
| Season | Season associated with the purchase |
| Review Rating | Customer's product review rating |
| Subscription Status | Whether the customer has a subscription |
| Shipping Type | Shipping method selected |
| Discount Applied | Indicates whether a discount was applied |
| Promo Code Used | Indicates whether a promotional code was used |
| Previous Purchases | Number of previous purchases |
| Payment Method | Payment method used |
| Frequency of Purchases | How frequently purchases are made |

## 3. Tools and Technologies

| Tool | Purpose |
|---|---|
| Python | Data analysis and preparation |
| Pandas | Data loading, exploration, cleaning, and transformation |
| Jupyter Notebook | Executing Python code |
| PostgreSQL | Storing and querying the cleaned dataset |
| SQL | Business analysis and data aggregation |
| SQLAlchemy | Connecting Python to PostgreSQL and loading data |
| psycopg2 | PostgreSQL database connectivity |
| Power BI Desktop | Dashboard development and visualization |

## 4. Project Workflow

### Step 1: Data Loading

- Imported Pandas in Jupyter Notebook.
- Loaded the customer shopping dataset into a Pandas DataFrame.
- Used `df.head()` to preview the first five records.
- Used `df.info()` to inspect column names, data types, and non-null values.
- Used `df.describe(include='all')` to review descriptive statistics for numerical and categorical columns.

### Step 2: Exploratory Data Analysis (EDA)

Explored the dataset to understand its structure and assess data quality.

The following Pandas methods were used:

- `df.head()` — Preview the dataset.
- `df.info()` — Inspect data types and non-null counts.
- `df.describe(include='all')` — Generate descriptive statistics.
- `df.isnull().sum()` — Identify missing values in each column.

This initial exploration helped identify missing review ratings and understand the variables available for further analysis.

### Step 3: Data Cleaning and Feature Engineering

Several data preparation steps were performed using Pandas.

**Handling missing values**

Missing values in the `Review Rating` column were filled using the median review rating within each product category. The missing-value check was performed again to verify the result.

**Standardizing column names**

- Converted column names to lowercase.
- Replaced spaces with underscores.
- Renamed `purchase_amount_(usd)` to `purchase_amount`.

This made the column names easier to reference in Python and SQL.

**Creating age groups**

Created a new `age_group` column using `pd.qcut()` to divide customer ages into four quantile-based groups:

- Young Adult
- Adult
- Middle-aged
- Senior

**Transforming purchase frequency**

Created a `purchase_frequency_days` column by mapping purchasing-frequency categories to approximate day intervals. For example, Weekly was mapped to 7 days, Monthly to 30 days, and Annually to 365 days.

**Removing a redundant column**

Compared `discount_applied` and `promo_code_used` and verified that their values matched throughout the dataset. The redundant `promo_code_used` column was then removed.

### Step 4: Loading Data into PostgreSQL

The cleaned Pandas DataFrame was loaded into PostgreSQL using SQLAlchemy and `psycopg2`.

The database used was `customer_behavior`, and the destination table was named `customer`.

This made the prepared dataset available for SQL-based business analysis.

### Step 5: SQL Analysis

SQL queries were written to investigate customer shopping behavior and answer business-related questions.

The analysis covered:

1. **Revenue by gender** — Compared total purchase revenue generated by male and female customers.
2. **Discount usage and spending** — Identified customers who used discounts but spent at least the average purchase amount.
3. **Product review ratings** — Identified the five products with the highest average review ratings.
4. **Shipping comparison** — Compared average purchase amounts for Standard and Express shipping.
5. **Subscription analysis** — Compared customer counts, average spending, and total revenue for subscribers and non-subscribers.
6. **Product discount rates** — Identified products with the highest percentage of purchases involving discounts.
7. **Customer segmentation** — Grouped customers into New, Returning, and Loyal segments based on previous purchases.
8. **Product rankings by category** — Ranked products within each category to identify the top three.
9. **Repeat buyer subscription behavior** — Examined subscription status among customers with more than five previous purchases.
10. **Revenue by age group** — Analyzed purchase revenue across age groups.

The queries used SQL concepts such as filtering, aggregate functions, `GROUP BY`, `CASE` statements, subqueries, Common Table Expressions (CTEs), and window functions.

### Step 6: Power BI Dashboard

The cleaned customer data was used to create an interactive dashboard in Power BI Desktop.

The dashboard presents customer and purchasing information through KPI cards, charts, and category-based comparisons.

The visualizations cover:

- **Key metrics:** Number of customers, average purchase amount, and average review rating.
- **Product categories:** Purchase amounts and customer distribution by category.
- **Customer demographics:** Gender and age-related analysis.
- **Subscription behavior:** Subscriber and non-subscriber comparisons.
- **Shipping preferences:** Distribution by shipping type.
- **Payment methods:** Purchase amounts across payment methods.

The dashboard helps users explore customer shopping patterns and compare different aspects of purchasing behavior.

## 5. Dashboard Preview

The Power BI dashboard is available in the repository as:

`customer_behavior_dashboard.pbix`

Open the file using Power BI Desktop to explore the dashboard and its visualizations.

To display a preview directly in this README, add a screenshot of the dashboard to an `images` folder and insert the following Markdown:

`![Customer Shopping Behavior Dashboard](images/dashboard.png)`

## 6. Results and Key Findings

The project transformed raw customer shopping data into a cleaned dataset suitable for SQL analysis and Power BI reporting.

Key observations from the provided dataset include:

- **Data volume:** Analyzed 3,900 customer purchase records across 18 original columns.
- **Data quality:** Identified 37 missing values in the review-rating column and filled them using category-level median ratings.
- **Data preparation:** Standardized column names, created age-group and purchase-frequency features, and removed a redundant column.
- **Customer spending:** Analyzed revenue and average purchase amounts across gender and subscription status.
- **Product performance:** Investigated review ratings, purchase frequency, and discount usage across products and categories.
- **Customer behavior:** Examined repeat purchases, customer segments, shipping preferences, and payment methods.

The analysis demonstrates how Python, SQL, and Power BI can be combined to prepare, analyze, and communicate insights from customer shopping data.

## 7. How to Run the Project

### Prerequisites

Install or set up the following:

- Python 3.x
- Jupyter Notebook
- PostgreSQL Server
- pgAdmin or another PostgreSQL client
- Power BI Desktop

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/customer-shopping-behavior-analysis.git
cd customer-shopping-behavior-analysis
```

Replace the repository URL with your actual GitHub repository.

### Step 2: Install Python Dependencies

Run the following command in a Jupyter Notebook cell or terminal:

```bash
pip install pandas sqlalchemy psycopg2-binary openpyxl jupyter
```

### Step 3: Load the Dataset

Place the dataset in the project directory.

The uploaded notebook currently expects a CSV file named `customer_shopping_behavior.csv`. Either export the provided Excel dataset to that filename or update the loading statement to:

```python
import pandas as pd

df = pd.read_excel("customer_behavior_dataset.xlsx")
```

Run the notebook cells in order to explore, clean, and transform the dataset.

### Step 4: Configure PostgreSQL

- Start PostgreSQL Server.
- Create a database named `customer_behavior`.
- Configure the database connection in the notebook using your own credentials.
- Run the data-loading code to create and populate the `customer` table.

Keep database passwords outside the notebook and repository. Use environment variables or another secure configuration method.

### Step 5: Execute SQL Queries

Open `customer_behavior_sql_queries.sql` in pgAdmin or your preferred PostgreSQL SQL editor.

Connect to the `customer_behavior` database and execute the queries against the `customer` table.

### Step 6: Open the Power BI Dashboard

- Open `customer_behavior_dashboard.pbix` in Power BI Desktop.
- Update the data source connection if necessary.
- Refresh the data if your local database connection is configured.
- Explore the available charts, KPIs, and visualizations.

## 8. Project Structure

```text
customer-shopping-behavior-analysis/
│
├── customer_behavior_dataset.xlsx
├── Customer_Shopping_Behavior_Analysis.ipynb
├── customer_behavior_sql_queries.sql
├── customer_behavior_dashboard.pbix
├── README.md
│
└── images/
    └── dashboard.png
```

The `images/dashboard.png` file is optional and should be added if you want a dashboard screenshot to appear in the README.

## 9. Skills Demonstrated

- Data loading and exploration using Pandas
- Data cleaning and preprocessing
- Feature engineering
- Exploratory Data Analysis (EDA)
- SQL querying and aggregation
- PostgreSQL database integration
- Python-to-database connectivity
- Power BI dashboard development
- Analytical thinking and business problem-solving
- Data storytelling and visualization

## 10. Conclusion

This project demonstrates an end-to-end data analytics workflow using Python, PostgreSQL, SQL, and Power BI.

By combining data exploration, cleaning, feature engineering, database querying, and dashboard development, the project shows how customer shopping data can be transformed into structured analysis that supports better understanding of purchasing patterns and customer behavior.

---

**Author:** [Safwan Abdul Majid]

**GitHub:** [https://github.com/Safwan-Abdul-Majid/customer_behavior_analysis/edit/main/README.md]

**Project:** Customer Shopping Behavior Analysis
