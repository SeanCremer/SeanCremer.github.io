## Load Script for SaleItem tables A,B and C

```sql

/*** Load Scripts for the Sale Tables ***/

DECLARE @DepartmentCounter INT = 1,
        @SubGroupCounter   INT = 1,
        @ItemCounter       INT = 1,
        @SaleCounter       INT = 1;


WHILE @DepartmentCounter <= 10
BEGIN
  WHILE @SubGroupCounter <= 10
  BEGIN
    WHILE @ItemCounter <= 10
    BEGIN
      WHILE @SaleCounter <= 50
      BEGIN
        
        -- Using DepartmentCounter to poulate Quantity not so randomly

        INSERT dbo.SaleItemA (DepartmentId, SubGroupId, ItemId, Quantity)
        VALUES (@DepartmentCounter, @SubGroupCounter,@ItemCounter,@DepartmentCounter);

        INSERT dbo.SaleItemB (DepartmentId, SubGroupId, ItemId, Quantity)
        VALUES (@DepartmentCounter, @SubGroupCounter,@ItemCounter,@DepartmentCounter);

        INSERT dbo.SaleItemC (DepartmentId, SubGroupId, ItemId, Quantity)
        VALUES (@DepartmentCounter, @SubGroupCounter,@ItemCounter,@DepartmentCounter);


        SET @SaleCounter = @SaleCounter + 1;
      END
      SET @SaleCounter =1;
      SET @ItemCounter = @ItemCounter + 1;
    END
    SET @ItemCounter = 1;
    SET @SubGroupCounter = @SubGroupCounter + 1;
  END
  SET @SubGroupCounter = 1;
  SET @DepartmentCounter = @DepartmentCounter + 1;
END
GO

```