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
    - [Concept \& OVER() with PARTITION BY](#concept--over-with-partition-by)
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
  - [Lesson 13 : Optimize Database](#lesson-13--optimize-database)
    - [Basic Knowledge](#basic-knowledge)

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
ใช้แก้ไขหลังเราสร้าง table ไปแล้ว
- Add, Delete, Rename column/Table
- Add, Drop constraints
- Alter datatype

ex. เราสามารถ alter constraint ได้
``` sql
ALTER TABLE <Table_Name>
ADD CONSTRAINT <CONSTRAINT_NAME> CHECK(constraint);

ALTER TABLE <Table_Name>
DROP CONSTRAINT <CONSTRAINT_NAME>;

ALTER TABLE <Table_Name>
RENAME CONSTRAINT <old_constraint> TO <new_constraint> ;
```
สามารถเพิ่มเงื่อนไขให้มันได้ เพื่อกรองให้ผ่านเงื่อนไขก่อนจะทำ actionนั้นๆ
``` sql
ALTER TABLE <table_name>
DROP COLUMN IF EXISTS <column_name> ;

มันจะ drop column-> firstname ถ้ามันมีอยู่จริง
```
การแก้ไข column type
``` sql
ALTER TABLE <table_name>
ALTER COLUMN <column_name> TYPE <New_type> ;
```
การแก้ไขเพื่อเพิ่มการตั้งค่า set/drop default
``` sql
ALTER TABLE <table_name>
ALTER COLUMN <column_name> SET DEFAULT <VALUE> ;
``` 

## Lesson 7 : View
### UPDATE
ต้องการแก้ไขค่า
```sql
UPDATE <table_name>
SET <Column_name> = <value>;
```
ส่วนใหญ่มันมักจะมาคู๋กับ Where clause เพื่อให้การ update เจาะจงไปใน transaction ที่เราต้องการให้ update จริงๆ<br>
ex.
```sql
UPDATE songs
SET genre = 'POP'
WHERE song_id = 4;
```
### DELETE
ใช้ลบ row ในtable
``` sql
DELETE FROM <table_name>
WHERE <condition>
```
ถ้าเราอยากรู้ว่าเรา deleted อะไรไป สามารถ print log ได้ โดบการใช้ return
``` sql
DELETE FROM <table_name>
WHERE <condition>
RETURNING *
```
### CREATE VIEW
ก่อนที่มันจะเกิด VIEW ขึ้นได้ เราเคยมีท่าที่เป็นการสร้าง Table ที่ทำหน้าที่สร้าง table ที่ ingest ข้อมูลจาก table อื่นๆมา
``` sql
CREATE TABLE <table_name>
AS
SELECT <column_name> 
FROM <table2_name>
WHERE <condition> ;
```
ซึ่งสิ่งนี้มันตามมาด้วยปัญหา:
1. เราจะเก็บข้อมูลซ้ำซ้อน -> Data store redundance
2. data ถ้าเกิดการเปลี่ยนแปลงไป table ปลายทางจะไม่ได้รับรู้ถึงการเปลี่ยนไปของมัน
   
View เลยเข้ามาแก้ปัญหา ณ จุดนี้<br>
โดย View จะทำหน้าที่เหมือนกับ table ทุกประการ แต่การเก็บค่านั้น จะไม่ได้เก็บ physically ข้อมูล แต่เป็นการเก็บ logics ของ Statement นั้น จุดประสงค์ของการใช้ view คือการ query อะไรต่างๆที่ไม่ complex มาก มันจะทำได้รวดเร็วโคดๆ
``` sql
CREATE VIEW <view_name>
AS
<Statement>;

ex.
CREATE VIEW customer_anonymous
AS
SELECT customer_id, initials
FROM customer
WHERE first_name IS NULL ;
```

### MATERIALIZED VIEW
ปัญหาของ view คือ performance มันขึ้นกับ statement ด้านหลัง
``` sql
CREATE MATERIALIZED VIEW <mat_view_name>
AS <statement>;
```
และเมื่อต้องการอัพเดท VIEW ให้ใช้ command ซึ่งจะช่วยให้ไม่ต้อง update data manually ทั้งยังสามารถตั้ง trigger ได้ด้วย
``` sql
REFRESH MATERIALIZED VIEW <view_name>;
```
### MANAGING VIEW
เราสามารถ 
- ALTER View/MaterializeView
- DROP View/MaterializeView
- CREATE OR REPLACE View แต่ทำกับ MaterializeView ไม่ได้

## Lesson 8 : Window Function
### Concept & OVER() with PARTITION BY
หลักการทำงานของ window function ทั่วไปจะเป็นการ apply function อะไรซักอย่าง โดยไม่ต้องการควบรวม(group) rows แบบพวก aggregated function
ซึ่งแปลว่าที่ id เดียวกัน มันจะได้ค่าจากการผ่าน window function เหมือนกัน
``` sql
AGG(agg_column) OVER(PARTITION BY partition_column);
                     |-----------Window-----------|
```
EX :
<img src="utils\Screenshot 2025-12-24 105632.png">
จะสังเกตได้ว่า มันมี no_of_transactions_by_type ที่เกิดจาก window function และได้ค่าเหมือนกันใน customer_id เดียวกัน เนื่องจากใช้ cusyomer_id เป็น partition
``` sql
SELECT *,
SUM (price_in_transaction) OVER(PARTITION BY customer_id)
FROM payment ;
```
>[!NOTE] 
>เราสามารถใส่ PARTITION COLUMN ได้มากกว่า 1 Aggregate function ก็สามารถเปลี่ยนไปได้ด้วย

### OVER() with ORDER BY
สมมุติถ้าเราต้องการ cumulative sum (รวมผลแบบสะสม) เช่น<br>
จะเห็นว่า ที่ column sum จะเป็นค่าของ cumulative sum ของทุก row ลงไปเรื่อยๆ
<img src='utils\Screenshot 2025-12-24 111441.png'>
``` sql
SELECT *,
sum (amount) OVER(ORDER BY payment_date)
from payment;
```
>[!Note]
>เราสามารถใช้ window function แบบ partition ต่อด้วย order ได้ 

```sql
SELECT *
SUM(amount)
  OVER(PARTITION BY custom_id
       ORDER BY payment_date, payment_id
      )
FROM payment ;
```
### RANK()
สามารถจัดอันดับจาก ค่าใน column ต่างๆได้ ex. จัดอันดับหนังที่ยาวนานที่สุด
``` sql
SELECT *
RANK() OVER(ORDER BY length desc)
FROM film ;
```
ถ้าต้องการให้เรียงอันดับของค่า rankด้วยเลย จะใช้ DENSE_RANK()
``` sql
SELECT *
DENSE_RANK() OVER(ORDER BY length desc)
FROM film ;
```
>[!Note]
> Window function ไม่สามารถ อยู่ภายใต้ where clause ได้<br>
> ต้องไปใช้ท่า subquery แทน<br>
> ex. 
``` sql
SELECT *
WHERE(RANK() OVER(ORDER BY length desc)) =1
FROM film ;
                    |
                 Subquery
                    |
                    V
SELECT * FROM(
              SELECT *
              DENSE_RANK() OVER(ORDER BY length desc) as ranking
              FROM film 
              ) 
WHERE ranking = 1
```
### FIRST_VALUE()
มันจะเลือกค่าแรกของทุกๆการกวาด window function เช่น PARTITION
``` sql
SELECT *
FIRST_VALUE(count(*)) OVER(PARTITION BY country ORDER BY count(*))
FROM customer_list ;
```
### LEAD & LAG
LEAD() มันจะเลือกเอาค่าที่ตัวถัดไปมาแปะไว้ มันจะให้ค่าเป็น null เมื่อสุด partition ไม่มีตัวถัดไปให้เอาค่ามาแปะไว้

``` sql
SELECT *
LEAD(name) OVER(PARTITION BY country ORDER BY count(*))
FROM customer_list ;
```
ex. สังเกตว่ามันจะเอาค่าตัวถัดไปมาแปะไว้ ถ้าหมดในgroupของมัน ตัวถัดไป = Null
<img src='utils\Screenshot 2025-12-24 134100.png'>

LAG() มันจะกลับกัน คือจะเอาค่าก่อนหน้ามาแปะไว้แทน
``` sql
SELECT *
LAG(COUNT(*)) OVER(PARTITION BY country ORDER BY count(*))
FROM customer_list ;
```
<img src='utils\Screenshot 2025-12-24 134343.png'>

## Lesson 9 : Grouping 
### GROUPING SETS
ทำการ grouping ตาม set ที่ต้องการ ex.
``` sql
SELECT month, staff_id, SUM(amount)
FROM payment
GROUP BY 
    GROUPING SETS(
            (staff_id),
            (month),
            (staff_id , month)
    );
```
<img src='utils\Screenshot 2025-12-24 141029.png'>

จะสังเกตได้ว่า :<br>
ในบรรทัดแรก,สอง มันเป็นการแบ่งตาม เดือนและstaff_id <br>
ในบรรทัดที่สาม เป็นค่าการแบ่งของ เดือนเท่านั้น รวมstaff_idเข้าด้วยกัน <br>
จะมีบางบรรทัดที่เดือนจะถูกควบรวม เหลือgroupแค่staff_id <br>
ex.แบบบรรทัด 6,7<br>
<img src='utils\Screenshot 2025-12-24 141702.png'>

มันดีกว่าการไปนั่ง group union group union group ที่performance มันจะกากมากๆ

### ROLLUP
Concept RollUp กับ Cube เป็น subclause ของ group by clause <br>
RollUp จะเสมือนเป็นการสร้างความเป็น hierarchy ในตัว
``` sql
GROUP BY
ROLLUP (column1, column2, column3, ...)

มันเทียบได้กับ

GROUP BY
GROUPING SETS(
  (column1, column2, column3),
  (column1, column2),
  (column1),
  ()
)
ex. (year, quater, month)
```
>[!Note]
> ใน RollUp function order ในการเขียนนั้นสำคัญมาก<br>
> Core : ใช้สำหรับ Natural hierarchy ดีสุด

ex.
```sql
SELECT 
  quater,
  month,
  date,
  SUM(amount)
FROM payment
GROUP BY
  ROLLUP(
    quater,
    month,
    date
  )
ORDER BY 1,2,3 ;
```
โดยการเรียงลำดับจะเป็นแบบนี้ มันจะเรียงไปเรื่อยๆจนครบทุกวันในเดือนนั้น
<img src='utils\Screenshot 2025-12-24 145101.png'>

จะปิดด้วย aggregrate ระดับเดือน (rows ที่ 29)
และจบที่ row 30 ที่เป็นการรวมของทั้ง quater นั้น
<img src='utils\Screenshot 2025-12-24 145124.png'>

ถ้าเป็นแบบในบรรทัดที่ 49 คือ รวมยอดทุกquater
<img src='utils\Screenshot 2025-12-24 145136.png'>

### CUBE
คล้ายกับ rollup มากๆ แต่เป็นการทำ grouping set กับทุก combination ที่มี ไม่ใช่แค่ใน hierarchical ดังนั้นก็ไม่ต้องสนเรื่อง Natural hierachy อีกแล้ว
```sql
GROUP BY
CUBE (column1,column2,column3)

มันเทียบเท่ากับการทำ
GROUP BY
  GROUPING SETS(
    (column1,column2,column3),
    (column1,column2),
    (column1,column3),
    (column2,column3).
    (column1),
    (column2),
    (column3),
    ()
)
```
### SELF-JOIN
ใช้แปลงค่าที่ต้องได้จาก table ตัวเอง เช่น
| Student_ID | Student_name | Auditor_id | Commentator_id |
|-----|-----|-----|-----|
|001 | Kim | 003 | 002|
|002 | DD | 004 | 001|
|003 | Katung | 001 | 002 |
|004 | Mean | 002 | 003|

แล้วใช้ self join เพื่อเปลี่ยนค่า id -> name

| Student_ID | Student_name | Auditor_id | Commentator_id |
|-----|-----|-----|-----|
|001 | Kim | Katung | DD|
|002 | DD | Mean | Kim|
|003 | Katung | Kim | DD |
|004 | Mean | DD | Katung|

### CROSS-JOIN
สร้าง cartesina product 
ex. 
|Letter|
|-----|
|A|
|B|

กับ table
|Number|
|-----|
|1|
|2|
|3|

พอ cross join กันจะได้
|Letter|Number|
|---|---|
|A|1|
|A|2|
|A|3|
|B|1|
|B|2|
|B|3|

``` sql
SELECT
t1.column1
t2.column2
FROM table1 t1
CROSS JOIN table2 t2
ไม่ต้อง specific columnในการสร้าง relationship
```

### NATURAL-JOIN
เหมือนกับการ join ทั่วๆไป ต่างกันแค่มัน auto implied column ที่จะเอามาเกิด relationship กันเป็น columnที่ชื่อเหมือนกันเท่านั้น ข้อจำกัดคือ ห้ามมี columnที่ชื่อซ้ำกันมากกว่า 1 ในทั้ง 2 ตาราง

``` sql
SELECT *
FROM payment 
NATURAL LEFT JOIN customer
```

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
## Lesson 13 : Optimize Database
### Basic Knowledge
ก่อนที่จะ optimize DB ได้ต้องรู้ก่อนว่าเราจะช่วยเพิ่มประสิทธิภาพส่วนไหนได้บ้าง 
1. Storage Engine : ทำการ read data ระหว่าง disk กับ memory(RAM) สิ่งที่ต้องจัดการคือ
   1. concurrency
   2. data integrity
2. Query Processor : รับ query จาก sql-server แล้วมันจะไปจัด plan เพื่อ optimal execution 
   
Query Process :<br>
Parsing and Binding : เมื่อรับ query มาแล้วจะทำกระบวนการนี้ ซึ่งจะ 
1. make sure ว่า syntax ถูก แล้ว 
2. translate SQL -> Tree of logical operator
3. make sure ว่า object ต่างๆถูกสร้างไว้จริง 
4. associate ทุก table, column ลง parse tree -> Algebraric tree
5. ส่งไปยัง query optimizer
6. สร้าง execution plan และเลือกอันที่ดีที่สุด เทียบโดย cost : ลงรายละเอียกตรงนี้ 
   1. มันจะมีการทำ "execution plan reuse": เนื่องจากการสร้าง execution plan แต่ละรอบ มันแพง server ก็เลยำยายามจะใช้ plan ที่เคยสร้างไว้อยู่แล้ว @Plan Cache
   2. ก่อนจะส่ง planเข้า storage engine ตัว optimizer มันจะมาเทียบ estimated plan กับ actual plan ที่เคยเก็บไว้ใน plan cache ถ้ามันพบที่ match มันก็จะใช้ตัวนั้น
   3. การใช้ reuse จะ avoid : overhead ของการ create actual execution plan
   4. Noted : execution plan จะไม่ได้เก็บไว้ตลอดเวลานะ มันจะถูกลบออกไปเมื่อครบ ageมัน ด้วยระบบ "Lazy writer process"
   
7. mapping querry expression เป็น tree expression ที่จะถูก execute ผ่าน engine