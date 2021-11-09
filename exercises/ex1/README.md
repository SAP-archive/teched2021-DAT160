# Exercise 1 - SAP Data Intelligence 

In this exercise you learn how to download data from external data sources of unusual format that needs some pre-pocessing before it is stored to a SAP Data Intelligence managed data source (Exercise 1.1). In the second Exercise you create a pipeline with a more complex processing. 

## Exercise 1.1 Review Data Collection Pipelines

This exercise explains how a complex data collection could be setup with SAP Data Intelligence. Something that you cannot do with the limited tools of DataFlow in SAP Data Warehouse Cloud.  

### Setup a HTTP Connection

1. Launch the "Connection Management"-App on Launchpad
[Start Connection Management](./images/

### Pipeline Download DWD Weather Stations

### Pipeline Download Weather Data 




## Exercise 1.2 Sub Exercise 2 Description

After completing these steps you will have...

1.	Enter this code.
```abap
DATA(lt_params) = request->get_form_fields(  ).
READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc <> 0.
    response->set_status( i_code = 400
                     i_reason = 'Bad request').
    RETURN.
  ENDIF.

```

2.	Click here.
<br>![](/exercises/ex1/images/01_02_0010.png)


## Summary

You've now ...

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

