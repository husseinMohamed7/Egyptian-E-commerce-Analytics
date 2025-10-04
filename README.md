# 🛒 Egyptian E-commerce Analytics - Full Project Prompt

## 📋 Project Overview

**Project Name:** Egyptian E-commerce Data Analytics Platform

**Duration:** 3 Days

**Objective:** Build an end-to-end data engineering and analytics solution for an Egyptian online retail store to derive actionable business insights and support data-driven decision making.

---

## 🎯 Business Goals

1. **Understand Customer Behavior**
   - Identify high-value customer segments
   - Analyze purchase patterns across different cities
   - Calculate Customer Lifetime Value (CLV)

2. **Optimize Product Strategy**
   - Identify best and worst performing products/categories
   - Monitor inventory levels and stockouts
   - Analyze profit margins by category

3. **Improve Marketing ROI**
   - Evaluate performance of different marketing channels
   - Calculate Customer Acquisition Cost (CAC)
   - Measure campaign effectiveness

4. **Drive Revenue Growth**
   - Identify revenue trends and seasonality
   - Analyze order patterns by day/time
   - Discover cross-selling opportunities

---

## 🏗️ Technical Architecture

```
Data Sources (CSV Files)
    ↓
Python ETL Scripts
    ↓
Snowflake Data Warehouse
    ├── Raw Layer (Landing Zone)
    ├── Staging Layer (Cleaned Data)
    └── Analytics Layer (Business Logic)
        ↓
    dbt Transformations
        ↓
Power BI Dashboards
```

---

## 📊 Data Model

### Fact Tables
- **fact_orders**: Core transaction data
- **fact_order_items**: Product-level order details
- **fact_daily_sales**: Aggregated daily metrics

### Dimension Tables
- **dim_customers**: Customer master data
- **dim_products**: Product catalog
- **dim_date**: Date dimension for time-based analysis
- **dim_geography**: City/region information

### Aggregate Tables (Marts)
- **mart_customer_rfm**: RFM segmentation
- **mart_product_performance**: Product KPIs
- **mart_marketing_roi**: Channel performance
- **mart_city_analytics**: Geographic insights

---

## 📅 Day-by-Day Execution Plan

### **DAY 1: Data Generation & Infrastructure Setup** ⚙️

**Morning (4 hours):**
1. ✅ Set up project structure
2. ✅ Generate realistic Egyptian e-commerce data
   - 500 products across 10 categories
   - 3,000 customers from 10 Egyptian cities
   - 10,000 orders over 2 years
   - Marketing campaigns data
3. ✅ Set up Snowflake account (free trial)
4. ✅ Create database schema (raw, staging, analytics)

**Afternoon (4 hours):**
5. ✅ Create Python ETL scripts
6. ✅ Load CSV data into Snowflake
7. ✅ Validate data quality
8. ✅ Create initial staging views

**Evening (2 hours):**
9. Document data dictionary
10. Set up Git repository

**Deliverables:**
- ✅ 5 CSV files with data
- ✅ Snowflake database with populated tables
- ✅ Python loading scripts
- ✅ Initial documentation

---

### **DAY 2: Data Transformation & Business Logic** 🔄

**Morning (4 hours):**
1. Set up dbt project
   ```bash
   dbt init egyptian_ecommerce
   ```
2. Create staging models (data cleaning)
   - stg_orders
   - stg_customers
   - stg_products
   - stg_order_items

3. Create intermediate models
   - int_order_metrics (calculate totals, margins)
   - int_customer_orders (join customers with orders)

**Afternoon (4 hours):**
4. Create analytics models (business logic)
   
   **Customer Analytics:**
   - `mart_customer_rfm.sql` - RFM segmentation
   - `mart_customer_lifetime_value.sql` - CLV calculation
   
   **Product Analytics:**
   - `mart_product_performance.sql` - Sales, profit, stock
   - `mart_category_trends.sql` - Category-level metrics
   
   **Marketing Analytics:**
   - `mart_marketing_roi.sql` - Channel performance
   - `mart_campaign_effectiveness.sql`
   
   **Sales Analytics:**
   - `mart_daily_sales.sql` - Daily aggregations
   - `mart_city_analytics.sql` - Geographic insights

