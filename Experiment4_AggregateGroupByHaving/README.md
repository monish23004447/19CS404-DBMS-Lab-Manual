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
--
-- How many appointments are scheduled for each patient?

```sql
--
select PatientID, count(*) as TotalAppointments
from Appointments
group by PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/fc36bbc7-aa2d-468a-a521-b0a3ba667c48)

**Question 2**
---
-- How many patients are covered by each insurance company?
```sql
--
select InsuranceCompany, count(distinct PatientID) as TotalPatients
from Insurance
group by InsuranceCompany;
```

**Output:**

![image](https://github.com/user-attachments/assets/19ec6ff2-04c9-4080-8878-c56a78d6bdea)


**Question 3**
---
-- How many prescriptions were written for each medication?

```sql
--
select Medication, count(*) as TotalPrescriptions
from prescriptions
group by Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/f9c4780f-1e1b-4364-abe0-dddbcfde23d6)

**Question 4**
---
-- Write a SQL query to find the average length of email addresses (in characters):

```sql
--
select avg(length(email)) as avg_email_length
from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/03dfcfa2-7570-473a-93db-dc83ef07aad0)


**Question 5**
---
-- 
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city
```sql
--
select avg(length(email)) as avg_email_length_below_30
from customer
where city='Mumbai';
```

**Output:**

![image](https://github.com/user-attachments/assets/d17f3292-5973-41e0-bf4a-28e9666f41b8)


**Question 6**
---
-- Write a SQL query to count the number of customers. Return number of customers.

```sql
--
select count(*) as COUNT
from customer;
```

**Output:**

![image](https://github.com/user-attachments/assets/90f6f025-9c96-4065-8c6e-c3e7e4d0926f)


**Question 7**
---
-- 
Write a SQL query to  find the average salary of all employees?


```sql
--
select avg(income) as Average_Salary
from employee;
```

**Output:**
![image](https://github.com/user-attachments/assets/540be69d-c622-4b62-8ca9-701184dc338a)



**Question 8**
---
-- 
Write the SQL query to find how many patients have more than 3 medical records?.
```sql
--
select PatientID, count(*) as TotalRecords
from MedicalRecords
group by PatientID
having count(*) > 3;
```

**Output:**

![image](https://github.com/user-attachments/assets/ecbacda7-1888-4da4-9e69-51da42252bd9)


**Question 9**
---
-- 
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.
```sql
--
select p.category_id, p.product_name, t.Price
from products p
join(
select category_id, max(Price) as Price
from products
group by category_id
having max(Price) > 15)
as t on p.category_id=t.category_id and p.Price=t.Price;
```

**Output:**
![image](https://github.com/user-attachments/assets/3adbaec3-71e2-4034-bf44-1f5c8f9857b2)


**Question 10**
---
-- 
Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.
```sql
--
select count(*) as COUNT
from customer
where city!="Noida";
```

**Output:**

![image](https://github.com/user-attachments/assets/82d47b52-bfd7-4824-b647-97cf0f17e6b0)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
