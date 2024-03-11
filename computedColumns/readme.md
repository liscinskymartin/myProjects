[Home](../README.md)
# Computed Columns in SQL Server
## Problem
Dynamics and Salesforce offer the feature of Calculated/Computed/Rollup fields. The value of the field is calculated based on the values of other fields; in the context of rollup fields, values of different records are considered.
Firstly, it is necessary to investigate the existing solutions of Dynamics and Salesforce.
Based on their implementation, design, and develop our implementation.
The idea is that the user will define calculated fields as a rule/workflow.

## Solution
* The result of the investigation: Dynamics uses SQL scripts (UDF-User Defined Function), and these columns are defined in SQL Server as computed columns, so their values are recalculated during the query.
* The core of the whole implementation is the translation process of the defined formula (XML Workflow) to UDF.
* In the image below, you can find more information about the translation.
![translate](translate.png)
* Actually supported functions: TBD
* Based on our company strategy, this project was stopped, so rollup fields were not implemented. 

[->Next: Data Model Explorer](../dataModelExplorer/readme.md)