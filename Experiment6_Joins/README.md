# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1199" height="704" alt="image" src="https://github.com/user-attachments/assets/4903212e-2398-4df7-a09c-7108adedf825" />

```sql
select p.first_name as patient_name , t.* from patients p
join test_results t
on p.patient_id=t.patient_id
where t.test_name='Blood Pressure';
```

**Output:**

<img width="1206" height="537" alt="image" src="https://github.com/user-attachments/assets/db63e9e5-c342-4189-94ad-c6a991528ec9" />

**Question 2**
---
<img width="1199" height="718" alt="image" src="https://github.com/user-attachments/assets/3d675e26-0e61-4125-b920-3788f01728c3" />

```sql
select s.* from salesman s
left join customer c
on s.salesman_id=c.salesman_id
where c.cust_name='Fabian Johns';
```

**Output:**

<img width="1195" height="544" alt="image" src="https://github.com/user-attachments/assets/beac1cf3-f3cb-42d1-b3c8-a953c8415274" />

**Question 3**
---
<img width="1200" height="707" alt="image" src="https://github.com/user-attachments/assets/4116906c-b379-408d-b913-cc6a6aacbb58" />

```sql
select p.first_name as patient_name from patients p
join doctors d 
on p.doctor_id = d.doctor_id
where d.first_name='Emily' and d.last_name='Johnson' and p.discharge_date is not null;
```

**Output:**

<img width="1203" height="520" alt="image" src="https://github.com/user-attachments/assets/c7f4c083-f9f2-4726-a734-e97d7b356520" />

**Question 4**
---
<img width="1201" height="717" alt="image" src="https://github.com/user-attachments/assets/83af50db-1dd3-4b77-8d0d-4731fc96f90f" />

```sql
select p.* from patients p
join appointments a
on p.patient_id=a.patient_id
where a.appointment_date between '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="1199" height="534" alt="image" src="https://github.com/user-attachments/assets/b1061ce2-97c5-441f-8fa7-2e877d521453" />

**Question 5**
---
<img width="1206" height="798" alt="image" src="https://github.com/user-attachments/assets/7fa020d4-836c-4e31-afc8-ff3838f0be73" />

```sql
select o.ord_no, o.purch_amt , c.cust_name, c.city from orders o
join customer c
on o.customer_id=c.customer_id
where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="1198" height="595" alt="image" src="https://github.com/user-attachments/assets/ef552f26-073f-42a9-b9f6-617e85ef1ba8" />

**Question 6**
---
<img width="1208" height="751" alt="image" src="https://github.com/user-attachments/assets/ad57540e-6524-4560-ba08-1a8a93e6f96c" />

```sql
select n.*, d.department_name from nurses n
join departments d
on n.department_id=d.department_id;
```

**Output:**

<img width="1194" height="695" alt="image" src="https://github.com/user-attachments/assets/da94c5a7-c543-410a-9f58-a9a51d69d68d" />

**Question 7**
---
<img width="1185" height="659" alt="image" src="https://github.com/user-attachments/assets/b544fce9-a2cb-4188-842e-d07c2923549a" />

```sql
select p.* from patients p
join doctors d
on p.doctor_id=d.doctor_id
where d.first_name='John' and d.last_name='Smith';
```

**Output:**

<img width="1200" height="540" alt="image" src="https://github.com/user-attachments/assets/b7ae2a35-67b1-436f-9f5d-e54f02bbbe89" />

**Question 8**
---
<img width="1194" height="680" alt="image" src="https://github.com/user-attachments/assets/9e4c1802-c289-4afb-89bb-c16bfe1e01de" />

```sql
select p.first_name, s.* from patients p
join surgeries s
on p.patient_id=s.patient_id
where p.discharge_date between '2024-03-01' and '2024-03-31' and not p.admission_date = p.discharge_date;
```

**Output:**

<img width="1205" height="537" alt="image" src="https://github.com/user-attachments/assets/1c0ab199-9fe1-461d-a6ad-48c1df351bd1" />

**Question 9**
---
<img width="1196" height="490" alt="image" src="https://github.com/user-attachments/assets/e6bcec4e-a4c7-4223-8000-baa0e82d24f8" />

```sql
select c.cust_name, o.ord_no, o.ord_date, o.purch_amt from customer c
left join orders o
on c.customer_id = o.customer_id;
```

**Output:**

<img width="1210" height="470" alt="image" src="https://github.com/user-attachments/assets/9ed41ef3-07f1-4f83-bac2-10567fdb0011" />

**Question 10**
---
<img width="1206" height="728" alt="image" src="https://github.com/user-attachments/assets/9ebeb914-1062-4345-bc4b-37ba3011d2d8" />

```sql
select n.nurse_id, d.department_name from nurses n
join departments d
on n.department_id = d.department_id
where n.first_name='David' and n.last_name='Moore';
```

**Output:**

<img width="1200" height="526" alt="image" src="https://github.com/user-attachments/assets/98ded8ca-da82-4d41-99f1-6d8e426ce000" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
