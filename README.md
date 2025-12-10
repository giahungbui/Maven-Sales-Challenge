# CRM Sales Dashboard
## Business Scenario

MavenTech is a U.S.-based company specialising in enterprise hardware solutions. The company recently implemented a new CRM platform to manage sales opportunities, but leadership faced a critical challenge:

Although large volumes of sales data were being collected, managers had limited visibility into:
- Quarterly performance trends  
- Individual sales effectiveness  
- Product contribution  
- Team-level performance comparisons  

As a Business Intelligence Developer, I designed an **interactive Power BI dashboard system** that enables managers to analyse sales performance at three levels:

- Individual sales representatives  
- Products, industries, and customers  
- Sales teams (strategic comparison)

This solution transforms raw CRM data into actionable management insights.

### Assumptions

- Sales managers require both individual and team-level performance monitoring.  
- Teams are allowed to compare performance across the business.  
- Quarterly performance tracking is essential for:
  - Target evaluation  
  - End-of-quarter sales pushes  
- Dashboards must be easy to interpret, supported with tooltips and intuitive visuals.

## Objective
The main objective is to create an interactive dashboard that sales managers can use to answer the following questions:

- How is the overall team and each individual performing against our main KPIs?
- Are there any team members who may need additional support in specific areas?
- Is my team outperforming the business-wide average?
- How does the team’s performance compare to the overall company average?
- What are the quarter-over-quarter sales trends for each team?
- How is each salesperson currently performing?
- Which products are generating the highest sales?
  

## Dataset

This dataset, available on Maven Analytics, contains B2B sales opportunities from a CRM database for a fictitious company, MavenTech, which sells computer hardware to large businesses. The dataset includes information on:

- accounts: Account details of clients including company name, industry, year established, number of employees, annual revenue,location, and parent company.
- products: Details of products offered including product name, series, and sale price.
- sales_pipeline: Records of sales opportunities with details including sales agent, product name, company name, sales pipeline stage, date of first engagement, date of closing a deal, and revenue.
- sales_teams: Details of each sales agent including name, name of manager, and regional office.
  
The dataset covers the period from October 2016 to December 2017 and supports detailed analysis of revenue performance, pipeline health, individual productivity, product effectiveness, sector profitability, and team-level comparisons.

### Data Preparation

The data model was relatively clean; however, several important preprocessing steps were required to ensure accuracy and analytical reliability:
- In the sales pipeline table, the product name "GTXPro" was standardized to "GTX Pro" to match the products table. This was handled using Find & Replace in Power Query.
- A merge between the sales pipeline and products table was performed using the product column to enable correct product revenue analysis.
- The sales teams table was merged with the sales pipeline using the sales_agent field to integrate manager-level insights.
- The accounts table was merged with sales pipeline using the account field to enable sector and customer analysis.
- A dedicated Date Table was created to support:
  - Quarter filtering
  - Quarter-over-quarter (QoQ) analysis
  - Trend visualisation

---
### 1. Quarterly Performance Overview

This page enables team managers to efficiently monitor overall team performance alongside the results of individual sales agents. It provides a high-level performance snapshot for the selected quarter.

Key visuals include:

- **KPI Cards**
  - Total Sales (current quarter, previous quarter, company average)
  - Average Deal Value (current quarter, previous quarter, company average)
  - Won Deals (current quarter, previous quarter, conversion rate)
  - Average Weeks to Close (current quarter, previous quarter, company average)
  - Engaging Deals (current quarter, potential value)

- **Total Sales Trend Line**
  - Displays total revenue performance by quarter to highlight growth patterns

- **Sales Opportunities Funnel**
  - Visualizes deal distribution across pipeline stages for the selected quarter

- **Performance by Agents Table**
  - Total Sales  
  - Won Deals  
  - Conversion Rate  
  - Average Deal Value  
  - Average Weeks to Close  

This page allows managers to quickly benchmark individuals against team and company performance.

---

### 2. Engaging Sales Opportunities

This page provides a detailed table of currently engaging opportunities. It allows managers to:

- Review active deals in progress
- Identify high-potential revenue opportunities
- Filter opportunities by sales agent and quarter
- Support short-term revenue forecasting

---

### 3. Sales by Region

This page tracks sales performance across geography, industry, and product categories to help identify market trends and revenue drivers.

Key visuals include:

- Choropleth map of total sales by location
- Sales by industry
- Top 5 customer accounts by total sales
- Sales and conversion rate by product

This page supports strategic market and product performance analysis.

---

### 4. Performance by Teams

This page allows managers to track their team’s performance relative to other teams by quarter.

Key metrics include:

- Total Sales
- Number of Won Deals
- Conversion Rate
- Average Deal Value
- Average Weeks to Close

This page supports internal benchmarking and helps highlight high-performing and underperforming teams.
