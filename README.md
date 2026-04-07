# AeroFit Treadmill : Customer Profiling & Probability Analysis

> **Descriptive analytics project** | Python · pandas · seaborn · Jupyter  
> Identifying the right treadmill for the right customer using data from 180 purchase records.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Business Problem](#business-problem)
3. [Dataset](#dataset)
4. [Project Structure](#project-structure)
5. [Analysis Summary](#analysis-summary)
6. [Key Findings](#key-findings)
7. [Customer Profiles](#customer-profiles)
8. [Probability Results](#probability-results)
9. [Recommendations](#recommendations)
10. [How to Run](#how-to-run)
11. [Dependencies](#dependencies)


---

## Project Overview

AeroFit sells three treadmill models at different price and feature tiers. The market research team needs to understand **who buys each model** so that:

- Store staff can recommend the right product to new customers
- Marketing campaigns can target the right audience for each model
- Underserved customer segments can be identified and pursued

This project uses descriptive statistics, visualisation, and probability analysis to build a clear, data-backed profile for each product.

---

## Business Problem

| Model  | Tier        | Price  |
|--------|-------------|--------|
| KP281  | Entry-level | $1,500 |
| KP481  | Mid-level   | $1,750 |
| KP781  | Advanced    | $2,500 |

**Two core tasks:**
1. Build a customer profile for each model using charts and summary tables
2. Compute marginal and conditional probabilities to quantify how likely different customer types are to buy each model

---

## Dataset

**Source:** AeroFit store purchase records : 3 months  
**Records:** 180 customer purchases  
**Missing values:** None  
**Duplicate rows:** None

| Feature       | Type        | Description                                         |
|---------------|-------------|-----------------------------------------------------|
| Product       | Categorical | KP281, KP481, or KP781                              |
| Age           | Numerical   | Customer age in years                               |
| Gender        | Categorical | Male / Female                                       |
| Education     | Numerical   | Years of education                                  |
| MaritalStatus | Categorical | Single / Partnered                                  |
| Usage         | Numerical   | Planned sessions per week                           |
| Income        | Numerical   | Annual income in USD                                |
| Fitness       | Numerical   | Self-rated fitness 1 (poor) – 5 (excellent)         |
| Miles         | Numerical   | Expected miles walked/run per week                  |

---

## Project Structure

```
Customer-Profiling-and-Probability-Analysis/
├── data/                    # Raw dataset (aerofit_treadmill.csv)
├── notebooks/               # Technical implementation
│   └── customer_profiling_eda.ipynb
├── reports/                 # Documented insights
│   └── analysis_report.docx
├── visuals/                 # Key charts & distribution plots
│   └── aerofit_customer_profile_distribution.png
└── README.md                # Project documentation & summary
```

---
### 🚀 Key Deliverables

* 📓 **[Exploratory Data Analysis (Jupyter Notebook)](notebooks/customer_profiling_eda.ipynb)** — *Python implementation using Pandas, Seaborn, and Matplotlib to identify customer segments.*
* 📑 **[Customer Profiling Report (PDF)](reports/analysis_report.pdf)** — *A comprehensive business report translating probability analysis into actionable marketing strategies.*
* 📊 **[Visualization Gallery](visuals/aerofit_customer_profile_distribution.png)** — *Statistical distributions and heatmaps showing the correlation between income, age, and product choice.*
* 📈 **[Probability Analysis Summary](#probability-results)** — *Calculated conditional probabilities to predict which treadmill a customer is most likely to buy.*
---

## Analysis Summary

The notebook follows this structure:

1. **Setup** : library imports, consistent plot theming
2. **Data Loading** : CSV load, shape and head inspection
3. **Dataset Overview** : dtypes, categorical conversion, `describe()`
4. **Data Quality Check** : null values, duplicates, outlier flags
5. **Univariate Analysis**
   - Numerical: three-panel plots (histogram + KDE, boxplot, violin) for Age, Usage, Fitness, Income, Miles, Education
   - Categorical: count distributions for Product, Gender, MaritalStatus
6. **Bivariate Analysis** : Product vs. all features (boxplots, countplots, stacked histograms)
7. **Correlation Analysis** : masked heatmap, Miles-correlation bar chart, pairplot coloured by Product
8. **Probability Analysis**
   - Marginal probabilities (product market share)
   - Conditional probabilities for Gender, MaritalStatus, Income, Fitness, Usage, Age
   - Specific business questions (e.g., P(KP781 | Male))
9. **Customer Profiles** : synthetic summary table per product
10. **Business Insights** : plain-language observations after each analysis section
11. **Recommendations** : six actionable items for sales and marketing teams
12. **Conclusion**

---

## Key Findings

### Market Share
- **KP281** accounts for **44.4%** of purchases — the most popular model by a clear margin
- **KP481** takes **33.3%** of purchases
- **KP781** accounts for **22.2%** of purchases

### Top Differentiators
- **Income** and **self-rated fitness** are the two strongest predictors of product choice more useful than age or marital status
- Miles, Usage, and Fitness are strongly correlated (r > 0.67) committed, fit customers cluster around the KP781
- Income and Education are moderately correlated (r = 0.62) higher education drives purchasing power for premium models

### Outliers
- High-income buyers (>$80K) and high-mileage customers (>200 miles/week) are genuine KP781 buyer signals **retained** in all analyses
- Usage of 6–7 days/week is rare but real; these customers consistently chose the KP781

---

## Customer Profiles

| Attribute       | KP281 (Entry)           | KP481 (Mid)             | KP781 (Advanced)       |
|-----------------|-------------------------|-------------------------|------------------------|
| Price           | $1,500                  | $1,750                  | $2,500                 |
| Market Share    | 44%                     | 33%                     | 22%                    |
| Typical Age     | 18–35                   | 24–34                   | 28–45                  |
| Income Range    | $39K–$53K               | $45K–$60K               | $75K+                  |
| Gender Skew     | Balanced                | Slightly Female         | Strongly Male          |
| Fitness Level   | Average (2–3)           | Average (2–3)           | High (4–5)             |
| Weekly Usage    | 3 days                  | 3 days                  | 4–5 days               |
| Miles / Week    | 50–100                  | 75–130                  | 120–200+               |
| Marital Status  | Both; more Partnered    | Both balanced           | More Single            |

---

## Probability Results

### Marginal
| Product | P(Product) |
|---------|------------|
| KP281   | 0.444      |
| KP481   | 0.333      |
| KP781   | 0.222      |

### Key Conditional Probabilities

| Condition            | P(KP281) | P(KP481) | P(KP781) |
|----------------------|----------|----------|----------|
| Given: Male          | 0.394    | 0.267    | 0.339    |
| Given: Female        | 0.506    | 0.411    | 0.083    |
| Given: Income >$80K  | 0.125    | 0.083    | 0.792    |
| Given: Fitness = 5   | ~0.18    | ~0.24    | ~0.58    |
| Given: Fitness ≤ 2   | 0.667    | 0.256    | 0.077    |
| Given: Single        | 0.397    | 0.329    | 0.274    |
| Given: Partnered     | 0.472    | 0.340    | 0.189    |

**Two-question rule:** A customer's income bracket + self-rated fitness correctly routes ~75% of buyers to the right product.

---

## Recommendations

| # | Action | Why |
|---|--------|-----|
| 1 | Build a 2-question in-store recommendation guide (fitness + income) | Routes most customers accurately without technical jargon |
| 2 | Run a KP781 campaign targeting high-fitness female buyers | Only ~8% of female buyers currently choose KP781 — underserved |
| 3 | Market KP281/KP481 as "smart value" for the <$60K income segment | Entry/mid models need clearer budget-friendly positioning |
| 4 | Launch a loyalty upgrade programme for existing KP281/KP481 owners | 12-month users are natural KP781 candidates; trade-in offers help |
| 5 | Pilot a 40+ "healthy ageing" campaign | This age group is nearly absent from current data — untapped market |
| 6 | Test household/couple-focused KP781 messaging for partnered buyers | Partnered customers buy KP781 at lower rates than single customers |

---

## How to Run

### 1. Clone or download the project files

```bash
git clone https://github.com/your-username/aerofit-analysis.git
cd aerofit-analysis
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Launch the notebook

```bash
jupyter notebook customer_profiling_eda.ipynb
```

### 4. Run all cells in order

The notebook is structured sequentially. Run cells from top to bottom. All plots render inline.

> **Note:** The dataset file `aerofit_treadmill.csv` must be in the same directory as the notebook. If you prefer to load from the original URL, uncomment the URL line in the data loading cell.

---

## Dependencies

| Library    | Version (tested) | Purpose                         |
|------------|------------------|---------------------------------|
| Python     | 3.8+             | Core language                   |
| pandas     | 1.5+             | Data manipulation, crosstabs    |
| numpy      | 1.23+            | Numerical operations            |
| matplotlib | 3.6+             | Base plotting                   |
| seaborn    | 0.12+            | Statistical visualisation       |
| jupyter    | 1.0+             | Notebook environment            |

Install all at once:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

---

## Author

**Shital V Rewanwar**  
Data Analysis Project — AeroFit Case Study  
Dataset: [AeroFit Treadmill Purchase Records](https://d2beiqkhq929f0.cloudfront.net/public_assets/assets/000/001/125/original/aerofit_treadmill.csv)
