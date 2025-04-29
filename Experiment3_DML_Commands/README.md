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
--
-- Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

```sql
--
update Employees
set salary=8000
where employee_id=105 
 and salary<5000;

```

**Output:**

![image](https://github.com/user-attachments/assets/f99a6110-d3fd-48d8-a466-f2082b88213d)

**Question 2**
---
-- Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table

```sql
-- 
update products
set reorder_lvl=reorder_lvl*1.3
where category='Food' and quantity<(0.5*reorder_lvl);
```

**Output:**

![image](https://github.com/user-attachments/assets/a1cf1a45-5379-441b-b705-f06ce3553f3b)

**Question 3**
---
-- Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.
```sql
-- 
update suppliers
set supplier_name='A1 Suppliers'
where supplier_id=8;
```

**Output:**



**Question 4**
---
-- Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

```sql
--
update Employees
set email='Unavailable';
```

**Output:**

![image](https://github.com/user-attachments/assets/2174fe76-69e3-400d-acb1-06e4a0f3876b)


**Question 5**
---
-- Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```sql
--
delete from Customer
where (grade=3 or agent_code='A008') and outstanding_amt<5000;
```

**Output:**
![image](https://github.com/user-attachments/assets/e8023c13-bb00-4f2a-869c-12abc14fc4f6)


**Question 6**
---
-- 
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
--
delete from Customer
where CUST_COUNTRY not in ('India','USA');
```

**Output:**

![image](https://github.com/user-attachments/assets/a8e9950f-8851-4c41-a321-1ef663ae0460)


**Question 7**
---
-- Write a SQL statement to display name and commission of first 5 salesmen.

table info

salesman(name,commission) 

```sql
--
select name,commission
from salesman
limit 5;


```

**Output:**

![image](https://github.com/user-attachments/assets/1e09dc1c-49fc-4886-8010-5ec642a5145d)


**Question 8**
---
-- Write a SQL query to assess the performance of value2 as 'Poor', 'Average', or 'Excellent' based on whether it is less than 30, between 30 and 70, or greater than 70 in the Calculations table
```sql
--
select id,value2,
case
when value2<30 then 'Poor'
when value2 between 30 and 70 then 'Average'
when value2>70 then 'Excellent'
end as performance
from Calculations;

```

**Output:**

![image](https://github.com/user-attachments/assets/568a3988-7181-47fa-9e58-176ec7c983b1)


**Question 9**
---
-- Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission


```sql
--
select salesman_id,name,city,commission
from salesman
where city not in('Paris','Rome');
```

**Output:**

![image](https://github.com/user-attachments/assets/1b031e64-273a-4c3b-a981-fab6ce082177)

**Question 10**
---
-- 
Write a SQL query to retrieve all orders where the purchase amount is between 500 and 4000 but exclude orders with purchase amounts of 948.50 and 1983.43. The query should return the columns: ord_no, purch_amt, ord_date, customer_id, and salesman_id.

```sql
--
select ord_no,purch_amt,ord_date,customer_id,salesman_id
from orders
where purch_amt between 500 and 4000 and purch_amt not in (948.50,1983.43);
```

**Output:**

![image](https://github.com/user-attachments/assets/9eb3fb44-ed71-49d7-8c70-6e712c645bd4)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
