
# Exercise 2 - Exercise 2 Description

In this exercise, we will utilize SAP Data Warehouse Cloud to create an analytical data model which can be consumed by SAP Analytics Cloud 

## Exercise 2.1 - Get started with SAP Data Warehouse Cloud

In [Exercise 1](../ex1/README.md) you have pushed a result set to SAP Data Warehouse Cloud using SAP Data Intelligence Cloud. Apart from that, there are also three existing tables in HANA Cloud that we want to use to build a consolidated table containing all the relevant information we need to derive insights going forward. Before starting off with modeling in SAP Data Warehouse Cloud we will logon to SAP Data Warehouse Cloud for the first time.

1. Logon to <a href="https://di-dwc-teched2021.eu10.hcs.cloud.sap/">SAP Data Warehouse Cloud </a><br> 
<br>![](./images/ex2_0.png)
2. Specify the following information:<br>
   <br> E-Mail or User Name: `christian.tietz+0XY@sap.com`  where XY is your assigned participant number
   <br> Password: `Welcome01`<br>
   <br>to get to the SAP Data Warehouse Cloud Home Screen. 

## Exercise 2.2 - Build a consolidated SAP Data Warehouse Cloud model 
   
3. Now, you should see the Home Screen of SAP Data Warehouse Cloud. Just click on the highlighted icon to get to your associated SAP Data Warehouse Cloud Space<br> 
<br>![](./images/ex2_1.png)<br>
4. Just click on your assigned space in the SAP Data Warehouse Cloud Space Management component<br> 
<br>![](./images/ex2_2.png)<br>
5. Make yourself familiar with the different areas of your assigned SAP Data Warehouse Cloud space. Now, we choose to take a look at the `Connections` tab<br> 
<br>![](./images/ex2_3.png)<br>
6. You will realize that a local connection of type SAP HANA has already been created. As a next step, we will tick of this connection and validate it<br> 
<br>![](./images/ex2_5.png)<br>
7. We notice that the usage of Data Flows is enabled for this connection which is exactly what we need in what follows<br> 
<br>![](./images/ex2_5_1.png)<br>
8. As the next step we switch to the `Data Builder` component of SAP Data Warehouse Cloud<br> 
<br>![](./images/ex2_5_2.png)<br>
9. We select the `Data Flow` component<br> 
<br>![](./images/ex2_6.png)<br>
10. Take a moment to familiarize yourself with the Data Flow environment in SAP Data Warehouse Cloud. Click on the `Sources` tab<br> 
<br>![](./images/ex2_7.png)<br>
11. Select the marked area in the Sources tab. This area is referring to your assigned HANA Cloud Database schema accessible from within your assigned SAP Data Warehouse Cloud space (cf. Step 4 from above) and is containing the content that is available to you<br> 
<br>![](./images/ex2_9.png)<br>
12. Identify your associated table `TECHED2021_DEVICES_WEATHERSTATION_TAXY` where <b> XY refers to your assigned participant number</b>. Drag & drop it to the Data Flow canvas and select `Import and Deploy` to proceed. Note that you are now using the table that you have filled using SAP Data Intelligence (cf. [Exercise 1](../ex1/README.md))<br>
<br>![](./images/ex2_10.png)<br>
13. Label the imported table as `Source` <br>
<br>![](./images/ex2_11.png)<br>
14. At this point, we want to enrich the imported content with other tables containing information about the Daily Weather, about the Devices used as well as about the Services that have been taken place in the past. For this sake we make use of the pre-populated HANA Database connection called `HANA TechEd` in your assigned SAP Data Warehouse Cloud space (cf. Steps 6 and 7 from above). To do so, we click on the `Connections` tab in same area on the left hand side of the entire Data Flow screen<br>
<br>![](./images/ex2_12.png)<br>
15. Drag & drop the table `DAILY_WEATHER` to the Data Flow canvas<br>
<br>![](./images/ex2_13.png)<br>
16. Now, drag & drop the tables `DEVICES` and `SERVICES` to the Data Flow canvas<br>
<br>![](./images/ex2_13_2.png)<br>
17. As the next step, we will apply a projection on each of the four tables highlighted in the Data Flow canvas to get rid of some columns that we do not need for further processing. To do so, take a look at the `Operators` bar above the Data Flow canvas. We initially select the `Projection` operator and drag & drop it to the Data Flow canvas and right behind the first table from above, respectively <br>
<br>![](./images/ex2_14.png)<br>
18. We do realize that both the Table operator and the Projection operator do have ports that are exposed (cf. the area in the screenshot marked in red). Just hoover with your mouse over the output port of the Table operator and draw a line from this mentioned output port to the input port of the Projection operator to connect both<br>
<br>![](./images/ex2_15.png)<br>
19. Right now, just click on the Projection Operator named `Projection 1`. Then switch to the `Details` tab on the right hand side of the Data Flow screen. You will get to more detailed information about the columns, filter applied (if at all) and so on<br>
<br>![](./images/ex2_16.png)<br>
20. Our goal is to remove columns that are not needed. We start off with the column `LATITUDE_DEVICE` that we would like to remove completely. To proceed with this, just click on the three dots on the right hand side when selecting the mentioned column <br>
<br>![](./images/ex2_17.png)<br>
21. Once you have done that there are three options you can choose in principle. We select the option `Remove Column`<br>
<br>![](./images/ex2_17_1.png)<br>
22. Now we do proceed exactly as described in the aforementioned steps 20 and 21 and remove the following columns from the `Projection 1` Operator: 
- `LONGITUDE_DEVICE` <br>
- `HEIGHT` <br>
- `LATITUDE_STATION` <br>
- `LONGITUDE_STATION` <br>
- `DISTANCE` <br>
You will end up with having five columns remaining as output in the Projection 1 Operator<br>
<br>![](./images/ex2_17_2.png)<br>
23. 
## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
