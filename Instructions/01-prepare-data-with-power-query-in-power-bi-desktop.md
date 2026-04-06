# Lab 01: Get data in Power BI

## Lab scenario 

This lab is designed to introduce you to Power BI Desktop application and how to connect to data and how to use data preview techniques to understand the characteristics and quality of the source data.

In this lab, you learn how to:

- Open Power BI Desktop.
- Connect to different data sources.
- Preview source data with Power Query.
- Use data profiling features in Power Query.

## Lab objectives

In this lab, you will perform:

- Set Power BI Desktop options
- Connect and preview to source data
- Use data preview techniques to better understand the data

## Estimated timing: 60 minutes    

## Architecture Diagram

![Picture 1](Linked_image_Files/Mod1-PL300.png)
   
## Exercise 1: Prepare Data

In this exercise you will create eight Power BI Desktop queries. Six queries will source data from SQL Server, and two from CSV files.

### Task 1: Get started with Power BI Desktop

In this task, you start by opening a starter Power BI file (.pbix). The starter file doesn't contain any data, but has been specially configured to help you complete the lab. The following report-level settings have been disabled in the starter file:

### Open the Starter Power BI File

To begin the exercise, follow these steps:

1. Open **File Explorer** on your machine.

2. Navigate to the following path:

   ```
   C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-Main\Allfiles\Labs\01-get-data-in-power-bi
   ```
3. Locate the file named: **01-Starter-Sales Analysis.pbix**

	![Picture 19](images/pl3n1.png)
	
4. Double-click the file to open it in **Power BI Desktop**.

   > **Note:** This starter file has been specially configured to help you complete the lab. The following report-level settings have been disabled in the starter file:

   - Data Load > Import relationships from data sources on first load
   - Data Load > Autodetect new relationships after data is loaded

### Task 2: Get data from SQL Server

In this task you will create queries based on SQL Server tables.

1. On the **Home** ribbon tab, from inside the **Data** group, click **SQL Server**.

	![Picture 19](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(11).png)

2. In the **SQL Server Database** window, in the **Server** box, enter **localhost**.

	![Picture 21](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(12).png)

	> **Note**: In this lab you’ll connect to the SQL Server database by using **localhost**. This isn’t a recommended practice when creating your own solutions. It’s because gateway data sources cannot resolve **localhost**.

3. Click **OK**.

	![Picture 22](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(13).png)

4. If prompted for credentials, in the **SQL Server Database** window, select **Windows > Use my current credentials**, and then **Connect**.

	>**Note**: Select **OK** if encrypted connection warning appears

5. In the **Navigator** window, at the left, expand the **AdventureWorksDW2020** database.

	> **Note**: The **AdventureWorksDW2020** database is based on the **AdventureWorksDW2017** sample database. It has been modified to support the learning objectives of the course labs.

	![Picture 28](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(17).png)

6. Select—but don’t check—the **DimEmployee** table.

	![Picture 29](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(18).png)

7. In the right pane, notice a preview of the table data.

	> **Note**: The preview data allows you to determine the columns and a sample of rows.

8. To create queries, select the checkbox next to the following six tables:

	- DimEmployee

	- DimEmployeeSalesTerritory

	- DimProduct

	- DimReseller

	- DimSalesTerritory

	- FactResellerSales

9. To apply transformations to the data of the selected tables, click **Transform Data**.

	>**Note**: You won’t be transforming the data in this lab. The objectives of this lab focus on exploring and profiling the data in the **Power Query Editor** window.

	![Picture 30](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(19).png)

### Task 3: Preview Data in Power Query Editor

In this task you will preview the data of the SQL Server queries. First, you will learn relevant information about the data. You will also use column quality, column distribution, and column profile tools to understand the data and to assess data quality.

1. In the **Power Query Editor** window, at the left, notice the **Queries** pane.

	![Picture 31](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(20).png)

	> **Note**: The **Queries** pane contains one query for each table you checked.

2. Select the first query—**DimEmployee**.

	![Picture 33](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(21).png)

	> **Note**: The **DimEmployee** table in the SQL Server database stores one row for each employee. A subset of the rows from this table represents the salespeople, which will be relevant to the model you’ll develop.

3. At the bottom left, in the status bar, notice the table statistics—the table has 33 columns, and 296 rows.

	![Picture 36](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(22).png)

4. In the data preview pane, scroll horizontally to review all columns.

5. Notice that the last five columns contain **Table** or **Value** links.

 	> **Note**: These five columns represent relationships to other tables in the database. They can be used to join tables together. You’ll join tables in the **Load Data in Power BI Desktop** lab.

6. To assess column quality, on the **View** ribbon tab, from inside the **Data Preview** group, check **Column Quality**.

	![Picture 35](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(23).png)

	> **Note**: The column quality feature allows you to easily determine the percentage of valid, error, or empty values found in columns.

7. For the **Position** column (sixth last column), notice that 94% of rows are empty (null).

	![Picture 38](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(24).png)

