# PL-300 Module 4: Create DAX Calculations in Power BI Desktop, Part 1

## Lab scenario
In this lab you will create calculated tables, calculated columns, and simple measures using Data Analysis Expressions (DAX).

In this lab you learn how to:

- Create calculated tables

- Create calculated columns

- Create measures

## Lab story

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, for the first 10 labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop

2. Load Data in Power BI Desktop

3. Model Data in Power BI Desktop

4. **Create DAX Calculations in Power BI Desktop, Part 1**

5. Create DAX Calculations in Power BI Desktop, Part 2

6. Design a Report in Power BI Desktop, Part 1

7. Design a Report in Power BI Desktop, Part 2

8. Create a Power BI Dashboard

9. Perform Data Analysis in Power BI Desktop

10. Enforce Row-Level Security

## Lab objectives
In this lab, you will perform:

- Create calculated tables
- Create calculated columns
- Create measures

## Estimated timing: 60 minutes

## Architecture Diagram

![Picture 1](Linked_image_Files/Mod4-PL300.png)

## Exercise 1: Create Calculated Tables

In this exercise you will create two calculated tables. The first will be the **Salesperson** table, to allow a direct relationship between it and the **Sales** table. The second will be the **Date** table.

### Task 1: Get started

In this task you will setup the environment for the lab.

**Important**: If you are continuing on from the previous lab (and you completed that lab successfully), do not complete this task; instead, continue from the next task.

1. To open the Power BI Desktop, click the Microsoft Power BI Desktop shortcut.

 	![Picture 50](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image1.png)

2. To close the getting started window, at the top-left of the window, click **X**.

 	![Picture 49](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image2.png)

3. To open the starter Power BI Desktop file, click the **File** ribbon tab to open the backstage view.

4. Select **Open Report**.

 	![Picture 48](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image3.png)

5. Click **Browse Reports**.

 	![Picture 47](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image4.png)

6. In the **Open** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\Labs\04-create-dax-calculations-in-power-bi-desktop\Starter** folder.

7. Select the **Sales Analysis** file.

8. Click **Open**.

 	![Picture 35](images/openimage.png)

9. Close any informational windows that may open.

10. Notice the yellow warning message beneath the ribbon.

	>**Note**: The message alerts you to the fact that the queries have not been applied to load as model tables.

11. On the **"There are pending changes in your queries that haven't been applied"** warning message, select **Discard Changes**.

	![Picture 8](Linked_image_Files/discard-changes-1.png)

12. Now you will see another pop up as shown below, select **Discard**.

	![Picture 8](Linked_image_Files/discard-changes-2.png)

13. To create a copy of the file, click the **File** ribbon tab to open the backstage view.

14. Select **Save As**.

 	![Picture 34](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image6.png)

15. If prompted to apply changes, click **Apply Later**.

	![Picture 22](images/applylater.png)

16. In the **Save As** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\MySolution** folder.

17. Click **Save**.

	![Picture 13](images/save.png)

### Task 2: Create the Salesperson table

In this task you will create the **Salesperson** table (direct relationship to **Sales**).

1. In Power BI Desktop, in Report view, on the **Modeling** ribbon, from inside the **Calculations** group, click **New Table**.

	![Picture 1](images/newtable1.png)

2. In the formula bar (which opens directly beneath the ribbon when creating or editing calculations), type **Salesperson =**, press **Shift+Enter**, type **'Salesperson (Performance)'**, and then press **Enter**.

	![Picture 4](images/salespersonformula.png)

	>**Note**: For your convenience, all DAX definitions in this lab can be copied from the snippets file, located in **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt**.

	>**Note**: A calculated table is created by first entering the table name, followed by the equals symbol (=), followed by a DAX formula that returns a table. Note that the table name cannot already exist in the data model.

	>**Note**: The formula bar supports entering a valid DAX formula. It includes features like auto-complete, Intellisense and color-coding, enabling you to quickly and accurately enter the formula.

	>**Note**: This table definition creates a copy of the **Salesperson (Performance)** table. It copies the data only, however model properties like visibility, formatting, etc. are not copied.

	**Tip**: You’re encouraged to enter “white space” (i.e. carriage returns and tabs) to layout formulas in an intuitive and easy-to-read format—especially when formulas are long and complex. To enter a carriage return, press **Shift+Enter**. “White space” is optional.

