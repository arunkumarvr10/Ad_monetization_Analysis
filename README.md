# 📊 Mobile Ad Monetization Analytics Dashboard

**Tool:** Power BI Desktop  
**Dataset:** Synthetic dataset based on real Q4 2024 industry benchmarks (Appodeal, Business of Apps, MonetizeMore)  
**Domain:** Ad Tech / Mobile App Monetization  
**Project Type:** Portfolio Project — built to demonstrate ad monetization analytics skills

---

## 📌 Project Overview

This project analyzes mobile app ad performance data across 12 publishers, 5 ad networks, 4 ad formats, and 6 countries for the full year of 2024. The goal is to identify revenue optimization opportunities, flag underperforming publishers, and surface geo and format-level eCPM insights — the core responsibilities of an Ad Monetization Analyst role.

---

## 📁 Files

| File | Description |
|------|-------------|
| `GreedyGame_AdMonetization_Dashboard.pbix` | Main Power BI dashboard (4 pages) |
| `GreedyGame_Ad_Monetization_Dataset.csv` | Raw dataset — 1,668 rows × 15 columns |
| `README.md` | Project documentation |

---

## 📊 Dataset Details

- **Rows:** 1,668
- **Columns:** 15
- **Date Range:** January 2024 — December 2024
- **Total Revenue:** $963,199

### Columns

| Column | Description |
|--------|-------------|
| `date` | Date of record (YYYY-MM-DD) |
| `publisher_name` | App/publisher name (12 publishers) |
| `app_genre` | Genre — Casual, Puzzle, Racing, Hyper-Casual, etc. |
| `platform` | iOS or Android |
| `country` | US, IN, BR, GB, DE, ID |
| `ad_network` | AdMob, Meta Audience Network, Unity Ads, AppLovin, IronSource |
| `ad_format` | Banner, Interstitial, Rewarded Video, Native |
| `ad_requests` | Total ad requests sent to network |
| `impressions` | Ads actually served to users |
| `fill_rate` | Impressions ÷ Ad Requests |
| `ecpm` | Effective Cost Per Mille (revenue per 1,000 impressions) |
| `revenue_usd` | Total ad revenue in USD |
| `clicks` | User clicks on ads |
| `ctr` | Click-Through Rate |
| `dau` | Daily Active Users of the app |

### Data Quality
- ✅ Zero null values
- ✅ Zero duplicate rows
- ✅ No negative values in any numeric column
- ✅ Fill rate always between 0 and 1 (logically valid)
- ✅ Impressions never exceed ad requests
- ✅ eCPM benchmarks based on real Q4 2024 industry data

---

## 📈 Dashboard Pages

### Page 1 — Revenue Overview
- KPI Cards: Total Revenue ($963.2K), Total Impressions (433M), Avg eCPM ($5.23), Avg Fill Rate (87.6%)
- Monthly Revenue Trend Line Chart (Jan–Dec 2024)
- Revenue by Ad Format & Network (Stacked Bar)
- Slicers: Platform, Country

### Page 2 — Ad Format Performance
- Avg eCPM by Ad Format (Bar Chart)
- Avg eCPM by Ad Network (Bar Chart)
- Revenue Share by Ad Format (Donut Chart)
- Fill Rate vs eCPM by Format (Scatter Chart)

### Page 3 — Publisher Performance
- Revenue by Publisher (Bar Chart)
- Publisher × Format eCPM Matrix (with color scale)
- Avg Fill Rate by Publisher (with 85% reference line)
- Slicer: Ad Network

### Page 4 — Geo & Network Analysis
- Avg eCPM by Country (Bar Chart)
- Total Revenue by Country (Bar Chart)
- Ad Network Performance Summary (Table)
- Revenue: Country × Network (Matrix)
- Slicer: Ad Format

---

## 🔑 DAX Measures Used

```
Total Revenue = SUM(AdData[revenue_usd])
Total Impressions = SUM(AdData[impressions])
Total Ad Requests = SUM(AdData[ad_requests])
Avg eCPM = AVERAGE(AdData[ecpm])
Avg Fill Rate = AVERAGE(AdData[fill_rate])
Fill Rate % = FORMAT([Avg Fill Rate], "0.0%")
CTR % = FORMAT(AVERAGE(AdData[ctr]), "0.00%")
Revenue Per 1K Impressions = DIVIDE([Total Revenue], [Total Impressions] / 1000, 0)
MoM Revenue Change = VAR CurrentMonth = [Total Revenue]
                     VAR PrevMonth = CALCULATE([Total Revenue], DATEADD(AdData[date], -1, MONTH))
                     RETURN DIVIDE(CurrentMonth - PrevMonth, PrevMonth, 0)
Revenue Share by Format = DIVIDE([Total Revenue], CALCULATE([Total Revenue], ALL(AdData[ad_format])), 0)
```

---

## 💡 Key Business Insights

1. **Rewarded Video delivers 37× higher eCPM than Banner** ($11.68 vs $0.31) — publishers heavily reliant on Banner ads are leaving significant revenue on the table. Shifting even 20% of Banner inventory to Rewarded Video could meaningfully increase total revenue.

2. **US market generates 46% of total revenue ($446K)** despite representing only 35% of records — geo-targeting and prioritizing premium markets like US, GB, and DE for high-eCPM ad formats should be a core monetization strategy.

3. **Q4 2024 shows a clear 25% revenue spike** (Oct–Dec) vs Q1 baseline — publishers should maximize ad inventory, increase frequency caps, and prioritize premium networks during the Q4 window to capture peak advertiser demand.

4. **AdMob leads all networks** with highest avg eCPM ($5.01) and fill rate (92%) — making it the most reliable primary network, while AppLovin ($6.38 eCPM) performs better for high-value impressions despite slightly lower fill rate.

5. **TriviaKing Plus and PuzzleWorld HD show the highest Rewarded Video eCPM** (19.05 and 14.58 respectively) — engagement-driven genres are better suited for Rewarded Video monetization compared to Hyper-Casual titles like RunnerZ.

---

## 🛠 Tools & Skills Demonstrated

- **Power BI Desktop** — data modelling, DAX measures, multi-page dashboard
- **DAX** — aggregation, time intelligence (DATEADD), DIVIDE with error handling, FORMAT, ALL/CALCULATE
- **Data Analysis** — eCPM benchmarking, fill rate analysis, publisher performance comparison, geo analysis
- **Ad Tech Domain Knowledge** — programmatic advertising, mediation, ad formats (Banner/Interstitial/Rewarded Video/Native), ad networks, eCPM optimization

---

## 📚 Data Sources & Benchmarks

eCPM benchmarks used to build the synthetic dataset are based on:
- Appodeal Q4 2024 eCPM Report
- Business of Apps — Mobile Advertising Rates 2024
- MonetizeMore — eCPM Insights 2024-25
- Tenjin Ad Monetization Benchmark Report 2024

---

## 👤 Author

**Arun**  
Data Analyst | Power BI | SQL | Python  
Portfolio Project — June 2024