8. To assess column distribution, on the **View** ribbon tab, from inside the **Data Preview** group, check **Column Distribution**.

	![Picture 40](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(25).png)

9. Review the **Position** column again, and notice that there are four distinct values, and one unique value.

10. Review the column distribution for the **EmployeeKey** (first) column—there are 296 distinct values, and 296 unique values.

	![Picture 43](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(26).png)

	> **Note**: When the distinct and unique counts are the same, it means the column contains unique values. When modeling, it’s important that some model tables have unique columns. These unique columns can be used to create one-to-many relationships, which you will do in the **Model Data in Power BI Desktop** lab.

11. In the **Queries** pane, select the **DimEmployeeSalesTerritory** query.

	![Picture 44](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(27).png)

	> **Note**: The **DimEmployeeSalesTerritory** table stores one row for each employee and the sales territory regions they manage. The table supports relating many regions to a single employee. Some employees manage one, two, or possibly more regions. When you model this data, you’ll need to define a many-to-many relationship.

12. In the **Queries** pane, select the **DimProduct** query.

	![Picture 46](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(28).png)

	> **Note**: The **DimProduct** table contains one row per product sold by the company.

13. Horizontally scroll to reveal the last columns.

14. Notice the **DimProductSubcategory** column.

	> **Note**: When you add transformations to this query in the **Load Data in Power BI Desktop** lab, you’ll use the **DimProductSubcategory** column to join tables.

15. In the **Queries** pane, select the **DimReseller** query.

	![Picture 49](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(29).png)

	> **Note**: The **DimReseller** table contains one row per reseller. Resellers sell, distribute, or value add to the Adventure Works products.

16. To view column values, on the **View** ribbon tab, from inside the **Data Preview** group, check **Column Profile**.

	![Picture 41](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(30).png)

17. Select the **BusinessType** column header.

18. Notice the new pane beneath the data preview pane.

19. Review the column statistics and value distribution in the data preview pane.

20. Notice the data quality issue: there are two labels for warehouse (**Warehouse**, and the misspelled **Ware House**).

	![Picture 51](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(31).png)

21. Hover the cursor over the **Ware House** bar, and notice that there are five rows with this value.

    > **Note**: You’ll apply a transformation to relabel these five rows in the **Load Data in Power BI Desktop** lab.

22. In the **Queries** pane, select the **DimSalesTerritory** query.

	![Picture 52](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(32).png)

	> **Note**: The **DimSalesTerritory** table contains one row per sales region, including **Corporate HQ** (headquarters). Regions are assigned to a country, and countries are assigned to groups. In the **Model Data in Power BI Desktop** lab, you’ll create a hierarchy to support analysis at region, country, or group level.

23. In the **Queries** pane, select the **FactResellerSales** query.

	![Picture 54](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(33).png)

	> **Note**: The **FactResellerSales** table contains one row per sales order line—a sales order contains one or more line items.

24. Review the column quality for the **TotalProductCost** column, and notice that 8% of the rows are empty.

	![Picture 63](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(34).png)

	> **Note**: Missing **TotalProductCost** column values is a data quality issue. To address the issue, in the **Load Data in Power BI Desktop** lab, you’ll apply transformations to fill in missing values by using the product standard cost, which is stored in the related **DimProduct** table.

### Task 4: Get data from a CSV file

In this task you will create a query based on a CSV file.

1. To add a new query, in the **Power Query Editor** window, on the **Home** ribbon tab, from inside the **New Query** group, click the **New Source** down-arrow, and then select **Text/CSV**.

	![Picture 70](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(35).png)

2. In the **Open** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\Resources** folder, and select the **ResellerSalesTargets.csv** file.

3. Click **Open**.

4. In the **ResellerSalesTargets.csv** window, review the preview data.

5. Click **OK**.

	![Picture 71](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(36).png)
 
6. In the **Queries** pane, notice the addition of the **ResellerSalesTargets** query.

	![Picture 72](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(37).png)

	> **Note**: The **ResellerSalesTargets** CSV file contains one row per salesperson, per year. Each row records 12 monthly sales targets (expressed in thousands). Note that the business year for the Adventure Works company commences on July 1.

7. Notice that no column contains empty values.

	> **Note**: When there isn’t a monthly sales target, a hyphen character is stored instead.

8. Review the icons in each column header, to the left of the column name.

	![Picture 74](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image(38).png)

	> **Note**: The icons represent the column data type. **123** is whole number, and **ABC** is text.

9. Repeat the steps to create a query based on the **ColorFormats.csv** file.

    > *The **ColorFormats** CSV file contains one row per product color. Each row records the HEX codes to format background and font colors.*

10. You should now have two new queries, **ResellerSalesTargets** and **ColorFormats**.

	![Picture 19](images/pl3n2n.png)
	
### Review
 In this lab, you have completed the following :
- Get started with Power BI Desktop
- Get data from SQL Server
- Preview Data in Power Query Editor
- Get data from a CSV file

## You have successfully completed the lab
