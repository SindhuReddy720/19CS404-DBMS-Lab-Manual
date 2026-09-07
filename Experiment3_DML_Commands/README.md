# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**

Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.

PRODUCTS TABLE <br>

name               type <br>
-----------------  --------------- <br>
product_id         INT <br>
product_name       VARCHAR(100) <br>
category           VARCHAR(50) <br>
cost_price         DECIMAL(10,2) <br>
sell_price         DECIMAL(10,2) <br>
reorder_lvl        INT <br>
quantity           INT <br>
supplier_id        INT <br>
```sql
update products
set reorder_lvl=40
where category="Grocery";
```

**Output:**

<img width="1215" height="487" alt="image" src="https://github.com/user-attachments/assets/16834de3-6bde-4acd-af83-9ed3c3390ddb" />


**Question 2**

Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000 <br>

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------+-----+ <br>
|CUST_CODE| CUST_NAME| CUST_CITY| WORKING_AREA| CUST_COUNTRY| GRADE| OPENING_AMT| RECEIVE_AMT| PAYMENT_AMT|OUTSTANDING_AMT| PHONE_NO  | AGENT_CODE | <br>
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+-------+----+ <br>
| C00013  | Holmes  | London   | London   | UK   |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       | <br>
| C00001  | Micheal | New York | New York | USA  |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       | <br>
| C00020  | Albert  | New York | New York | USA  |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       | <br>

```sql
delete from Customer
where GRADE=3
     AND CUST_NAME LIKE '%BBB%'
     AND PAYMENT_AMT>2000;
```

**Output:**

<img width="1205" height="568" alt="image" src="https://github.com/user-attachments/assets/b12fed00-93bc-41cd-8f44-cb4b064ce0ec" />


**Question 3**

Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id <br>
product_name <br>
category <br>
cost_price <br>
sell_price <br>
reorder_lvl <br>
quantity <br>
supplier_id <br>

```sql
update Products
set product_name="Premium Bread"
where product_id=5;
```

**Output:**

<img width="1216" height="492" alt="image" src="https://github.com/user-attachments/assets/c2efc2c6-538e-49ca-ac14-1680ce9d7008" />


**Question 4**

Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.

cid         name        type        notnull     dflt_value  pk <br>
----------  ----------  ----------  ----------  ----------  ---------- <br>
0           id          INTEGER     0                       1 <br>
1           value1      REAL        0                       0 <br>
2           value2      REAL        0                       0 <br>
3           base        INTEGER     0                       0 <br>
4           exponent    INTEGER     0                       0 <br> 
5           number      REAL        0                       0 <br>
6           decimal     REAL        0                       0 <br>
 

```sql
select id,value1,
  CASE 
     WHEN value1>50 THEN "High"
     ELSE "Low"
  END AS value_category
FROM Calculations;
```

**Output:**

<img width="1206" height="367" alt="image" src="https://github.com/user-attachments/assets/42aac77e-cd8d-42d9-b9d6-0891116a3a8c" />


**Question 5**

Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id <br>
product_name <br>
category <br>
cost_price <br>
sell_price <br>
reorder_lvl <br>
quantity <br>
supplier_id <br>

```sql
update Products
set quantity=quantity*1.1;
```

**Output:**

<img width="1203" height="692" alt="image" src="https://github.com/user-attachments/assets/ee02b873-e41b-4266-99f7-cf4194af296a" />


**Question 6**

Write a SQL query to retrieve the year, month, and day from the hiredate column in the emp table.

```sql
select strftime('%Y',hiredate) AS Year,
       strftime('%m',hiredate) AS Month,
       strftime('%d',hiredate) AS Day
from emp;
```

**Output:**

<img width="902" height="465" alt="image" src="https://github.com/user-attachments/assets/1cf33e97-c06d-43bd-a9dc-c753c7df8631" />

**Question 7**

Write a SQL query to calculate the discounted price for each product. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage <br>
------------+----------------+--------------------- <br>
101 | 50.00 | 0.10 <br>
102 | 75.00 | 0.15 <br>
103 | 100.00 | 0.20 <br>

```sql
select product_id,original_price,discount_percentage,original_price*(1-discount_percentage)
AS discounted_price
from Products;
```

**Output:**

<img width="1211" height="512" alt="image" src="https://github.com/user-attachments/assets/cf664047-8e3d-4d07-a394-215600ccb044" />

**Question 8**

Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table

name               type <br>
--------------  ---------- <br>
product_id         INT <br>
product_name       VARCHAR(10) <br>
category           VARCHAR(50) <br>
cost_price         DECIMAL(10) <br>
sell_price         DECIMAL(10) <br>
reorder_lvl        INT <br>
quantity              INT <br>
supplier_id           INT <br>

```sql
update products
set reorder_lvl=reorder_lvl*1.3
where category='Food' 
   AND quantity<(reorder_lvl*0.5);
```

**Output:**

<img width="1212" height="457" alt="image" src="https://github.com/user-attachments/assets/9ee469ea-1c55-481a-8907-6adb12234c60" />


**Question 9**

Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount.

Sample table: products

product_id | original_price | discount_percentage 

------------+----------------+--------------------- 

101 | 100.00 | 0.60 

102 | 150.00 | 0.40 

103 | 200.00 | 0.10

```sql
select product_id,original_price,discount_percentage,(original_price*discount_percentage) AS discount_amount
from products
where (original_price*discount_percentage)>50;
```

**Output:**

<img width="1215" height="351" alt="image" src="https://github.com/user-attachments/assets/4446f908-4085-4abf-8dc1-f1b8b8d08a4b" />


**Question 10**

Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization
```sql
delete from Doctors
where specialization = "Cardiology";
```

**Output:**

<img width="1188" height="412" alt="image" src="https://github.com/user-attachments/assets/90fa544a-020d-4406-bb71-5ed50295776e" />

**SEB Result**

<img width="955" height="77" alt="image" src="https://github.com/user-attachments/assets/9373caba-f89c-4c95-a81f-e3275f33ca9d" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
