
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
12. Identify your associated table `TECHED2021_DEVICES_WEATHERSTATION_TAXY` where <b> XY refers to your assigned participant number</b>. Drag & drop it to the Data Flow canvas and select `Import and Deploy` to proceed. Note that you are now using the table that you have filled using SAP Data Intelligence (cf. [Exercise 1] (../ex1/README.md))<br>
<br>![](./images/ex2_10.png)<br>
13. Label the imported table as `Source` <br>
<br>![](./images/ex2_11.png)<br>



## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
