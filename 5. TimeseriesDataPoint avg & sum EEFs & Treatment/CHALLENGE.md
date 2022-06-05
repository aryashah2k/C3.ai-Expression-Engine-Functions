# Module 5

## Get the Package, Try it Yourself

Two datasets (TimeseriesDataPoint1.csv and TimeseriesDataPoint2.csv) are provided in the folder SampleSeedData.  When seeding data, place the file in lightbulbExercise/test/seed/SourceSmartBulbMeasurement.  When provisioning, check the box “Include test data” or seed data inside the test folder will not be included with provisioning. 

Prior to provisioning this data, you will want to execute SmartBulbMeasurement.removeAll() and SmartBulbMeasurementSeries.removeAll(). 

Make sure the data is normalized after provisioning.  The normalization will use the specified treatment. 

Treatments of avg or previous were applied to the field temperature during the demonstration.  Use c3ShowType(Treatments) to view other treatments available.  We have focused on aggregation, but the documentation also discusses disaggregation where the metric interval is smaller than the normalization interval. 

Test out some of the treatments using TimeSeriesDataPoint2.csv. 

```
var s_metric = SimpleMetric.make({ 
    "id": "Weight_SmartFridge", 
    "name": "Weight", 
    "srcType": "SmartFridge",   
    "path": "fridgeWeight", 
    "expression": 'avg(avg(normalized.data.weight))' 
}); 
```
-----------------------------------------------------

```
var s_spec = EvalMetricsSpec.make({ 
  ids: ["FRDG1"], 
  expressions: ["Weight"], 
  start: "2014-12-31", 
  end: "2015-01-05", 
  interval: "HOUR" 
}); 


c3Viz(SmartFridge.evalMetricsWithMetadata(s_spec,[s_metric])); 
```
