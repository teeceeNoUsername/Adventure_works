# Manufacture Sales Analysis


### The Brief
---
**Track KPIs** (sales, revenue, profit, returns), **compare regional performance, analyze product-level trends and forecasts**, and identify **high-value customers**

### Date Sources
A folder of raw csv files, containing information about transactions,returns, products, customers and territories.

### Tools
  - PowerBI

### The Objective
  - Transformation of the raw data
  - Build a relational data model
  - Create new calculated columns and DAX measures
  - Design an interactive report to analyze and visualize the data

### Transformation of the raw data
1. I created new queries to connect to the AdventureWorks_Product_Categories and AdventureWorks_Product_Subcategories 

  - Name your queries AW_Product_Category_Lookup and AW_Product_Subcategory_Lookup 
  - Confirm that headers have been promoted and that detected data types are correct 

 2. I made the following modifications to the AW_Product_Lookup query:

  - Add a calculated column that extracts all characters before the dash ("-") in the ProductSKU column, named "SKUType" 
  - Update the SKUType calculation above to return all characters before second dash, instead of the first 
  - Replace zeros (0) in the ProductStyle column with "NA" 
  - Update the DiscountPrice calculation to 15%, by multiplying the ProductPrice values by 0.85 (instead of 0.9) 
   
3. Using the Statistics tools in the Query Editor, confirm the following values:

  - Average product cost (£413.66) 
  - Number of distinct product colors (10) 
  - Number of distinct customer names (18,110) 
  - Maximum annual customer income (£170,000) 
  - Count of order numbers (56,046)
  - Count of distinct order numbers (25,164) 

4. Make the following modifications to the AW_Customer_Lookup query:

  - Added a new calculated column for the year of birth (named "BirthYear"), based on BirthDate 
  - Added a conditional column to categorize customer income (named "IncomeLevel"), based on the following criteria 
      - If AnnualIncome >= $150,000, then IncomeLevel = "Very High"
      - If AnnualIncome >= $100,000, then IncomeLevel = "High"
      - If AnnualIncome >= $50,000, then IncomeLevel = "Average"
      - Otherwise IncomeLevel = "Low"
   
  ### Build a relational data model
- I created all table relationships;

- Cardinality is 1-to-Many for all relationships 
- Filtered are all One-Way (no two-way filters) 
- Filtered direction correctly flows "downstream" to data tables
- Product-related tables follow a snowflake schema
![Screenshot 2024-04-26 022452](https://github.com/teeceeNoUsername/Adventure_works/assets/64446759/cd653193-685f-4f12-8aa3-8e351791ed33)

###  DAX measures
Created a measure named "Product Models" to calculate the number of unique product model names

- Spot check: A total of 119 unique product models

Created a measure named "ALL Returns" to calculate the grand total number of returns, regardless of the filter context 

- Spot check: A total of 1,809 returns

Created a measure to calculate "% of All Returns" 

- Spot check: A value of 61.64% for the Accessories product category

Created a measure named "Bike Returns" to calculate total returns for bikes specifically 

- Spot check: You should see a total of 427 bike returns

Created a measure named "Total Cost", by multiplying order quantities by product costs at the row-level

- Spot check: You should see a total cost of £14,456,986.32

Once you've calculated Total Cost, create a new measure for "Total Profit", defined as the total revenue minus the total cost 

- Spot check: You should see a total profit of £10,457,580.86

Create a measure to calculate Total Orders for the previous month (named "Prev Month Orders") 

- Spot check: Create a matrix with "Start of Month" on rows to confirm accuracy

Create a measure named "Order Target", calculated as a 10% lift over the previous month 

- Spot check: Create a matrix with "Start of Month" on rows to confirm accuracy

Total Returns for the previous month (named "Prev Month Returns")

- Spot check: Create a matrix with "Start of Month" on rows to confirm accuracy

90-Day Rolling Profit (named "90-day Rolling Profit") 

- Spot check: You should see a 90-day rolling profit of £2,142,623.27


### Vizualization of the data
![Screenshot 2024-04-26 023852](https://github.com/teeceeNoUsername/Adventure_works/assets/64446759/cd6032cf-c1a8-4aab-b9a2-34c48a2b5fec)

![Screenshot 2024-04-26 023835](https://github.com/teeceeNoUsername/Adventure_works/assets/64446759/f98c78f8-fcc7-4b49-9366-fb91be10c448)

![Screenshot 2024-04-26 023756](https://github.com/teeceeNoUsername/Adventure_works/assets/64446759/be5621df-df8b-4459-ac86-50b18e3aaaff)

### Results/Findings
The analysis result are summarized as follows:
1. The company sales have been steadily increasing over the past year,with a noticeable peak during the latter years
2. Accessories Product Category is the best-performing in terms of sales and revenue

### Recommendations

- Interest in marketing and promotion durng peak sales to maximize revenue
- Focus on expanding and promoting Clothing Products Category

### Refernces
- Maven Analytics
- [Youtube](http://youtube.com)

