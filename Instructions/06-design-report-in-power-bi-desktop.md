# PL-300 Module 6: Design a Report in Power BI Desktop

## Lab scenario
In this lab you will create a three-page report. You will then publish it to Power BI, whereupon you will open and interact with the report.

In this lab you learn how to:

- Design a report

- Configure visual fields and format properties

### Lab story

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, for the first 10 labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop

2. Load Data in Power BI Desktop

3. Model Data in Power BI Desktop

4. Create DAX Calculations in Power BI Desktop

5. Create Advanced  DAX Calculations in Power BI Desktop

6. **Design a Report in Power BI Desktop**

7. Enhance a Report in Power BI Desktop

8. Create a Power BI Dashboard

9. Perform Data Analysis in Power BI Desktop

10. Enforce Row-Level Security

## Lab objectives
In this lab, you will perform:

- Design a report
- Configure visual fields and format properties
  
## Estimated timing: 60 minutes    

## Architecture Diagram

![Picture 1](Linked_image_Files/Mod6-PL300.png)   

## Exercise 1: Create a Report

In this exercise you will create a three-page report named **Sales Report**.

### Task 1: Get started – Sign in

In this task you will setup the environment for the lab by signing in to Power BI.

1. To open Microsoft Edge, on the taskbar, click the Microsoft Edge program shortcut.

 	![Picture 65](Linked_image_Files/07-design-report-in-power-bi-desktop_image1.png)

1. In the Microsoft Edge browser window, navigate to **https://powerbi.microsoft.com**.

 	**Tip**: You can also use the Power BI Service favorite on the Microsoft Edge favorites bar.

1. Click **Sign In** (located at the top-right corner).

 	![Picture 63](Linked_image_Files/lab6-image(2).png)

1. Enter the account details 

   - Enter the Lab username in **Enter your email address** page.
     * Azure Username/Email: <inject key="AzureAdUserEmail"></inject> 
     
   - Complete the sign up process by selecting the username

   - Enter the password 
   
     * Azure Password: <inject key="AzureAdUserPassword"></inject>
 
1. If prompted to update the password, reenter the provided password, and then enter and confirm a new password.

 	**Important**: Be sure to record your new password.

1. Complete the sign in process by clicking on **Continue**

   ![](Linked_image_Files/lab6-image-T01.png)
   
1. Enter a 10 digit phone number and select Get started. Select Get started once more. You will be redirected to Power BI.
   
   ![](Linked_image_Files/lab6-image-(T02).png)
   
   ![](Linked_image_Files/lab6-image-(T003).png)

1. If prompted by Microsoft Edge to stay signed in, click **Yes**.

1. Leave the Microsoft Edge browser window open.

### Task 2: Get started – Enable Map and filled map visuals

In this task you will enable map and filled map visuals in the environment for the lab by updating the Integration settings in the Power BI Admin portal. 

1. To open the Power BI Admin portal, at the top-right corner of the browser, click on the ellipses and then select the **Settings** icon.

1. Select **Admin portal**.

   ![Picture 102](Linked_image_Files/lab6-image-(102).png)

1. Scroll down the page to Integration settings. Click the arrow to expand the Map and filled map visuals option.

   ![Picture 103](Linked_image_Files/image(103).png)

1. Set the Map and filled map visuals option to **Enabled**.

   >**Note**: If the Map and filled map visuals is **Enabled** skip the step.

1. Click **Apply**, to apply the changes. 

   ![Picture 104](Linked_image_Files/enable.png)

1. A message will appear at the top-right of the browser stating the Tenant settings changes will be applied within the next 15 minutes. 

   ![Picture 105](Linked_image_Files/enable-(1).png)

1. Leave the Microsoft Edge browser window open.

### Task 3: Get started – Open report

In this task you will setup the environment for the lab by opening the starter report.

**Important**: If you are continuing on from the previous lab (and you completed that lab successfully), do not complete this task; instead, continue from the next task.

1. To open the Power BI Desktop, click the Microsoft Power BI Desktop shortcut.

   ![](Linked_image_Files/powerbi.png)

2. To close the getting started window, at the top-right of the window, click **X**.

	![Picture 47](Linked_image_Files/close.png)

3. To sign in to the Power BI service, at the top-right, click **Sign In**.

	![Picture 66](Linked_image_Files/07-design-report-in-power-bi-desktop_image5.png)

4. Complete the sign in process using the same account used to sign in to the Power BI service. (**Note:** Select Work or school account if asked, and complete the sign in process)

