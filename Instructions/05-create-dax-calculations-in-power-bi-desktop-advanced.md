# PL-300 Module 5: Create DAX Calculations in Power BI Desktop, Part 2

## Lab scenario

In this lab you will create measures with DAX expressions involving filter context manipulation.

In this lab you learn how to:

- Use the CALCULATE() function to manipulate filter context

- Use Time Intelligence functions

### Lab story

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, for the first 10 labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop

2. Load Data in Power BI Desktop

3. Model Data in Power BI Desktop

4. Create DAX Calculations in Power BI Desktop, Part 1

5. **Create DAX Calculations in Power BI Desktop, Part 2**

6. Design a Report in Power BI Desktop, Part 1

7. Design a Report in Power BI Desktop, Part 2

8. Create a Power BI Dashboard

9. Perform Data Analysis in Power BI Desktop

10. Enforce Row-Level Security

## Lab objectives
In this lab, you will perform:

- Use the CALCULATE() function to manipulate filter context
- Use Time Intelligence functions

## Estimated timing: 60 minutes  

## Architecture Diagram

![Picture 1](Linked_image_Files/Mod5-PL300.png)

## Exercise 1: Work with Filter Context

In this exercise you will create measures with DAX expressions involving filter context manipulation.

### Task 1: Get started

In this task you will setup the environment for the lab.

**Important**: If you are continuing on from the previous lab (and you completed that lab successfully), do not complete this task; instead, continue from the next task.

1. To open the Power BI Desktop, on the taskbar, click the Microsoft Power BI Desktop shortcut.

    ![Picture 12](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image1.png)

2. To close the getting started window, at the top-left of the window, click **X**.

    ![Picture 11](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image2.png)

3. To open the starter Power BI Desktop file, click the **File** ribbon tab to open the backstage view.

4. Select **Open Report**.

    ![Picture 10](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image3.png)

5. Click **Browse Reports**.

    ![Picture 9](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image4.png)

6. In the **Open** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\Labs\05-create-dax-calculations-in-power-bi-desktop-advanced\Starter** folder.

7. Select the **Sales Analysis** file.

8. Click **Open**.

    ![Picture 8](images/openimage.png)

9. Close any informational windows that may open.

10. Notice the yellow warning message beneath the ribbon.

    >**Note**: The message alerts you to the fact that the queries have not been applied to load as model tables.

11. On the **"There are pending changes in your queries that haven't been applied"** warning message, select **Discard Changes**.

	![Picture 8](Linked_image_Files/discard-changes-1.png)

12. Now you will see another pop up as shown below, select **Discard**.

	![Picture 8](Linked_image_Files/discard-changes-2.png)


13. To create a copy of the file, click the **File** ribbon tab to open the backstage view.

14. Select **Save As**.

    ![Picture 7](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image6.png)

15. If prompted to apply changes, click **Apply Later**.

    ![Picture 22](images/applylater.png)

16. In the **Save As** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\MySolution** folder.

17. Click **Save**.

    ![Picture 2](images/save.png)

### Task 2: Create a matrix visual

In this task you will create a matrix visual to support testing your new measures.

1. In Power BI Desktop, in Report view, create a new report page by clicking on the plus '+' sign at the bottom left. 

    ![](images/L5E1T2S1.png)

2. On **Page 3**, add a matrix visual.

    ![Picture 13](images/visuvalizationtab.png)

3. Resize the matrix visual to fill the entire page.

4. To configure the matrix visual fields, from the **Data** pane, drag the **Region \| Regions** hierarchy, and drop it inside the visual.

    >**Note**: The labs use a shorthand notation to reference a field or hierarchy. It will look like this: **Region \| Regions**. In this example, **Region** is the table name and **Regions** is the hierarchy name.

5. Add also the **Sales \| Sales** field.

6. To expand the entire hierarchy, at the top-right of the matrix visual, click the forked-double arrow icon twice.

    ![Picture 47](images/arrowww.png)

    >**Note**: You may recall that the **Regions** hierarchy has the levels **Group**, **Country**, and **Region**.

7. To format the visual, in the **Visualizations** pane, select the **Format** pane.

    ![](images/format_visual.png)

8. In the **Search** box, enter **Stepped**.

