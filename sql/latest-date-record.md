# SQL Date Range

This is an example where a sub-select and MAX operator is used to fetch the record with the latest date.

```SQL
SELECT  DiscountCode, EffectiveFrom, Discount
FROM    PurchaseDiscountTable
WHERE   EffectiveFrom = (SELECT MAX(EffectiveFrom) AS Expr1
                        FROM   PurchaseDiscountTable
                        WHERE  (PurchaseDiscountCode = A.PurchaseDiscountCode))

```