5. To open the starter Power BI Desktop file, click the **File** ribbon tab to open the backstage view.

6. Select **Open Report**.

	![Picture 10](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image(3).png)

7. Click **Browse Reports**.

	![Picture 30](Linked_image_Files/07-design-report-in-power-bi-desktop_image7.png)

8. In the **Open** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\Labs\06-design-report-in-power-bi-desktop\Starter** folder.

9. Select the **Sales Analysis** file.

10. Click **Open**.

	![Picture 16](Linked_image_Files/image(8).png)

11. Close any informational windows that may open.

12. On the **"There are pending changes in your queries that haven't been applied"** warning message, select **Discard Changes**.

	![Picture 8](Linked_image_Files/discard-changes-(1).png)

13. Now you will see another pop up as shown below, select **Discard**.

	![Picture 8](Linked_image_Files/discard.png)

14. To create a copy of the file, click the **File** ribbon tab to open the backstage view.

15. Select **Save As**.

	![Picture 8](Linked_image_Files/07-design-report-in-power-bi-desktop_image9.png)

16. If prompted to apply changes, click **Apply Later**.

17. In the **Save As** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\Allfiles\MySolution** folder.

18. Click **Save**.

	![Picture 4](Linked_image_Files/image(11).png)

       > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
	
	- Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
	- Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
	- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
	- If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 4: Design page 1

In this task you will design the first report page. When you’ve completed the design, the page will look like the following:

   ![Image of page 1, comprising a logo, two slicers, and three visuals.](Linked_image_Files/image(12).png)

1. In Power BI Desktop, to rename the page, at the bottom-left, right-click **Page 1**, and then select **Rename**.

	![Picture 36](Linked_image_Files/image(13).png)

	*Tip: You can also double-click the page name to rename it.*

1. Rename the page as **Overview**, and then press **Enter**.

	![Picture 37](Linked_image_Files/overview.png)

1. To add an image, on the **Insert** ribbon tab, from inside the **Elements** group, click **Image**.

	![Picture 1](Linked_image_Files/image(15).png)

1. In the **Open** window, navigate to the **C:\PL300\PL-300-Microsoft-Power-BI-Data-Analyst-prod\AllFiles\Resources** folder.

1. Select the **AdventureWorksLogo.jpg** file, and then click **Open**.

	![Picture 11](Linked_image_Files/image(16).png)

1. Drag the image to position it at the top-left corner, and also drag the guide markers to resize it.

	![Picture 12](Linked_image_Files/07-design-report-in-power-bi-desktop_image17.png)

1. To add a slicer, first de-select the image by clicking an empty area of the report page.
1. In the **Data** pane, select the **Date \| Year** field (not the **Year** level of the hierarchy).
	
	>**Note**: The labs use a shorthand notation to reference a field. It will look like this: **Date \| Year**. In this example, **Date** is the table name and **Year** is the field name.

1. Notice that a table of year values has been added to the report page.

1. To convert the visual from a table to a slicer, in the **Visualizations** pane, select the **Slicer**.

	![Picture 49](Linked_image_Files/image(18).png)

1. To convert the slicer from a list to a dropdown, navigate to Visualizations > Format visual > Visual > Slicer Settings > Style, and then select Dropdown from the dropdown menu.

	![Picture 18](Linked_image_Files/06_slicer_style-1.png)

1. Resize and position the slicer so it sits beneath the image and is the same width as the image.

	![Picture 19](Linked_image_Files/07-design-report-in-power-bi-desktop_image20.png)

1. In the **Year** slicer, open the dropdown list, select **FY2020**, and then collapse the dropdown list.

	![Picture 20](Linked_image_Files/image(21).png)

	>**Note**: The report page is now filtered by year **FY2020**.

1. De-select the slicer by clicking an empty area of the report page.

1. Create a second slicer, based on the **Region \| Region** field (not the **Region** level of the hierarch).

1. Leave the slicer as a list, and then resize and position the slicer beneath the **Year** slicer.

	![Picture 21](Linked_image_Files/07-design-report-in-power-bi-desktop_image22.png)


1. De-select the slicer by clicking an empty area of the report page.

1. To add a chart to the page, in the **Visualizations** pane, click the **Line and Stacked Column Chart** visual type.

	![Picture 51](Linked_image_Files/image(26).png)

