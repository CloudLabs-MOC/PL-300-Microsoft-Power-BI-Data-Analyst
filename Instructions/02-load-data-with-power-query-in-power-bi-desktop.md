# Lab 02: Clean, transform, and load data in Power BI

## Lab scenario
In this lab, you'll use data cleansing and transformation techniques to start shaping your data model. You'll then apply the queries to load each as a table to the semantic model.

In this lab you learn how to:

- Apply various data transformations.

- Load queries to the semantic model.
  
## Estimated timing: 90 Minutes  

## Architecture Diagram

  ![Picture 8](Linked_image_Files/Mod2-PL300.png)

## Exercise 1: Load Data

In this exercise you will apply transformations to each of the queries created in the previous lab.

### Task 1: Get started

In this task you will setup the environment for the lab.

1. Open **File Explorer** on your machine.

2. Navigate to the following path:

   ```
   C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-Main\Allfiles\Labs\02-transform-data-power-bi
   ```
3. Locate the file named: **02-Starter-Sales Analysis.pbix**

	![Picture 19](images/lab2pl300-1.png)
	
4. Double-click the file to open it in **Power BI Desktop**.

1. Close any informational windows that may open.

1. If prompted to apply changes, click **Apply Later**.

    ![Picture 19](images/lab2pl300-2.png)

### Task 2: Configure the Salesperson query

In this task, you'll use Power Query Editor to configure the **Salesperson** query.

> **Important:** When instructed to rename columns, it’s important that you rename them exactly as described.

1. To open the **Power Query Editor** window, on the **Home** ribbon tab, from inside the **Queries** group, click the **Transform Data** icon.

	![](./images/lab2-04-1.png)

1. In the **Power Query Editor** window, in the **Queries** pane, select the **DimEmployee** query.

	![](./images/lab2-04-5.png)

	> **Note:** In the Power Query Editor window, in the Queries pane. If you see that the all the queries showing warning then, select **Edit credentials**, 
	
	 ![](./images/lab2-04-2.png)

	- In the **SQL Server database** pane, select **Use my current credentials (1)**, and then click **Connect (2)**.

		![](./images/lab2-04-3.png)

	- In the **Encryption Support** dialog, click **OK**.
	
	   ![](./images/lab2-04-4.png)

1. To rename the query, in the **Query Settings** pane (located at the right), in the **Name** box, replace the text with **Salesperson (1)**, and then press **Enter**. Then verify the name has been updated in **Queries (2)** pane.

	![](./images/lab2-04-6.png)

	> **Note:** The query name determines the model table name. It’s recommended to define concise and user-friendly names.

1. To locate a specific column, on the **Home** ribbon tab, from inside the **Manage Columns** group, select the **Choose Columns (1)** down-arrow, and then select **Go to Column (2)**.

	![](./images/lab2-04-7.png)

	> **Note:** **Go to Column** is a useful feature with many columns. Otherwise, you can horizontally scroll to find columns.

1. In the **Go to Column** window, to order the list by column name, select the **AZ (1)** sort button, and then select **Name (2)**. 

	![](./images/lab2-04-8.png)

1. In the field selection list, scroll to locate **SalesPersonFlag (1)**, select it, and click **OK (2)**.

	![](./images/lab2-04-9.png)

1. Select the **SalesPersonFlag (1)** column, then filter the column to select only Salespeople that is, **TRUE (2)**, and click **OK (3)**.

	![](./images/lab2-04-10.png)

1. In the **Query Settings** pane, in the **Applied Steps** list, notice the addition of the **Filtered Rows** step.

	![](./images/lab2-04-11.png)

	> **Note:** Each transformation you create results in another step logic. It’s possible to edit or delete steps. It’s also possible to select a step to preview the query results at that stage of the query transformation.

1. To remove columns, on the **Home** ribbon tab, from inside the **Manage Columns** group, select the **Choose Columns** icon.

	![](./images/lab2-04-12.png)

1. In the **Choose Columns** window, to uncheck all columns, uncheck the **(Select All Columns)** item.

1. To include columns, check the following six columns **(1)** and **OK (2)**:

	- EmployeeKey
	- EmployeeNationalIDAlternateKey
	- FirstName
	- LastName
	- Title
	- EmailAddress

	  ![](./images/lab2-04-13.png)

