# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

Write a SQL query to  find the average salary of all employees?

Table: employee <br>

name        type <br>
----------  ---------- <br>
id          INTEGER <br>
name        TEXT <br>
age         INTEGER <br>
city        TEXT <br>
income      INTEGER <br>

```sql
select AVG(income) as Average_Salary
from employee;
```

**Output:**

<img width="507" height="390" alt="image" src="https://github.com/user-attachments/assets/0a93304b-8a87-4baf-bb95-064bc415d3ec" />


**Question 2**

Write a SQL query to find the customer with longest name?

Table: customer

name        type <br>
----------  ---------- <br>
id          INTEGER <br>
name        TEXT <br>
city        TEXT <br>
email       TEXT <br>
phone       INTEGER <br>

```sql
select name,MAX(length(name)) as length
from customer;
```

**Output:**

<img width="663" height="390" alt="image" src="https://github.com/user-attachments/assets/2e1e5981-1dd6-41fc-981b-bf313e68feeb" />

**Question 3**

Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type <br>
----------  ---------- <br>
id          INTEGER <br>
name        TEXT <br>
city        TEXT <br>
email       TEXT <br>
phone       INTEGER <br>

```sql
select count(distinct city) as unique_cities
from customer;
```

**Output:**

<img width="467" height="397" alt="image" src="https://github.com/user-attachments/assets/57cf53e6-2195-47f7-bbe5-5f2aab6a574a" />


**Question 4**

What is the count of male and female patients?

Sample table: Patients Table

<img width="1076" height="161" alt="image (3)" src="https://github.com/user-attachments/assets/e513d4e9-f07e-4f26-958e-84c18020cb51" />

```sql
select Gender,count(*) as TotalPatients
from Patients
group by Gender;
```

**Output:**

<img width="630" height="427" alt="image" src="https://github.com/user-attachments/assets/162a5349-6a7b-41f1-8126-ff88822238ec" />

**Question 5**

How many prescriptions were written for each medication?

Sample tablePrescriptions Table

<img width="1082" height="154" alt="image (8)" src="https://github.com/user-attachments/assets/f4fea56d-577a-4b87-9a33-74f8a772a5d0" />

```sql
select Medication,count(*) as TotalPrescriptions
from Prescriptions
group by Medication;
```

**Output:**

<img width="767" height="827" alt="image" src="https://github.com/user-attachments/assets/731068e5-47a1-45e7-b3a9-f986f6249604" />


**Question 6**

Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.

Sample table: employee

<img width="1011" height="215" alt="unnamed" src="https://github.com/user-attachments/assets/ec528ac5-b136-4edb-a919-7069c9504da2" />

```sql
select age,MAX(income)
from employee
group by age
having MAX(income)>2000000;
```

**Output:**

<img width="607" height="437" alt="image" src="https://github.com/user-attachments/assets/0956e07b-181a-4a5d-91f9-ea1acbf21acb" />


**Question 7**

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

Sample table: employee1

<img width="1031" height="203" alt="unnamed" src="https://github.com/user-attachments/assets/37506e16-5f0c-4b5a-a6d8-7ef6a00ffb52" />


```sql
select jdate,MIN(workhour)
from employee1
group by jdate
having MIN(workhour)<10;
```

**Output:**

<img width="632" height="512" alt="image" src="https://github.com/user-attachments/assets/71386be3-6484-4d35-b6c6-081b4ff6af22" />

**Question 8**

Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

Sample table: products

<img width="972" height="212" alt="unnamed" src="https://github.com/user-attachments/assets/60a54e4b-3707-4515-a153-9a347370420c" />

```sql
select category_id,MIN(price) as Price
from products
group by category_id
having MIN(price)<10;
```

**Output:**

<img width="628" height="442" alt="image" src="https://github.com/user-attachments/assets/2193b855-bba9-4c19-9a03-9f8046e21630" />


**Question 9**

Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1

<img width="1031" height="203" alt="unnamed" src="https://github.com/user-attachments/assets/c1a614be-fa07-4d16-a54e-f457931ab7d2" />

```sql
select jdate,SUM(workhour)
from employee1
group by jdate
having SUM(workhour)>40;
```

**Output:**

<img width="656" height="455" alt="image" src="https://github.com/user-attachments/assets/0e97f44e-58b0-4218-8ae5-146196c3e320" />


**Question 10**

Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer

<img width="668" height="138" alt="image (3)" src="https://github.com/user-attachments/assets/0e4f38ec-a9b2-4d6f-9803-b292757ee671" />


```sql
select count(city) as COUNT
from customer
where city="Noida";
```

**Output:**

<img width="456" height="380" alt="image" src="https://github.com/user-attachments/assets/73df409b-b071-499a-86a9-984e7b22ebbc" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