9. Set the **Stepped Layout** property to **Off**.

    ![Picture 49](images/stepped.png)

10. Verify that the matrix visual now has four column headers.

    ![Picture 50](images/group.png)

    >**Note**: At Adventure Works, the sales regions are organized into groups, countries, and regions. All countries—except the United States—have just one region, which is named after the country. As the United States is such a large sales territory, it’s divided into five sales regions.

    >**Note**: You’ll create several measures in this exercise, and then test them by adding them to the matrix visual.

### **Task 3: Manipulate filter context**

In this task you will create several measures with DAX expressions that use the CALCULATE() function to manipulate filter context.

1. Right-click on the **Sales** table and select **New measure** option to add a measure to the **Sales** table, based on the following expression:

    >**Note**: For your convenience, all DAX definitions in this lab can be copied from the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\Labs\05-create-dax-calculations-in-power-bi-desktop-advanced\Assets\Snippets.txt** file.

    ```
    Sales All Region =

    CALCULATE(SUM(Sales[Sales]), REMOVEFILTERS(Region))
    ```

    >**Note**: The CALCULATE() function is a powerful function used to manipulate the filter context. The first argument takes an expression or a measure (a measure is just a named expression). Subsequent arguments allow modifying the filter context.

    >**Note**: The REMOVEFILTERS() function removes active filters. It can take either no arguments, or a table, a column, or multiple columns as its argument.

    >**Note**: In this formula, the measure evaluates the sum of the **Sales** column in a modified filter context, which removes any filters applied to the columns of the **Region** table.

2. Add the **Sales All Region** measure to the matrix visual.

    ![Picture 52](images/country.png)

3. Notice that the **Sales All Region** measure computes the total of all region sales for each region, country (subtotal) and group (subtotal).

    >**Note**: The new measure is yet to deliver a useful result. When the sales for a group, country, or region is divided by this value it will produce a useful ratio known as “percent of grand total”.

4. In the **Data** pane, ensure that the **Sales All Region** measure is selected (when selected, it will have a dark gray background), and then in the formula bar, replace the measure name and formula with the following formula:

    **Tip**: To replace the existing formula, first copy the snippet. Then, click inside the formula bar and press **Ctrl+A** to select all text. Then, press **Ctrl+V** to paste the snippet to overwrite the selected text. Then press **Enter**.

     ```
     Sales % All Region =
     DIVIDE(
	SUM(Sales[Sales]),
	CALCULATE(
	SUM(Sales[Sales]),
	REMOVEFILTERS(Region)))
     ```

     >**Note**: The measure has been renamed to accurately reflect the updated formula. The DIVIDE() function divides the **Sales** measure (not modified by filter context) by the **Sales** measure in a modified context, which removes any filters applied to the **Region** table.

5. In the matrix visual, notice that the measure has been renamed and that a different values now appear for each group, country, and region.

6. Format the **Sales % All Region** measure as a percentage with two decimal places.

7. In the matrix visual, review the **Sales % All Region** measure values.

    ![Picture 53](images/allregion.png)

8. Add another measure to the **Sales** table, based on the following expression, and format as a percentage:

   ```
   Sales % Country =
   DIVIDE(
   SUM(Sales[Sales]),
   CALCULATE(
	SUM(Sales[Sales]),
	REMOVEFILTERS(Region[Region])))
   ```
    
9. Notice that the **Sales % Country** measure formula differs slightly from the **Sales % All Region** measure formula.

    >**Note**: The difference is that the denominator modifies the filter context by removing filters on the **Region** column of the **Region** table, not all columns of the **Region** table. It means that any filters applied to the group or country columns are preserved. It’ll achieve a result that represents the sales as a percentage of country.

10. Add the **Sales % Country** measure to the matrix visual.

11. Notice that only the United States’ regions produce a value which is not 100%.

    ![Picture 54](images/northamrica.png)

    >**Note**: You may recall that only the United States has multiple regions. All other countries comprise a single region, which explains why they are all 100%.

