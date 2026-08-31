# Data Science Salary Analysis (2024)

A comprehensive Exploratory Data Analysis (EDA) on global data science job market trends, compensation, and key influencing factors from 2020 to 2024.

---

## 🚀 Project Overview

This project analyzes a dataset of **14,838 rows and 11 columns** covering data science salaries and employment details worldwide. The goal is to uncover market trends, examine salary distributions, identify high-paying niches, and provide strategic insights for job seekers and professionals.

**Description:** This dataset provides insights into data science job salaries from 2020 to 2024, including experience levels, employment types, job titles, and company characteristics. It serves as a valuable resource for understanding salary trends and the factors that influence compensation in the data science field.

### Features

| Column | Description |
|---|---|
| `work_year` | The year the salary data was recorded |
| `experience_level` | Employee experience level (e.g., entry-level, mid-level, senior-level) |
| `employment_type` | Type of employment (e.g., full-time, part-time, contract) |
| `job_title` | Job title / role within the data science field |
| `salary` | Salary as originally reported |
| `salary_currency` | Currency of the reported salary |
| `salary_in_usd` | Salary converted to USD for standardization |
| `employee_residence` | Employee's country of residence |
| `remote_ratio` | Proportion of remote work allowed for the position |
| `company_location` | Country where the company is located |
| `company_size` | Company size, by employee count / revenue |

---

## 📊 Data Source

Dataset sourced from Kaggle: [Data Science Salaries 2024](https://www.kaggle.com/datasets/your-dataset-link-here)

---

## 🔍 Insights

### 1. Data Processing & Cleaning Strategy

- **Dataset shape:** 14,838 rows × 11 columns.
- **Temporal distribution:** Heavily concentrated in 2022–2024, with very few records from 2020–2021.
- **`salary` column:** Dropped, since `salary_in_usd` combined with the currency columns already provides standardized, comparable values.
- **`remote_ratio` column:** Treated as categorical, since it only takes a few discrete values (e.g., 0, 50, 100).
- **Duplicates:** High duplication rate (~38%) — the data source should be re-verified.
- **Missing values:** None found.
- **Ordinal columns:** `experience_level` and `company_size` have a natural order, making them suitable for ordinal encoding during modeling.
- **Outliers:** Concentrated in `salary_in_usd` (right-skewed due to a minority of ultra-high earners) — a normal characteristic of salary data.
- **High-cardinality categoricals:** `job_title`, `company_location`, `employee_residence`, and `salary_currency` have many unique classes, but only a handful dominate while the rest each account for less than 1%.
  - **Action:** Group rare categories into a broader "Other" bucket to reduce noise.

---

### 2. Salary Analysis & Influencing Factors

- **Non-influential factors:** `work_year` and `remote_ratio` show no clear impact on salary level.
- **Experience level:** Clearly impacts salary — more experience generally means higher pay. However, the largest salary variance and most prominent outliers appear in the `MI` (mid-level) and `SE` (senior) groups rather than `EX` (executive), which is somewhat counterintuitive.
- **Company size:** Small (`S`) companies tend to pay less than Medium (`M`) and Large (`L`) companies at the same experience level.
- **Employment type:** Full-time (`FT`) roles pay the most (likely reflecting hours and commitment level), while Freelance (`FL`) pays the least.
  - *Note:* Over 90% of records are Full-time, so this comparison may be biased by class imbalance.
- **Cross-analysis (experience × company size × salary):**
  - Medium (`M`) companies pay the highest salaries across all experience levels.
  - At the `MI` and `SE` levels, Medium companies out-pay Large companies on average and show much higher variance — meaning greater upside potential for top-tier salaries than at large corporations.
- **Geography:** US-based salaries are significantly higher than the rest of the world across all experience levels. This may reflect genuine market dynamics, a data collection bias toward the US, or both.

---

### 3. Key Takeaways & Recommendations

### a. Characteristics of High-Paying Roles
- **Location:** US-based (interpret with caution given potential data bias).
- **Experience:** Mid-level or Senior.
- **Company size:** Medium-sized companies.

### b. Where Should Entry-Level Candidates Apply?
- **Location:** US market.
- **Company size:** Medium-sized companies.
- **Job roles:** High-demand core tracks such as Data Engineer, Data Analyst, Data Scientist, and ML-adjacent roles like Machine Learning Engineer.

---

## 🛠️ Tech Stack & Libraries

- **Python 3.12**
- **Pandas & NumPy** — data manipulation & cleaning
- **Matplotlib & Seaborn** — data visualization & statistical distribution plotting
- **SciPy** — statistical calculations & outlier evaluation

---

## 📁 Project Structure

```
.
├── data/               # Raw and processed datasets
├── notebooks/          # EDA and analysis notebooks
├── README.md
```
