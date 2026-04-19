<h1 align="center">Ecommerce Sales Analysis - Excel & Looker Studio</h1>

<p align="center">
  <img width="1319" height="989" alt="Screenshot 2026-04-17 122509" src="https://github.com/user-attachments/assets/b7855d94-345b-40b1-a3fd-e0a9b3830638" />
</p>

*Gervon Alcide*


An end-to-end data analysis project on a public ecommerce dataset. 
I cleaned and structured the raw data in Excel, performed exploratory 
analysis using pivot tables, extracted business insights, and built an 
interactive sales dashboard in Looker Studio.

## Setup
**Tools:** Microsoft Excel, Google Sheets, Google Looker Studio  
**Dataset:** [Online Sales Dataset — Kaggle](https://www.kaggle.com/datasets/shreyanshverma27/online-sales-dataset-popular-marketplace-data)  
**Records:** 240 rows, 8 columns  
**Live Dashboard:** [View Interactive Dashboard](https://datastudio.google.com/s/rcDzUJurFyI)  
**Excel File:** [Online Sales Data.xlsx](https://github.com/user-attachments/files/26870066/Online.Sales.Data.xlsx)


---

## Data Cleaning

<img width="667" height="634" alt="Screenshot 2026-04-16 193628" src="https://github.com/user-attachments/assets/d563be40-7507-4fbc-a88e-0a133507d835" />
<br>

### Steps for cleaning
- Named and stored the file appropriately with a backup of the original data
- Converted raw data into a structured Excel table (240 rows)
- Formatted `Unit Price` and `Total Revenue` columns as currency
- Replaced static `Total Revenue` values with a formula (`Unit Price × Units Sold`) to handle future entries automatically
- Applied data validation to the following columns:
  - `Units Sold`: whole numbers only
  - `Unit Price` and `Total Revenue`: decimals only
  - `Transaction ID`: whole number with warning for values outside the standard 5-digit range
  - `Product Category`, `Region` and `Payment Method`: dropdown lists that automatically incorporate new values
- Checked for and confirmed zero duplicate rows
- Verified date integrity with the formula below:

```excel
=COUNTIF(Date,"<"&DATE(2020,1,1))+COUNTIF(Date,">"&DATE(2027,1,1))
```
Returned 0, confirming no unrealistic dates.
<br>

<img width="1368" height="666" alt="Screenshot 2026-04-16 210440" src="https://github.com/user-attachments/assets/46481a2f-1d0d-4c98-9414-c2db21cf97f6" />

---

## Analysis

Added a `Cumulative Revenue` column to track running total revenue across all transactions

5 pivot tables with accompanying charts to explore the data from multiple angles:
1. Revenue by Product Category
2. Units Sold by Product Category
3. Revenue by Region
4. Revenue by Payment Method
5. Monthly Revenue & Cumulative Revenue
<br>
<img width="971" height="645" alt="Screenshot 2026-04-16 212432" src="https://github.com/user-attachments/assets/9dcbd3ab-713e-4157-9981-48d4368a7330" />
<img width="787" height="667" alt="Screenshot 2026-04-16 212635" src="https://github.com/user-attachments/assets/7befd7e1-8284-4ce8-8138-bed7e951c70e" />
<img width="1438" height="501" alt="Screenshot 2026-04-16 212500" src="https://github.com/user-attachments/assets/e89f5468-ad34-4a09-8e4e-40367daab4dc" />

---

## Insights
1. Revenue declined consistently month over month, peaking in January and bottoming in July.
2. Decline in total revenue per month is most stark in Jan-Feb and Apr-May; with Feb and May making ~4k less than Jan and Apr respectively.
3. High volume product categories are not necessarily high revenue. Electronics made the most revenue (35k) while selling the 3rd least (66 units), while Clothing sold the most units (145) but was 3rd least in revenue ($8k).
5. Books were the second most sold category but generated the least revenue.
6. North America drove the highest regional revenue; Europe slightly lower than Asia.
7. Credit Cards accounted for the majority of revenue (60%); Debit Cards were by far the lowest.

---

## Dashboard

I imported the cleaned dataset into Looker Studio and built an interactive dashboard with 5 visuals and 5 filter controls.
<br>

<p align="center">
  <img width="1319" height="989" alt="Screenshot 2026-04-17 122509" src="https://github.com/user-attachments/assets/b7855d94-345b-40b1-a3fd-e0a9b3830638" />
</p>
<br>

**Visuals**:
- Time series combo chart showing weekly revenue and cumulative revenue over time
- Revenue by Product Category bar graph
- Units Sold by Product Category bar graph
- Revenue by Payment Method bar graph
- Revenue by Region Donut chart

**Interactive Controls**:
- Product Category filter
- Region filter
- Payment Method filter
-  Month filter
-  Week filter


**[→ View Live Interactive Dashboard](https://datastudio.google.com/s/rcDzUJurFyI)**
