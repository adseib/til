# SQL Select from a Filtered Table Using CASE

In this example I want to retrieve the name of the user who last changed order information along with the details of the order itself. If there is no modified by, then select who created the record but not both. The sub-select in the FROM clause provides a single record, the modified or created by, for each row in the order table.

Also I am comparing the street address from a customer information table with the street address on the order. Useful for validation or data maintenance.

```SQL
SELECT
T10.OrderNum,
T10.CustomerCode,
T10.CustomerName,
T10.UserEntered,
T11.UserName,
T10.StreetEntered,
T10.CityEntered,
T10.PhoneEntered,
T12.Street,
T12.City,
T12.Phone

FROM
 (SELECT
 T0.OrderNum,
 T0.CustomerCode,
 T0.CustomerName,
 CASE WHEN T0.ModifiedBy IS NULL THEN T0.CreatedBy
 ELSE 'No User' END AS "UserEntered",
 T1.Street AS "StreetEntered",
 T1.City AS "CityEntered",
 T1.Phone AS "PhoneEntered"
 FROM OrderTable T0
 INNER JOIN OrderAddress T1 ON T0.OrderKey = T1.OrderKey) T10

INNER JOIN UserTable T11 ON T10.UserEntered = T11.UserId
INNER JOIN CustomerTable T12 ON T10.CustomerCode = T12.CustomerCode

```
