# Sales Method Performance Analysis

## Overview

A data analysis project evaluating the revenue performance and efficiency of three sales outreach methods; Email, Call, and Email + Call — across a six-week period. The project covers data validation, exploratory analysis, a custom business metric, and a final recommendation for the sales team.

---

## Business Question

**Which sales method should the company prioritize to maximize long-term revenue?**

---

## Dataset

**File:** `product_sales.csv`  
**Rows:** 15,000 customers  
**Columns:** 8

| Column | Type | Description |
|---|---|---|
| `week` | Integer | Week number (1–6) |
| `sales_method` | String | Outreach method used: Email, Call, or Email + Call |
| `customer_id` | String | Unique customer identifier |
| `nb_sold` | Integer | Number of items sold |
| `revenue` | Float | Revenue generated from the customer |
| `years_as_customer` | Integer | How long the customer has been with the company |
| `nb_site_visits` | Integer | Number of website visits by the customer |
| `state` | String | US state of the customer |

---

## Data Cleaning Summary

| Column | Issue | Resolution |
|---|---|---|
| `sales_method` | 5 values instead of 3 (typos, capitalization) | Mapped to 3 standard values |
| `revenue` | 1,074 missing values | Replaced with mean revenue per sales method |
| `years_as_customer` | 2 values exceeding max possible (47, 63) | Capped at 39 (company founded 1984) |
| All others | No issues | No changes required |

---

## Analysis Highlights

### Revenue Trends Over 6 Weeks
- **Email** — Highest revenue in week 1, but declined consistently over time
- **Call** — General upward trend with fluctuations; began declining toward week 6
- **Email + Call** — Steady, consistent revenue growth across all 6 weeks

### Business Metric: ARCPSE
**Average Revenue per Customer Sales Effort (ARCPSE)** normalizes revenue by the relative effort each method requires:

| Sales Method | Effort Weight | ARCPSE |
|---|---|---|
| Email | 0.5 | 180.10 |
| Email + Call | 1.0 | 158.80 |
| Call | 3.0 | 15.29 |

Formula: `ARCPSE = Total Revenue / (Number of Customers × Sales Effort)`

---

## Recommendation

**Prioritize the Email + Call method.**

Although Email has the highest ARCPSE, Email + Call customers show higher site visit counts, more items purchased per customer, and the only consistent upward revenue trend over the full six-week period. These factors make it the most sustainable choice for long-term growth.

The Call method is the least efficient — high effort, low ARCPSE, and a declining revenue trend — and should be deprioritized.

---

## Requirements

```bash
pip install pandas numpy seaborn matplotlib
```

**Python version:** 3.8+

---

## Usage

Open and run the analysis notebook from top to bottom. All cleaning steps, visualizations, and metric calculations are documented inline.