3. In the **Data** pane, notice that the table icon is a shade of blue (denoting a calculated table).

	![Picture 10](images/salespersondata.png)

	>**Note**: Calculated tables are defined by using a DAX formula which returns a table. It’s important to understand that calculated tables increase the size of the data model because they materialize and store values. They’re recomputed whenever formula dependencies are refreshed, as will be the case for this data model when new (future) date values are loaded into tables.

	>**Note**: Unlike Power Query-sourced tables, calculated tables can’t be used to load data from external data sources. They can only transform data based on what has already been loaded into the data model.

4. Switch to Model view.

      ![](Linked_image_Files/upd-1.png)

5. Notice that the **Salesperson** table is available (take care, it might be hidden from view, in which case scroll horizontally to locate it).

6. Click on **Manage relationships** under the Home tab.
    
      ![](Linked_image_Files/upd-2.png)
    
7. Under Manage relationships, select **New**.

      ![](Linked_image_Files/upd-3.png)
   
8. Create a relationship from the **Salesperson \| EmployeeKey** column to the **Sales \| EmployeeKey** column.

      ![](Linked_image_Files/upd-5.png)

9. Right-click the inactive relationship between the **Salesperson (Performance)** and **Sales (1)** tables, and then select **Delete (2)**.

      ![](Linked_image_Files/upd-4.png)

10. When prompted to confirm the deletion, click **Delete**.

	![Picture 3](Linked_image_Files/upd-6.png)

11. In the **Salesperson** table, multi-select the following columns, and then hide them (set the **Is Hidden** property to **Yes**):

	- EmployeeID

	- EmployeeKey

	- UPN

      ![Picture 3](Linked_image_Files/upd-7.png)

12. In the model diagram, select the **Salesperson** table.

13. In the **Properties** pane, in the **Description** box, enter: **Salesperson related to Sales**

	>**Note**: You may recall that descriptions appear as tooltips in the **Data** pane when the user hovers their cursor over a table or field.

14. For the **Salesperson (Performance)** table, set the description to: **Salesperson related to region(s)**

	>**Note**: The data model now provides two alternatives when analyzing salespeople. The **Salesperson** table allows analyzing sales made by a salesperson, while the **Salesperson (Performance)** table allows analyzing sales made in the sales region(s) assigned to the salesperson.

### **Task 3: Create the Date table**

In this task you will create the **Date** table.

1. Switch to Data view.

   ![Picture 29](images/viewpoint.png)

2. On the **Home** ribbon tab, from inside the **Calculations** group, click **New Table**.

   ![Picture 30](images/newtable.png)

3. In the formula bar, enter the following:

   ```
   Date = CALENDARAUTO(6)
   ```

   ![Picture 30](images/formulabar.png)
	
   >**Note**: The CALENDARAUTO() function returns a single-column table consisting of date values. The “auto” behaviour scans all data model date columns to determine the earliest and latest date values stored in the data model. It then creates one row for each date within this range, extending the range in either direction to ensure full years of data are stored.

   >**Note**: This function can take a single optional argument, the last month's number of a year. When omitted, the value is 12, meaning December is the year's last month. In this case, 6 is entered, meaning that June is the last month of the year.

4. Notice the column of date values.

   ![Picture 7](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image17.png)

   > **Note** The dates shown are formatted using US regional settings (i.e. mm/dd/yyyy).
 
5. At the bottom-left corner, in the status bar, notice the table statistics, confirming that 1826 rows of data have been generated, which represents five full years’ data.

	![Picture 9](images/table15.png)

### Task 4: Create calculated columns

In this task you will add additional columns to enable filtering and grouping by different time periods. You will also create a calculated column to control the sort order of other columns.

>**Note**: For your convenience, all DAX definitions in this lab can be copied from the snippets file, located in **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt**.

