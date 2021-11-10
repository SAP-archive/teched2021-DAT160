# Exercise 3 - Build an analytical View in SAP Data Warehouse Cloud and use SAP Analytics Cloud for Consumption Purposes

In this exercise, we will make use of the consolidated, local (relational) SAP Data Warehouse Cloud table (cf. [Exercise 2](../ex2/README.md)) to finally build an analytical view on top. This view itself can then be consumed using SAP Analytics Cloud going forward.

## Exercise 3.1 - Build an analytical View in SAP Data Warehouse Cloud 

1. Click on the associated icon to create a new `graphical view` 
<br>![](./images/ex3_1.png)<br>
2. Once the new environment is appearing we take a look at the `Repository`
<br>![](./images/ex3_2.png)<br>
3. We open up the `Tables` node and select the `TAXY Final Table` to drop it to the canvas. As always, XY refers to your personal participant number
<br>![](./images/ex3_3.png)<br>
4. Now, we select the `View` node and take a look at its details by clicking on the `Details` tab
<br>![](./images/ex3_4.png)<br>
5. As the next step, we rename the `Business Name` of the view as highlighted in the screenshot below. As always, please replace XY by your assigned participant number. Moreover, we do choose the option `Analytical Dataset` in the drop down menu that appears when clicking on the `Semantic Usage` area
<br>![](./images/ex3_5.png)<br>
6. Furthermore, we expose the view for analytical consumption
<br>![](./images/ex3_6.png)<br>
7. As we have chosen to create an analytical view we will need to distinguish between `Measures` and `Dimensions` that we will label on a column level accordingly. For this purpose, we first select the column `PRECIPITATION_HEIGHT` and click on the three dots as highlighted in the screenshot below
<br>![](./images/ex3_7.png)<br>`Measures`
8. Once the drop down menu is showing up, we take the action `Change to Measure`
<br>![](./images/ex3_8.png)<br>
9. Now, let us repeat the steps 7 and 8 for the column `SUN_DURATION`. The final distribution of the columns should look as follows
<br>![](./images/ex3_10.png)<br>
10. At this stage, we are ready to deploy the graphical view. For this purpose, we do select the `Deploy` button and rename the business name of the view as highlighted in the screenshot below. As always, please replace XY by your assigned participant number
<br>![](./images/ex3_11.png)<br>
11. You are notified once the view deployment was successful
<br>![](./images/ex3_12.png)<br>


## Exercise 3.2 - Build a Dashboard in SAP Analytics Cloud to gain some Insights in the consolidated Data Foundation (Optional)

12. Click on the associated button at the upper right of the screen and change the selection to `Analytics`
<br>![](./images/ex3_13.png)<br>
13. Now, you are located in the Home Screen of SAP Analytics Cloud. Go ahead and select the highlighted icon to start off with building a dashboard and an SAP Analytics Cloud Story, respectively
<br>![](./images/ex3_14.png)<br>
14. You will be directed to the `Story Builder` application of SAP Analytics Cloud. We choose the `Responsive` layout
<br>![](./images/ex3_15.png)<br>
15. Therein, we right click on the empty space of the left page appearing at the screen and choose to remove it. In addition, we select the `Data` View as highlighted in the screenshot below
<br>![](./images/ex3_16.png)<br>
16. Let us click on the associated icon which is marked in the screenshot below
<br>![](./images/ex3_17.png)<br>
17. We choose the `Connect to Live Data` area and select the connection `SAP Data Warehouse Cloud` connectivity
<br>![](./images/ex3_18.png)<br>
18. Proceed with selecting your assigned space (only one space should appear in the associated drop down list)
<br>![](./images/ex3_19.png)<br>
19. Next, you can select your dataset and your analytical view just built in SAP Data Warehouse Cloud, respectively
<br>![](./images/ex3_20.png)<br>
20. At this stage we will leverage the power of SAP Analytics Cloud to build powerful visualizations. For this sake, we click on the tab named `More` and choose the option `Chart`
<br>![](./images/ex3_21.png)<br>
21. Now, we select the measures we have just defined in the graphical view in SAP Data Warehouse Cloud (cf. steps 7 to 9 from above). To do so, we click on the `Designer` tab and select the `+` icon in the `Measures` section highlighted in the associated screenshot. We add the two measures `PRECIPITATION_HEIGHT` as well as `SUN_DURATION`
<br>![](./images/ex3_22.png)<br>
22. As the next step, we add the desired dimension `REPAIR_CODE` to the bar graph and change the `Chart Orientation` setup to `Vertical`. Let us finally take a look at the resulting bar graph by clicking on the `Designer` tab once again
<br>![](./images/ex3_24.png)<br>
23. To have a better overview of the created visualization we can extend the bar graph accordingly
<br>![](./images/ex3_25.png)<br>
24. Congratulations! You have created a visualization which is showing the relationship between both Sun Duration and Repair Code as well as between Precipitation Height and Repair Code. We do realize that Repair Code 304 seems to correlate with the Sun Duration in some way. This could act as a starting point for further Data Science investigations (which is not part of this exercise though)
<br>![](./images/ex3_26.png)<br>
## Summary

Congratulations! You have finished Exercise 3 which is the last one in this Hands- On Workshop! We hope you enjoyed to accomplish the use case presented and to implement it end-to-end by leveraging powerful functionalities provided by the SAP HANA Data & Analytics portfolio overall!
