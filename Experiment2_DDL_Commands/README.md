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
--
-- Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
--
 insert into Employee(EmployeeID,Name,Department,Salary)
select EmployeeID,Name,Department,Salary
from Former_employees;
```

**Output:**

![image](https://github.com/user-attachments/assets/9d7d7f66-b74e-4693-9f00-74b6431ca403)


**Question 2**
---
-- Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'

```sql
--
 Alter table Employees
add column Date_of_joining Date;
Alter table Employees
rename column job_title to Designation;
```

**Output:**

![image](https://github.com/user-attachments/assets/abc35dc5-f543-4b51-8b74-08f58b58fba3)


**Question 3**
---
-- Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT


```sql
--
 create table Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```

**Output:**

![image](https://github.com/user-attachments/assets/84eacaa0-a3c3-414b-b424-b8b0359391f0)


**Question 4**
---
--Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).


```sql
--
create table Shipments(
ShipmentID INTEGER Primary Key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID));
```

**Output:**

![image](https://github.com/user-attachments/assets/82695b04-2ba9-45ad-8143-f5ae5a759c2b)


**Question 5**
---
-- Write a SQL query to Rename the "city" column to "location" in the "customer" table.

```sql
--
Alter table customer
Rename column city to location;
```

**Output:**

![image](https://github.com/user-attachments/assets/c53dd968-94c0-4431-924d-8dbdf5c57d47)


**Question 6**
---
-- In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as Null.

```sql
--
insert into Employee(EmployeeID,Name,POsition,Department,Salary)values(5,'George Clark','Consultant',' ',' '),(7,'Noah Davis','Manager','HR',60000),(8,'Ava Miller','Consultant','IT',' ');
```

**Output:**

![image](https://github.com/user-attachments/assets/77d907fb-8c4b-48e5-a726-4212f43c684e)


**Question 7**
---
-- Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).


```sql
--
create table Orders(
OrderID INTEGER Primary Key,
OrderDate DATE Not Null,
CustomerID INTEGER,
Foreign key (CustomerID) references Customers(CustomerID));
```

**Output:**

![image](https://github.com/user-attachments/assets/aeb1bd48-388a-44cb-bd4a-6fd1e4d03276)


**Question 8**
---
-- Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
--
 create table contacts(
contact_id INTEGER Primary Key,
first_name TEXT Not NUll,
last_name TEXT Not Null,
email TEXT,
phone TEXT Not Null check(length(phone)>=10));
```

**Output:**

![image](https://github.com/user-attachments/assets/f9d93ff7-fd24-4082-b35f-fe023a0c7827)


**Question 9**
---
--nsert a customer with CustomerID 301, Name Michael Jordan, Address 123 Maple St, City Chicago, and ZipCode 60616 into the Customers table.

```sql
--
insert into Customers(CustomerID,Name,Address,City,ZipCode)values(301,'Michael Jordan','123 Maple St','Chicago',60616);
```

**Output:**

![image](https://github.com/user-attachments/assets/ad4ff452-b879-4d2c-861e-4f66aed269e5)



**Question 10**
---
-- Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEX

```sql
--
 create table Department(
DepartmentID INTEGER Primary Key,
DepartmentName TEXT unique Not Null,
Location TEXT);
```

**Output:**

![image](https://github.com/user-attachments/assets/5afe1275-9ce4-4a8c-8eb8-3b241ec7d46d)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