**Evening (2 hours):**
5. Run dbt tests
   ```bash
   dbt test
   dbt docs generate
   dbt docs serve
   ```
6. Validate all models
7. Optimize queries

**Deliverables:**
- ✅ dbt project with 15+ models
- ✅ Tested and documented transformations
- ✅ Analytics tables ready for BI

---

### **DAY 3: Visualization & Insights** 📊

**Morning (4 hours):**

**Power BI Setup:**
1. Connect Power BI to Snowflake
2. Import analytics tables
3. Create relationships and measures

**Key Measures to Create:**
```dax
Total Revenue = SUM(orders[total])
Total Orders = COUNT(orders[order_id])
Avg Order Value = [Total Revenue] / [Total Orders]
Customer Count = DISTINCTCOUNT(orders[customer_id])
Revenue Growth = 
    DIVIDE(
        [Total Revenue] - CALCULATE([Total Revenue], DATEADD(dim_date[date], -1, YEAR)),
        CALCULATE([Total Revenue], DATEADD(dim_date[date], -1, YEAR))
    )
```

**Afternoon (4 hours):**

**Dashboard 1: Executive Overview** 📈
- KPI Cards: Revenue, Orders, AOV, Customers
- Revenue trend line (monthly)
- Revenue by category (bar chart)
- Top 10 products (table)
- Geographic sales map
- Order status breakdown (donut)

**Dashboard 2: Customer Analytics** 👥
- RFM Segments matrix
- Customer distribution by city
- CLV distribution histogram
- New vs Returning customers
- Customer age groups analysis
- Purchase frequency chart

**Dashboard 3: Product Performance** 📦
- Category performance table
- Profit margin by category
- Stock status alerts
- Product sales ranking
- Slow-moving inventory
- ABC analysis chart

**Dashboard 4: Marketing ROI** 📢
- Marketing spend vs revenue
- Channel performance comparison
- CAC by channel
- Conversion rates
- ROI calculation
- Campaign timeline

**Evening (2 hours):**
5. Add filters and slicers
6. Create drill-through pages
7. Format and polish dashboards
8. Export to PDF for presentation

**Deliverables:**
- ✅ 4 interactive Power BI dashboards
- ✅ PDF report
- ✅ Presentation-ready insights

---

## 🎨 Power BI Design Guidelines

### Color Palette (Egyptian Theme)
- Primary: `#C8A882` (Sand/Gold)
- Secondary: `#2C5F2D` (Nile Green)
- Accent: `#D4AF37` (Egyptian Gold)
- Background: `#F5F5F5` (Light Gray)
- Text: `#333333` (Dark Gray)

### Visual Hierarchy
1. KPI cards at the top
2. Main insight in center (largest visual)
3. Supporting details below/sides
4. Filters on left sidebar

### Best Practices
- Max 6-7 visuals per page
- Use consistent formatting
- Add tooltips with extra info
- Enable drill-through
- Mobile-responsive layout

---

## 📈 Key Metrics & KPIs

### Revenue Metrics
- **Total Revenue**: Sum of all completed orders
- **Revenue Growth**: MoM and YoY
- **Revenue by Category/City/Channel**
- **Average Order Value (AOV)**: Total Revenue / Orders

### Customer Metrics
- **Total Customers**: Unique customer count
- **New Customers**: First-time buyers this period
- **Customer Retention Rate**: % repeat customers
- **Customer Lifetime Value (CLV)**: Avg revenue per customer
- **Churn Rate**: % customers who stopped buying

### Product Metrics
- **Units Sold**: Total quantity sold
- **Revenue per Product**
- **Profit Margin**: (Price - Cost) / Price
- **Stock Turnover**: Sales / Avg Inventory
- **Out of Stock Rate**: % products with zero stock

### Marketing Metrics
- **Customer Acquisition Cost (CAC)**: Marketing Spend / New Customers
- **Return on Ad Spend (ROAS)**: Revenue / Ad Spend
- **Conversion Rate**: Orders / Clicks
- **Cost per Click (CPC)**: Spend / Clicks

### Operational Metrics
- **Order Fulfillment Rate**: Completed / Total Orders
- **Cancellation Rate**: Cancelled / Total Orders
- **Average Delivery Time**
- **Return Rate**: Returned / Completed Orders

