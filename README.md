# LITA_CAPSTONE_PROJECT-SALES_DATA-

### OUTLINE
[ PROJECT OVERVIEW: ](#project-overview)

[ DATA DESCRIPTION: ](#data-description)

[ DASH BOARD REVIEW: ](#dash-board-review)

[ STATISTICS ABOUT THE DATASET: ](statistics-about-the-dataset)

[ METHODOLOGY: ](methodology)

[ DATA ANALYSIS: ](data-analysis)

[ DASH BOARD OVERVIEW WITH POWER BI: ](dash-board-review-with-powerbi)

[ INSIGHTS GENERATION: ](insights-generation)


[ RECOMMENDATION: ](recommendation)


[ CONCLUSION: ](conclusion)



### PROJECT OVERVIEW:
---
Making reference to the data and capstone project document shared earlier, by analyzing the sales performance of a retail store and carrying out the following exploratory process of the sales data to uncover key insights such as
- Top Selling Products
- Regional Performances
- Monthly Sales Trend and
By telling a compelling story and building an interactive dashboard Power Bi report: **To gather insight, Highlight findings And making business decisions.**

### DATA DESCRIPTION:
---
This dataset includes the following Columns:
- Order Number
- Customer Id
- products
- region
- Order Date
- Quantity
- Unit Price
  
### DASH BOARD REVIEW:
---
- Customer Id
- products: Items sold in the store
- region: The other regional branches of the store ( North, South, East West) 
- Order Date: Date order was palced
- Quantity: The number of units of the product ordered in each transaction
- Unit Price: The aquisition cost per unit of the product

### STATISTICS ABOUT THE DATASET:
---
Number of Unique Customers: 50,000
Number of Products: 6
Total Sales: 10587500 ![image](https://github.com/user-attachments/assets/e260abe1-8773-4574-ac85-2f3f97b30e34)
Total Region: 4 


### METHODOLOGY:
---

#### Data Collection
The dataset for this analysis was provided by LITA_ The Incubator Hub for leaening and training purposes. The data was provided in Excel sheet [download Here] (https://canvas.instructure.com/files/273182802/download?download_frd=1) or https://eu.docworkspace.com/d/sILre1-uDAsKJzrgG?sa=wa&ps=1&fn=LITA%20Capstone%20Dataset%20(1).xlsx
 The excel sheet making it accessible to 
- analyse the excel sheet
  The excel sheet was further converted to CSV format for easy importing of files into:
  - SQL to write various queries
  - Power BI to create dashboards using various charts (pieChart and clustered Column Chart)


### DATA ANALYSIS:
---

#### Calculation in Excel 
- *Generating Total Sales* ```(=F2* G2)``` ![Capture total sales as revenue](https://github.com/user-attachments/assets/a230d6b0-fd45-426d-8c78-e1da9e9b53cf)

- *calculating average sales by product* 
``` =AVERAGEIF($C1:$C50001,$C2,$H1:$H50001)```
 ![Capture sales data average by product](https://github.com/user-attachments/assets/288b1f45-dfc4-46a9-8b70-92f3db897fe9)

- *calculating total revenue by region
``` ==SUMIF($D1:$D50001,$D12630,$H1:$H50001)```
![Capture total revenue by region sales data](https://github.com/user-attachments/assets/13c7134e-d9b1-48e9-8ad2-7642f83a542a)

#### Excel Chart
![my project capstone chart1](https://github.com/user-attachments/assets/d7ed65cf-2221-41e6-b382-8697adcf8f9b)

![my project capstone chart2](https://github.com/user-attachments/assets/f7a767c5-d757-41aa-93b8-33025e62cd93)

    
#### Pivot Table 
 
  ![Capturesales new pivot table](https://github.com/user-attachments/assets/ee087769-ac31-4711-ba6f-a1d4c37f4457)

#### Queries in SQL
- SQL
  1. ```Select product,
     sum(quantity*unitprice) as totalsale
     From [dbo] Group by product;
  2. ```Select region,
     count(*) as NumberOfTransactions
     From [dbo] Group by region;
  3. ```select top 1 product,
     sum(quantity*unitprice) as totalsales
     From [dbo]
     Group by product
     Order by totalsales desc;
  4. ```Select month(OrderDate) as month,
     sum(quantity*unitprice) as MonthlySales
     From [dbo]
     Where year(OrderDate) = year(GetDate())
     Group by month(OrderDate)
     Order by month;
  5. ```Select top 5 customer_id,
     sum(quantity*unitprice) as totalpurchaseAmount
     From [dbo]
     Group by customer_id
     Order by TotalPurchaseAmount desc;
  6. ```Select region,
     sum(quantity*unitprice) as totalsales,
     Sum(quantity*unitprice) * 1.0/ (select sum(quantity*unitprice)
     From [dbo] * 100
     As PercentageOfTotalSales
     From [dbo]
     Group by region;
  7. ```WITH QUANTITY AS (
     SELECT SUM(quantity * UnitPrice) AS 
     TotalSalesAmount
     FROM [dbo].['LITA Capstone project$']
     )
     SELECT REGION, SUM(quantity * UnitPrice) AS RegionSales,
     (SUM(quantity * UnitPrice) * 100.0)/ts.TotalSalesAmount AS PercentageContribution
     FROM [dbo].['LITA Capstone project$']
     CROSS JOIN QUANTITY ts
     GROUP BY Region,
     ts.TotalSalesAmount;
  8. ```Select distinct product
     From [dbo]
     Where product Not In(
     Select product
     From [dbo]
     Where OrderDate >= DateAdd(quarter, -1, GetDate()) and OrderDate < GetDate());
![Capturesales data sql1](https://github.com/user-attachments/assets/dd6ae0c6-94f4-435a-a29f-529866bac3e8)

![Capturesales data sql2](https://github.com/user-attachments/assets/d3efed3a-8a25-4cdd-95e8-f279e970a7dd)

![Capturesales data sql3](https://github.com/user-attachments/assets/c9dbfe7d-d8ed-4c51-bddc-4437b613f40a)



### DASH BOARD OVERVIEW WITH POWER BI:
---
![image](https://github.com/user-attachments/assets/83b20752-08f5-48a7-a528-7f576f047632)

### INSIGHTS GENERATION:
- - -

#### Insights on Total Sales (Revenue) In The Different Regions
- South Region: Leads in Total sales and generates more revenue with 4,675,000  which indicates a potentially larger transaction values per sale.
- East Region: Close behind is the East region with total sales of 2,450,000  which is about 23.14% of the total Sales. This indicates a competitive market with a strong transaction 
- North Region: Shows great performance with 1,950,000 in sales and 18.42% of Total Sales (Revenue), showing consistent customer interest in the retail shop and the items stocked in it 
- West Region: Shows equally a good market as it is actively competitive with the Northern market with a close range performance of 1,512,500 and 14.29% of the total revenue. indicating steady purchasing activity.

#### Insights on the total revenue generated by each product
- Shoes: Leads in Total sales and generates more revenue with 3,087,500  which indicates a potentially higher priced item or larger quantity of the item sold.
- Shirt: Close behind is shirt  with total sales of 2,450,000  which is about 23.14% of the total Sales. This indicates a competitive market and categorised as the second best  purchased product

**Chart Display**
![my project capstone chart2](https://github.com/user-attachments/assets/f7a767c5-d757-41aa-93b8-33025e62cd93)

### RECOMMENDATION:
---
**Region Comparison:** Implement targeted marketing strategies, campaign or advert to create more awareness in the North and West region especially so as to curate more sales and generate more revenue

**Sales Optimization:** Make most effective use of the market trend by stocking more items with lead revenue generating power which are (Shoes and Shirts)

### CONCLUSION:
---
The retail shops in the North ancd west region needs more focus and attention on 
- boosting revenue through marketing strategies
- studying of market trend within the region to adequately decode the hihgest selling product in the region, so as to stock more. 

