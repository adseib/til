# Find a Fractional Balance

In trying to pull out stock balances that were fractional I came across the [FLOOR function (Transact-SQL)](https://docs.microsoft.com/en-us/sql/t-sql/functions/floor-transact-sql).

Initially I did a CAST and ROUND.

```SQL
SELECT StockCode
      ,Location
      ,StockBalance
      ,CAST(ROUND((StockBalance),0,1) as decimal) AS WholeStockBalance

FROM schema.stockmastertable

WHERE CAST(ROUND((StockBalance),0,1) as decimal) <> StockBalance
```

The FLOOR function returns the largest integer of a numeric and preserves the datatype and on the whole a bit cleaner.

```SQL
SELECT StockCode
      ,Location
      ,StockBalance
      ,FLOOR(StockBalance) AS WholeStockBalance

FROM schema.stockmastertable

WHERE FLOOR(StockBalance) <> StockBalance
```
