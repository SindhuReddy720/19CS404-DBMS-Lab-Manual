# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**

Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
 
-------------+----------------+------------+-------+-------------

 3002 | Nick Rimando   | New York   |   100 |        5001    
 3007 | Brad Davis     | New York   |   200 |        5001  
 3005 | Graham Zusi    | California |   200 |        5002


```sql
ALTER TABLE customer
ADD birth_date timestamp;
```

**Output:**

<img width="1225" height="448" alt="image" src="https://github.com/user-attachments/assets/afe3ca14-440f-4c1b-a99d-63959a12b2a0" />


**Question 2**

Create a table named Orders with the following constraints:

OrderID as INTEGER should be the primary key.  
OrderDate as DATE should be not NULL.  
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1222" height="365" alt="image" src="https://github.com/user-attachments/assets/39c93426-333a-40a4-8d05-41224f3ddb1e" />


**Question 3**

Create a table named Orders with the following columns:

OrderID as INTEGER<br>
OrderDate as TEXT<br>
CustomerID as INTEGER

```sql
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**

<img width="1216" height="445" alt="image" src="https://github.com/user-attachments/assets/4cbbfec6-7147-4d78-8bff-34643049c65d" />


**Question 4**

Create a table named Tasks with the following columns:

TaskID as INTEGER<br>
TaskName as TEXT<br>
DueDate as DATE

```sql
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**

<img width="1222" height="457" alt="image" src="https://github.com/user-attachments/assets/e9188a23-fd46-4d07-ba9f-c14297edc915" />

**Question 5**

Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode <br>
----------  -----------  ----------  ----------  ---------- <br>
302         Laura Croft  456 Elm St  Seattle     98101 <br>
303         Bruce Wayne  789 Oak St  Gotham      10001 <br>

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(302,"Laura Croft","456 Elm St","Seattle",98101);

INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode)
VALUES(303,"Bruce Wayne","789 Oak St","Gotham",10001);
```

**Output:**

<img width="1227" height="461" alt="image" src="https://github.com/user-attachments/assets/aa4783ba-666b-445c-a598-aed5fcda13ab" />


**Question 6**

Create a table named Products with the following constraints:

ProductID should be the primary key.<br>
ProductName should be NOT NULL.<br>
Price is of real datatype and should be greater than 0.<br>
Stock is of integer datatype and should be greater than or equal to 0.

```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName TEXT NOT NULL,
Price REAL CHECK(Price>0),
Stock INTEGER CHECK(Stock>=0)
);
```

**Output:**

<img width="1223" height="357" alt="image" src="https://github.com/user-attachments/assets/d23253d8-5a67-4a00-b83d-02e9e6008066" />


**Question 7**

Create a table named Shipments with the following constraints:

ShipmentID as INTEGER should be the primary key.<br>
ShipmentDate as DATE.<br>
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).<br>
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY(SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1217" height="321" alt="image" src="https://github.com/user-attachments/assets/bf701504-9bc9-4da4-89f2-7715bee40257" />


**Question 8**

Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

ISBN             Title                 Author <br>
---------------  --------------------  --------------- <br>
978-6655443321   Big Data Analytics    Karen Adams <br>

Note: The Publisher and Year columns will use their default values.

```sql
INSERT INTO Books(ISBN,Title,Author)
VALUES("978-6655443321","Big Data Analytics","Karen Adams");
```

**Output:**

<img width="1208" height="407" alt="image" src="https://github.com/user-attachments/assets/02ce97dd-70d6-479d-981d-57015b0354ef" />


**Question 9**

Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id <br>
-------------+----------------+------------+-------+------------- <br>
        3002 | Nick Rimando   | New York   |   100 |        5001 <br>
        3007 | Brad Davis     | New York   |   200 |        5001 <br>
        3005 | Graham Zusi    | California |   200 |        5002

```sql
ALTER TABLE customer
ADD COLUMN discount DECIMAL(5,2);
```

**Output:**

<img width="1210" height="443" alt="image" src="https://github.com/user-attachments/assets/73d88cdf-1f4b-4897-bc4b-93d46699111e" />


**Question 10**

Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.

```sql
INSERT INTO Products(ProductID,Name,Category,Price,Stock)
VALUES(101,"Laptop","Electronics",1500,50);
```

**Output:**

<img width="1227" height="325" alt="image" src="https://github.com/user-attachments/assets/b05bcf58-984b-4cf1-aba6-21779e77ce00" />

**SEB Result**

<img width="967" height="78" alt="image" src="https://github.com/user-attachments/assets/6869662d-4114-4d5b-b60a-18c007221c9c" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