1. On the **Table Tools** contextual ribbon, from inside the **Calculations** group, click **New Column**.

	![Picture 11](images/newcolumn.png)

2. In the formula bar, type the following (or copy from the snippets file), and then press **Enter**:

	```
	Year =
	"FY" & YEAR('Date'[Date]) + IF(MONTH('Date'[Date]) > 6, 1)
	```

	>**Note**: A calculated column is created by first entering the column name, followed by the equals symbol (=), followed by a DAX formula that returns a single-value result. The column name cannot already exist in the table.

	>**Note**: The formula uses the date’s year value but adds one to the year value when the month is after June. It’s how fiscal years at Adventure Works are calculated.

3. Verify that the new column was added.

	![Picture 12](images/year15.png)

4. Perform step-1 again, then use the snippets file definitions to create the following two calculated columns for the **Date** table:
   
   > **Note:** after creating quarter column, again perform step-1, for creating new column for month.
	
	- Quarter

	- Month

   ![Picture 14](images/quartermonth17.png)
	
   > **Note:** For creating the mentioned above columns, you can copy the formula from the snippets file, located in **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt**.

5. To validate the calculations, switch to Report view.

6. To create a new report page, at the bottom-left, click the plus icon.

	![Picture 15](images/page1.png)

7. To add a matrix visual to the new report page, in the **Visualizations** pane, select the matrix visual type.

   **Tip**: You can hover the cursor over each icon to reveal a tooltip describing the visual type.

	![Picture 51](images/visuvalizationtab.png)

8. In the **Data** pane, from inside the **Date** table, drag the **Year** field into the **Rows** well/area.

	![Picture 17](images/year.png)

9. Drag the **Month** field into the **Rows** well/area, directly beneath the **Year** field.

	![Picture 18](images/year.png)

10. At the top-right of the matrix visual (or bottom, depending on the location of the visual), click the forked-double arrow icon (which will expand all years down one level).

	![Picture 19](images/doublearrow.png)

11. Notice that the years expand to months, and that the months are sorted alphabetically rather than chronologically.

	![Picture 20](images/yearrrr.png)

	>**Note**: By default, text values sort alphabetically, numbers sort from smallest to largest, and dates sort from earliest to latest.

12. To customize the **Month** field sort order, switch to Data view.

13. Add the **MonthKey** column to the **Date** table.

    ```
    MonthKey =
    (YEAR('Date'[Date]) * 100) + MONTH('Date'[Date])
    ```

    >**Note**: This formula computes a numeric value for each year/month combination.

14. In Data view, verify that the new column contains numeric values (e.g. 201707 for July 2017, etc.).

	![Picture 21](images/monthkeyy.png)

15. Switch back to Report view.

16. In the **Data** pane, ensure that the **Month** field is selected (when selected, it will have a dark gray background).

17. On the **Column Tools** contextual ribbon, from inside the **Sort** group, click **Sort by Column**, and then select **MonthKey**.

	![Picture 22](images/column.png)

18. In the matrix visual, notice that the months are now chronologically sorted.

	![Picture 23](images/yearfy.png)

### Task 5: Complete the Date table

In this task, you will complete the design of the **Date** table by hiding a column and creating a hierarchy. You will then create relationships to the **Sales** and **Targets** tables.

1. Switch to Model view.

2. In the **Date** table, hide the **MonthKey** column (set **Is Hidden** to **Yes**).

3. On the **Data** right side pane, select the **Date** table, right click on the **Year** column, and select **create hierarchy**. 

4. Rename newly created hierarchy to **Fiscal** by right click and **Rename**. 
5. Add the following two remaining fields to the Fiscal hierarchy by selecting them in the data pane, right-clicking, and selecting **Add to hierarchy** -> **Fiscal**.
	
	- Quarter

	- Month

	![Picture 24](images/fiscal.png)

6. Create the following two model relationships:

	- **Date \| Date** to **Sales \| OrderDate**

	- **Date \| Date** to **Targets \| TargetMonth**

7. Hide the following two columns:

	- Sales \| OrderDate

	- Targets \| TargetMonth

### Task 6: Mark the Date table

In this task, you will mark the **Date** table as a date table.

