# Module 6

## Get the Package, Try it Yourself

Two datasets (TimedDataPoint1.csv and TimedDataPoint2.csv) are provided in the folder SampleSeedData.  When seeding data, place the file in lightbulbExercise/test/seed/SourceFridgeWeight.  When provisioning, check the box “Include test data” or seed data inside the test folder will not be included with provisioning. 

Prior to provisioning this data, you will want to execute SmartBulbMeasurement.removeAll() and SmartBulbMeasurementSeries.removeAll(). 

Make sure the data is normalized after provisioning.  The normalization will use the specified treatment. 

Treatments of avg or previous were applied to the field weight during the demonstration.  Use c3ShowType(Treatments) to view other treatments available.  We have focused on aggregation, but the documentation also discusses disaggregation where the metric interval is smaller than the normalization interval. 

Follow along with the video or try other treatments using TimedDataPoint2.csv. 


```
var s_metric = SimpleMetric.make({ 
    "id": "Temperature_SmartBulb", 
    "name": "Temperature", 
    "srcType": "SmartBulb",   
    "path": "bulbMeasurements", 
    "expression": “avg(avg(normalized.data.temperature))” 
}); 

 

var s_spec = EvalMetricsSpec.make({ 
  ids: ["SMBLB1"], 
  expressions: ["Temperature"], 
  start: "2014-12-31", 
  end: "2015-01-05", 
  interval: "HOUR" 
}); 


c3Viz(SmartBulb.evalMetricsWithMetadata(s_spec,[s_metric])) 
```
