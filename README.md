# Influencer Marketing Performance & Campaign ROI Analysis

An end-to-end data analytics and commercial feasibility project evaluating the top 100 UK YouTube creators in 2024 to help marketing teams optimize influencer spend and campaign ROI.

---

## 📌 Project Overview
Marketing teams often face the challenge of selecting the right influencers for brand campaigns. Relying purely on follower or subscriber counts frequently leads to poor campaign ROI because high subscriber numbers do not always translate to high average views or conversion rates.

This project analyzes the top 100 UK YouTube channels using **SQL Server**, **Power BI**, and **Python (YouTube Data API)** to:
1. Identify high-performing channels based on actual viewership and engagement efficiency.
2. Filter out channels with declining returns or view dilution caused by excessive upload volume.
3. Model campaign ROI across three distinct partnership types: **Product Placement**, **Sponsored Series**, and **3-Month Retainer**.

---

## 🛠️ Tools & Technologies
- **Python:** YouTube Data API v3 integration and data extraction (`google-api-python-client`, `pandas`).
- **SQL Server (T-SQL):** Data transformation, quality checks, views creation, and ROI simulation CTEs.
- **Power BI & DAX:** Interactive dashboard design and custom KPI calculation.
- **Excel:** Initial exploratory data inspection.

---

## 🔄 Project Workflow

```
[Kaggle Dataset + YouTube API] 
         │
         ▼
  [Python Extraction] ──> Fetch channel stats (subscribers, views, uploads)
         │
         ▼
[SQL Server (ETL & DQA)] ──> String parsing, data cleaning, 4 Quality Checks, View creation
         │
         ▼
[Commercial Modeling (SQL)] ──> ROI simulation across 3 marketing campaign types
         │
         ▼
[Power BI Dashboard] ──> Interactive metrics & creator benchmarking for stakeholders
```

---

## 🧹 Data Cleaning & Quality Assurance (DQA)

Raw data was cleaned and standardized in SQL Server (`view_uk_youtubers_2024`) by extracting handles, parsing channel names, and ensuring strict data constraints:
- **Row count check:** Exactly 100 records verified.
- **Column count check:** Confirmed 4 core fields (`channel_name`, `total_subscribers`, `total_views`, `total_videos`).
- **Data type validation:** Schema verified via `INFORMATION_SCHEMA.COLUMNS`.
- **Duplicate records test:** Evaluated `COUNT(*) > 1` grouped by channel name (0 duplicates found).

---

## 📊 Key Metrics & DAX Formulas

- **Average Views per Video:**
  $$\text{Avg Views} = \frac{\text{Total Views}}{\text{Total Videos}}$$
- **Subscriber Engagement Rate:**
  $$\text{Engagement Rate} = \frac{\text{Total Subscribers}}{\text{Total Videos}}$$
- **Views per Subscriber Ratio:**
  $$\text{Views / Sub} = \frac{\text{Total Views}}{\text{Total Subscribers}}$$

---

## 📈 Dashboard Preview

![Power BI Dashboard](assets/images/powerbi_dashboard.png)

---

## 💰 Commercial Feasibility & Campaign ROI Analysis

To provide actionable recommendations, campaigns were simulated with realistic marketing assumptions:
- **Product Price:** $5.00
- **Conversion Rate:** 2.0%
- **Campaign Cost Assumptions:**
  - *Product Placement (Single Video):* $50,000 fixed fee
  - *Sponsored Video Series (11 Videos):* $55,000 ($5,000 / video)
  - *Influencer Retainer (3-Month Contract):* $130,000 fixed contract

### Summary of Campaign Results:

| Creator | Campaign Type | Avg Views / Video | Campaign Cost | Gross Revenue | Net Profit (Loss) | Recommendation |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Dan Rhodes** | Product Placement | 11.15M | $50,000 | $1,115,000 | **+$1,065,000** | **Best for Product Placement** |
| **NoCopyrightSounds** | Product Placement | 6.92M | $50,000 | $692,000 | **+$642,000** | Strong secondary option |
| **DanTDM** | Product Placement | 5.34M | $50,000 | $534,000 | **+$484,000** | High brand trust & loyalty |
| **Mister Max** | 3-Month Retainer | 14.06M | $130,000 | $1,406,000 | **+$1,276,000** | **Best for Maximum Reach** |
| **Yogscast** | Sponsored Series (11 vids) | 710K | $55,000 | $71,000 | **+$16,000** | Moderate return |
| **GRM Daily** | Sponsored Series (11 vids) | 510K | $55,000 | $51,000 | **-$4,000** | ⚠️ Avoid (View dilution) |
| **Manchester City** | Sponsored Series (11 vids) | 240K | $55,000 | $24,000 | **-$31,000** | ⚠️ Avoid (Negative ROI) |

---

## 💡 Key Business Takeaways
1. **High Upload Volume Dilutes Views:** Channels that publish thousands of videos (e.g., GRM Daily with 14,000+ uploads) have significantly lower average viewership per video, resulting in negative ROI for fixed-rate multi-video deals.
2. **Top Recommended Partner:** **Dan Rhodes** delivers the highest return per single video collaboration ($1M+ projected net profit) with strong organic engagement across the UK audience.
3. **Budget Protection:** Establishing baseline viewership thresholds prevents committing budget to high-subscriber channels that fail to cover fixed partnership costs.

---

## 📁 Repository Structure
```
├── assets/
│   ├── datasets/         # Raw and processed CSV datasets
│   ├── docs/             # Requirements documents and workbooks
│   ├── images/           # Dashboard screenshots and SQL verification outputs
│   └── scripts/
│       ├── python/       # YouTube Data API extraction scripts
│       └── sql/          # DQA tests, transformations, and ROI queries
└── README.md
```
