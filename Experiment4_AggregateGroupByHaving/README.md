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
<img width="1200" height="571" alt="image" src="https://github.com/user-attachments/assets/d4523002-ca47-475d-bba6-17c2021fe94c" />

```sql
select avg(purch_amt) as AVERAGE from orders;
```

**Output:**

<img width="1202" height="435" alt="image" src="https://github.com/user-attachments/assets/06860ad3-4c2f-4f66-a2cc-4dbe53251cc5" />

**Question 2**
---
<img width="1195" height="547" alt="image" src="https://github.com/user-attachments/assets/7c2d4bd9-12b4-40b4-a309-57470426cadc" />


```sql
select (max(price)-min(price)) as price_diff from fruits;
```

**Output:**

<img width="1199" height="423" alt="image" src="https://github.com/user-attachments/assets/7f2b3179-fdba-446b-87e4-22c2f441cf8c" />

**Question 3**
---
<img width="1191" height="521" alt="image" src="https://github.com/user-attachments/assets/ae8967df-a63a-4bd5-8b8f-e23066bbca5d" />

```sql
select avg(length(email)) as avg_email_length_below_30 from customer
where city in ('Mumbai');
```

**Output:**

<img width="1197" height="428" alt="image" src="https://github.com/user-attachments/assets/1deebb57-69d4-4b57-9f73-de991a3deddb" />

**Question 4**
---
<img width="1204" height="728" alt="image" src="https://github.com/user-attachments/assets/df7f31b5-9e7a-4dac-bf44-2e25024eb213" />

```sql
select InsuranceCompany, count(*) as TotalExpiredPatients from Insurance
group by InsuranceCompany;

```

**Output:**

<img width="1203" height="799" alt="image" src="https://github.com/user-attachments/assets/8ca17e4d-86c2-4a0e-a16e-096bed9b0de7" />

**Question 5**
---
<img width="1197" height="647" alt="image" src="https://github.com/user-attachments/assets/0e50b214-75c9-4c28-a4b3-eff7ef9b3449" />


```sql
select strftime("%Y",ValidityPeriod) as ValidityYear, count(*) as TotalPatients from Insurance
group by strftime("%Y",ValidityPeriod);
```

**Output:**

<img width="1199" height="510" alt="image" src="https://github.com/user-attachments/assets/09a582f2-b3e0-43ed-9739-cdca3d182c64" />

**Question 6**
---
<img width="1202" height="658" alt="image" src="https://github.com/user-attachments/assets/28169fdc-4827-4c51-85aa-5d2f9a48a75b" />

```sql
select PatientID, count(*) as TotalAppointments from Appointments
group by PatientID;
```

**Output:**

<img width="1202" height="755" alt="image" src="https://github.com/user-attachments/assets/b179a3a6-7c65-4d49-b102-d589304d095f" />

**Question 7**
---
<img width="1203" height="602" alt="image" src="https://github.com/user-attachments/assets/eff94000-27ac-4195-baa4-e4c626b56e44" />

```sql
SELECT age, min(Income) as Income from employee
group by age
having min(Income)<1000000;
```

**Output:**

<img width="1202" height="561" alt="image" src="https://github.com/user-attachments/assets/5036407e-04f3-4cc8-a69b-4af0b8cb5013" />


**Question 8**
---
<img width="1202" height="547" alt="image" src="https://github.com/user-attachments/assets/a0e0e51c-7333-4a86-95c0-64fba30079d4" />

```sql
select age, MAX(income) from employee
group by age
having max(income)>2000000;
```

**Output:**

<img width="1201" height="477" alt="image" src="https://github.com/user-attachments/assets/571174cb-a443-4b83-9ed9-68a0da719b3f" />

**Question 9**
---
<img width="1202" height="611" alt="image" src="https://github.com/user-attachments/assets/467d602f-f540-49ca-aece-7f5a5b226be0" />

```sql
select occupation , MIN(workhour) from employee1
group by occupation
having min(workhour)>8;
```

**Output:**

<img width="1195" height="609" alt="image" src="https://github.com/user-attachments/assets/f2ffd8d1-e55d-4419-93bf-1a200d0e6da3" />

**Question 10**
---
<img width="1197" height="588" alt="image" src="https://github.com/user-attachments/assets/dae9c4a2-4c20-4954-9b57-83e4f417941a" />


```sql
select city, AVG(income) from employee
group by city
having avg(income)>500000;
```

**Output:**

<img width="1198" height="557" alt="image" src="https://github.com/user-attachments/assets/cd6101b9-7d11-481e-9b61-aa1a2759e24a" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
