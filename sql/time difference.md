#SQL Date Range

To simplify date range lookup the between operator comes in handy

```
Select [DateColumn]

From [Table].[DateColumn]

Where [DateColumn] between 'fromDate' and 'toDate'
```

However becuase I often work with datetime but run dates without the time, there is [potential](http://stackoverflow.com/questions/5125076/sql-query-to-select-dates-between-two-dates) to end up with results from ```toDate 00:00:00.000```

The following is more specific:
=======


```
Select [DateColumn]

From [Table].[DateColumn]

Where [DateColumn] >= 'fromDate' and [DateColumn] <= 'toDate'
```

or rather

```
Select [DateColumn]

From [Table].[DateColumn]

Where [DateColumn] between 'fromDate' and 'toDate 23:59:59.999'
```
