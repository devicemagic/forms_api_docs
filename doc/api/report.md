# Reports API

## CSV GET Performance Metric Report

* GET `/api/v3/reports/performance_metric_report` 

Returns a Performance Metric Report in CSV format for all children accounts of the calling account.

**This report needs to be enabled on the account**

### URI query parameters

Key | Type |  Required | Description
--- | --- | --- | ---
:month | integer | true | the month of the report to retrieve
:year | integer | true | the year of the report to retrieve 
---

**Fields Returned:**


```
* Org Id
* Org Short Name
* Org Name
* Form Id
* Form Name
* Pending Submission Id
* Destination Id
* Destination Name
* Destination Delivery Id
* Skipped
* Delivery Created At
* Transport Type
* Format Type
* Submission Upload Time Seconds
* Delivery Time Seconds
* File Size
* Repeat Group Count
```
