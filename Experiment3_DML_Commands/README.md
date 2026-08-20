# Experiment 3: DML Commands

### NAME : JOANN ELIZABETH SAMUEL
### REGISTER NUMBER : 212224040139

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
Write a SQL query to Select all patients whose name starts with A.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```
SELECT * FROM Patients WHERE first_name LIKE 'A%';
```

**Output:**
<img width="1208" height="359" alt="image" src="https://github.com/user-attachments/assets/813acf1f-ceee-4e98-97de-840fbad7e19a" />

**Question 2**
<img width="832" height="193" alt="image" src="https://github.com/user-attachments/assets/2130ebc8-d70f-4815-bcf0-6404fb0b70c1" />

```
SELECT SUBSTR(Address, 1,INSTR(Address,'(')-1) AS PlaceName FROM EmployeeInfo;
```

**Output:**
<img width="416" height="323" alt="image" src="https://github.com/user-attachments/assets/9514928b-e2e3-4c34-9083-1b3333198e3b" />

**Question 3**
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization

```
DELETE FROM Doctors WHERE last_name IS NULL;
```

**Output:**
<img width="1204" height="725" alt="image" src="https://github.com/user-attachments/assets/5c51b323-afc3-4e1e-b5ed-2e0ef296d9d7" />

**Question 4**
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization


```
DELETE FROM Doctors WHERE doctor_id IS 1;
```

**Output:**
<img width="1205" height="261" alt="image" src="https://github.com/user-attachments/assets/aa2b9eb2-20ae-4a14-98f0-bfa0c83c04d1" />

**Question 5**
Write a SQL query to calculate the discounted price for each product. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage
------------+----------------+---------------------
101 | 50.00 | 0.10
102 | 75.00 | 0.15
103 | 100.00 | 0.20

```
SELECT product_id, original_price, discount_percentage,original_price *(1-discount_percentage) AS discounted_price FROM Products;
```

**Output:**
<img width="1204" height="456" alt="image" src="https://github.com/user-attachments/assets/5c47fce3-b07f-4d9a-ad28-54a7e88a851f" />

**Question 6**
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```
UPDATE suppliers SET address = '58 Lakeview, Magnolia' WHERE SUPPLIER_ID =5;
```

**Output:**
<img width="1195" height="402" alt="image" src="https://github.com/user-attachments/assets/5729cd9f-a2f3-459a-bd74-22a2b09cf7d7" />

**Question 7**
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```
UPDATE products SET product_name = 'Premium Bread' WHERE product_id=5;
```

**Output:**
<img width="1200" height="428" alt="image" src="https://github.com/user-attachments/assets/f560bceb-19f6-4525-b473-eb84a5854712" />


**Question 8**
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3
```
DELETE FROM Customer WHERE CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada') AND GRADE >=3;

```

**Output:**
<img width="1200" height="799" alt="image" src="https://github.com/user-attachments/assets/b821a72a-b568-4d24-b7d9-7de0911c1d6e" />

**Question 9**
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'.

```
DELETE FROM customer WHERE WORKING_AREA IS 'New York';
```

**Output:**
<img width="796" height="482" alt="image" src="https://github.com/user-attachments/assets/f9f01376-accb-4e21-a4a0-74fc9af542af" />

**Question 10**
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```
SELECT id,decimal,CASE 
WHEN decimal>100 THEN 'High'
WHEN decimal>=50 THEN 'Medium'
ELSE 'Low' END AS category FROM Calculations;
```

**Output:**
<img width="779" height="480" alt="image" src="https://github.com/user-attachments/assets/13d901fe-1be8-4185-b06d-9f4ed9386f34" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
