# Module 2

## dateTime formatting and timeZone field in Transforms

### Key Takeaways:

1. To explore available Expression Engine Functions, use c3ShowType(ExpressionEngineFunction) 

2. Datetime formats are handled using Expression Engine Function dateTime() with a JODA patten syntax (http://joda-time.sourceforge.net/apidocs/org/joda/time/format/DateTimeFormat.html). 

3. If the time zone is not specified in the header (e.g. TransformSourceSmartBulbToSmartBulbMeasurementSeries), start and end fields of a metric are assumed to be in the same time zone as the source data.  If the field timeZone is included in the transform and loaded into target, the data is normalized into the specified time zone and metrics will assume this time zone for the start and end times provided in the metric spec.