1. In the **Applied Steps** list, notice the addition of another query step.

	![](./images/lab2-04-14.png)

1. To create a single name column, first select the **FirstName** column header. While pressing the **Ctrl** key, select the **LastName** column.

	![](./images/lab2-04-15.png)

1. Right-click either of the select column headers **(1)**, and then in the context menu, select **Merge Columns (2)**.

	![](./images/lab2-04-16.png)

	> **Note:** Many common transformations can be applied by right-clicking the column header, and then choosing them from the context menu. Note that additional transformations are available in the ribbon.

1. In the **Merge Columns** window, in the **Separator** dropdown list, select **Space (1)**.

1. In the **New Column Name** box, replace the text with **Salesperson (1)** and click **(OK)**.

	 ![](./images/lab2-04-17.png)

1. To rename the **EmployeeNationalIDAlternateKey** column, double-click the **EmployeeNationalIDAlternateKey** column header and replace the text with **EmployeeID**, and then press **Enter**.

	 ![](./images/lab2-04-18.png)

1. Rename the **EmailAddress** column to **UPN**.

	![](./images/lab2-04-19.png)

	>**Note:** UPN is an acronym for User Principal Name.

1. In the status bar at the bottom-left corner of the Power Query Editor, verify that the query has 5 columns and 18 rows.

	![](./images/lab2-04-20.png)

### Task 3: Configure the SalespersonRegion query

In this task you will configure the **SalespersonRegion** query.

1. In the **Queries** pane, select the **DimEmployeeSalesTerritory** query.

	![](./images/lab2-04-21.png)

2. In the **Query Settings** pane, rename the query to **SalespersonRegion**.

	![](./images/lab2-04-22.png)

3. To remove the last two columns, first select the **DimEmployee** column header.

4. While pressing the **Ctrl** key, select the **DimSalesTerritory** column header.

5. Right-click either of the select column headers, and then in the context menu, select **Remove Columns**.

	![](./images/lab2-04-23.png)

6. In the status bar, verify that the query has 2 columns and 39 rows.

	![](./images/lab2-04-24.png)

### Task 4: Configure the Product query

In this task you will configure the **Product** query.

**Important**: When detailed instructions have already been provided, the lab steps will now provide more concise instructions. If you need the detailed instructions, you can refer back to the steps of previous tasks.

1. Select the **DimProduct** query.

	![](./images/lab2-04-25.png)

2. Rename the query to **Product**.

3. Locate the **FinishedGoodsFlag (1)** column, and then filter the column to retrieve products that are finished goods i.e. TRUE **(2)**, and click **OK (3)**.

	![](./images/lab2-04-26.png)

1. To remove columns, on the **Home** ribbon tab, from inside the **Manage Columns** group, select the **Choose Columns** icon.

	![](./images/lab2-04-12.png)

1. In the **Choose Columns** window, to uncheck all columns, uncheck the **(Select All Columns)** item.

1. To include columns, check the following six columns **(1)** and **OK (2)**:

	- ProductKey

	- EnglishProductName

	- StandardCost

	- Color

	- DimProductSubcategory

	  ![](./images/lab2-04-27.png)

5. Notice that the **DimProductSubcategory** column represents a related table (it contains **Value** links).

6. In the **DimProductSubcategory** column header, at the right of the column name, click the expand button.

	![](./images/lab2-04-28.png)

7. To uncheck all columns, uncheck the **(Select All Columns)** item.

1. Select **EnglishProductSubcategoryName** and **DimProductCategory (1)**, and uncheck the **Use Original Column Name as Prefix (2)** checkbox before selecting **OK (3)**.

	![](./images/lab2-04-29.png)

	> **Note:** By selecting these two columns, a transformation will be applied to join to the **DimProductSubcategory** table, and then include these columns. The **DimProductCategory** column is, in fact, another related table in the data source.

	> **Note:** Query column names must always be unique. If left checked, this checkbox would prefix each column with the expanded column name (in this case **DimProductSubcategory**). Because it’s known that the selected column names don’t collide with column names in the **Product** query, the option is deselected.

11. Notice that the transformation resulted in the addition of two columns, and that the **DimProductSubcategory** column has been removed.

12. Expand the **DimProductCategory** column, and then introduce only the **EnglishProductCategoryName** column.

	![](./images/lab2-04-30.png)

