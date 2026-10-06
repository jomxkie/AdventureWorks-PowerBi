# Adventure Works Sales Dashboard

### Turning 2.5 years of sales data into a growth, market, and margin playbook

**Role:** Data Analyst (end-to-end: data modeling, DAX, visualization, insight writing) **Tool:** Power BI **Data period:** January 2021 – June 2023 **Dataset:** Adventure Works (sales, products, customers, territories)

---

## I. Project Overview

**The situation.** Adventure Works is a bicycle and cycling-gear company selling across six countries. Leadership had transactional sales data but no single view showing *how fast the business is growing, where the money comes from, and whether growth is profitable.*

**The goal.** Build a one-page executive dashboard that answers those questions in under a minute, and pairs every chart with a clear recommendation, so the dashboard drives decisions instead of just reporting numbers.

**The headline result:**

| Total Revenue | Units Sold | Avg Order Value | Total Profit | Profit Margin |
| --- | --- | --- | --- | --- |
| **$24.91M** | **84K** | **$990.09** | **$10.46M** | **41.97%** |

**Scope:** Revenue trend and forecast, country performance, product category volume, and month-over-month tracking, with a year slicer for 2021–2023.

> 📸 *\[Insert full dashboard screenshot here\]*

---

## II. Business Questions

The dashboard was designed backwards from the questions a sales leader would actually ask:

1. **Is revenue growing, and how stable is that growth?** (trend + forecast)
2. **Which countries contribute most to revenue and profitability?**
3. **Which product categories drive the highest sales volume?**
4. **Are we growing profitably, or just growing?** (margin and profit tracking)
5. **How did we perform most recently versus the prior month?**

Each question maps to one visual, so a reader can move from question to answer without hunting.

---

## III. Key Insights

### 1. Revenue has grown strongly, but it is volatile

Weekly revenue rose from roughly **$0.1M in 2021** to **$0.3M–$0.45M per week by mid-2023**, a roughly 3–4x increase. The trend line is clearly upward, but weekly swings are large, and the forecast band widens considerably, which signals real uncertainty in planning.

### 2. Two markets generate over 60% of revenue

The **United States ($7.94M)** and **Australia ($7.42M)** together contribute about **$15.4M, or roughly 62% of total revenue**. The three European markets (UK, Germany, France) combine for **$7.79M (\~31%)**, and Canada adds $1.77M (\~7%).

### 3. Margins are remarkably consistent, so profit follows revenue

Profit margin sits in a tight **41.5%–42.8%** band across every country. That means country profit rankings are driven by *revenue scale*, not pricing power or cost differences. The US leads on profit ($3.36M), followed by Australia ($3.08M).

### 4. Australia and Canada have very different sales profiles

- **Australia:** \~$413 revenue per unit (17,951 units), a high-value mix.
- **United States:** \~$266 revenue per unit.
- **Canada:** \~$162 revenue per unit despite selling 10,894 units, more units than France or Germany, but the lowest revenue of the six markets. Canada has the **highest margin (42.83%)** but the weakest revenue per unit.

### 5. Accessories dominate volume

Accessories account for **57.81K of 84.17K units (68.7%)**, versus Bikes at 13.93K and Clothing at 12.44K. Accessories are the traffic driver of the business; bikes are the lower-volume, higher-ticket product.

### 6. Recent momentum is positive but modest

June 2023 compared with May 2023:

- Revenue: **$1.83M (+3.31%)**
- Profit: **$771.58K (+2.77%)**
- Units: **8,260 (+0.74%)**

Revenue is growing faster than units, which suggests growth is coming from **price/mix rather than pure volume**, a healthy sign worth monitoring.

---

## IV. Business Recommendations

