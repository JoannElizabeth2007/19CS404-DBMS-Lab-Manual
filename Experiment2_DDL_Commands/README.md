# Experiment 2: DDL Commands

### NAME : JOANN ELIZABETH SAMUEL
### REGISTER NUMBER : 212224040139

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
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**

<img width="1188" height="370" alt="image" src="https://github.com/user-attachments/assets/e0471a6e-bd8b-4cf9-b8d7-b1c70740a4de" />

**Question 2**
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.

```
CREATE TABLE Attendance(
AttendanceID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK(Status IN('Present', 'Absent', 'Leave')),
FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**
<img width="1202" height="285" alt="image" src="https://github.com/user-attachments/assets/1bd97343-a4e2-41a0-8d79-82d571da6263" />


**Question 3**
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER
```
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER
);
```

**Output:**


**Question 4**
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (001,'Sarah Parker','Manager','HR',60000);
```

**Output:**
<img width="1201" height="245" alt="image" src="https://github.com/user-attachments/assets/c8aa122c-41a9-4167-a259-6cd89de27458" />

**Question 5**
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
```
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL,
Location TEXT
);
```

**Output:**
<img width="1204" height="289" alt="image" src="https://github.com/user-attachments/assets/449955e8-82bd-468c-818a-42837f6baab6" />


**Question 6**
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
```
CREATE TABLE Locations(
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**
<img width="1205" height="244" alt="image" src="https://github.com/user-attachments/assets/bfd02030-61ce-44c2-a69e-b214f193a090" />


**Question 7**
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

```
INSERT INTO Student_details(RollNo, Name, Gender, Subject,MARKS)
VALUES(201,'David Lee','M','Physics',92);
```

**Output:**
<img width="1204" height="364" alt="image" src="https://github.com/user-attachments/assets/405005da-cc79-474b-b0b9-4b2b1463b501" />


**Question 8**
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```
ALTER TABLE Student_details ADD COLUMN Date_of_birth Date;
```

**Output:**
<img width="1215" height="312" alt="image" src="https://github.com/user-attachments/assets/00cd368c-855c-4c35-a0c6-23cc41050806" />


**Question 9**
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.

```
INSERT INTO Employee(EmployeeID, Name,Position)
VALUES(4,'Emily White','Analyst');
```

**Output:**
<img width="1210" height="366" alt="image" src="https://github.com/user-attachments/assets/20191ae7-f3e0-4d26-8ff8-dec29dd57192" />


**Question 10**
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0

```
ALTER TABLE Student_details ADD COLUMN mobilenumber number;
```

**Output:**
<img width="1206" height="360" alt="image" src="https://github.com/user-attachments/assets/87cf18e7-1249-4426-a018-26eb2ab4c39f" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
