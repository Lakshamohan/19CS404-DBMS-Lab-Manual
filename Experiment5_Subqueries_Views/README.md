# Experiment 5: Subqueries and Views
# NAME: LAKSHA M
# REG NO: 212224220050
## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1245" height="575" alt="502391393-32e95891-dff9-4722-9eaf-20f3bbee8461" src="https://github.com/user-attachments/assets/dd3541ca-2a7d-4119-9898-ac2f0ebcf6b0" />


```sql
SELECT ord_no,purch_amt,ord_date,customer_id,salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);

```

**Output:**

<img width="1237" height="440" alt="502394664-359d41ca-5efe-4579-b117-c1f0992bef8c" src="https://github.com/user-attachments/assets/efca6619-90e4-4756-8661-df6e2809b4b0" />


**Question 2**
---
<img width="983" height="680" alt="502394861-ca9e0098-92e6-410e-a8d4-ba048c5967ea" src="https://github.com/user-attachments/assets/cf081c93-cc94-4509-add3-73e2b2aaaa21" />


```sql
select * from CUSTOMERS 
WHERE SALARY>4500;
```

**Output:**

<img width="1202" height="428" alt="502395132-aba31961-13f4-44a4-9d4e-6094e8dff79f" src="https://github.com/user-attachments/assets/08833032-4745-4793-9fef-4638a6acca57" />


**Question 3**
---
<img width="1077" height="537" alt="502395447-e6c23c51-7a95-4604-ab2f-7491fa507ba8" src="https://github.com/user-attachments/assets/7971f764-2b1a-45d4-9eb7-1967fcd9d6df" />


```sql
SELECT name, city FROM customer WHERE city IN (SELECT city FROM customer WHERE id IN (3, 7))
```

**Output:**

<img width="547" height="488" alt="502395753-e6aabf38-f47d-481a-90ec-b7ddb4f96b44" src="https://github.com/user-attachments/assets/eb135eea-e449-4342-b135-e75a5bee55d0" />


**Question 4**
---
<img width="1250" height="647" alt="502396037-243600c1-1812-46f4-b3cc-10382f3d2cf8" src="https://github.com/user-attachments/assets/ec8dcde1-c1aa-4ba3-9cbd-30364c8f62bc" />


```sql
SELECT student_id, student_name, subject, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="1202" height="427" alt="502396733-daba31e0-3e19-4b2e-96b0-c2142ea142ea" src="https://github.com/user-attachments/assets/7cedc63c-b07a-4b18-b647-8e9a5ed18955" />


**Question 5**
---
<img width="1277" height="716" alt="502396920-12ad7c10-eaed-4fcf-a659-1d4130270ac6" src="https://github.com/user-attachments/assets/88adc98a-a2c1-4cfe-af63-84f614cf243a" />


```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    orders o
JOIN
    salesman s ON o.salesman_id = s.salesman_id
WHERE
    s.city = 'New York';
```

**Output:**

<img width="1115" height="446" alt="502397199-962963f7-7300-4bdb-b52b-1b6776f15eaf" src="https://github.com/user-attachments/assets/b808d2dd-36e8-4a7c-afae-5793774c0966" />


**Question 6**
---
<img width="1226" height="578" alt="502397323-0a207fb4-0a64-4a95-8dd4-76f3d37e8a3b" src="https://github.com/user-attachments/assets/17fc4d62-e9f7-429b-9ff9-d97f40da3d8e" />


```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**

<img width="655" height="427" alt="502397626-e902a398-306d-4621-af8a-eea691868235" src="https://github.com/user-attachments/assets/104ca694-77fb-4ca9-9288-321406807790" />


**Question 7**
---
<img width="1165" height="432" alt="502397792-a1f1e393-32ac-4203-a339-8dd2df0ecc5b" src="https://github.com/user-attachments/assets/cc544266-1bc1-4cbc-abba-7e07030ff9de" />


```sql
SELECT grade, COUNT(*)
FROM customer
WHERE grade>(
    SELECT AVG(grade)   
    FROM customer 
    WHERE city='New York'
)
GROUP BY grade;
```

**Output:**

<img width="497" height="336" alt="502398068-e4b3afa9-cf1c-4d7a-aae7-84b365b754a9" src="https://github.com/user-attachments/assets/7016811e-60c2-4c6a-8a75-ce3f972bf374" />


**Question 8**
---
<img width="1012" height="428" alt="502398353-c25d7db3-547c-46b5-bd4c-a95b6419db0a" src="https://github.com/user-attachments/assets/d46ad219-a1e8-4a43-916c-9094512c6d13" />


```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (SELECT AVG(LENGTH(department_name)) FROM Departments);
```

**Output:**

<img width="496" height="392" alt="502398615-3abfa893-b6ff-4254-852a-b0277e655687" src="https://github.com/user-attachments/assets/e91b3e6a-ddf0-4264-821e-fdd84c708b5f" />


**Question 9**
---
<img width="1262" height="631" alt="502398954-ecb4bb5e-1aa5-4b76-b0d1-46deb7a99d8b" src="https://github.com/user-attachments/assets/a195cb6f-d586-4eb4-b4f3-511505ea73ce" />


```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    orders o
JOIN
    salesman s ON o.salesman_id = s.salesman_id
WHERE
    s.city = 'London';
```

**Output:**

<img width="1113" height="405" alt="502399186-79a5ca10-566c-47ee-967e-70d341ac31ec" src="https://github.com/user-attachments/assets/15a7a33d-b15b-4f27-9e48-00333806cebf" />


**Question 10**
---
<img width="963" height="653" alt="502399291-5483c0e8-d374-4361-a414-38a4515389eb" src="https://github.com/user-attachments/assets/1f771903-dbf9-4b98-8ec7-be49ff75704a" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1091" height="578" alt="502399517-13e5fb0b-2e9d-4dbf-974c-e71a43315f48" src="https://github.com/user-attachments/assets/496897df-8c98-4fbc-b31f-3cf7bbdd62a7" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

<img width="1217" height="76" alt="image" src="https://github.com/user-attachments/assets/f918c578-f62c-4159-9f01-9794b119f417" />


