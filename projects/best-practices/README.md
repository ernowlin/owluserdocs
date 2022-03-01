# Best Practices

### **Understanding owl activities and what the key/date columns mean for each**

* [https://docs.owl-analytics.com/dq-visuals/](https://docs.owl-analytics.com/dq-visuals/)
* Training with Owl-team Zoom/On-site support&#x20;
* Running with sample data&#x20;
* Introducing anomalies on sample data and running an owlcheck to see the anomalies.

### **Using the tool with practical scenarios**

* Having Well Defined Use Cases
  * Determine a single table (dataset) that you would like to scan
  * Have an expectation of what you would expect Owl to find in this dataset
  * Understand which activities would capture the expected findings
* Target internal datasets with known data issues
* Historical Comparisons:
  * If pre-cleaned data is available with data findings that have been cleaned via legacy methods such as internal rules, run these datasets and compare the results from Owl to Internal findings.
* Work with data owners to understand findings or review expected findings

### Explorer

* The date selected with the calendar widget in the Scope (home) tab should align with the calendar widget assigned on the final (Save/Run) tab.&#x20;
* If you elect to Unlock the cmd line and override the final parameters, do not re-lock or the changes will be overwritten.  In general, only advanced users should override the guided settings.
* Pushdown and parallel JDBC cannot be used together. If you are using pushdown, do not select the parallel JDBC option
