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
<img width="1017" height="533" alt="499680465-a52f8e2f-add2-41c8-a36e-599ba2c59a47" src="https://github.com/user-attachments/assets/648a1be1-d713-4348-9f2f-e5a2fbe48c6a" />


```sql
select DoctorID, count(*) as "TotalRecords" 
from MedicalRecords
group by DoctorID;
```

**Output:**

<img width="577" height="666" alt="499680851-e0a015fc-50ec-40a2-9455-9b4bec783bb4" src="https://github.com/user-attachments/assets/17dc1691-80cf-4a7c-a6e9-e7af7a080e39" />


**Question 2**
---
<img width="617" height="607" alt="499681182-12081dd9-6f7a-4aa3-a018-cef7e6799ca1" src="https://github.com/user-attachments/assets/54ae4332-ab23-40b5-8daa-8538474d5499" />


```sql
select strftime("%H",AppointmentDateTime) as HourOfDay,count(*) as "TotalAppointments"
from Appointments
group by HourOfDay
order by HourOfDay;
```

**Output:**

<img width="672" height="571" alt="499681352-c4f00b25-f5bf-49a6-bfe0-6b040dc0e252" src="https://github.com/user-attachments/assets/026eaff2-44d5-48a1-9327-c0240b231ed1" />


**Question 3**
---
<img width="968" height="618" alt="499681460-28a831bf-0a64-4bbd-aac5-b778a0e15574" src="https://github.com/user-attachments/assets/4b113828-68a2-4911-a2a8-ae0195d36702" />


```sql
select Medication,AVG(Dosage) as AvgDosage from Prescriptions 
group by Medication; 
```

**Output:**

<img width="607" height="788" alt="499681717-a18260ea-f21d-4346-82d7-b021f63adb4b" src="https://github.com/user-attachments/assets/a48b8072-1513-4e46-8769-2f964055809a" />


**Question 4**
---
<img width="920" height="453" alt="499683082-ce906369-3740-4789-8473-fddae9b4d241" src="https://github.com/user-attachments/assets/523a9881-e8dc-4df2-8936-c52c53af3082" />


```sql
select sum(purch_amt) as "TOTAL" from orders;
```

**Output:**

<img width="332" height="345" alt="499683793-77ca1575-9816-4116-91a1-24e5ebec2771" src="https://github.com/user-attachments/assets/fcbb5ea8-5b13-410a-befe-052895e1d8e2" />


**Question 5**
---
<img width="982" height="506" alt="499692283-9e5fcb15-e91a-4ab8-a1a0-2c2af22ccca7" src="https://github.com/user-attachments/assets/b70d4f13-d35e-4745-8c29-e06074a6c5e1" />


```sql
select count(customer_id) as COUNT from customer
where grade is not null;
```

**Output:**

<img width="327" height="340" alt="499692510-c57fbc28-4e8e-49be-8de6-503d87c562a5" src="https://github.com/user-attachments/assets/cf245417-5b7f-40ea-bf95-00d2fa4030cb" />


**Question 6**
---
<img width="852" height="450" alt="499692911-eea0fcf0-a2e1-4b5b-a114-cfebe1ad70d1" src="https://github.com/user-attachments/assets/aec620d1-46e3-4d19-adf0-f10396edca9e" />


```sql
select AVG(income) as "avg_income" from employee
WHERE name like "A%";
```

**Output:**

<img width="336" height="345" alt="499693060-2d07f21e-f9b6-479d-985f-00876d827c8b" src="https://github.com/user-attachments/assets/3232dcca-e0c3-4106-be3a-4f01ac05a14b" />


**Question 7**
---
<img width="697" height="532" alt="499693146-bdfb0a14-b823-4790-baa8-c2a9f55ca927" src="https://github.com/user-attachments/assets/15741407-c222-4821-8ca5-ffb96fb2ec5e" />


```sql
select name  as "fruit_name", inventory as "lowest_quantity" from fruits
order by inventory asc
limit 1;
```

**Output:**

<img width="648" height="345" alt="499693548-7badcacf-9407-440b-860c-09bbd7d3eda5" src="https://github.com/user-attachments/assets/10a3a02a-97f0-413a-a1f4-c8375fe6adad" />


**Question 8**
---
<img width="1230" height="502" alt="499693712-032846c9-53a7-412c-b10e-aa3e847bc662" src="https://github.com/user-attachments/assets/66a7bd80-a5c0-4d80-a48e-d7682b5670a3" />


```sql
SELECT age,MIN(income) AS "MIN(income)"
FROM employee
group by age 
having MIN(income)<400000;
```

**Output:**

<img width="560" height="418" alt="499693940-056b4d33-0c70-4769-8ccf-ca8df14d13f1" src="https://github.com/user-attachments/assets/ac5db882-857b-4b0e-b5ed-5ffa3b6015c0" />


**Question 9**
---
<img width="1208" height="513" alt="499694095-c397acfd-32e6-418e-9a94-13ad82575bde" src="https://github.com/user-attachments/assets/2c67479d-2d6e-4f03-b12e-4e750b986a72" />


```sql
SELECT occupation,AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="617" height="366" alt="499694342-20908258-713a-4105-bb2b-448d80184f36" src="https://github.com/user-attachments/assets/446ed824-1d6c-4ab4-b0bc-109963785143" />


**Question 10**
---
<img width="1170" height="553" alt="499694590-b751698a-b8b6-4e7b-aa8b-9c8161b28dd5" src="https://github.com/user-attachments/assets/08b35c7a-93a1-47a9-88cf-101d1b451cc1" />


```sql
select occupation,SUM(workhour) as "SUM(workhour)"
from employee1
group by occupation 
having SUM(workhour)>20;
```

**Output:**

<img width="607" height="493" alt="499695159-3f1a548f-ffe0-4fb8-883e-60685b6f466c" src="https://github.com/user-attachments/assets/5f48d76a-b5fa-4533-ae2c-b9ed29dba0d9" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
