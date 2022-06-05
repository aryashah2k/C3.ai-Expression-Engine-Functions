# Module 3

## Get the Package, Try it Yourself

The goal of this exercise is to efficiently explore the most recent value of the temperature of each smart bulb.  To show the amount of time it takes to access this data when using a large dataset, it’s preferred you upload the large dataset available in SmartBulbMeasurement.csv.  Do not seed this data.  This should be uploaded via the RestAPI Client.  Directions are available in the Development Core Course in Module Work with Timestamped Data, EXERCISE: Upload Data with an API. 

Be sure to normalize the SmartBulbMeasurement data after uploading.  If the data is not normalized prior to executing a console command that accesses the data, the normalization will be initiated and the response time will be slow.  Subsequent data access times will be faster once this data has been normalized. 

Access the most recent value of all smart bulb temperatures using a combination of evaluate, projection, latestValue and latest.  Confirm some of these are the correct value and timestamp by using fetch directly on the SmartBulbMeasurement Type. 

### Code Snippets

```
c3Grid(SmartBulbMeasurement.fetch({ 
filter:'parent.id == "SBMS_serialNo_SMBLB1"', 
order:'descending(start)', 
limit:1 
}))
```

-------------------------------------------------------------------------------------------

```
var s_metric = SimpleMetric.make({ 
    "id": "MostRecentTemperature_SmartBulb", 
    "name": "MostRecentTemperature", 
    "srcType": "SmartBulb",   
    "path": "bulbMeasurements", 
    "expression": "latestValue(normalized.data.temperature)" 
}); 


var s_spec = EvalMetricsSpec.make({ 
  ids: ["SMBLB1"], 
  expressions: ["MostRecentTemperature"], 
  start: "2015-01-01", 
  end: "2015-01-01", 
  interval: "DAY" 
}); 


c3Viz(SmartBulb.evalMetricsWithMetadata(s_spec,[s_metric])); 
```
------------------------------------------------------------------------------------------

```
c3Grid(SmartBulb.evaluate({ 
projection: 'id,latestValue(bulbMeasurements[0].normalized.data.temperature),latest(bulbMeasurements[0].normalized.data.temperature)', 
group:'id', 
timeRangeStart: '2015-01-01', 
timeRangeEnd: '2015-01-01', 
interval:'DAY', 
})) 
```