13. Rename the following four columns:

	- **EnglishProductName** to **Product**

	- **StandardCost** to **Standard Cost** (include a space)

	- **EnglishProductSubcategoryName** to **Subcategory**

	- **EnglishProductCategoryName** to **Category**

14. In the status bar, verify that the query has six columns and 397 rows.

	![](./images/lab2-04-31.png)

### Task 5: Configure the Reseller query

In this task you will configure the **Reseller** query.

1. Select the **DimReseller** query.

	![](./images/lab2-04-32.png)

2. Rename the query to **Reseller**.

1. Select the following columns using **Ctrl**:

	- ResellerKey

	- BusinessType

	- ResellerName

	- DimGeography

1. Right-click on any one of the selected column headers and choose **Remove Other Columns**

4. Expand the **DimGeography (1)** column, to include columns, check the following six columns **(2)** and **OK (3)**:

	- City

	- StateProvinceName

	- EnglishCountryRegionName

	  ![](./images/lab2-04-33.png)

5. In the **Business Type** column header, click the down-arrow, and then review the distinct column values, and notice the incorrect spelling of warehouse.

	![](./images/lab2-04-34.png)

6. Right-click the **Business Type** column header, and then select **Replace Values**.

	![](./images/lab2-04-35.png)

7. In the **Replace Values** window, configure the following values:

	- In the **Value to Find** box, enter **Ware House (1)**

	- In the **Replace With** box, enter **Warehouse (2)**

8. Click **OK (3)**.

	![](./images/lab2-04-36.png)

9. Rename the following four columns:

	- **BusinessType** to **Business Type** (include a space)

	- **ResellerName** to **Reseller**

	- **StateProvinceName** to **State-Province**

	- **EnglishCountryRegionName** to **Country-Region**

10. In the status bar, verify that the query has 6 columns and 701 rows.

	![](./images/lab2-04-37.png)

### Task 6: Configure the Region query

In this task you will configure the **Region** query.

1. Select the **DimSalesTerritory** query.

	![](./images/lab2-04-38.png)

2. Rename the query to **Region**.

1. In the **SalesTerritoryAlternateKey** column, select the filter dropdown **(1)**, uncheck **0 (2)**, and then choose **OK (3)**.

	![](./images/lab2-04-39.png)

4. Select the following columns using **Ctrl**:

	- SalesTerritoryKey

	- SalesTerritoryRegion

	- SalesTerritoryCountry

	- SalesTerritoryGroup

1. Right-click on any one of the selected column headers and choose **Remove Other Columns**

5. Rename the following three columns:

	- **SalesTerritoryRegion** to **Region**

	- **SalesTerritoryCountry** to **Country**

	- **SalesTerritoryGroup** to **Group**

6. In the status bar, verify that the query has 4 columns and 10 rows.

	![](./images/lab2-04-40.png)

### Task 7: Configure the Sales query

In this task you will configure the **Sales** query.

1. Select the **FactResellerSales** query.

	![](./images/lab2-04-41.png)

2. Rename the query to **Sales**.

3. Select the following columns using **Ctrl**:

	- SalesOrderNumber

	- OrderDate

	- ProductKey

	- ResellerKey

	- EmployeeKey

	- SalesTerritoryKey

	- OrderQuantity

	- UnitPrice

	- TotalProductCost

	- SalesAmount

	- DimProduct

1. Right-click on any one of the selected column headers and choose **Remove Other Columns**

	>**Note:** You may recall in the **Prepare Data in Power BI Desktop** lab that a small percentage of **FactResellerSales** rows had missing **TotalProductCost** values. The **DimProduct** column has been included to retrieve the product standard cost column to assist fixing the missing values.

4. Expand the **DimProduct (1)** column, uncheck all columns, and then check only the **StandardCost (2)** and **OK (3)**:

	![](./images/lab2-04-42.png)

5. To create a custom column, on the **Add Column (1)** ribbon tab, from inside the **General** group, click **Custom Column (2)**.

	![](./images/lab2-04-43.png)

6. In the **Custom Column** window, in the **New Column Name** box, replace the text with **Cost (2)**.

