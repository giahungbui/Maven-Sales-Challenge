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

---
## Data Preparation

The data model was relatively clean; however, several important preprocessing steps were required to ensure accuracy and analytical reliability:

- The product name **"GTXPro"** in the `sales_pipeline` table was standardized to **"GTX Pro"** to match the naming convention in the `products` table. This was handled using **Find & Replace in Power Query**.
- Since five sales agents are missing from the sales pipeline table and there's no data to clarify this, it's presumed they are new hires who haven't yet begun to prospect opportunities.
- Engaging deals without close dates were properly handled to prevent incorrect quarter assignments.
- The missing values within the dataset are expected occurrences and should be retained in their current state.


### Calculated Fields & Measures

The following calculated fields and measures were created using **DAX** to support the dashboards:

- Total Sales, Last Quarter Sales, Company Average Sales
- Won Deals, Last Quarter Won Deals
- Conversion Rate
- Average Sales Value, Last Quarter Average Sales Value, Company Average Sales Value
- Weeks to Close, Last Quarter Weeks to Close, Company Weeks to Close
- Engaging Deals, Proposing Deals, Lost Deals
- Potential Sales from Engaging Deals

---
## Data Modeling
A dedicated **Date Table** was created to serve as the central time dimension for the entire model. This enables:
- Quarter-based filtering
- Quarter-over-Quarter (QoQ) comparisons
- Year-over-Year and trend analysis
- Consistent time-based KPI calculations across all dashboards

The Date Table drives all official time intelligence calculations using **close_date** as the primary reference.


To construct a unified analytical fact table, the following merges were performed:

- The `sales_pipeline` table was merged with the `products` table using the **product** field to enable product-level revenue and conversion analysis.
- The `sales_teams` table was merged with `sales_pipeline` through the **sales_agent** field to integrate manager and team-level insights.
- The `accounts` table was merged with `sales_pipeline` using the **account** field to support sector and customer-based performance analysis.

The resulting data model looks like this:
![Data Modeling](Data Modeling.png)

--- 
## Dashboard Planning

Since the dashboard is designed for sales managers, usability is treated as the highest priority. The dashboard is optimized for:

- Minimal training requirements
- Clear and intuitive KPI presentation
- Simple and consistent navigation
- Strong visual hierarchy for quick interpretation

The report is structured into four main pages, each serving a specific analytical purpose.

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
