The goal of this exercise is to populate the SmartBulbMeasurment Type using the imperfect csv source file.  The timeZone setting for the SmartBulbMeasurementSeries Type will also be affected.  If you have existing data on your tag, you will want to execute SmartBulbMeasurement.removeAll() and SmartBulbMeasurementSeries.removeAll() prior to starting this exercise. 

The sample file for SourceSmartBulbMeasurement is called SmartBulbMeasurement_TimeZone.csv.  It is available in the SampleSeedData folder.  Move this file to lightbulbExercise/test/seed/SourceSmartBulbMeasurement prior to beginning the exercise.  When provisioning, check the box “Include test data” or seed data inside the test folder will not be included with provisioning. 

Make sure the data is normalized after provisioning.  If specified, in addition to being normalized, the data will be converted to the time zone specified in the timeZone field in TransformSourseSmartBulbToSmartBulbMeasurementSeries. 

The SimpleMetric TotalPower for the SmartBulb Type is already available in the package.  Use this metric to test your time zone settings.  Testing includes adding a timeZone field to TransformSourceSmartBulbToSmartBulbMeasurementSeries or specifying a timeZone field in the metric. 
