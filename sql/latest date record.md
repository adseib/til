#SQL Date Range

'''
SELECT         PartNumber, A.DiscountCode, A.EffectiveFrom, A.Discount
FROM            PurchaseDiscountTable AS A INNER JOIN
                         PartMasterTable ON A.PurchaseDiscountCode = PartMasterTable.PurchaseDiscountCode
WHERE        (A.EffectiveFrom =
                             (SELECT        MAX(EffectiveFrom) AS Expr1
                               FROM            PurchaseDiscountTable
                               WHERE        (PurchaseDiscountCode = A.PurchaseDiscountCode)))
ORDER BY PartNumber
'''