7. In the **Custom Column Formula** box, enter the following expression (after the equals symbol) **(2)**:

   **Power Query**
   ```
   if [TotalProductCost] = null then [OrderQuantity] * [StandardCost] else [TotalProductCost]
   ```

   >**Note:** This expression tests if the **TotalProductCost** value is missing. If it is, produces a value by multiplying the **OrderQuantity** value by the **StandardCost** value; otherwise, it uses the existing **TotalProductCost** value.

   > **Note:** Alternatively, you can copy the expression from the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\Labs\02-transform-data\02-Snippets.txt** file.

8. Click **OK (3)**.

	![](./images/lab2-04-44.png)

9. Select the following columns using **Ctrl**:

	- TotalProductCost

	- StandardCost

1. Right-click on any one of the selected column headers and choose **Remove Columns**

10. Rename the following three columns:

	- **OrderQuantity** to **Quantity**

	- **UnitPrice** to **Unit Price** (include a space)

	- **SalesAmount** to **Sales**

11. To modify the column data type, in the **Quantity** column header, at the left of the column name, click the **1.2 (1)** icon, and then select **Whole Number (2)**.

	![](./images/lab2-04-45.png)

	>**Note:** Configuring the correct data type is important. When the column contains numeric value, it’s also important to choose the correct type if you expect to perform mathematic calculations.

12. Modify the following three column data types to **Fixed Decimal Number**.

	- Unit Price

	- Sales

	- Cost

	>**Note:** The fixed decimal number data type allows for 19 digits, and allows for more precision to avoid rounding errors. It’s important to use the fixed decimal number type for financial values, or rates (like exchange rates).

13. In the status bar, verify that the query has 10 columns and 999+ rows.

	![](./images/lab2-04-46n.png)

	>**Note**: A maximum of 1000 rows will be loaded as preview data for each query.

### Task 8: Configure the Targets query

In this task you will configure the **Targets** query.

1. Select the **ResellerSalesTargets** query.

	![](./images/lab2-04-47n.png)

	> **Note:** If you receive a warning message asking to specify how to connect, select **Edit Credentials**, and use anonymous access to Connect.

2. Rename the query to **Targets**.

3. To unpivot the 12 month columns (**M01**-**M12**), first multi-select the **Year** and **EmployeeID** column headers.

	![Picture 5673](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image54.png)

4. **Right-click** either of the select column headers, and then in the context menu, select **Unpivot Other Columns**.

	![](./images/lab2-04-48.png)

5. Notice that the column names now appear in the **Attribute** column, and the values appear in the **Value** column.

1. In the **Value** column, open the filter dropdown **(1)**, uncheck **- (2)**, and then select **OK (3)**.

	![](./images/lab2-04-49.png)

	>**Note**: You may recall that the hyphen character was used in the source CSV file to represent zero (0).

7. Rename the following two columns:

	- **Attribute** to **MonthNumber** (there is no space between the two words it will be removed later)

	- **Value** to **Target**

	> **Note:** You’ll now apply transformations to produce a date column. The date will be derived from the **Year** and **MonthNumber** columns. You’ll create the column by using the **Columns From Examples** feature.

8. To prepare the **MonthNumber** column values, right-click the **MonthNumber** column header, and then select **Replace Values**.

	![](./images/lab2-04-50.png)

9. In the **Replace Values** window, in the **Value To Find** box, enter **M (1)** and leave the **Replace with** empty.

10. Click **OK (2)**.

	![](./images/lab2-04-51.png)

11. Modify the **MonthNumber** column data type to **Whole Number**.

	![](./images/lab2-04-52.png)

12. On the **Add Column (1)** ribbon tab, from inside the **General** group, click The **Column From Examples (2)** icon.

	![](./images/lab2-04-53.png)

13. Notice that the first row is for year **2017** and month number **7**.

14. In the **Column1** column, in the first grid cell, commence entering **7/1/2017**, and then press **Enter**.

	>**Note:** The virtual machine uses US regional settings, so this date is in fact July 1, 2017.

15. Notice that the grid cells update with predicted values.

	>**Note**: The feature has accurately predicted that you are combining values from the **Year** and **MonthNumber** columns.

16. Notice also the formula presented above the query grid.

	![](./images/lab2-04-54.png)

17. To rename the new column, double-click the **Merged** column header.

18. Rename the column as **TargetMonth**.

	![](./images/lab2-04-55.png)

19. To add the new column, click **OK**.

	![](./images/lab2-04-56.png)