1. Switch to Report view.

2. In the **Data** pane, select the **Date** table (not the **Date** field).

3. On the **Table Tools** contextual ribbon, from inside the **Calendars** group, click **Mark as Date Table**, and then select **Mark as Date Table**.

	![Picture 8](images/markasdate.png)

4. In the **Mark as Date Table** window, in the **Date Column** dropdown list, select **Date**.

	![Picture 37](images/datecooo.png)

5. Click **OK**.

	![Picture 26](Linked_image_Files/clickok.png)

6. Save the Power BI Desktop file.

	>**Note**: Power BI Desktop now understands that this table defines date (time). It’s important when relying on time intelligence calculations. You’ll work with time intelligence calculations in the **Create DAX Calculations in Power BI Desktop, Part 2** lab.

	>**Note**: Note that this design approach for a date table is suitable when you don’t have a date table in your data source. If you have a data warehouse, it would be appropriate to load date data from its date dimension table rather than “redefining” date logic in your data model.

## Exercise 2: Create Measures

In this exercise, you will create and format several measures.

### Task 1: Create simple measures

In this task, you will create simple measures. Simple measures aggregate values in a single column or count rows of a table.

1. In Report view, on **Page 2**, in the **Data** pane, drag the **Sales \| Unit Price** field into the matrix visual.

	>**Note**: The labs use a shorthand notation to reference a field. It will look like this: **Sales \| Unit Price**. In this example, **Sales** is the table name and **Unit Price** is the field name.

	![Picture 27](images/unirprice.png)

	>**Note**: You may recall that in the **Model Data in Power BI Desktop** lab, you set the **Unit Price** column to summarize by **Average**. The result you see in the matrix visual is the monthly average unit price (sum of unit price values divided by the count of unit prices).

2. In the visual fields pane (located beneath the **Visualizations** pane), in the **Values** field well/area, notice that **Unit Price** is listed.

	![Picture 28](images/values.png)

3. Click the down-arrow for **Unit Price**, and then notice the available menu options.

	![Picture 30](images/removef.png)

	>**Note**: Visible numeric columns allow report authors at report design time to decide how column values will summarize (or not). It can result in inappropriate reporting. Some data modellers don’t like leaving things to chance, however, and choose to hide these columns and instead expose aggregation logic defined in measures. It’s the approach you will now take in this lab.

4. To create a measure, in the **Data** pane, right-click the **Sales** table, and then select **New Measure**.

	![Picture 31](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image38.png)

5. In the formula bar, add the following measure definition:

	```
	Avg Price =  
	‎AVERAGE(Sales[Unit Price])
	```


6. Add the **Avg Price** measure to the matrix visual.

7. Notice that it produces the same result as the **Unit Price** column (but with different formatting).

8. In the **Values** well, open the context menu for the **Avg Price** field, and notice that it is not possible to change the aggregation technique.

	![Picture 32](images/average.png)

	>**Note**: It’s not possible to modify the aggregation behavior of a measure.

9. Use the snippets file definitions to create the following five measures for the **Sales** table:

	- Median Price

	- Min Price

	- Max Price

	- Orders

	- Order Lines

	>**Note**: The DISTINCTCOUNT() function used in the **Orders** measure will count orders only once (ignoring duplicates). The COUNTROWS() function used in the **Order Lines** measure operates over a table.

	>**Note**: In this case, the number of orders is calculated by counting the distinct **SalesOrderNumber** column values, while the number of order lines is simply the number of table rows (each row is a line of an order).

	![Picture 32](images/L4E2T1S9.png)

10. Switch to Model view, and then multi-select the four price measures: **Avg Price**, **Max Price**, **Median Price**, and **Min Price**.

11. For the multi-selection of measures, configure the following requirements:

	- Set the format to two decimal places

	- Assign to a display folder named **Pricing**

       ![Picture 33](Linked_image_Files/L4E2T1S11.png)
        

12. Hide the **Unit Price** column.

	>**Note**: The **Unit Price** column is now not available to report authors. They must use the pricing measures you’ve added to the model. This design approach ensures that report authors won’t inappropriately aggregate prices, for example, by summing them.

