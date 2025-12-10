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
## Dashboard Planning

Since the dashboard is designed for sales managers, usability was the top priority. The dashboard is optimized for:

- Minimal training requirements
- Clear KPI presentation
- Simple navigation
- Strong visual hierarchy

The report is structured into four main pages, each with a specific analytical purpose.

### 1. Quarterly Performance Overview
Team managers can use this page to efficiently monitor overall team performance alongside the individual results of each sales agent. The page will display these metrics using the following visuals:
- KPI Cards:
  - Total Sales (current quarter, previous quarter, company average)
  - Average Deal Value (current quarter, previous quarter, company average)
  - Won Deals (current quarter, previous quarter, conversion rate)
  - Average Weeks to Close (current quarter, previous quarter, company average)
  - Engaging Deals (current quarter, potential value)
- Total sales trend line by quarter for...
- Sales Opportunities funnel by quarter for ... 
- Performance by Agents table:
  - Total sales
  - Wins
  - Conversion rate
  - Average sale value
  - Weeks to close

### 2. Sales opportunities - provides a detailed table of currently engaging opportunities. This enables managers to identify potential sales.

### 3. 
