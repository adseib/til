#SQL Date Range

This is an example where a subselect and MAX operator to fetch the latest date.

```
SELECT         DiscountCode, EffectiveFrom, Discount
FROM            PurchaseDiscountTable
WHERE        (EffectiveFrom =
                             (SELECT        MAX(EffectiveFrom) AS Expr1
                               FROM         PurchaseDiscountTable
                               WHERE        (PurchaseDiscountCode = A.PurchaseDiscountCode)))

```