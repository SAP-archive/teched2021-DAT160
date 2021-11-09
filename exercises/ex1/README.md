# Exercise 1 - SAP Data Intelligence 

In this exercise you learn how to download data from external data sources of unusual format that needs some pre-pocessing before it is stored to a SAP Data Intelligence managed data source (Exercise 1.1). In the second Exercise you create a pipeline with a more complex processing. 

## Exercise 1.1 Review Data Collection Pipelines

This exercise explains how a complex data collection could be setup with SAP Data Intelligence. Something that you cannot do with the limited tools of DataFlow in SAP Data Warehouse Cloud.  

### Setup a HTTP Connection

1. Launch the "Connection Management"-App on Launchpad
![Start Connection Management](./images/start_connectionmgmt.png)
2. Open the 'Edit'-screen of the connection 'DWDStations'
![Edit Connection](./images/edit_connection.png)
3. In the details of the connection you see that we have in addition to the "Basic details" specifications of the HTTP address:
	1. Host: opendata.dwd.de 
	2. Port: 443 (General port for downloading content)
	3. Protocol: HTTPS
	4. Path: /climate_environment/CDC/observations_germany/climate/daily/kl/recent/KL_Tageswerte_Beschreibung_Stationen.txt (path to the data we want to download)
	5. Authentication: NoAuth (because no authentication is needed)
![Details Connection](./images/dwdstations_connection.png)
	
As you see this is pretty straightforward way of accessing external data. 

When you click on the composed URL :

[http://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/daily/kl/recent/KL_Tageswerte_Beschreibung_Stationen.txt](http://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/daily/kl/recent/KL_Tageswerte_Beschreibung_Stationen.txt)

you see that the format is not directly usable and you rather like to have a classic "csv"-file with English column names. 


### Pipeline Download DWD Weather Stations

In this exercise we have a look at the pipeline that 

1. uses this connection, 
2. downloads the data,
3. transforms it into "csv"-format
4. saves it to an object store.

On the "Launchpad" start the "Modeler" 

![Start Modeler](./images/start_modeler.png)

Once it has started (it can take a while because the apps is started the first time and needs to initialize the "user workspace") you can select on the left-hand panel the "graph"-category "TechEd 2021".

![Filter graphs](./images/graph_filter.png)

With a double click on the graph "Get DWD Stations" you can open the pipeline. 

![Open getdwd pipeline](./images/getdwdstations_graph.png)


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