12. To improve the readability of this measure in visual, overwrite the **Sales % Country** measure with this improved formula.

    ```
    Sales % Country =
    IF(
     ISINSCOPE(Region[Region]),
     DIVIDE(
	SUM(Sales[Sales]),
	CALCULATE(
	  SUM(Sales[Sales]),
	REMOVEFILTERS(Region[Region]))))
    ```

    >**Note**: Embedded within the IF() function, the ISINSCOPE() function is used to test whether the region column is the level in a hierarchy of levels. When true, the DIVIDE() function is evaluated. The absence of a false part means that blank is returned when the region column is not in scope.

13. Notice that the **Sales % Country** measure now only returns a value when a region is in scope.

    ![Picture 55](images/salescou.png)

14. Add another measure to the **Sales** table, based on the following expression, and format as a percentage:

    ```
    Sales % Group =
    DIVIDE(
      SUM(Sales[Sales]),
      CALCULATE(
	SUM(Sales[Sales]),
	REMOVEFILTERS(
	  Region[Region],
	  Region[Country])))
    ```

    >**Note**: To achieve sales as a percentage of group, two filters can be applied to effectively remove the filters on two columns.

15. Add the **Sales % Group** measure to the matrix visual.

16. To improve the readability of this measure in visual, overwrite the **Sales % Group** measure with this improved formula.

    ```
    Sales % Group =
      IF(
	ISINSCOPE(Region[Region])
	|| ISINSCOPE(Region[Country]),
	DIVIDE(
   	  SUM(Sales[Sales]),
	  CALCULATE(
	     SUM(Sales[Sales]),
             REMOVEFILTERS(
		Region[Region],
		Region[Country]))))
      ```


17. Notice that the **Sales % Group** measure now only returns a value when a region or country is in scope.

18. In Model view, place the three new measures into a display folder named **Ratios**.

    ![Picture 56](images/rations.png)

19. Save the Power BI Desktop file.

    >**Note**: The measures added to the **Sales** table have modified filter context to achieve hierarchical navigation. Notice that the pattern to achieve the calculation of a subtotal requires removing some columns from the filter context, and to arrive at a grand total, all columns must be removed.

## Exercise 2: Work with Time Intelligence

In this exercise you will create a sales year-to-date (YTD) measure and sales year-over-year (YoY) growth measure.

### Task 1: Create a YTD measure

In this task you will create a sales YTD measure.

1. In Report view, on **Page 2**, notice the matrix visual that displays various measures with years and months grouped on the rows.

2. Add a measure to the **Sales** table, based on the following expression, and formatted to zero decimal places:

   ```
   Sales YTD = TOTALYTD(SUM(Sales[Sales]), 'Date'[Date], "6-30")
   ```

   >**Note**: The TOTALYTD() function evaluates an expression—in this case the sum of the **Sales** column—over a given date column. The date column must belong to a date table marked as a date table, as was done in the **Create DAX Calculations in Power BI Desktop, Part 1** lab.

   >**Note**: The function can also take a third optional argument representing the last date of a year. The absence of this date means that December 31 is the last date of the year. For Adventure Works, June in the last month of their year, and so “6-30” is used.

4. Add the **Sales** field and the **Sales YTD** measure to the matrix visual.

5. Notice the accumulation of sales values within the year.

    ![Picture 59](images/salesytd.png)

    >**Note**: The TOTALYTD() function performs filter manipulation, specifically time filter manipulation. For example, to compute YTD sales for September 2017 (the third month of the fiscal year), all filters on the **Date** table are removed and replaced with a new filter of dates commencing at the beginning of the year (July 1, 2017) and extending through to the last date of the in-context date period (September 30, 2017).

    >**Note** that many Time Intelligence functions are available in DAX to support common time filter manipulations.

### **Task 2: Create a YoY growth measure**

In this task you will create a sales YoY growth measure.

1. Add an additional measure to the **Sales** table, based on the following expression:

   ```
   Sales YoY Growth =
   VAR SalesPriorYear =
   CALCULATE(
   SUM(Sales[Sales]),
   PARALLELPERIOD('Date'[Date],-12,MONTH))
   RETURN
   SalesPriorYear
   ```

   >**Note**: The **Sales YoY Growth** measure formula declares a variable. Variables can be useful for simplifying the formula logic, and more efficient when an expression needs to be evaluated multiple times within the formula (which will be the case for the YoY growth logic). Variables are declared by a unique name, and the measure expression must then be output after the **RETURN** keyword.

   >**Note**: The **SalesPriorYear** variable is assigned an expression which calculates the sum of the **Sales** column in a modified context that uses the PARALLELPERIOD() function to shift 12 months back from each date in filter context.

