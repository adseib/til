# SQL Missing Values

To find blanks, or nulls while targeting multiple columns without having multiple OR operators, IN can do the trick. If the column is null it returns an empty string. Repeating the COALESCE function means returning a value if any of the columns are missing values, add multiple values to a single COALESCE function to find if just one value is missing in a sequence of columns.

```SQL

SELECT
*
FROM ORDERS 
WHERE '' IN
(
COALESCE(ORDERS.Date, '' ),
COALESCE(ORDERS.NeedDate, '' ),
COALESCE(ORDERS.ShipDate, '' ),
COALESCE(ORDERS.TargetDate, '' )
)
```
