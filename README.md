# CodePilot – AI Coding Assistant SQL Business Analysis

## Project Overview

**CodePilot** is an AI-powered coding assistant designed to support software development teams.

This project uses SQL to analyze how developers and customers are using CodePilot. The analysis focuses on developer adoption, customer and team usage, feature usage, usage trends over time, and the relationship between product usage and revenue.

The goal of this project is to demonstrate how SQL can be used to answer practical **business questions** from structured data.

---

## Business Objectives

The analysis aims to:

* Measure developer adoption
* Compare usage across customers and teams
* Identify the most frequently used CodePilot features
* Analyze usage trends over time
* Compare product usage with customer revenue
* Identify an additional business question for further investigation

---

## Dataset

The project uses a dummy dataset containing four related tables:

| Table             | Description                                                |
| ----------------- | ---------------------------------------------------------- |
| `customers`       | Contains customer details and subscription plans           |
| `developers`      | Contains developers, their customers, and teams            |
| `usage_events`    | Contains CodePilot usage activity and accepted suggestions |
| `monthly_revenue` | Contains monthly revenue generated from each customer      |

### Dataset Size

| Table           | Records |
| --------------- | ------: |
| Customers       |       4 |
| Developers      |      12 |
| Usage Events    |      24 |
| Monthly Revenue |      12 |

The dataset covers **January to March 2026**.

### Relationships

```text
Customers
    |
    ├── Developers
    |       |
    |       └── Usage Events
    |
    └── Monthly Revenue
```

---

## Business Assumptions

The following assumptions are used for the analysis:

* A developer is considered **Active** if they have at least one usage event.
* A developer with no usage events is considered **Inactive**.
* Each usage event represents an interaction with CodePilot.
* Accepted suggestions represent AI suggestions accepted by developers.
* Revenue represents the monthly revenue generated from each customer.
* The dataset is dummy data created for SQL analysis.

---

# Business Analysis

## 1. Developer Adoption

### Business Question

> How many developers are actively using CodePilot, and how many are inactive?

### SQL Concepts

* `CASE WHEN`
* `COUNT()`
* `LEFT JOIN`
* `GROUP BY`
* Subqueries

### Finding

There are **10 active developers out of 12**, resulting in an overall adoption level of **83.33%**.

Two developers are inactive.

---

## 2. Customer and Team Usage

### Business Question

> Which customers and teams use CodePilot the most?

Usage events and accepted suggestions are aggregated for each customer and team.

### SQL Concepts

* `JOIN`
* `LEFT JOIN`
* `COUNT()`
* `SUM()`
* `COALESCE()`
* `GROUP BY`
* `ORDER BY`

### Finding

**AlphaTech and CloudNova together account for 75% of all usage events.**

Among teams, the **Platform** and **Data** teams have the highest usage.

---

## 3. Feature Usage

### Business Question

> Which CodePilot features are used most frequently?

Usage events are grouped by event type, such as:

* Code completion
* Chat
* Code review

### SQL Concepts

* `COUNT()`
* `GROUP BY`
* `ORDER BY`

### Finding

**Code completion** is the most frequently used feature, representing **66.67% of all usage events**.

---

## 4. Usage Over Time

### Business Question

> How does CodePilot usage change from month to month?

Usage events are grouped by month to analyze:

* Number of usage events
* Number of active developers
* Accepted suggestions

### SQL Concepts

* `DATE_FORMAT()`
* `COUNT()`
* `COUNT(DISTINCT)`
* `SUM()`
* `GROUP BY`
* `ORDER BY`

### Finding

| Month         | Usage Events |
| ------------- | -----------: |
| January 2026  |           10 |
| February 2026 |           10 |
| March 2026    |            4 |

January and February each recorded **10 usage events**, while March recorded only **4**.

The number of active developers also decreased from **8 to 4** in March.

---

## 5. Usage vs Revenue

### Business Question

> Is higher CodePilot usage associated with higher customer revenue?

Total usage and total revenue are calculated separately for each customer and then compared.

### SQL Concepts

* `JOIN`
* `LEFT JOIN`
* Subqueries
* `COUNT()`
* `SUM()`
* `COALESCE()`
* `GROUP BY`

### Finding

AlphaTech and CloudNova have relatively high CodePilot usage as well as high three-month revenue.

However, this dataset **does not establish that higher CodePilot usage causes higher revenue**.

An interesting observation is that **March usage decreased while total revenue continued to increase**.

---

## 6. Additional Business Question

### Business Question

> Why did CodePilot usage decline sharply in March, particularly for some customers, while revenue continued to increase?

### Approach

March usage can be compared across customers to identify which customers experienced the decline.

Further investigation could examine:

* Developer engagement
* Feature adoption
* Training
* Product issues
* Customer-specific factors

### Finding

BetaWorks and DeltaSoft recorded **zero usage events in March**, while AlphaTech and CloudNova continued to use CodePilot.

Therefore, the March decline was **not uniform across all customers** and requires further investigation.

---

# SQL Skills Demonstrated

This project demonstrates the use of:

```text
SELECT
WHERE
JOIN
LEFT JOIN
GROUP BY
ORDER BY
COUNT()
COUNT(DISTINCT)
SUM()
COALESCE()
CASE WHEN
Subqueries
DATE_FORMAT()
MONTH()
YEAR()
```

These SQL concepts were applied to business-oriented questions rather than only basic database operations.

---

# Project Structure

A suggested GitHub repository structure is:

```text
CodePilot-SQL-Analysis/
│
├── README.md
│
├── sql/
│   ├── database_setup.sql
│   ├── developer_adoption.sql
│   ├── customer_usage.sql
│   ├── team_usage.sql
│   ├── feature_usage.sql
│   ├── monthly_usage.sql
│   ├── usage_vs_revenue.sql
│   └── march_analysis.sql
│
├── report/
│   └── CodePilot_SQL_Business_Analysis.pdf
│
└── screenshots/
    └── sql_workbench_results/
```

---

# Tools Used

* **SQL**
* **MySQL / SQL Workbench**
* **GitHub**

---

# Conclusion

This project demonstrates how SQL can be used to transform application usage data into business insights.

The analysis starts by understanding developer engagement, then examines differences across customers and teams, identifies popular features, analyzes usage over time, and compares product usage with revenue.

The analysis also identifies the significant March usage decline, particularly for BetaWorks and DeltaSoft, as an area that would require further investigation.

The SQL queries and their outputs are maintained separately in SQL Workbench for demonstration and review.