---

## 🔢 SQL Queries You'll Write

### RFM Segmentation
```sql
WITH customer_rfm AS (
  SELECT 
    customer_id,
    DATEDIFF(day, MAX(order_date), CURRENT_DATE()) as recency,
    COUNT(DISTINCT order_id) as frequency,
    SUM(total) as monetary
  FROM orders
  WHERE status = 'Completed'
  GROUP BY customer_id
)
SELECT 
  customer_id,
  NTILE(5) OVER (ORDER BY recency DESC) as r_score,
  NTILE(5) OVER (ORDER BY frequency) as f_score,
  NTILE(5) OVER (ORDER BY monetary) as m_score,
  CASE 
    WHEN r_score >= 4 AND f_score >= 4 THEN 'Champions'
    WHEN r_score >= 4 AND f_score = 3 THEN 'Loyal Customers'
    WHEN r_score >= 3 AND f_score >= 3 THEN 'Potential Loyalists'
    WHEN r_score >= 4 AND f_score <= 2 THEN 'New Customers'
    WHEN r_score = 3 AND f_score <= 2 THEN 'Promising'
    WHEN r_score <= 2 AND f_score >= 4 THEN 'At Risk'
    WHEN r_score <= 2 AND f_score = 3 THEN 'Cannot Lose Them'
    ELSE 'Hibernating'
  END as segment
FROM customer_rfm;
```

### Product Performance
```sql
SELECT 
  p.category,
  p.product_name,
  COUNT(DISTINCT oi.order_id) as orders,
  SUM(oi.quantity) as units_sold,
  SUM(oi.total_price) as revenue,
  SUM((oi.unit_price - p.cost) * oi.quantity) as profit,
  ROUND(profit / revenue * 100, 2) as margin_pct,
  p.stock_quantity
FROM products p
JOIN order_items oi ON p.product_id = oi.product_id
JOIN orders o ON oi.order_id = o.order_id
WHERE o.status = 'Completed'
GROUP BY p.category, p.product_name, p.stock_quantity
ORDER BY revenue DESC;
```

### Marketing ROI
```sql
SELECT 
  m.channel,
  m.cost as marketing_spend,
  COUNT(DISTINCT o.order_id) as orders_generated,
  SUM(o.total) as revenue_generated,
  revenue_generated / marketing_spend as roas,
  marketing_spend / orders_generated as cac,
  (revenue_generated - marketing_spend) as net_profit
FROM marketing_campaigns m
LEFT JOIN orders o 
  ON m.channel = o.marketing_channel
  AND o.order_date BETWEEN m.start_date AND m.end_date
GROUP BY m.channel, m.cost
ORDER BY roas DESC;
```

---

## 📚 Technologies & Tools

### Required Software
- **Python 3.8+**: Data generation and ETL
- **Snowflake**: Cloud data warehouse (free trial)
- **dbt Core**: Data transformations
- **Power BI Desktop**: Visualization (free)
- **Git**: Version control
- **VS Code**: Development IDE

### Python Libraries
```bash
pip install pandas numpy snowflake-connector-python python-dotenv
```

### dbt Packages
```yaml
# packages.yml
packages:
  - package: dbt-labs/dbt_utils
    version: 1.1.1
```

---

## 📝 Project Structure

