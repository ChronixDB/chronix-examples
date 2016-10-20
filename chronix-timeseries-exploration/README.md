# Time Series Exploration with Chronix
This example shows how Chronix can be plugged into a rich client application. 
The example is a simple ui with two text fields for range and function queries, a line chart to show the time series, and a table view to show the result of the functions.
It uses a central Chronix Server to query the time series. 
##### Screenshot of the JavaFX Example
![Image of Chronix JavaFX Example](https://raw.githubusercontent.com/ChronixDB/chronix.examples/master/img/Chart-0.2.png)

![Image of Chronix JavaFX Example](https://raw.githubusercontent.com/ChronixDB/chronix.examples/master/img/Result-0.2.png)

## How to start?
To start you have to do a few steps:

### Prerequisites
1. JDK 8
2. Chronix Server 

### Download and execution
First ensure that you have a Java 8 runtime environment in your PATH. 
That should be easy ;-).

Then download, unzip and start  the [Chronix Server](https://github.com/ChronixDB/chronix.server/releases/tag/0.2).
```
wget https://github.com/ChronixDB/chronix.server/releases/download/0.2/chronix-0.2.zip
unzip chronix-0.2.zip

./chronix-solr-6.0.1/bin/solr start
Waiting up to 30 seconds to see Solr running on port 8983 [|]  
Started Solr server on port 8983 (pid=2504). Happy searching!
```
So lets download and execute the JavaFX application.

You can download the example application on GitHub [ChronixDB Examples Releases](https://github.com/ChronixDB/chronix.examples/releases). 
Copy the example to a directory of your choice, e.g., /home/chronix/examples/javaFXExample.jar and execute it.

```Shell

cd <Your-Download-Directory>
java -jar chronix-timeseries-exploration-{version}.jar
```
You should then see the application shown in the screenshot, but with an empty chart.
In the right lower corner you will find a small circle that indicates if the application is connected to Chronix.
- Green says: YES
- Red says: NO

So if the state is green, everything is fine. Time to execute a few queries!
## Some details about the time series data
The data set used for this example is one week of operational time series data.

| Fields        | Values                     |
| ------------- |:-------------------------- | 
| host          | prod39                     |
| source        | os                         |  
| group         | unix                       |
| metric        | "Unix Top metrics"         |
| start         | 26.08.2013 00:00:17.361    |
| end           | 01.09.2013 23:59:18.096    |

## Some example queries
The first text area is for range queries. 
The second text area is for filter queries (e.g. analyses like ag=max, analysis=trend)
```JSON
#Get the average load (metric) on day 28.08.2013
Range Query: metric:\\Load\\avg AND start:2013-08-28T00:00:00.000Z AND end:2013-08-29T23:59:59.999Z

#Get the maximum, minimum, average of the load (metric) on day 28.08.2013
Range Query: metric:\\Load\\avg AND start:2013-08-28T00:00:00.000Z AND end:2013-08-29T23:59:59.999Z
Filter Query: function=max;min;avg
```
