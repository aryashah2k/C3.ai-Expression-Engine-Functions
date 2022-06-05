# Module 4

## Detailed Analysis of SwitchCountPreviousWeek and Bindings

### Key Takeaways:

1. The status field for SmartBulbMeasurement uses a treatment of previous, with normalization on an hourly basis.  With the current setting, this cannot catch switch changes more frequent than an hour. 

2. SwitchCount Compound Metric sums up the abs(rollingDiff()) on an hourly basis, matching the frequency of normalization. 

3. The SwitchCountPreviousWeek Compound Metric is created using the window Expression Engine Function using ‘SUM’. 

4. The number of days to go back (e.g. -7) and the width of the window (e.g. 7) can be turned into variables to be specified at the time of metric execution using bindings.