20. Select the following columns using **Ctrl**:

	- Year

	- MonthNumber

1. Right-click on any one of the selected column headers and choose **Remove Columns**

21. Modify the following column data types:

	- **Target** as fixed decimal number

	- **TargetMonth** as date

22. To multiply the **Target** values by 1000, select the **Target** column header, and then on the **Transform (1)** ribbon tab, from inside the **Number Column** group, click **Standard (2)**, and then select **Multiply (3)**.

	>**Note**: You may recall that the target values were stored as thousands.

	![](./images/lab2-04-57.png)

1. In the **Multiply** window, in the **Value** box, enter **1000 (1)**, and select **OK (2)**.

	![](./images/lab2-04-58.png)

25. In the status bar, verify that the query has 3 columns and 809 rows.

	![](./images/lab2-04-59n.png)

### Task 9: Configure the ColorFormats query

In this task you will configure the **ColorFormats** query.

1. Select the **ColorFormats** query.

	![](./images/lab2-04-60n.png)

2. Notice that the first row contains the column names.

3. On the **Home** ribbon tab, from inside the **Transform** group, click **Use First Row as Headers**.

	![](./images/lab2-04-61.png)

4. In the status bar, verify that the query has 3 columns and 10 rows.

	![](./images/lab2-04-62n.png)

### Task 10: Update the Product query

In this task you will update the **Product** query by merging the **ColorFormats** query.

1. Select the **Product** query.

	![](./images/lab2-04-63n.png)

2. To merge the **ColorFormats** query, on the **Home** ribbon tab, click the **Combine (1)** down-arrow, then click **Merge Queries (2)**.

	![](./images/lab2-04-64.png)

	>**Note:** Merging queries allows integrating data, in this case from different data sources (SQL Server and a CSV file).

3. In the **Merge** window, in the **Product** query grid, select the **Color (1)** column header.

4. Beneath the **Product** query grid, in the dropdown list, select the **ColorFormats (2)** query.

5. In the **ColorFormats** query grid, select the **Color (3)** column header.

6. When the **Privacy Levels** window opens, for each of the two data sources, in the corresponding dropdown list, select **Organizational (1)** and Click **Save (2)**.

	![](./images/lab2-04-65.png)

	>**Note**: Privacy levels can be configured for data source to determine whether data can be shared between sources. Setting each data source as **Organizational** allows them to share data, if necessary. Note that Private data sources can never be shared with other data sources. It doesn’t mean that Private data cannot be shared; it means that the Power Query engine cannot share data between the sources.

8. In the **Merge** window, use the default **Join Kind** - maintaining the selection of Left Outer and click **OK (4)**.

	![](./images/lab2-04-66.png)

9. Expand the **ColorFormats (1)** column to include the following two columns **(2)** and click **OK (3)**

	- Background Color Format

	- Font Color Format

	  ![](./images/lab2-04-67.png)

10. In the status bar, verify that the query now has 8 columns and 397 rows.

	![](./images/lab2-04-68n.png)

### Task 11: Update the ColorFormats query

In this task you will update the **ColorFormats** to disable its load.

1. Select the **ColorFormats** query.

	![](./images/lab2-04-60n.png)

2. In the **Query Settings** pane, click the **All Properties** link.

	![](./images/lab2-04-70.png)

3. In the **Query Properties** window, uncheck the **Enable Load To Report (1)** checkbox.

	>**Note:** Disabling the load means it will not load as a table to the data model. This is done because the query was merged with the **Product** query, which is enabled to load to the data model.

4. Click **OK (2)**.

	![](./images/lab2-04-71.png)

### Task 12: Review final product

In this task you will complete the lab.

1. Verify that you have eight queries, correctly named as follows:

	- Salesperson

	- SalespersonRegion

	- Product

	- Reseller

	- Region

	- Sales

	- Targets

	- ColorFormats (which will not load to the data model)

2. To load the data model, on the **File** backstage view, select **Close &amp; Apply**.

	![](./images/lab2-04-72.png)

	>**Note:** All load-enabled queries are now loaded to the data model.

3. In the **Data** pane (located at the right), notice the seven tables loaded to the data model.

	![](./images/lab2-04-73.png)

4. Save the Power BI Desktop file.
   
### Review
In this lab, you have completed:

- Configured the different queries in Power BI  Desktop.

## You have successfully completed the lab
