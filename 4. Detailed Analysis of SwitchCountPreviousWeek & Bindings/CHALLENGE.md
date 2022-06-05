# Module 4

## Get the Package, Try it Yourself

The goal of this exercise is to create a single plot, displaying two switch count windows, both specified at runtime using bindings (e.g. a rolling sum for the last 3 days and last 7 days).  

Seed data files Rolling.csv and Rolling2.csv are available in the SampleSeedDataFolder.  These can be placed in lightbulbExercise/test/seed/SourceSmartBulbMeasurement.  Prior to provisioning this data, you will want to execute SmartBulbMeasurement.removeAll() and SmartBulbMeasurementSeries.removeAll().  When provisioning, check the box “Include test data” or seed data inside the test folder will not be included with provisioning. 

Test in the console and then provision the SwitchCountWindow Compound Metric with variables (bindings) and plot a 3 day and 7 day window together on the same plot. 

### Code Snippets

```
var energy_spec = EvalMetricsSpec.make({ 
 ids: ['SMBLB1'], 
 expressions: ['SwitchCountPreviousWeek'], 
 start: '2014-12-30', 
 end: '2015-02-03', 
 interval: 'DAY', 
}); 


c3Viz(SmartBulb.evalMetrics(energy_spec)); 
```
--------------------------------------------

```
var m = CompoundMetric.make({ 
  id:"SwitchCountWindow", 
  name:"SwitchCountWindow", 
  expression:"window('SUM', SwitchCount, var1, var2)", 
  variables: [{ 
    name: "var1", 
    dataType: "integer" 
    },{ 
    name: "var2", 
    dataType: "integer" 
  }] 
}); 

var spec = EvalMetricsSpec.make({ 

  ids: ["SMBLB1"], 
  expressions: ["SwitchCountWindow"], 
  start: "2014-12-01", 
  end: "2015-03-01", 
  interval: "DAY", 
  bindings: [{ 
    "var1": -1, 
    "var2": 1 
    },{ 
    "var1": -5, 
    "var2": 5 
    }] 
}); 


c3Viz(SmartBulb.evalMetricsWithMetadata(spec, [m])); 
```
