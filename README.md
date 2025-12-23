# Dabase Lesson Content
- [Dabase Lesson Content](#dabase-lesson-content)
  - [DESCRIPTION DATASET](#description-dataset)
    - [](#)
  - [Lesson 1 : Basic Function](#lesson-1--basic-function)
    - [SELECT](#select)
    - [ORDER BY](#order-by)
    - [SELECT DISTINCT](#select-distinct)
    - [LIMIT](#limit)
    - [COUNT()](#count)
  - [Lesson 2 : Basic Filtering](#lesson-2--basic-filtering)
    - [WHERE](#where)
    - [AND/OR](#andor)
    - [BETWEEN](#between)
    - [IN](#in)
    - [LIKE](#like)
  - [Lesson 3 : Basic Grouping](#lesson-3--basic-grouping)
    - [GROUP BY](#group-by)
    - [HAVING](#having)
    - [LENGTH ,LOWER, UPPER](#length-lower-upper)
    - [LEFT RIGHT](#left-right)
    - [CONCATINATE](#concatinate)
    - [POSITION](#position)
    - [SUBSTRING](#substring)
    - [INTERVAL and TIMESTAMP](#interval-and-timestamp)
  - [Lesson 4 : Casting type](#lesson-4--casting-type)
    - [EXTRACT](#extract)
    - [TO\_CHAR](#to_char)
    - [Mathematical Function operation](#mathematical-function-operation)
    - [CASE WHEN](#case-when)
    - [CASE WHEN SUM](#case-when-sum)
    - [COALESCE](#coalesce)
    - [CAST](#cast)
    - [REPLACE](#replace)
  - [Lesson 5 : Join](#lesson-5--join)
    - [INNER JOIN](#inner-join)
    - [FULL-OUTER JOIN](#full-outer-join)
    - [LEFT-OUTER JOIN](#left-outer-join)
    - [RIGHT-OUTER JOIN](#right-outer-join)
    - [JOIN MULTIPLETABLE](#join-multipletable)
    - [UNION](#union)
    - [SUBQUERY IN WHERE](#subquery-in-where)
    - [SUBQUERY IN FROM](#subquery-in-from)
    - [CORRELATE SUBQUERY IN SELECT](#correlate-subquery-in-select)
  - [Lesson 6 : Manging Table \& Databasee](#lesson-6--manging-table--databasee)
    - [CREATE DATABASE](#create-database)
    - [DATA TYPE](#data-type)
    - [CREATE TABLE](#create-table)
    - [DROP OBJECT](#drop-object)
    - [INSERT](#insert)
    - [CHECK](#check)
    - [ALTER TABLE](#alter-table)
  - [Lesson 7 : View](#lesson-7--view)
    - [UPDATE](#update)
    - [DELETE](#delete)
    - [CREATE VIEW](#create-view)
    - [MATERIALIZED VIEW](#materialized-view)
    - [MANAGING VIEW](#managing-view)
  - [Lesson 8 : Window Function](#lesson-8--window-function)
    - [OVER() with PARTITION BY](#over-with-partition-by)
    - [OVER() with ORDER BY](#over-with-order-by)
    - [RANK()](#rank)
    - [FIRST\_VALUE()](#first_value)
    - [LEAD \& LAG](#lead--lag)
  - [Lesson 9 : Grouping](#lesson-9--grouping)
    - [GROUPING SETS](#grouping-sets)
    - [ROLLUP](#rollup)
    - [CUBE](#cube)
    - [SELF-JOIN](#self-join)
    - [CROSS-JOIN](#cross-join)
    - [NATURAL-JOIN](#natural-join)
  - [Lesson 10 : STORE PROCEDURE \& UDF](#lesson-10--store-procedure--udf)
    - [USER DEFINE FUNCTION](#user-define-function)
    - [TRANSACTION](#transaction)
    - [ROLLBACK](#rollback)
    - [STORE PROCEDURE](#store-procedure)
  - [Lesson 11 : Query optimization](#lesson-11--query-optimization)
    - [USER Management](#user-management)
    - [CREATE USER ROLE](#create-user-role)
    - [GRANT \& REVOKE PRIVILAGE](#grant--revoke-privilage)
    - [INDEX](#index)
    - [B-TREE](#b-tree)
    - [BITMAP INDEX](#bitmap-index)
  - [Lesson 12 : CTE](#lesson-12--cte)
    - [COMMON TABLE EXPRESSION](#common-table-expression)
    - [](#-1)

## DESCRIPTION DATASET
### 
## Lesson 1 : Basic Function
### SELECT
### ORDER BY
### SELECT DISTINCT
### LIMIT
### COUNT()
## Lesson 2 : Basic Filtering
### WHERE
### AND/OR
### BETWEEN
### IN
### LIKE
## Lesson 3 : Basic Grouping
### GROUP BY
### HAVING
### LENGTH ,LOWER, UPPER
### LEFT RIGHT
### CONCATINATE
### POSITION
### SUBSTRING
### INTERVAL and TIMESTAMP
## Lesson 4 : Casting type
### EXTRACT
### TO_CHAR
### Mathematical Function operation
### CASE WHEN
### CASE WHEN SUM
### COALESCE
### CAST
### REPLACE
## Lesson 5 : Join
### INNER JOIN
### FULL-OUTER JOIN
### LEFT-OUTER JOIN
### RIGHT-OUTER JOIN
### JOIN MULTIPLETABLE
### UNION
### SUBQUERY IN WHERE
### SUBQUERY IN FROM
### CORRELATE SUBQUERY IN SELECT
## Lesson 6 : Manging Table & Databasee
### CREATE DATABASE
``` sql
CREATE DATABASE <DB_NAME>;
```
ใช้ double quote เพื่อให้เกิดการเว้น space ในชื่อ database นั้นได้ ex:
``` sql
CREATE DATABASE "Production DB";
```
>[!Note] ความจริงก็ไม่ควรใช้ space ใช้เป็น _ (Underscore) จะดีกว่า

เราสามารถใช้ Encoding ได้เพื่อกันการตั้งชื่อ db เป็นภาษาอื่นๆ
- default encoding = UTF-8
``` sql 
CREATE DATBASE Production_DB
    WITH ENCODING = 'UTF-8';
```
และสามารถ add comment ให้กับ database นั้นๆได้ด้วย
``` sql
COMMENT ON <DB_NAME> IS 'Some comment to add to this specific database';

```
### DATA TYPE
หลักการคิดเรื่อง data type คือขนาดและความเหมาะสมในการเก็บข้อมูลในชนิดต่างๆ
หลักๆ ข้อมูลแบ่งเป็น 3 data type
1. Numeric
2. String
3. DateTime
4. Others
ซึ่งถ้าให้ลงรายละเอียดจะสามารถ เจาะลึกได้ประมาณนี้

<h2>Numeric</h2>

| Type | StorageSize | Range |
|-----|-----|-----|
|INT| 4 bytes | -2พันล้าน ถึง +2พันล้าน |
|SMALLINT| 2 bytes | -3หมื่น ถึง +3หมื่น |
|BIGINT| 8 bytes|-9ล้านล้านล้าน ถึง +9ล้านล้านล้าน|
|NUMERIC/DECIMAL| Variable| เก็บทศนิยมได้ มันrequire 2 parameters (precision, scale) ; precision =จำนวนหน่วยที่ต้องการเก็บทั้งหมดรวมก่อนหน้าจุด Scale = ตำแหน่งทศนิยมที่ต้องการเก็บ |
|SERIAL|Variable, autofill|1 ถึง 2พันล้าน|

<h2>String</h2>

| Type | StorageSize | Example | Note |
|-----|-----|-----|-----|
|VARCHAR(n) (Character varying)|Length n limit|'hello world'|flexxible ต่ำไปหน่อย|
|CHAR(n) (Character)|Fixxed n length|'K'|Perfomance ไม่ค่อยดีเท่า |
|TEXT | Variable Unlimited length|'hello world WOW'|คิดว่าดีสุด |
>[!NOTE] 
>ทำยังไงกับพวก zipcode , phone-number ที่มี 0นำหน้าแบบไม่มีความหมาย <br>
>ex : 0483 , 0953314298 <br>
>คำตอบคือ ควรจัดเก็บแบบ String  

<h3>DateTime</h3>

|Type|Description|Example|
|-----|-----|-----|
|Date|Date only without time|'2025-12-30'|
|Time (with/without timezone)|Time only without date|'14:30:22.678', '14:30:22.678 +07'|
|timestamp|Date and time |'2025-12-30 14:30:22.678 +07'|
|intervals|Time interval|'3 days 01.02.30.567'|

<h2>Others</h2>

|Type|Description|Example|Range|
|-----|-----|-----|-----|
|boolean|True/False||TRUE,FALSE,NULL|
|enum|list ของค่าตามลำดับ|movie_rating('G','PG',...)|UDF|
|Array|list of value|text[] , int[]||
### CREATE TABLE
ตอนสร้าง table สามารภใส่ constrain ให้ได้ เพื่อกำหนด rule ต่างๆที่ต้อง applied ใน table เพื่อกัน invalid data 
1. Not Null : ห้ามเว้นว่าง
2. Unique : ทุก record มีค่าที่ต่างกันหมด
3. Default : ใส่ค่าให้เมื่อได้ Null มา
4. Primary Key :ต้อง not null และ unique
5. References : ใช้รับค่าจาก tableอื่นๆ (FK) เท่านัน มันจะไม่ยอมให้่มีการ insert ใน column นี้ 
6. Check : เป็นการเช็คให้ชัวร์ว่าผ่านทุก constrains ก่อนจะ insert

``` sql
CREATE TABLE <TABLE_NAME> (
<COLUMN_NAME> <COLUMN_TYPE> <CONSTRAIN>,
<COLUMN_NAME> <COLUMN_TYPE> <CONSTRAIN>
); 
```
ex;

``` sql
CREATE TABLE STAFF(
    STAFF_ID SERIAL PRIMARY KEY,
    STAFF_NAME TEXT,
    STAFF_Saraly INT NOT NULL
);
```
### DROP OBJECT

``` sql
DROP TABLE <TABLE_NAME>;
DROP SCHEMA <SCHEMA_NAME>;

แต่ถ้าต้องการลบแต่ข้อมูลใน Table 
TRUNCATE TABLE <TABLE_NAME>; 
```
### INSERT
```sql
INSERT INTO <TABLE_NAME>
VALUES (value1, value2, value3 ,...);
```
### CHECK
ใช้ตรวจสอบก่อนการทำการ insert rows ต่างๆ
``` sql
CREATE TABLE Staff(
    Name Text CHECK (lenght(Name)>1)
)
```
### ALTER TABLE
เราสามารถ alter constraint ได้
``` sql
ALTER TABLE <Table_Name>
ADD CONSTRAINT <CONSTRAINT_NAME> CHECK(constraint);

ALTER TABLE <Table_Name>
DROP CONSTRAINT <CONSTRAINT_NAME>;\

ALTER TABLE <Table_Name>
RENAME CONSTRAINT <old_constraint> TO <new_constraint>
```
## Lesson 7 : View
### UPDATE
### DELETE
### CREATE VIEW
### MATERIALIZED VIEW
### MANAGING VIEW
## Lesson 8 : Window Function
### OVER() with PARTITION BY
### OVER() with ORDER BY
### RANK()
### FIRST_VALUE()
### LEAD & LAG 
## Lesson 9 : Grouping 
### GROUPING SETS
### ROLLUP
### CUBE
### SELF-JOIN
### CROSS-JOIN
### NATURAL-JOIN
## Lesson 10 : STORE PROCEDURE & UDF
### USER DEFINE FUNCTION
### TRANSACTION
### ROLLBACK
### STORE PROCEDURE
## Lesson 11 : Query optimization
### USER Management
### CREATE USER ROLE
### GRANT & REVOKE PRIVILAGE
### INDEX
### B-TREE
### BITMAP INDEX
## Lesson 12 : CTE
### COMMON TABLE EXPRESSION
### 