| # | Finding | Recommendation | Why it matters |
| --- | --- | --- | --- |
| 1 | Revenue is growing but volatile | **Improve demand forecasting** (weekly/seasonal models, tie to promotions and inventory) | Narrower forecast bands reduce stock-outs, overstock, and cash-flow surprises |
| 2 | US + Australia ≈ 62% of revenue | **Expand into Europe**, prioritizing the UK, which already leads European revenue ($2.90M), and invest in lagging Canada revenue per unit | Reduces concentration risk; Europe's combined revenue already rivals a top-two market |
| 3 | Accessories = 68.7% of units | **Implement cross-selling**: bundle accessories with bikes and clothing at checkout | Accessories can pull higher-value products into the basket and raise average order value |
| 4 | 41.97% margin, flat across markets | **Optimize costs and discounting**: audit discount depth and supplier costs by category | Margin is uniform, so any improvement scales across the entire business |
| 5 | June revenue +3.31%, profit +2.77% | **Sustain growth** by tracking month-over-month momentum and watching the units-vs-revenue gap | Early warning if growth turns from mix-driven to stalling |

---

## V. Impact / Value

**What the dashboard delivers to the business:**

- **One-minute executive view:** five KPIs, trend, market table, and category chart on a single page.
- **Decision-ready, not just descriptive:** every insight is paired with a recommended action directly on the dashboard.
- **Early-warning tracking:** month-over-month cards flag changes in revenue, units, and profit.

**Illustrative value of the recommendations** *(scenario estimates based on dashboard figures, not realized results)*:

| Lever | Scenario | Estimated annual effect |
| --- | --- | --- |
| Margin improvement | +1 percentage point on the $24.91M revenue base | ≈ **$249K** additional profit across the full period |
| Cross-selling | +1% lift in revenue from accessory bundles | ≈ **$249K** additional revenue |
| Europe expansion | +10% growth in UK/Germany/France revenue ($7.79M base) | ≈ **$779K** additional revenue |

*These are sensitivity illustrations to show where the biggest levers sit; they are not forecasts.*

---

## VI. Techstack and Power BI Technical

**Tools:** Power BI Desktop · Power Query · DAX · Data modeling (star schema) *\[Add/adjust: SQL Server / Excel / CSV source, GitHub, etc.\]*

### Data modeling

- Star schema with a central **Sales** fact table connected to **Date, Product, Customer, and Territory** dimensions
- Dedicated **Date table** marked as the date dimension to enable time intelligence

### Key measures (DAX)

*\[Replace with your actual measures if different\]*

```dax
Total Revenue = SUM(Sales[Revenue])

Total Profit = [Total Revenue] - SUM(Sales[TotalCost])

Profit Margin % = DIVIDE([Total Profit], [Total Revenue])

Avg Order Value = DIVIDE([Total Revenue], DISTINCTCOUNT(Sales[OrderNumber]))

Revenue Prev Month = CALCULATE([Total Revenue], DATEADD('Date'[Date], -1, MONTH))

Revenue MoM % = DIVIDE([Total Revenue] - [Revenue Prev Month], [Revenue Prev Month])
```

### Visualization and design choices

- **KPI cards** across the top for instant orientation
- **Line chart with trend line and forecast band** to show growth direction and uncertainty
- **Conditional formatting on the country table** (revenue shading) to highlight the top markets at a glance
- **Bar chart** for category volume ranking
- **Sparkline-style cards with prior-month comparison** for month-over-month tracking
- **Year slicer** for interactive filtering
- **Insights panel** with business takeaways written directly on the report, because a dashboard should say what to do, not only what happened
- Consistent blue palette with the key KPI highlighted

---

## VII. What I've Learned

1. **Design from questions, not from charts.** Starting with the business questions made every visual earn its place.
2. **Insight beats decoration.** A dashboard without recommendations is a report; adding the "so what" turned it into a decision tool.
3. **Check the story behind the totals.** Looking beyond revenue to revenue per unit and margin revealed that Australia, the US, and Canada have very different profiles.
4. **Forecasts communicate uncertainty, not just direction.** The widening forecast band made the case for better demand planning more convincingly than the trend line alone.
5. **Validate your numbers.** Cross-checking dashboard totals against component calculations (for example, the US + Australia share of revenue) is essential for stakeholder trust.
6. **Next time I would:** add a product-level profit view (to confirm whether accessories are also profit leaders), include discount and returns data, and build a region-by-category matrix to sharpen the cross-selling recommendation.

---

*Dashboard built with Power BI · Data: Adventure Works · \[Link to GitHub / Power BI service\]*