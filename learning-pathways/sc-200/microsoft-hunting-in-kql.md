# Microsoft Hunting in KQL

Introduction

Kusto Query Language (KQL) is a powerful tool to explore your data and discover patterns, identify anomalies and outliers, create statistical modeling, and more. KQL is a simple yet powerful language to query structured, semi-structured, and unstructured data.

#### MS Learning Topics:

* Construct KQL statements for Microsoft Sentinel (✔)
* Analyse query results using KQL (✔)
* Work with data in Microsoft Sentinel using Kusto Query Language (✔)

#### Common Operators

search operator

```kusto
search "frog"

search in (SecurityEvent,SecurityAlert,A*) "err"
```

The search is not column specific and will search across all tables. This helps new analysts if you are new in KQL before attempting to filter down.



where operator

```kusto
SecurityEvent
| where TimeGenerated > ago(1d)

SecurityEvent
| where TimeGenerated > ago(1h) and EventID == "4624"

SecurityEvent
| where TimeGenerated > ago(1h)
| where EventID == 4624
| where AccountType =~ "user"

SecurityEvent | where EventID in (4624, 4625)
```

The where operator filters a table to the subset of rows.



let operator

```kusto
let timeOffset = 7d;
let discardEventId = 4688;
SecurityEvent
| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
| where EventID != discardEventId
```

You can use this to declare and reuse variables.



```kusto
let suspiciousAccounts = datatable(account: string) [
    @"\administrator", 
    @"NT AUTHORITY\SYSTEM"
];
SecurityEvent | where Account in (suspiciousAccounts)
```

```kusto
let LowActivityAccounts =
    SecurityEvent 
    | summarize cnt = count() by Account 
    | where cnt < 1000;
LowActivityAccounts | where Account contains "SQL"
```

Let statements allow for the creation of dynamic tables or lists.



extend operator

```kusto

SecurityEvent
| where ProcessName != "" and Process != "Frog"
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
```

This creates a new column with the search you put in.



order operator

```kusto
SecurityEvent
| where ProcessName != "" and Process != ""
| extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
| order by StartDir desc, Process asc
```

The order by operator can utilise any column or multiple columns by using a comma separator. Each column can be ascending or descending. The default order for a column is descending.



project operator

you will get the column set in the search.



summarise operator

```kusto
SecurityEvent | summarize by Activity

SecurityEvent
| where EventID == "4688"
| summarize count() by Process, Computer
```

summaries by Activity column values.



`Bin()` will round down values to an integer multiple of the given bin size. The `timechart` displays a time series based on the bin size.

The `arg_max` function returns a row selected based on the row having the max value for an expression.

`dcount` provides a distinct count.



join operator&#x20;

This will merge all the rows in both columns.

You would use this if you were trying to be more specific on columns.



union operator

You would use this to merge two different tables all into one set of data.
