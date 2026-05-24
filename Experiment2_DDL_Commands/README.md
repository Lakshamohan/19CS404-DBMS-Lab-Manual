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
<img width="952" height="395" alt="494667736-6a6feebd-3659-4180-98ab-04aad57ce1f8" src="https://github.com/user-attachments/assets/b607c9d0-44e8-43e7-8930-fd40b28dfe3a" />


```sql
INSERT INTO Products(Name,Category,Price,Stock)VALUES
("Smartphone","Electronics",800,150),
("Headphones","Accessories",200,300);
```

**Output:**

<img width="1192" height="341" alt="494668121-2ef0fea9-897d-432e-bcc4-9e953736453b" src="https://github.com/user-attachments/assets/2a546bc7-57f6-4c83-ac82-35ced1d1340d" />


**Question 2**
---
<img width="955" height="450" alt="494667837-d2fe2391-cf6e-462e-909b-0cae3b12a0ad" src="https://github.com/user-attachments/assets/6cf5c883-3079-44a0-9cbf-c7023a1c4873" />


```sql
ALTER TABLE books ADD COLUMN ISBN varchar(30);
ALTER TABLE books ADD COLUMN domain_dep varchar(30);
```

**Output:**
<img width="1192" height="372" alt="494668214-fa63fe0d-aaad-454d-89d0-50b49f576610" src="https://github.com/user-attachments/assets/93b87fa7-ce35-42a7-8e5a-c3a12b21ce58" />


**Question 3**
---
<img width="1006" height="255" alt="494669166-9d071155-a7ce-40ce-af08-add67d019e8b" src="https://github.com/user-attachments/assets/b8666e9c-594c-434e-a81e-7879771dbc8a" />


```sql
create table Orders
(
OrderID  INTEGER primary key,
OrderDate  DATE  not NULL,
CustomerID  INTEGER  references Customers(CustomerID)
);
```

**Output:**

<img width="1293" height="160" alt="494668457-b07dd8f1-e1d5-4fe2-a41a-149f60c60280" src="https://github.com/user-attachments/assets/ded37fee-cedf-4894-99b6-e754286f1c5d" />


**Question 4**
---
<img width="947" height="218" alt="494668481-bcb912e9-6462-4395-84cf-34c9e60f99c6" src="https://github.com/user-attachments/assets/e8470340-21eb-4788-90ae-af16fbf8bc5f" />


```sql
ALTER TABLE employee ADD first_name varchar(50);
ALTER TABLE employee ADD last_name varchar(50);
```

**Output:**

<img width="1152" height="187" alt="494668516-be23ac5e-b031-46d5-8d06-a44266f3b8e2" src="https://github.com/user-attachments/assets/528255a2-8222-49c2-af1f-9e3f5cd9a9eb" />


**Question 5**
---
<img width="571" height="246" alt="494668545-dd3c2c69-4e7c-4713-9663-0ffbc2fa3f77" src="https://github.com/user-attachments/assets/0ff6b049-989f-4b5d-a5ef-5911686f1875" />


```sql
INSERT INTO Products(ProductID, ProductName, Price, Stock)
select ProductID, ProductName, Price, Stock FROM Discontinued_products;
```

**Output:**
<img width="851" height="165" alt="494668590-854cd4e8-6cdf-4a8b-9eee-4830f5c18e6a" src="https://github.com/user-attachments/assets/c702839e-d7ab-4aca-97ca-4efa3fee0514" />


**Question 6**
---
<img width="1047" height="252" alt="494668626-ead66360-9343-445a-a570-519e09f6be2f" src="https://github.com/user-attachments/assets/4e26021c-08b6-4992-a5ae-250cb9c06052" />


```sql
create table Attendance (
AttendanceID INTEGER primary key,
EmployeeID  INTEGER  references Employees(EmployeeID),
AttendanceDate  DATE,
Status  TEXT check(status=='Present' or status=='Absent' or status=='Leave')
);
```

**Output:**
<img width="1302" height="182" alt="494668689-0b4e446f-d0de-4fc4-9ac4-705c3dea3a48" src="https://github.com/user-attachments/assets/3bfc3e25-2e2c-4d4a-b033-605c9f681bce" />


**Question 7**
---
<img width="872" height="273" alt="494668738-c1a297d2-1273-4828-967a-948bbd150400" src="https://github.com/user-attachments/assets/12be9621-1963-458d-bfa4-836dccf5faf0" />


```sql
create table Employees(
EmployeeID INTEGER primary key,
FirstName varchar(30) NOT NULL,
LastName varchar(30) NOT NULL,
Email varchar(30) UNIQUE,
Salary INTEGER CHECK(Salary>0),
DepartmentID  INTEGER references  Departments(DepartmentID)
);
```

**Output:**

<img width="1301" height="258" alt="494668800-e36b851c-e9cb-40d9-a601-fe563aa887f3" src="https://github.com/user-attachments/assets/cf4cba1a-8141-494c-ac03-057e0524e186" />


**Question 8**
---
<img width="807" height="155" alt="494668832-01724311-4363-4c16-9e77-29c06fc8910b" src="https://github.com/user-attachments/assets/f3df76c0-fe2a-4b1c-a1a3-9945863cdefc" />


```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
values(201,"David Lee","M","Physics",92);
```

**Output:**
<img width="1120" height="136" alt="494668862-176e3c9d-1c35-47f0-8fa7-4bc8903831da" src="https://github.com/user-attachments/assets/d93b6767-36cb-4fe9-b787-b165b69e2212" />


**Question 9**
---
<img width="1310" height="167" alt="494668893-85c619b8-4cab-4c7b-b5b0-f603e3780f4f" src="https://github.com/user-attachments/assets/9ad08017-6e54-4bdd-b0db-4073b31568ef" />


```sql
create table jobs(
job_id INTEGER , 
job_title varchar(30) DEFAULT "",
min_salary INTEGER DEFAULT 8000,
max_salary INTEGER DEFAULT NULL
);

```

**Output:**
<img width="1298" height="215" alt="494668931-369bafdb-d83a-4cc6-83ad-2ce66976710a" src="https://github.com/user-attachments/assets/9240fc38-bc20-4b2f-a9a3-77db4294f1a7" />


**Question 10**
---
<img width="757" height="237" alt="494668973-87fa6108-5dcd-4160-8bcc-0c142c68c41e" src="https://github.com/user-attachments/assets/aa89ddcc-4467-4a3f-87fc-2872ed081776" />


```sql
CREATE TABLE Departments
(DepartmentID  INTEGER,
DepartmentName TEXT
);

```

**Output:**
<img width="1197" height="207" alt="494669051-c28cc078-4ab0-4272-b761-bf4f08392e6a" src="https://github.com/user-attachments/assets/469a4a55-6384-4cfc-89e1-5658bff7ee44" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
<img width="1237" height="62" alt="494669277-82bf8a65-4624-4b1a-bae6-cc0bfaf89303" src="https://github.com/user-attachments/assets/ebae6b77-2727-4bce-8bfa-e0cc71f2832c" />
