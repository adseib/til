# Find a Record Function

A template function for returning specific attributes of a record. This is most useful in place of writing the same CASE statements repeatedly, especially if there are mulitple constraints.


```SQL
ALTER FUNCTION [schema].[database].[IsThisTheRecord]
(
	-- Add the parameters for the function here
	@RecordLookupValue varchar(100)
	,@SomeOtherContraint int(10)
)

RETURNS varchar(100)
AS
BEGIN
	-- Declare the return variable here
	DECLARE @Result varchar(100);
	DECLARE @RecordValue varchar(12);

	SET @RecordValue = (SELECT [RecordValue] FROM [schema].[database].[tablewithdata] WHERE [RecordLookupValue] = @RecordLookupValue AND [SomeOtherContraint] = @SomeOtherContraint)

	-- Add the T-SQL statements to compute the return value here
	SELECT @Result = 'Yes'
	FROM [schema].[database].[tablewithdata] WHERE [RecordLookupValue] = @RecordLookupValue AND [SomeOtherContraint] = @SomeOtherContraint) AND [RecordValue] = @RecordValue
		IF (@Result IS NULL)
			SET @Result = 'No';

	-- Return the result of the function
	RETURN @Result;

END;
```

Simply include the function in the query with the required variables:

```SQL
SELECT RecordValue, IsThisTheRecord(@RecordLookupValue,@SomeOtherContraint)
FROM   [schema].[database].[tablewithdata]
```