1. Resize and position the visual so it sits to the right of the logo, and so it fills the width of the report page.

	![Picture 26](Linked_image_Files/07-design-report-in-power-bi-desktop_image27.png)

1. Drag and drop the following fields into the visual:

	- Date \| Month

	- Sales \| Sales

1. In the visual fields pane (located beneath the **Visualizations** pane), notice that the fields are assigned to the **X-axis** and **Column y-axis** wells/areas.

	![Picture 27](Linked_image_Files/image(28).png)

	>**Note**: By dragging fields into a visual, they will be added to default wells/areas. For precision, you can drag fields directly into the wells/areas, as you will do next.

1. From the **Data** pane, drag the **Sales \| Profit Margin** field into the **Line y-axis** well/area.

	![Picture 28](Linked_image_Files/image(29).png)

1. Notice that the visual has 11 months only.

	>**Note**: The last month of the year, 2020 June, does not have any sales (yet). By default, the visual has eliminated months with BLANK sales. You will now configure the visual to show all months.

1. In the visual fields pane, in the **X-axis** well/area, for the **Month** field, click the down-arrow, and then select **Show Items With No Data**.

	![Picture 52](Linked_image_Files/image(30).png)

1. Notice that the month **2020 June** now appears.

1. De-select the chart by clicking an empty area of the report page.

1. To add a chart to the page, in the **Visualizations** pane, click the **Stacked column chart** visual type.

	![Picture 53](Linked_image_Files/E1T4S27.png)

1. Resize and position the visual so it sits beneath the column/line chart, and so it fills half the width of the chart above.

	![Picture 33](Linked_image_Files/07-design-report-in-power-bi-desktop_image32.png)

1. Add the following fields to the visual wells/areas:

	- X-axis: **Region \| Country**

	- Y-axis: **Sales \| Sales**

	- Legend: **Product \| Category**

1. De-select the chart by clicking an empty area of the report page.

1. To add a chart to the page, in the **Visualizations** pane, click the **Stacked Bar Chart** visual type.

	![Picture 54](Linked_image_Files/image-(33).png)

1. Resize and position the visual so it fills the remaining report page space.

	![Picture 35](Linked_image_Files/07-design-report-in-power-bi-desktop_image34.png)

1. Add the following fields to the visual wells/areas:

	- Y-axis: **Product \| Category**

	- X-axis: **Sales \| Quantity**

1. To format the visual, open the **Format** pane.

	![Picture 3](Linked_image_Files/formatvisual.png)

1. Expand the **Bars** and then the **Colors** group, and then set the **Default Color** property to a suitable color (to complement the column/line chart).

1. Set the **Data Labels** property to **On**.

	![Picture 2](Linked_image_Files/image(36).png)

1. Save the Power BI Desktop file.

	>**Note**: The design of the first page is now complete.
 
### Task 5: Design page 2

In this task you will design the second report page. When you’ve completed the design, the page will look like the following:

![Image of page 2, comprising a slicer and matrix.](Linked_image_Files/image(37).png)

**Important**: When detailed instructions have already been provided in the labs, the lab steps will provide more concise instructions. If you need the detailed instructions, you can refer back to other tasks in this lab.

1. To create a new page, at the bottom-left, click the plus icon.

	![Picture 42](Linked_image_Files/overview-1.png)

2. Rename the page to **Profit**.

	![Picture 43](Linked_image_Files/profit.png)

3. Add a slicer based on the **Region \| Region** field.

1. To convert the visual from a table to a slicer, in the **Visualizations** pane, select the **Slicer**.

	![Picture 49](Linked_image_Files/image(18).png)

4. Use the **Visualizations > Format visual > Visual > Slicer Settings > Selection** pane to enable the “**Select All**” option.

	![Picture 43](images/M6-T5-S4.png)

5. Resize and position the slicer so it sits at the left side of the report page, and so it is about half the page height.

	![Picture 44](Linked_image_Files/07-design-report-in-power-bi-desktop_image40.png)

6. Add a matrix visual, and resize and position it so it fills the remaining space of the report page

	![Picture 45](Linked_image_Files/07-design-report-in-power-bi-desktop_image41.png)
	
	![](Linked_image_Files/matrix.png)

7. Add the **Date \| Fiscal** hierarchy to the matrix **Rows** well/area.

	![Picture 46](Linked_image_Files/image(42).png)

8. Add the following five **Sales** table fields to the **Values** well/area:

	- Orders (from the **Counts** folder)

	- Sales

	- Cost

	- Profit

	- Profit Margin

	![Picture 55](Linked_image_Files/image(43).png)