2. Add the **Sales YoY Growth** measure to the matrix visual.

3. Notice that the new measure returns BLANK for the first 12 months (because there were no sales recorded before fiscal year 2017).

4. Notice that the **Sales YoY Growth** measure value for **2018 Jul** is the **Sales** value for **2017 Jul**.

    ![Picture 61](images/caliculation.png)

    >**Note**: Now that the “difficult part” of the formula has been tested, you can overwrite the measure with the final formula which computes the growth result.

5. To complete the measure, overwrite the **Sales YoY Growth** measure with this formula, formatting it as a percentage with two decimal places:

   ```
   Sales YoY Growth =
   VAR SalesPriorYear =
   CALCULATE(
   SUM(Sales[Sales]),
   PARALLELPERIOD('Date'[Date],-12,MONTH))
   RETURN
      DIVIDE((SUM(Sales[Sales]) - SalesPriorYear),SalesPriorYear)
   ```

6. In the formula, in the **RETURN** clause, notice that the variable is referenced twice.

7. Verify that the YoY growth for **2018 Jul** is **392.83%**.

    ![Picture 62](images/salessss.png)

    >**Note**: It means that July 2018 sales ($2,411,559) represent a nearly 400% (almost 4x) improvement over the sales achieved at the same time of the prior year ($489,328).

8. In Model view, place the two new measures into a display folder named **Time Intelligence**.

    ![Picture 63](images/timeintee.png)

### **Task 3: Finish up**

In this task you will complete the lab.

1. To clean up the solution ready for report development, at the bottom-left, right-click the **Page 2** tab, and then select **Delete** page.

    ![Picture 17](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image25.png)

2. When prompted to delete the page, click **Delete**.

    ![Picture 18](images/delete.png)

3. Delete **Page 3** also.

4. On the remaining page, to clear the page, select the table visual, and the press the **Delete** key.

5. Save the Power BI Desktop file.

6. After you have successfully saved the Power BI Desktop file, ask your instructor for your personal SharePoint URL. Make sure to use the browser in your LabVM environment to access this confidential link in order to upload the **Sales Analysis.pbix** file.

7. Navigate to the private SharePoint link shared by the instructor in the Lab VM and proceed with the following steps to reach your personal SharePoint directory:
	- Within the **Enter password (1)** field, enter the password provided by your instructor against your personal SharePoint URL.
 	- Click on the **Verify (2)** button.

		>**Note:** The confidentiality of this SharePoint link and its password must be strictly maintained, and under no circumstances should it be shared with anyone.

	![](images/validation-new.png)

8. To upload the recently saved Power BI Desktop file within the **CloudLabs Projects** sharepoint private group, perform the following steps:
 
 	- Once authentication is successful, verify that you can access the SharePoint directory associated with your name.
	- Click on the **+ New (1)** button and then select **Folder (2)** to create a sub folder.
 	- On the **Create a folder** dialog-box, name the folder with the following name based on the value of the Deployment ID: **<inject key="Deployment ID"></inject>-2 (3)**.
	- Click on the **Create (4)** button.
	- Select the newly created folder.

	![](images/new-folder-2.png)

	![](images/new-folder-3.png)

9. To upload the Power BI Desktop file within the newly created sub folder, perform the following steps:
	- Click on **Upload (1)**.
 	- Select **Files (2)** from the dropdown list.
 	- Navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\MySolution** folder and upload the **Sales Analysis.pbix** file.
	
 	![](images/new-folder-4.png)

    >**Note**: You’ll create a report based on the data model in the **Design a Report in Power BI Desktop, Part 1** lab.

    > **Congratulations** on completing the lab! Now, it's time to validate it. Here are the steps:
	
	- Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
	- Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
	- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
	- If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

## Review
In this lab, you have completed the following:

 - Measures with DAX expressions involving filter context manipulation 
 - Created a sales year-to-date (YTD) measure and sales year-over-year (YoY) growth measure

## You have successfully completed the lab
