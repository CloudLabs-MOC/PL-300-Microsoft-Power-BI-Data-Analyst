# Lab 05: Modify DAX filter context in Power BI

## Lab scenario

In this lab you will create measures with DAX expressions involving filter context manipulation.

## Lab objectives

In this lab you learn how to:

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

1. Click the Microsoft **Power BI Desktop** shortcut icon to open.

 	![Picture 50](./Linked_image_Files/pl300-lab5-01.png)

1. To open the starter Power BI Desktop file, click the **Open (1)** button at left panel and select **Browse this device (2)**.

	![](./Linked_image_Files/pl300-lab5-02.png)

1. In the **Open** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-Main\Allfiles\Labs\05-modify-dax-filter-context (1)** folder. Select the **05-Starter-Sales Analysis (2)** file and click **Open (3)**.

 	![Picture 35](./Linked_image_Files/pl300-lab5-03.png)

1. Close any informational windows that may open.

	![](./Linked_image_Files/pl300-lab5-04.png)

### Task 2: Create a matrix visual

In this task you will create a matrix visual to support testing your new measures.

1. In Power BI Desktop, in Report view, create a new report page by clicking on the plus '+' sign at the bottom left. 

    ![](images/L5E1T2S1.png)

2. On **Page 3**, add a matrix visual.

    ![Picture 13](images/visuvalizationtab.png)

3. Resize the matrix visual to fill the entire page.

4. To configure the matrix visual fields, from the **Data** pane, drag the **Region \| Regions** hierarchy, and drop it under **Rows** in Visualizations panel.

	![](./Linked_image_Files/pl300-lab5-05.png)

    >**Note**: The labs use a shorthand notation to reference a field or hierarchy. It will look like this: **Region \| Regions**. In this example, **Region** is the table name and **Regions** is the hierarchy name.

5. Similarly, drag the **Sales \| Sales** field and drop it under **Values** in Visualizations panel.

	![](./Linked_image_Files/pl300-lab5-06.png)

6. To expand the entire hierarchy, at the top-right of the matrix visual, click the forked-double arrow icon twice.

    ![Picture 47](images/arrowww.png)

    >**Note**: You may recall that the **Regions** hierarchy has the levels **Group**, **Country**, and **Region**.

7. To format the visual, in the **Visualizations** pane, select the **Format** pane.

    ![](images/format_visual.png)

8. In the **Search** box, enter **Layout**.

9. Select the **Layout** property to **Tabular**.

	![](./Linked_image_Files/pl300-lab5-07.png)

10. Verify that the matrix visual now has four column headers.

    ![Picture 50](images/group.png)

    >**Note**: At Adventure Works, the sales regions are organized into groups, countries, and regions. All countries—except the United States—have just one region, which is named after the country. As the United States is such a large sales territory, it’s divided into five sales regions.

    >**Note**: You'll create various measures in this exercise, and then test them by adding them to the matrix visual.

### Task 3: Manipulate filter context

In this task, you'll create several measures with DAX expressions that use the CALCULATE function to manipulate filter context.

> **Note:** The `CALCULATE()` function is a powerful function you can use to manipulate the filter context. The first argument takes an expression or a measure (a measure is just a named expression). Subsequent arguments allow modifying the filter context.

1. Right-click on the **Sales** table and select **New measure** option to add a measure to the **Sales** table. 

	![](./Linked_image_Files/pl300-lab5-08.png)

1. In the formula bar, add the following measure definition:

    >**Note**: For your convenience, all DAX definitions in this lab can be copied from the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-Main\AllFiles\Labs\05-modify-dax-filter-context\Snippets.txt** file.

    ```
    Sales All Region =
    CALCULATE(SUM(Sales[Sales]), REMOVEFILTERS(Region))
    ```

    >**Note**: The `REMOVEFILTERS()` function removes active filters. It can take either no arguments, or a table, a column, or multiple columns as its argument.

    >**Note**: In this formula, the measure evaluates the sum of the **Sales** column in a modified filter context, which removes any filters applied to the columns of the **Region** table.

2. Add the **Sales All Region** measure to the matrix visual.

    ![Picture 52](images/country.png)

1. Drag the **Sales \| Sales All Region** field and drop it under **Values** in Visualizations panel.

	![](./Linked_image_Files/pl300-lab5-09.png)

3. Notice that the **Sales All Region** measure computes the total of all region sales for each region, country (subtotal) and group (subtotal).

    >**Note**: The new measure is yet to deliver a useful result. When the sales for a group, country, or region is divided by this value it will produce a useful ratio known as “percent of grand total”.

4. In the **Data** pane, ensure that the **Sales All Region (1)** measure is selected (when selected, it will have a dark gray background), and then in the formula bar, replace the **measure name and formula (2)** with the following formula:

    > **Tip**: To replace the existing formula, first copy the snippet. Then, click inside the formula bar and press **Ctrl+A** to select all text. Then, press **Ctrl+V** to paste the snippet to overwrite the selected text. Then press **Enter**.

    ```
    Sales % All Region =
    DIVIDE(
	SUM(Sales[Sales]),
	CALCULATE(
	SUM(Sales[Sales]),
	REMOVEFILTERS(Region)))
    ```

	![](./Linked_image_Files/pl300-lab5-10.png)

    > **Note**: The measure has been renamed to accurately reflect the updated formula. The DIVIDE() function divides the **Sales** measure (not modified by filter context) by the **Sales** measure in a modified context, which removes any filters applied to the **Region** table.

5. In the matrix visual, notice that the measure has been renamed and that a different values now appear for each group, country, and region.

6. Switch to **Model view (1)**. Select **Sales % All Region (2)** field from Data panel and change the Properties as a percentage with **two decimal places (3)**.

	![](./Linked_image_Files/pl300-lab5-11.png)

1. Switch back to Report view.

	![](./Linked_image_Files/pl300-lab5-12.png)

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

11. Notice that only the United States regions produce a value which is not 100%.

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

	![](./Linked_image_Files/pl300-lab5-13.png)

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

### Task 2: Create a YoY growth measure

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

8. Switch to **Model view (1)**. Place the **two new measures (2)** into a display folder named **Time Intelligence (3)**.

	![](./Linked_image_Files/pl300-lab5-15.png)

### Task 3: Finish up

In this task you will complete the lab.

1. Save the Power BI Desktop file.

	![](./Linked_image_Files/pl300-lab5-14.png)

## Review
In this lab, you have completed the following:

 - Measures with DAX expressions involving filter context manipulation 
 - Created a sales year-to-date (YTD) measure and sales year-over-year (YoY) growth measure

## You have successfully completed the lab