```
egyptian-ecommerce/
│
├── data/                          # Generated CSV files
│   ├── products.csv
│   ├── customers.csv
│   ├── orders.csv
│   ├── order_items.csv
│   └── marketing_campaigns.csv
│
├── scripts/                       # Python ETL scripts
│   ├── generate_data.py
│   ├── load_to_snowflake.py
│   └── utils.py
│
├── sql/                          # SQL scripts
│   ├── 01_snowflake_setup.sql
│   ├── 02_staging_views.sql
│   └── 03_analytics_tables.sql
│
├── dbt_ecommerce/               # dbt project
│   ├── models/
│   │   ├── staging/
│   │   │   ├── stg_orders.sql
│   │   │   ├── stg_customers.sql
│   │   │   └── stg_products.sql
│   │   ├── intermediate/
│   │   │   └── int_order_metrics.sql
│   │   └── marts/
│   │       ├── mart_customer_rfm.sql
│   │       ├── mart_product_performance.sql
│   │       ├── mart_marketing_roi.sql
│   │       └── mart_daily_sales.sql
│   ├── tests/
│   ├── macros/
│   ├── dbt_project.yml
│   └── profiles.yml
│
├── powerbi/                     # Power BI files
│   ├── egyptian_ecommerce.pbix
│   └── report.pdf
│
├── docs/                        # Documentation
│   ├── data_dictionary.md
│   ├── business_glossary.md
│   └── insights_summary.md
│
├── .env                         # Environment variables
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🎓 Learning Outcomes

By completing this project, you will learn:

### Data Engineering
✅ Design dimensional data models (star schema)
✅ Build ETL pipelines with Python
✅ Implement data quality checks
✅ Use Snowflake for cloud data warehousing
✅ Apply dbt for transformation workflows

### Analytics Engineering
✅ Create staging, intermediate, and mart layers
✅ Write complex SQL for business logic
✅ Implement RFM segmentation
✅ Calculate CLV and retention metrics
✅ Build reusable dbt models

### Business Intelligence
✅ Connect BI tools to cloud warehouses
✅ Create executive dashboards
✅ Design effective visualizations
✅ Tell stories with data
✅ Present insights to stakeholders

### Best Practices
✅ Version control with Git
✅ Documentation and data dictionaries
✅ Code modularity and reusability
✅ Performance optimization
✅ Testing and validation

---

## 🚀 Getting Started Checklist

### Before You Start:
- [ ] Install Python 3.8+
- [ ] Install VS Code or preferred IDE
- [ ] Create Snowflake free trial account
- [ ] Install Power BI Desktop
- [ ] Install Git
- [ ] Set up GitHub repository

### Day 1 Tasks:
- [ ] Run data generation script
- [ ] Create Snowflake database and schema
- [ ] Load data into Snowflake
- [ ] Verify row counts
- [ ] Create staging views
- [ ] Commit code to Git

### Day 2 Tasks:
- [ ] Initialize dbt project
- [ ] Create staging models
- [ ] Create intermediate models
- [ ] Create mart models
- [ ] Run dbt tests
- [ ] Generate dbt docs

### Day 3 Tasks:
- [ ] Connect Power BI to Snowflake
- [ ] Create data model
- [ ] Build 4 dashboards
- [ ] Add filters and interactivity
- [ ] Document insights
- [ ] Export final report

---

## 💡 Pro Tips

1. **Start Simple**: Get basic pipeline working first, then add complexity
2. **Test Frequently**: Validate data at every step
3. **Document Everything**: Future you will thank present you
4. **Use Git**: Commit after each major milestone
5. **Focus on Insights**: Pretty dashboards mean nothing without business value
6. **Optimize Later**: Get it working, then make it fast
7. **Ask Questions**: What story does the data tell?
8. **Be Realistic**: 3 days is tight - prioritize must-haves

---

## 🎯 Success Criteria

Your project is successful if you have:

✅ **Working Data Pipeline**
- Data flows from CSV → Snowflake → dbt → Power BI
- All transformations run without errors
- Data quality is validated

✅ **Business Value**
- Dashboards answer real business questions
- Insights are actionable
- Metrics are accurate and meaningful

✅ **Technical Quality**
- Code is organized and documented
- SQL is optimized
- Models follow best practices

✅ **Presentation Ready**
- Professional-looking dashboards
- Clear narrative and insights
- Portfolio-worthy final product

---

## 📞 Support & Resources

### Documentation
- [Snowflake Docs](https://docs.snowflake.com/)
- [dbt Docs](https://docs.getdbt.com/)
- [Power BI Docs](https://docs.microsoft.com/power-bi/)

### Tutorials
- dbt Learn: https://courses.getdbt.com/
- Snowflake Quickstarts: https://quickstarts.snowflake.com/

### Community
- dbt Slack: https://www.getdbt.com/community/
- r/dataengineering
- r/BusinessIntelligence

---

## 🎉 Let's Build This!

You have all the tools and knowledge needed. Now it's time to execute!

**Start with Day 1 tasks and work systematically through each step.**

**Remember: Done is better than perfect. Ship it! 🚢**

---

**Good luck! You've got this! 💪**
