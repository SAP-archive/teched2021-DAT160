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

![Open getdwd pipeline](./images/getdwdstations_graph.png).


This is basically a 3-step pipeline:

1. Get data
2. Transform data (Custom Operator)
3. Write data

The first operator "HTTP Client" is a standard opertator that uses the connection we had seen in the "Connection Management". The configuration is in the config panel you can open with the "Open Configuration" button at the operator. 

![Open config panel](./images/config_http.png)

The transformation is done with a script in a custom operator. You can peek into the code by clicking the script button at the custom operator "Convert DWD Stations".

![Open script panel](./images/open_script.png).

Please be aware when you change the script in the pipeline context you branch the code from the basic custom operator script and it is stored with the pipeline. Further on if the script of the custom operator is changed it will not be overtaken by the "pipeline"-custom operator script.  

The transformed data is finally stored in an object store by the "Write File"-operator. The configuration is quite self-explaining. You have to select the connection from the already define connections in the Connection Management. For more information you can read the manual of the operator.  

![Open operator help](./images/operator_help.png).

The final operator "Graph Terminator" is completing the pipeline once it gets a signal at its inport. While the ports of most of the operators have a defined data type and you can only connect operators for which the inport and the corresponding outport have fitting data types, this operator digests all data types: 

![Any Datatype](./images/any_datatype.png).



### Pipeline Download Weather Data 

The other pipeline is more complex that reads the weather data from the weather stations of interest (A nearby installed device). The process is 

1. Get all weather stations from a HANA table "DEVICE_WEATHERSTATION" by an SQL-statement.
2. Creates an URL with a Custom Operator
3. Sends the created URL to the inport "inRequest" of the "HTTP Client" operator that executes the GET request. The output "zip"-file is send to a Custom Operator.
4. Unzips the downloaded data, extracts one file and transform this into a table-format.
5. Stores the data to a HANA Table: "DAILY_WEATHERDATA"
6. Decides when the data stream has come to an end and then sends a signal.
7. Completes the process.    


![Device Weather Pipeline](./images/device_weather_pipeline.png).

It is a pipeline that creates steadily a data stream by sending URLs to the HTTP and the resulting data is finally send to the HANA DB. The data messages carries kind of message metadata and the actual data. In the metadata attributes there is variable that tells if this message is the last message that finally triggers the last operator to complete the pipeline. Without stopping actively a pipeline the process runs continously. 


## Exercise 1.2 Create New Pipeline for Advanced Processing

The previous 2 pipelines are generic in the sense that past weather data can be used for all kind of impact analysis. The next pipeline is rather specific. The SenDI company has devices scattered across Germany. For an analysis if the weather is somehow damaging the devices either the temperatures or the precipitation and which product type is more susceptible for weather conditions you need to get the weather data from the nearest weather station. That means that we have to choose for each device location from the weather station list the nearest one. Luckily the data scientist of SentDi could solve this challenge with a publicly available "next neighbour"-algorithm within an hour and provides a ready to use operator. All you need to do is collecting the data 

1. Weather Stations downloaded already to SAP Data Intelligence internal Data Lake: DI Data Lake
2. HANA Table of the device asset data: DEVICES

and sending the data to the "Next Neighbour"-Custom Operator. The result will be send to an additional HANA Table that stores the pair of device 'ID' and the nearest station 'ID'.

Although we provide the resulting pipeline for checking, we strongly encourage you to run through the following steps of creating your own version. This hands-on might give you a better understanding how this 5th generation programming actually works. 

## Summary

You've now ...

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