13. Multi-select the **Order Lines** and **Orders** measures, and then configure the following requirements:

	- Set the format using the thousands separator

	- Assign to a display folder named **Counts**

	![Picture 36](Linked_image_Files/L4E2T1S13.png)

14. In Report view, in the **Values** well/area of the matrix visual, for the **Unit Price** field, click **X** to remove it.

	![Picture 38](images/valueee.png)

15. Increase the size of the matrix visual to fill the page width and height.

16. Add the following five measures to the matrix visual:

	- Median Price

	- Min Price

	- Max Price

	- Orders

	- Order Lines

17. Verify that the results looks sensible and are correctly formatted.

	![Picture 39](images/L4E2T1S17.png)

### Task 2: Create additional measures

In this task you will create additional measures that use more complex formulas.

1. In Report view, select **Page 1**.

	![Picture 40](images/pageee.png)

2. Review the table visual, noticing the total for the **Target** column.

	![Picture 41](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image45.png)

3. Select the table visual, and then in the **Visualizations** pane, remove the **Target** field.

	![Picture 42](images/targetss.png)

4. Rename the **Targets \| Target** column as **Targets \| TargetAmount**.

   **Tip**: There are several ways to rename the column in Report view: In the **Data** pane, you can right-click the column, and then select **Rename**—or, double-click the column, or press **F2**.

   >**Note**: You’re about to create a measure named **Target**. It’s not possible to have a column and measure in the same table with the same name.

5. Create the following measure on the **Targets** table:

   ```
   Target =
   IF(HASONEVALUE('Salesperson (Performance)'[Salesperson]),
      SUM(Targets[TargetAmount])
     )
   ```

   >**Note**: The HASONEVALUE() function tests whether a single value in the **Salesperson** column is filtered. When true, the expression returns the sum of target amounts (for just that salesperson). When false, BLANK is returned.

6. Switch to the **Model View** and format the **Target** measure for zero decimal places.

	**Tip**: You can use the **Measure Tools** contextual ribbon.

7. Hide the **TargetAmount** column.

	**Tip**: You can right-click the column in the **Data** pane, and then select **Hide**.
  	 ![Picture 42](images/L4E2T2S7.png)

9. Switch to the **Report View** and add the **Target** measure to the table visual.

10. Notice that the **Target** column total is now BLANK.

	![Picture 43](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image47.png)

11. Use the snippets file definitions to create the following two measures for the **Targets** table:

	- Variance

	- Variance Margin


12. Format the **Variance** measure for zero decimal places.

	![Picture 42](images/L4E2T2S11.png)

13. Format the **Variance Margin** measure as percentage with two decimal places.

	![Picture 42](images/L4E2T2S12.png)

14. Add the **Variance** and **Variance Margin** measures to the table visual.

15. Resize the table visual so all columns and rows can be seen.

	![Picture 44](Linked_image_Files/L4E2T2S14.png)

	>**Note**: While it appears all salespeople are not meeting target, remember that the table visual isn’t yet filtered by a specific time period. You’ll produce sales performance reports that filter by a user-selected time period in the **Design a Report in Power BI Desktop, Part 1** lab.

16. At the top-right corner of the **Data** pane, collapse and then expand open the pane.

	![Picture 45](images/fields.png)

	>**Note**: Collapsing and re-opening the pane resets the content.

17. Notice that the **Targets** table now appears at the top of the list.

	![Picture 46](images/fields.png)

	>**Note**: Tables that comprise only visible measures are automatically listed at the top of the list.

### Task 3: Finish up

In this task you will complete the lab.

1. Save the Power BI Desktop file.

2. If you intend to start the next lab, leave Power BI Desktop open.

    >**Note**: You’ll enhance the data model with more advanced calculations using DAX in the **Create DAX Calculations in Power BI Desktop, Part 2** lab.

    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
	
    - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
    - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
    - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
    - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.
      
### Review
In this lab, you have completed the following :
 
- Get started with Power BI Desktop
- Create different tables and columns
- Create Measures

## You have successfully completed the lab
