- [MySQL](#mysql)
- [SQL SEVER](#sql-sever)
  * [UNION & UNION ALL & JOINS](#union---union-all---joins)
  * [stored procedure](#stored-procedure)
    + [CREATE PROCEDURE or CREATE PROC:](#create-procedure-or-create-proc-)
    + [stored procedure with parameters](#stored-procedure-with-parameters)
    + [output parameters](#output-parameters)
    + [useful system stored proc](#useful-system-stored-proc)
    + [output parameters & return values](#output-parameters---return-values)
    + [advantages of using sq](#advantages-of-using-sq)
  * [DateTime](#datetime)
    + [datatime](#datatime)
    + [isdate](#isdate)
    + [Day, Month, Year](#day--month--year)
    + [DateName](#datename)
    + [DatePart, DateAdd, DateDiff](#datepart--dateadd--datediff)
    + [caculate age](#caculate-age)
  * [CAST & CONVERT](#cast---convert)
  * [math function](#math-function)
    + [ABS](#abs)
    + [CEILING & FLOOR](#ceiling---floor)
    + [POWER](#power)
    + [RAND](#rand)
    + [SQUARE](#square)
    + [SQRT](#sqrt)
    + [ROUND](#round)
  * [SCALAR USER DEFINED FUNCTIONS(UDF)](#scalar-user-defined-functions-udf-)
    + [**create**](#--create--)
    + [**call**](#--call--)
    + [**SCALAR FUNCTION or STORED PROCEDURE ?**](#--scalar-function-or-stored-procedure----)
    + [Inline Table Valued Functions](#inline-table-valued-functions)
  * [Derived table and CTE in sql server](#derived-table-and-cte-in-sql-server)
    + [views](#views)
    + [Temp tables](#temp-tables)
    + [table variable](#table-variable)
    + [derived table](#derived-table)
    + [CTE](#cte)
  * [CTE](#cte-1)
    + [1](#1)
    + [Updateable CTE](#updateable-cte)
      - [1. CTE on 1 base table](#1-cte-on-1-base-table)
      - [2. CTE on 2 base table](#2-cte-on-2-base-table)
    + [Recursive CTE](#recursive-cte)
  * [Normalization](#normalization)



# MySQL

- MySQL命令:

1. 每个命令后;
2. 不区分大小写

- ip:每一个域名解析成一个ip

​       端口号 

- INT 整数

  VARCHAR 字符串

- primary key

  不能为null

  一个table必须要有一个primary key,每个primary key可以有一列或多列组成

- foreign key

- 多对多:中间表

```mysql
create table tablename(
	col_name1 type not null auto_increment,
	col_name2 type default,
    primary key(col_name1)
);

desc tablename; # 查看表结构

insert into tablename(col_name1, col_name2, col_name3) values(value1, value2, value3);

update tablename set col_name1 = value, set col_name2 = value where id = 1;

delete from tablename where id = 1;

select * from tablename limit 4; -- 前四条数据
select * from tablename limit 2,3;
/*去掉前2条,
从第三条开始查询3条(分页)*/
select column_list from tablename where condition order by column_list desc /*反序*/ limit rom_limit;

```

# SQL SEVER

```mssql
-- foreign key
alter table ForeignKeyTable add constraint ForeignKeyTable_ForeignKeyColumn_FK
foreign key (ForeignKeyColumn) references PrimaryKeyTable(PrimaryKeyColumn)
/*
eg: 
alter table tblperson add constraint tblperson_GenderId_FK
foreign key (GenderId) references tblGender(ID)
*/

-- alter an existing column to add a default constraint
alter table Table_Name
add constraint Constraint_Name
default Default_Value for Existing_Column_Name
-- Adding a new column, with default value, to an existing table:
ALTER TABLE { TABLE_NAME } 
ADD { COLUMN_NAME } { DATA_TYPE } { NULL | NOT NULL } 
CONSTRAINT { CONSTRAINT_NAME } DEFAULT { DEFAULT_VALUE }
-- To drop a constraint
ALTER TABLE { TABLE_NAME } 
DROP CONSTRAINT { CONSTRAINT_NAME }

-- Cascading referential integrity constraint
/*
1. No Action: This is the default behaviour. an error is raised and the DELETE or UPDATE is rolled back.

2. Cascade: Specifies that if an attempt is made to delete or update a row with a key referenced by foreign keys in existing rows in other tables, all rows containing those foreign keys are also deleted or updated.

3. Set NULL: Specifies that if an attempt is made to delete or update a row with a key referenced by foreign keys in existing rows in other tables, all rows containing those foreign keys are set to NULL.  

4. Set Default: Specifies that if an attempt is made to delete or update a row with a key referenced by foreign keys in existing rows in other tables, all rows containing those foreign keys are set to default values.
*/

--GROUP BY
/*
1.WHERE filter before GROUP BY, HAVING after GROUP BY 
2.WHERE clause can be used with - Select, Insert, and Update statements, where as HAVING clause can only be used with the Select statement.
3.Aggregate functions cannot be used in the WHERE clause, unless it is in a sub query contained in a HAVING clause, whereas, aggregate functions can be used in Having clause.
*/
```

```mssql
-- see pic1
-- (INNER) JOIN 
select Name, Gender, Salary, DepartmentName
from tblEmployee
join tblDepartment
on tblEmployee.DepartmentId = tblDepartment.Id

-- LEFT (OUTER) JOIN
select Name, Gender, Salary, DepartmentName
from tblEmployee e
left join tblDepartment d
on e.DepartmentId = d.Id

-- RIGHT (OUTER) JOIN
select Name, Gender, Salary, DepartmentName
from tblEmployee e
right join tblDepartment d
on e.DepartmentId = d.Id

-- FULL JOIN
select Name, Gender, Salary, DepartmentName
from tblEmployee e
full join tblDepartment d
on e.DepartmentId = d.Id

-- CROSS JOIN
select Name, Gender, Salary, DepartmentName
from tblEmployee e
cross join tblDepartment d

```

- pic1:

tblEmployee:

![img](/Users/qing/Desktop/note/pic/Employee+Table.png)

tblDepartment:

![img](/Users/qing/Desktop/note/pic/Departments+Table.png)

output:

![img](/Users/qing/Desktop/note/pic/Inner+Join.png)

![img](/Users/qing/Desktop/note/pic/Joins+in+picture.png)

```mssql
-- left self JOIN (see pic.2)
select e.Name as Empolyee, m.Name as Manager
from tblEmployee e
left join tblEmployee m
on e.ManagerId = m.EmployeeId
```

- pic.2

  tblEmployee:

![img](/Users/qing/Desktop/note/pic/tblEmployee.png)

​	output:

![img](/Users/qing/Desktop/note/pic/Self+Join.png)

```mssql
--3 ways to replace NULL 
select e.Name as Empolyee, ISNULL(m.Name, NULL) as Manager
from tblEmployee e
left join tblEmployee m
on e.ManagerId = m.EmployeeId 

select e.Name as Empolyee, COALESCE(m.Name, NULL) as Manager
from tblEmployee e
left join tblEmployee m
on e.ManagerId = m.EmployeeId

select e.Name as Empolyee, CASE WHEN m.Name IS NULL THEN 'no manager' ELSE m.name END as Manager
from tblEmployee e
left join tblEmployee m
on e.ManagerId = m.EmployeeId
```

```mssql
-- NOT IN/EXCEPT
-- Q:retrieve customers who have never purchased Product 716
select distinct CustomerID
from Sales.SalesOrderHeader
where CustomerID NOT IN 
	(select distinct CustomerID
    from Sales.SalesOrderHeader sh
    join Sales.SalesOrderDetail sd
    on sh.SalesOrderID = sd.SalesOrderID
    where sd.ProductID = 716)
    order by CustomerID;
    
select distinct CustomerID
from Sales.SalesOrderHeader
except 
select distinct CustomerID
    from Sales.SalesOrderHeader sh
    join Sales.SalesOrderDetail sd
    on sh.SalesOrderID = sd.SalesOrderID
    where sd.ProductID = 716;
```

```mssql
/*INTERSECT vs INNER JOIN
1. INTERSECT filters duplicates and returns only DISTINCT rows that are common between the LEFT and Right Query, where as INNER JOIN does not filter the duplicates.
2. INNER JOIN treats two NULLS as two different values. So if you are joining two tables based on a nullable column and if both tables have NULLs in that joining column then, INNER JOIN will not include those rows in the result-set, where as INTERSECT treats two NULLs as a same value and it returns all matching rows.
*/

```

```mssql
/*
COALESCE - return the first NON NULL value
*/
select Id, coalesce(FirstName, MiddleName, LastName) as Name
from tblEmployee
```

## UNION & UNION ALL & JOINS

- UNION & UNION ALL
  1. UNION removes duplicate rows; UNION ALL does not
  2. UNION has to perform distinct sort to remove duplicates, which makes it lower than UNION ALL
- ORDER BY clause should be only used on the last SELECT statement in the UNION query

```mssql
select ID, Name, Email from tblIndiaCustomers 
UNION
select ID, Name, Email from tblUkCustomers 

select ID, Name, Email from tblIndiaCustomers 
UNION ALL
select ID, Name, Email from tblUkCustomers 
UNION ALL 
select ID, Name, Email from tblUSCustomers 
order by Name
```

![image-20190224172714090](/Users/qing/Desktop/note/pic/image-20190224172714090.png)

- UNION & JOINS

  UNION combines rows from 2 or more tables, while JOINS combine columns from 2 or more table



## stored procedure

### CREATE PROCEDURE or CREATE PROC:

when u write the same query over and over again, you can save that specific query as a stored procedure and call it just by its name

```mssql
create proc spGetEmployees
as 
begin
	select Name, Gender from tblEmployee
end
```

### stored procedure with parameters

```mssql
spGetEmployeeByGenderAndDepartment 'Male', 1

-- create stored procedure
create proc spGetEmployeeByGenderAndDepartment
@Gender nvarchar(20),
@DepartmentID int
as
begin
	select Name, Gender, DepartmentId from tblEmployee where Gender = @Gender and DepartmentId = @DepartmentId
end

-- change sp
ALTER proc spGetEmployees
as 
begin
	select Name, Gender from tblEmployee 
	order by Name
end

-- delete sp
DROP proc spGetEmployee

-- encrypt the text of sp
alter proc spGetEmployeeByGenderAndDepartment
@Gender nvarchar(20),
@DepartmentID int
WITH ENCRYPTION
as
begin
	select Name, Gender, DepartmentId from tblEmployee where Gender = @Gender and DepartmentId = @DepartmentId
end

```

### output parameters

- keywords OUT or OUTPUT

  ```MSSQL
  create proc spGetEmployeeCountByGender
  @Gender nvarchar(20),
  @EmployeeCount int OUTPUT
  as 
  begin
  	select @EmployeeCount = COUNT (Id)
  	from tblEmployee
  	where Gender = @Gender
  end
  
  -- execute 
  declare @TotalCount int
  execute spGetEmployeeCountByGender @EmployeeCount = 'male', @TotalCount out -- 没有out/output, print NULL
  print @TotalCount
  
  -- or
  
  declare @TotalCount int
  execute spGetEmployeeCountByGender @EmployeeCount = @TotalCount out, @Gender = 'male'
  print @TotalCount
  ```



### useful system stored proc

- sp_help 

  can view any database object like table, sp, trigger etc

- sp_helptext procedure_name

- sp_depends 

  can view what table sp depends on or what sp depends on this table

### output parameters & return values

**whenever u execute a sq, it returns an integer status variable.** *usually, zero: success; non-zero: failure*

- both are OK:

  - output parameters

    ```MSSQL
      create proc spGetTotalCountofEmployees1
      @TotalCount int output
      as begin
      	select @TotalCount = count(ID) from tblEmployee
      end
      ------------------------------------
      declare @TotalEmployees int
      execute spGetTotalCountofEmployees1 @TotalEmployees out
      select @TotalEmployees
    ```

  - return values

    ```MSSQL
      create proc spGetTotalCountofEmployees2
      as begin
      	return(select count(ID) from Emplyees)
      end
      --------------
      declare @TotalEmployees int
      execute @TotalEmployees = spGetTotalCountofEmployees2
      select @TotalEmp;oyees
    ```

- only parameters work

  - output parameters ✅

    ```mssql
    create proc spGetNamebyId1
    @Id int,
    @Name nvarchar(20) output
    as begin
    	select @Name = Name from tblEmployee where Id = @Id
    end
    
    declare @Name nvarchar(20)
    execute spGetNamebyId1 1, @Name out
    print @Name
    ```

  - return values ❌

    ```mssql
    create proc spGetNamebyId2
    @Id int
    as begin
    	return (select Name from tblEmployee where Id = @Id)
    end
    
    declare @EmployeeName nvchar(20)
    execute @EmployeeName = spGetNamebyId2 1
    print @EmployeeName
    ```

    error: convert the nvchar 'Sam' to int

![image-20190224214224153](/Users/qing/Desktop/note/pic/return value & output parameters.png)



### advantages of using sq

![image-20190224215557725](/Users/qing/Desktop/note/pic/pros of sp.png)



## DateTime

### datatime

![image-20190224221302367](/Users/qing/Desktop/note/pic/DateTime.png)

 ![image-20190224223441495](/Users/qing/Desktop/note/pic/DateTimeFunction.png)

![image-20190224223839287](/Users/qing/Desktop/note/pic/DateTimeFunctionQuery.png)



### isdate

- ISDATE() - 1 for success, 0 for failure

  >  for datetime2 values, isdate returns 0

  ![image-20190224225522333](/Users/qing/Desktop/note/pic/isdate.png)



### Day, Month, Year

![image-20190224225927697](/Users/qing/Library/Application Support/typora-user-images/image-20190224225927697.png)



### DateName

![image-20190224230728633](/Users/qing/Desktop/note/pic/DateName.png)

![image-20190224230825558](/Users/qing/Desktop/note/pic/DateName_abbr.png)



### DatePart, DateAdd, DateDiff

![image-20190224231941720](/Users/qing/Desktop/note/pic/datepart dateadd datediff.png)



### caculate age

![image-20190224234412373](/Users/qing/Desktop/note/pic/caculatingAge.png)

```mssql
SELECT Id, Name, DateofBirth, dbo.fnCalculateAge(DateofBirth) as Age FROM tblEmployees

CREATE FUNCTION fnCaculateAge(@DOB datetime)
RETURNS NVARCHAR(50)
AS
BEGIN

DECLARE @DOB DATETIME, @tempdate DATETIME, @years int, @months INT, @days INT
-- SET @DOB = '09/14/1994'

SELECT @tempdate = @DOB

SELECT @years = datediff(year, @tempdate, getdate())
                CASE
                    WHEN(month(@DOB) > month(getdate())) OR
                    (month(@DOB) = month(getdate() )and day(@DOB) > day(getdate() ))
                    THEN 1 ELSE 0
                END
SELECT @tempdate = dateadd (year, @years, @tempdate)
SELECT @months = datediff (month, @tempdate, getdate())  
                CASE
                    WHEN DAY(@DOB) > day(getdate())
                    THEN 1 ELSE 0
                END
SELECT @tempdate = dateadd (month, @months, @tempdate)

SELECT @days = datediff(day, @tempdate, getdate())
    
    DECLARE @Age NVARCHAR(50)
    SELECT @years as Year, @months as Months, @days as [Days]

    RETURN @Age
END
```



## CAST & CONVERT

```mssql
--Syntax of CAST and CONVERT functions from MSDN:
CAST ( expression AS data_type [ ( length ) ] )

CONVERT ( data_type [ ( length ) ] , expression [ , style ] )

--From the syntax, it is clear that CONVERT() function has an optional style parameter, where as CAST() function lacks this capability. 
```

![image-20190302104923108](/Users/qing/Desktop/note/learn/datetime style.png)

The following are the differences between the 2 functions.**

1. Cast is based on ANSI standard and Convert is specific to SQL Server. So, if **portability** is a concern and if you want to use the script with other database applications, use Cast(). 
2. Convert provides **more flexibility** than Cast. For example, it's possible to control how you want DateTime datatypes to be converted using styles with convert function.

The general guideline is to use CAST(), unless you want to take advantage of the style functionality in CONVERT().



## math function

### ABS

```mssql
Select ABS(-101.5) -- returns 101.5, without the '-'
```

### CEILING & FLOOR

```mssql
Select CEILING(15.2) -- Returns 16
Select CEILING(-15.2) -- Returns -15
Select FLOOR(15.2) -- Returns 15
Select FLOOR(-15.2) -- Returns -16
```
### POWER

```mssql
POWER(2,3) -- Returns 8
```
### RAND

RAND([Seed_Value]) - Returns a random float number between 0 and 1. Rand() function takes an optional seed parameter. When seed value is supplied, the RADN() function always returns the same value for the same seed.

```mssql
Select RAND(1) -- Always returns the same value
/*
generate a random number between 1 and 100
*/
Select FLOOR(RAND() * 100)
```
### SQUARE

```mssql
Select SQUARE(9) -- Returns 81
```
### SQRT

```mssql
Select SQRT(81) -- Returns 9
```
### ROUND
ROUND ( numeric_expression ,length [,function] )

1. Length parameter, specifies the number of the digits that we want to round to. If the length is a positive number, then the rounding is applied for the decimal part, where as if the length is negative, then the rounding is applied to the number before the decimal.
2. The optional function parameter, is used to indicate rounding or truncation operations. A value of 0, indicates rounding, where as a value of non zero indicates truncation. Default, if not specified is 0.
```mssql
-- Round to 2 places after (to the right) the decimal point
Select ROUND(850.556, 2) -- Returns 850.560

-- Truncate anything after 2 places, after (to the right) the decimal point
Select ROUND(850.556, 2, 1) -- Returns 850.550

-- Truncate anything after 1 place, after (to the right) the decimal point
Select ROUND(850.556, 1, 1) -- Returns 850.500

-- Round the last 2 places before (to the left) the decimal point
Select ROUND(850.556, -2) -- 900.000

-- Round the last 1 place before (to the left) the decimal point
Select ROUND(850.556, -1) -- 850.000
```



## SCALAR USER DEFINED FUNCTIONS(UDF)

### **create**

```mssql
CREATE FUNCTION Function_Name(@Parameter1 DataType, @Parameter2 DataType,..@Parametern Datatype)
RETURNS Return_Datatype
AS
BEGIN
    Function Body
    Return Return_Datatype
END
```

**Scalar functions** may or may not have parameters, but always return a single (scalar) value. The returned value can be of any data type, except **text, ntext, image, cursor, and timestamp**.

### **call**

**When calling a scalar user-defined function**, you must supply a two-part name, **OwnerName.FunctionName**. **dbo** stands for database owner.

```mssql
Select dbo.Age( dbo.Age('10/08/1982') 
```

**You can also invoke it using the complete 3 part name**, DatabaseName.OwnerName.FunctionName.
```mssql
Select SampleDB.dbo.Age('10/08/1982')
```



### **SCALAR FUNCTION or STORED PROCEDURE ?**

1. SP cannot use stored procedures in a **select or where clause**

###alter, drop

To alter a function we use ALTER FUNCTION FuncationName statement and to delete it, we use DROP FUNCTION FuncationName.

To view the text of the function use sp_helptext FunctionName



### Inline Table Valued Functions

**Create a function that returns EMPLOYEES by GENDER**
CREATE FUNCTION fn_EmployeesByGender(@Gender nvarchar(10))
RETURNS TABLE
AS
RETURN (Select Id, Name, DateOfBirth, Gender, DepartmentId
      from tblEmployees
      where Gender = @Gender)



## Derived table and CTE in sql server

### views

![image-20190419151743853](/Users/qing/Desktop/note/pic/views1.png)



### Temp tables

![image-20190419151938341](/Users/qing/Desktop/note/pic/temp table.png)

```mssql
select deptname, departmentID, count(*) as totalemployees
into #tempEmployeeCount
FROM tblemployee
JOIN tbldepartment
ON tblemployee.departmentID = tbldepartment.deptID
GROUP BY deptname, departmentID

SELECT deptname, totalemployee
FROM #tempemployeecount
WHERE totalemployees >= 2

DROP TABLE #tempemployeecount
```



### table variable

![image-20190419201343648](/Users/qing/Desktop/note/pic/table variable.png)

```mssql
DECLARE @tblemployeecount TABLE (deptName nvchar(20), departmentID int, totalemployees int)

INSERT @tblemployeecount
SELECT deptname, departmentID, COUNT (*) AS totalemployees
FROM tblemployee
JOIN tbldepartment
ON tblemployee.departmentid = tbldepartment.deptid
GROUP BY deptname, departmentid

SELECT deptname, totalemployees
FROM @tblemployeecount
WHERE totalemployees >= 2
GO
```



### derived table

![image-20190419202722183](/Users/qing/Desktop/note/pic/Derived table.png)

```mssql
SELECT deptname, totalemployees
FROM 
(
	SELECT deptname, departmentid, COUNT(*) AS totalemployees
	FROM tblemployee
	JOIN tbldepartment
	ON tblemployee.departmentID = tbldepartment.deptID
	GROUP BY deptname, departmentid
)
AS employeecount
WHERE totalemployees >= 2
GO
```



### CTE

![image-20190419204425478](/Users/qing/Desktop/note/pic/CTE.png)

```mssql
WITH employeecount (deptname, deptmentid, totalemployees)
AS 
(
	SELECT deptname, departmentid, count(*) AS totalemployees
	FROM tblemployee
	JOIN tbldepartment
	ON tblemployee.departmentid = tbldepartment.deptid
	GROUP BY deptname, departmentid
)

SELECT deptname, totalemployees
FROM employeecount
WHERE totalemployees >= 2
```



## CTE

### 1

- 

![image-20190419205202005](/Users/qing/Desktop/note/pic/cte1.png)

- A CTE can **only ** be referenced by a SELECT, INSERT, UPDATE, DELETE statement, that **immediately** follows the CTE.



- Creating **multiple** CTE using a single WITH 

  ![image-20190419211805698](/Users/qing/Desktop/note/pic/multiple CTE.png)

 

### Updateable CTE

#### 1. CTE on 1 base table

![image-20190419212947688](/Users/qing/Desktop/note/pic/cte on base table.png)

— if a CTE is based on a single base table, then UPDATE works as expected

#### 2. CTE on 2 base table

- 

![image-20190419213154436](/Users/qing/Desktop/note/pic/CTE on 2 base tables.png)

 

- ![image-20190419214447585](/Users/qing/Desktop/note/pic/cte on 2base tables.png)

   — if a CTE is based on more than 1 base table, and UPDATE affects only 1 base table, UPDATE succeeds **but not always as expected**

- 

![image-20190419213547222](/Users/qing/Desktop/note/pic/cte on 2 base table.png)

— if a CTE is based on more than 1 base table, and the UPDATE affects multiple base tables, UPDATE is not allowed.



### Recursive CTE

![image-20190419221933433](/Users/qing/Desktop/note/pic/recursive cte1.png)

![image-20190419221826334](/Users/qing/Desktop/note/pic/recursive CTE.png)



## Normalization

![image-20190419222509183](/Users/qing/Desktop/note/pic/normalization1.png)

- ![image-20190419222853213](/Users/qing/Desktop/note/pic/normalization2.png)



