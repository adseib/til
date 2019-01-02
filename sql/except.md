# SQL Except

Get the results from table 1 that are not in table 2. (The inverse of this being INTERSECT)

```SQL
Select [Items]

From [Table1].[Items]

Except

Select [Items]

From [Table2].[Items]

```

When to use this instead of a join and where clause? Well, two different aggregations from the same table is a good example:

```SQL
Select [Items], SUM(QuantitySold) AS "Qty Sold"
From [Table1].[Items]
Where Year[DateSold] = Year(Current_Date)
Group By [Items]

Except

Select [Items], SUM(QuantitySold) AS "Qty Sold"
From [Table1].[Items]
Where Year[DateSold] = Year(Current_Date)-1
Group By [Items]
```
This way I get the total quantity sold for all years, but only items that were not sold last year. (Seems like an arbitrary example but in my head it illustrates the power of using exception instead of filtering with subqueries)
