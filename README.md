# BI SSAS Lab: Harnessing Data Insights with Microsoft Analysis Services

Welcome to the BI SSAS Lab repository, where I demonstrate proficiency in SQL Server Analysis Services (SSAS) by tackling various Multidimensional Expressions (MDX) queries. Throughout this lab, I've delved into the intricacies of SSAS, crafting cubes, dimensions, and MDX queries to extract meaningful insights from sales data.

## Purpose and Benefits
By completing this lab, I have strengthened my proficiency in BI SSAS techniques and enhanced my ability to extract actionable insights from complex datasets. This project not only showcases my technical skills but also demonstrates my capability to derive valuable business intelligence from raw data. 

## Overview: Cubes, Dimensions, and Facts

### Cubes
Cubes organize data into manageable chunks for multidimensional analysis. They allow slicing, dicing, and analysis from different perspectives, such as product, customer, time, and channel.

### Dimensions
Dimensions provide context to data within cubes, representing categories for analysis. Examples include products, customers, and sales man, channels, and time. Dimensions help organize and filter data for deeper insights.

### Facts
Facts are measurable data points within cubes, representing numerical values like sales quantity and cost. Each fact is associated with specific dimensions, enabling multidimensional analysis and uncovering insights into performance and trends.

By combining cubes, dimensions, and facts, we can perform comprehensive analyses of our data, uncovering valuable insights that drive informed decision-making and business growth.

## Lab Details

### Setup
- Created SSAS project in Visual Studio Code.
- Configured data source and designed cubes ("sales", "product", "product_customer")  and dimensions in a Star Schema model.
  <div style="display:flex;">
    <img src="https://github.com/sarax0/SSAS-MDX-Sales-Data/assets/122404545/e90f3832-5203-435b-ad8a-51186cf44c95" alt="Data Source View" style="height:30%;">
    <img src="https://github.com/sarax0/SSAS-MDX-Sales-Data/assets/122404545/bd727ace-231e-4467-bb00-6f2692402cd3" alt="Sales Cube" style="height:30%;">
  </div>

### MDX Query Solutions
I successfully answered a series of queries using MDX to analyze the sales cube:

1. Displayed Sales Quantity measure.
   ```
    SELECT 
    [Measures].[Qty] ON 0
    FROM 
    [Sales Cube]
   ```
   ![image](https://github.com/sarax0/SSAS-MDX-Sales-Data/assets/122404545/dd1ec760-3685-4a79-b9d0-3bde95a18ab5)
   
2. Displayed Sales Quantity and Quantity Total Price measures.
   ```
    SELECT 
    {
      [Measures].[Qty],
      [Measures].[Qty Total Price]
    } ON 0
    FROM [Sales Cube]
   ```   
3. Displayed all measures in the sales cube.
   ```
    SELECT [Measures].AllMembers ON 0
    FROM [Sales Cube]
   ```
4. Displayed Quantity per Customer with Total Quantity.
   ```
     SELECT 
    [Measures].[Qty] ON 0,
    [Customer Dim].[Customer Name].MEMBERS ON 1
    FROM 
    [Sales Cube]
   ```

5. Displayed Quantity per Customer without Total Quantity.
   ```
    SELECT 
    [Measures].[Qty] ON 0,
    [Customer Dim].[Customer Name].CHILDREN ON 1
    FROM 
    [Sales Cube]
   ```
6. Displayed Quantity and Number of orders per Customer in Year (2007).
   ```
    SELECT
    	[Measures].[Qty] ON 0,
    	NON EMPTY
    	(
    		[Customer Dim].[Customer Name].CHILDREN,
    		[Time Dim].[Calendar Year].&[2007]
    	)
    	ON 1
    FROM 
    	[Prod_Cust Cube]
   ```
7. Displayed Quantity per year for Customer 1.
8. Displayed Quantity per customer for each product.
9. Displayed Quantity per customer for each product in each year.
10. Displayed Quantity of products bought by Customer 1 from Product 1 in 2007.
11. Displayed the number of Customers in Egypt.
12. Displayed Quantity per year for each channel.


## Conclusion

This repository stands as a testament to my proficiency in BI SSAS and MDX querying. Dive into the provided MDX queries to witness real-world problem-solving and the transformative potential of data analytics. Whether you're a seasoned BI professional or a newcomer, explore, learn, and leverage the power of SSAS for data-driven decision-making.

