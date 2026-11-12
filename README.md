# Influencer Marketing Performance & Campaign ROI Analysis

An end-to-end data analytics and commercial feasibility project evaluating the top 100 UK YouTube creators in 2024 to help marketing teams optimize influencer spend and campaign ROI.

---

## Project Overview

Marketing teams frequently struggle to select the right influencers for brand campaigns. Choosing creators based solely on follower or subscriber count often leads to poor campaign results, because large subscriber numbers do not always translate to high average views or sales conversions.

This project analyzes the top 100 UK YouTube channels using SQL Server, Power BI, and Python (YouTube Data API) to:
1. Identify high-performing channels based on actual viewership and engagement efficiency.
2. Filter out channels with declining returns or view dilution caused by high upload volumes.
3. Model campaign ROI across three distinct partnership types: Product Placement, Sponsored Video Series, and 3-Month Influencer Retainers.

---

## Tools Used

- **Python:** YouTube Data API v3 integration to fetch verified live channel statistics (subscribers, views, video count).
- **SQL Server (T-SQL):** Data transformation, schema constraints, data quality testing, and campaign ROI simulation.
- **Power BI:** Interactive reporting and visualization for business stakeholders.
- **Excel:** Initial exploratory inspection of raw dataset.

---

## Project Workflow

1. **Data Ingestion:** Extracted raw UK creator data from Kaggle and enriched it with live metrics using the YouTube Data API in Python.
2. **Data Cleaning (SQL):** Extracted clean channel names from raw strings, removed unnecessary attributes, and created structured database views (`view_uk_youtubers_2024`).
3. **Data Quality Testing (SQL):** Executed validation queries to verify row counts, column counts, data types, and check for duplicate records.
4. **Commercial Analysis (SQL):** Simulated potential revenue, costs, and net profit across multiple campaign formats.
5. **Dashboard Reporting (Power BI):** Visualized creator benchmarks and engagement metrics for marketing decision-makers.

---

## Data Cleaning and Validation

Before analyzing the data, four quality assurance checks were implemented in SQL Server to ensure complete data integrity:

- **Row Count Check:** Verified exactly 100 records exist in the cleaned dataset.
- **Column Count Check:** Confirmed all 4 required columns (`channel_name`, `total_subscribers`, `total_views`, `total_videos`) are present.
- **Data Type Validation:** Ensured appropriate data types (VARCHAR for channel names, INT for numerical metrics).
- **Duplicate Records Check:** Verified that there are zero duplicate channels in the view.

---

## Key Performance Metrics

- **Average Views per Video:** Total Views / Total Videos — Indicates how many people watch an average upload on the channel.
- **Subscriber Engagement Rate:** Total Subscribers / Total Videos — Evaluates audience acquisition efficiency relative to content output.
- **Views per Subscriber Ratio:** Total Views / Total Subscribers — Measures how actively subscribers watch content.

---

## Dashboard Preview

![Power BI Dashboard](assets/images/powerbi_dashboard.png)

---

## Campaign ROI & Commercial Feasibility Analysis

To evaluate business viability, three campaign models were simulated using standard marketing benchmarks:
- Product Unit Price: $5.00
- Conversion Rate: 2.0%

### Campaign Types Evaluated:
1. **Product Placement (Single Video):** One-time fixed fee of $50,000.
2. **Sponsored Video Series (11 Videos):** Total cost of $55,000 ($5,000 per video).
3. **Influencer Retainer (3-Month Contract):** Fixed contract cost of $130,000.

### Campaign Comparison Summary:

| Creator | Campaign Type | Avg Views / Video | Campaign Cost | Gross Revenue | Net Profit (Loss) | Recommendation |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Dan Rhodes** | Product Placement | 11.15M | $50,000 | $1,115,000 | **+$1,065,000** | Best choice for Product Placement |
| **NoCopyrightSounds** | Product Placement | 6.92M | $50,000 | $692,000 | **+$642,000** | Reliable secondary option |
| **DanTDM** | Product Placement | 5.34M | $50,000 | $534,000 | **+$484,000** | High brand trust & loyal audience |
| **Mister Max** | 3-Month Retainer | 14.06M | $130,000 | $1,406,000 | **+$1,276,000** | Best choice for broad reach |
| **Yogscast** | Sponsored Series (11 vids) | 710K | $55,000 | $71,000 | **+$16,000** | Moderate return |
| **GRM Daily** | Sponsored Series (11 vids) | 510K | $55,000 | $51,000 | **-$4,000** | Not recommended (View dilution) |
| **Manchester City** | Sponsored Series (11 vids) | 240K | $55,000 | $24,000 | **-$31,000** | Not recommended (Negative ROI) |

---

## Key Insights and Business Takeaways

1. **Upload Frequency vs. Viewership:** Channels with massive upload volumes (e.g., GRM Daily with 14,000+ videos) dilute their average views per video. Running fixed-cost campaigns on these channels results in negative net profit.
2. **Optimal Partner for Conversion:** Dan Rhodes represents the strongest partnership candidate for single-video campaigns, delivering the highest return on investment due to consistent high viewership per video.
3. **Risk Management:** Pre-campaign financial modeling helps marketing teams avoid spending budget on creators who cannot generate enough impressions to break even against campaign costs.

---

## Project Structure

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
