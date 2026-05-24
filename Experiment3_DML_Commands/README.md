# Experiment 3: DML Commands
# NAME: LAKSHA M
# REG NO: 212224220050
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
---
<img width="682" height="417" alt="496968210-be972849-03da-44ea-93bd-9eff61b23211" src="https://github.com/user-attachments/assets/6810c99f-0e34-4a40-9438-7aa48a8fb107" />


```sql
update Employees
set hire_date='2024-01-24'
where department_id=50;
```

**Output:**

<img width="776" height="222" alt="496968712-6424dc05-0812-4023-a983-6767d4417210" src="https://github.com/user-attachments/assets/e27c1c69-4109-488e-80eb-c3f120316f5f" />


**Question 2**
---
<img width="581" height="550" alt="496968889-3caa367e-001f-4d36-87b7-4709aff8c93c" src="https://github.com/user-attachments/assets/2d48c402-4333-409c-a94f-4b67f087bd45" />


```sql
update SALES
set sell_price=sell_price+3
where product_id IN (select product_id  from PRODUCTS where supplier_id=4);
```

**Output:**

<img width="772" height="282" alt="496969147-241291b1-d3d3-41f7-a43f-da4823300861" src="https://github.com/user-attachments/assets/c72c3abb-97ff-4acf-ac06-ff39bfd9fb0a" />


**Question 3**
---
<img width="747" height="365" alt="496969347-d72e6d02-b356-4814-8bec-1bd74c2bd638" src="https://github.com/user-attachments/assets/aadec72b-c9dc-4690-9c28-ea40f9b21e96" />


```sql
update products
set sell_price=CAST(cost_price*1.35 AS INT) 
where((sell_price-cost_price)/sell_price)*100<30;
```

**Output:**

<img width="707" height="242" alt="496969927-384eafd6-b4d4-40a5-b956-b3af27736c13" src="https://github.com/user-attachments/assets/c0663f50-babd-42ae-9e76-73ad31824cd8" />


**Question 4**
---
<img width="685" height="381" alt="496970080-ec3b8a4d-cac2-410b-af08-1a02c5776999" src="https://github.com/user-attachments/assets/10ba8f76-7c49-45d0-aab9-fe271b256e7a" />


```sql
update Products 
set category='Household'
where product_name like '%Detergent%';
```

**Output:**

<img width="735" height="282" alt="496970348-e8a50a25-0ca0-4df4-9942-a7c4aebbd0d2" src="https://github.com/user-attachments/assets/823b8322-e985-481e-9fc2-f43bd0dec487" />


**Question 5**
---
<img width="682" height="213" alt="496970644-7708a919-9962-405c-8564-8235917e596d" src="https://github.com/user-attachments/assets/e547c507-1a79-4005-b322-ae2c9d44a98d" />


```sql
update suppliers
set supplier_name='A1 Suppliers'
where supplier_id=8;
```

**Output:**

<img width="671" height="227" alt="496970790-b12629cd-46ac-436a-b160-1ce6082a1cb3" src="https://github.com/user-attachments/assets/f8d75406-53ac-4038-aa8d-ea343731af3e" />


**Question 6**
---
<img width="777" height="732" alt="496971022-ab76622e-3ff0-437a-8820-a2341d4657ca" src="https://github.com/user-attachments/assets/4b2f2976-ea79-4680-9a9c-3a4b78e6e838" />


```sql
delete from customer
where AGENT_CODE='A003' or  AGENT_CODE='A008';
```

**Output:**

<img width="480" height="770" alt="496971244-a3ca67fc-9f81-4879-bcf1-75cb12398a85" src="https://github.com/user-attachments/assets/d800cb10-5b06-4f3a-8703-70c9e6623e15" />


**Question 7**
---
<img width="768" height="356" alt="496971364-c3c11e6d-677b-4590-9ce8-1eb4833dab09" src="https://github.com/user-attachments/assets/1ff90d79-b9f4-426f-87d1-0dc8ee5dc777" />


```sql
delete from  Doctors
where (specialization='Pediatrics' or specialization='Cardiology') and last_name  like 'Brown'; 
```

**Output:**

<img width="762" height="677" alt="496971520-4cab9ef9-edf3-4309-8fbc-28769be6ad1d" src="https://github.com/user-attachments/assets/f571bf7d-9004-4583-ba49-546d26f0accd" />


**Question 8**
---
<img width="777" height="491" alt="496971667-1a7c3749-9f57-46e3-8bef-5b3febacbb00" src="https://github.com/user-attachments/assets/b59c3821-3397-4360-ae4b-bdef31ff3bf8" />


```sql
delete from Customer
where CUST_CITY like "l%";
```

**Output:**

<img width="777" height="761" alt="496971866-f5ff3ccd-00a0-4d9f-b370-c19bf08939bc" src="https://github.com/user-attachments/assets/859ec185-6735-4ecb-8078-2031e90e4877" />


**Question 9**
---
<img width="772" height="457" alt="496972023-5ac99887-e01b-4300-8860-9b75521f49b1" src="https://github.com/user-attachments/assets/07f5448e-de3a-499d-8ea4-1ba1296d4103" />


```sql
delete from Customer
where CUST_NAME like "______";
```

**Output:**

<img width="767" height="541" alt="496972183-e171e633-543c-4e61-a394-0ce1472f2d45" src="https://github.com/user-attachments/assets/96a08aa4-414f-402a-8d10-2505c4908753" />


**Question 10**
---
<img width="773" height="122" alt="496972252-17775a5a-a772-4cd9-9fae-ba9f2ff70db4" src="https://github.com/user-attachments/assets/51e93482-e246-487a-9e94-4586eeff2dce" />


```sql
delete from Doctors
where Specialization like 'Pediatrics' and first_name like 'Michael';
```

**Output:**

<img width="765" height="291" alt="496972374-7570f9ea-7dfc-4842-9f13-282101eb3ab8" src="https://github.com/user-attachments/assets/732be449-b281-4d42-a23e-edc7ddf01f01" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

<img width="1215" height="77" alt="image" src="https://github.com/user-attachments/assets/ba7de809-93e8-48fa-ad5e-79aa0fe36a71" />