9. In the **Filters** pane (located at the left of the **Visualizations** pane), notice the **Filter On This Page** well/area (you may need to scroll down).

	![Picture 57](Linked_image_Files/image(44).png)

10. From the **Data** pane, drag the **Product \| Category** field into the **Filter On This Page** well/area.

11. Inside the filter card, at the top-right, click the arrow to collapse the card.

	![Picture 58](Linked_image_Files/image(45).png)

	>**Note**: Fields added to the **Filters** pane can achieve the same result as a slicer. One difference is they don’t take up space on the report page. Another difference is that they can be configured to achieve more sophisticated filtering requirements.

12. Add each of the following **Product** table fields to the **Filter On This Page** well/area, collapsing each, directly beneath the **Category** card:

	- Subcategory

	- Product

	- Color

	![Picture 60](Linked_image_Files/image(46).png)

13. Save the Power BI Desktop file.

	>**Note**: The design of the second page is now complete.

### Task 6: Design page 3

In this task you will design the third—and final—report page. When you’ve completed the design, the page will look like the following:

![Image of page 3, comprising a slicer and three visuals.](Linked_image_Files/image(47).png)

1. Create a new page, and then rename it as **My Performance**.

	![](Linked_image_Files/performance.png)

1. To simulate the performance of row-level security filters, drag the **Salesperson (Performance) \| Salesperson** field to the page level filters in the filter pane.
	
	![Image of Salesperson field in filter pane.](Linked_image_Files/image(999).png) 

1. Select **Michael Blythe**. Data on the **My Performance** report page will now be filtered to display data for Michael Blythe only.

1. Add a dropdown slicer based on the **Date \| Year** field, and then resize and position it so it sits at the top-left corner of the page.

	![Picture 70](Linked_image_Files/07-design-report-in-power-bi-desktop_image49.png)

1. To convert the slicer from a list to a dropdown, navigate to Visualizations > Format visual > Visual > Slicer Settings > Style, and then select Dropdown from the dropdown menu.

	![Picture 18](Linked_image_Files/06_slicer_style-1.png)
	
1. In the slicer, set the page to filter by **FY2019**.

	![Picture 71](Linked_image_Files/image(50).png)

1. Add a **Multi-row Card** visual, and then resize and reposition it so it sits to the right of the slicer and fills the remaining width of the page.

	![Picture 56](Linked_image_Files/image(51).png)

	![Picture 74](Linked_image_Files/07-design-report-in-power-bi-desktop_image52.png)

1. Add the following four fields to the visual:

	- Sales \| Sales

	- Targets \| Target

	- Targets \| Variance

	- Targets \| Variance Margin

1. To format the visual, open the **Format visual** pane.
   
   ![Picture 3](Linked_image_Files/formatvisual.png)

	- In the **Values** group, increase the **Size** to **28**

	-  Set the **Background** group **Color** to a light gray color

	  ![Picture 79](Linked_image_Files/07-design-report-in-power-bi-desktop_image53.png)

1. Add a **Clustered Bar Chart** visual, and then resize and position it so it sits beneath the multi-row card visual and fills the remaining height of the page, and half the width of the multi-row card visual.

	![Picture 59](Linked_image_Files/image(54).png)

	![Picture 78](Linked_image_Files/07-design-report-in-power-bi-desktop_image55.png)

1. Add the following fields to the visual wells/areas:

	- Y-axis: **Date \| Month**

	- X-axis: **Sales \| Sales** and **Targets \| Target**

	![Picture 80](Linked_image_Files/image(56).png)

1. To create a copy of the visual, press **Ctrl+C**, and then press **Ctrl+V** and drag him to the side.

1. Position the new visual to the right of the original visual.

	![Picture 82](Linked_image_Files/07-design-report-in-power-bi-desktop_image57.png)

1. To modify the visualization type, in the **Visualizations** pane, select **Clustered Column Chart**.

	![Picture 61](Linked_image_Files/image(58).png)

	>**Note**: It’s now possible to see the same data expressed by two different visualization types. This isn’t a good use of the page layout, however, you’ll improve it in the **Enhance a Report in Power BI Desktop** lab by superimposing the visuals. By adding buttons to the page, you’ll allow the report user to determine which of the two visuals is visible.

	>**Note**: The design of the third—and final—page is now complete.
	
## Exercise 2: Explore the Report

