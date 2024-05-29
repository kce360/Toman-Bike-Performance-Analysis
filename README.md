# Toman Bike Performance Analysis

## Project Overview

This project involves developing a "Toman Bike Share" dashboard to display key performance metrics for informed decision-making. The dataset, instructions, and guidance are from the Absent Data YouTube channel.

### Request for Development of Toman Bike Share Dashboard

We need your expertise to develop a dashboard for "Toman Bike Share" that displays our key performance metrics for informed decision-making.

#### Requirements:
- **Hourly Revenue Analysis**
- **Profit and Revenue Trends**
- **Seasonal Revenue**
- **Rider Demographics**

#### Design and Aesthetics:
- Use our company colors
- Ensure the dashboard is easy to navigate

#### Data Source:
- Access to our databases will be provided. If no database, please create one.

#### Deadline:
- We need a preliminary version ASAP.

### Deliverables:
- Estimated timeline for completion
- Recommendation on raising prices next year

## Process

The three datasets provided were uploaded to MS SQL Server 19, where they were united, and a Common Table Expression (CTE) was created to use it:

```sql
WITH CTE AS (
SELECT * FROM bike_share_yr_0
UNION
SELECT * FROM bike_share_yr_1)

SELECT 
    dteday,
    season,
    a.yr,
    weekday,
    hr,
    rider_type,
    riders,
    price,
    COGS,
    riders * price as revenue,
    riders * price – COGS * riders as profit 
FROM CTE a
LEFT JOIN cost_table b
ON a.yr = b.yr
```

## Visualization

The visualization is made in Power BI (file in the folder).

## Recommendation

### Conservative Increase:
Considering the substantial increase last year, a more conservative increase might be prudent to avoid hitting a price ceiling where demand starts to drop. An increase in the range of 10-15% could test the market's response without risking a significant loss of customers.

### Price Setting:
- If the price in 2022 was $4.99, a 10% increase would make the new price about $5.49.
- A 15% increase would set the price at approximately $5.74.

### Recommended Strategy:
1. **Market Analysis**: Conduct further market research to understand customer satisfaction, potential competitive changes, and the overall economic environment. This can guide whether leaning towards the lower or higher end of the suggested increase.

2. **Segmented Pricing Strategy**: Consider different pricing for casual versus registered users, as they may have different price sensitivities.

3. **Monitor and Adjust**: Implement the new prices but be ready to adjust based on immediate customer feedback and sales data. Monitoring closely will allow you to fine-tune your pricing strategy without committing fully to a price that might turn out to be too high.