In this exercise you will explore the report that was published to Power BI.

### Task 1: Publish the report

In this task you will publish the report.

1. Select the **Overview** page.

2. Save the Power BI Desktop file.

3. On the **Home** ribbon tab, from inside the **Share** group, click **Publish**.

	![Picture 67](Linked_image_Files/image(59).png)

4. In the **Publish to Power** BI window, notice that **My Workspace** is selected.

5. To publish the report, click **Select**.

	![](Linked_image_Files/select-1.png)

6. When the publication has succeeded, click **Got It**.

	![](Linked_image_Files/got-it.png)

7. Leave Power BI Desktop open.

	>**Note**: You’ll explore the report in the Power BI service in the next exercise.

### Task 2: Explore the report

In this task you will explore the report that was published to Power BI.

1. In the Microsoft Edge browser window, in the Power BI service, in the **Navigation** pane (located at the left, and it could be collapsed), Select **My Workspace**.

2. Review the contents of the workspace, noticing the **Sales Analysis** report and dataset.

	>**Note**: When you published the Power BI Desktop file, the data model was published as a dataset.

	>**Note**: If you don’t see it, press **F5** to reload the browser, and then expand the workspace again.

	![Picture 94](Linked_image_Files/workspace-2.png)

3. To open the report, click the **Sales Analysis** report.

4. At the left, in the **Pages** pane, select the **Overview** page. 

5. In the **Regions** slicer, while pressing the **Ctrl** key, select multiple regions.

6. In the column/line chart, select any month column to cross filter the page.

7. While pressing the **Ctrl** key, select an additional month.

	>**Note**: By default, cross filtering filters all other visuals on the page.

8. Notice that the bar chart is filtered and highlighted, with the bold portion of the bars representing the filtered months.

9. Hover the cursor over the bar chart visual, and then at the top-right, hover the cursor over the filter icon.

	![Picture 95](images/M6-Ex2-T2-S9.png)

	>**Note**: The filter icon allows you to understand all filters that are applied to the visual, including slicers and cross filters from other visual.

10. Hover the cursor over a bar, and then notice the tooltip information.

11. To undo the cross filter, in the column/line chart, click an empty area of the visual.

12. Hover the cursor over the Stacked column visual, and then at the top-right, click the **Focus mode** icon.

	![Picture 96](images/M6-Ex2-T2-S12.png)

	>**Note**: Focus mode zooms the visual to full page size.

13. Hover the cursor over different segments of the bar charts to reveal tooltips.

14. To return to the report page, at the top-left, click **Back to Report**.

	![Picture 86](Linked_image_Files/image(66).png)

15. Try out each of the options, except **Chat in Teams**.

16. At the left, in the **Pages** pane, select the **Profit** page.

	![Picture 84](Linked_image_Files/image(68).png)

17. Notice that the **Region** slicer has a different selection to the **Region** slicer on the **Overview** page.

	>**Note**: The slicers are not synchronized. You’ll modify the report design to ensure they sync between pages in the **Enhance a Report in Power BI Desktop** lab.

18. In the **Filters** pane (located at the right), expand a filter card, and apply some filters.

	>**Note**: The **Filters** pane allows you to define more filters than could possibly fit on a page as slicers.

19. In the matrix visual, use the plus (+) button to drill into the **Fiscal** hierarchy.

20. Select the **My Performance** page.

	![Picture 89](Linked_image_Files/image(69).png)

21. At the top-right on the menu bar, click **View**, and then select **Full Screen**.

	![Picture 98](Linked_image_Files/image(70).png)

22. Interact with the page by modifying the slicer, and cross filtering the page.

23. At the bottom of the window, notice the commands to change page, navigate backwards or forwards between pages, or to exit full screen mode.

24. Click the left icon to exit full screen mode.

    ![Picture 91](Linked_image_Files/image(71).png)

    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
	
    - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
    - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
    - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
    - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 2: Finish up

In this task you will complete the lab.

1. To return to your workspace, click on **My Workspace**.

	![Picture 99](Linked_image_Files/07-design-report-in-power-bi-desktop_image72.png)

2. Leave the Microsoft Edge browser window open.

   >**Note**: You will enhance the report design with advanced features in the **Enhance a Report in Power BI Desktop** lab.
  
## Review
 In this lab, you have completed the following :
- Get started – Sign in
- Enable Map and filled map visuals
- Design page 1,2 and 3
- Publish and explore the Report

## You have successfully completed the lab

