# Experiment 5: Subqueries and Views

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
<img width="1194" height="735" alt="image" src="https://github.com/user-attachments/assets/cd46168f-8ec5-4be8-95be-27e4f7abdde1" />

```sql
select t1.student_name, t1.grade from GRADES t1
JOIN (
    SELECT subject, max(grade) as max_grade
    from GRADES
    GROUP BY subject
) t2
on t1.subject=t2.subject and t1.grade=t2.max_grade;
```

**Output:**

<img width="1199" height="554" alt="image" src="https://github.com/user-attachments/assets/d8455420-b705-42f3-aa11-a3df92eb87b7" />

**Question 2**
---
<img width="1190" height="770" alt="image" src="https://github.com/user-attachments/assets/5c99794f-0f04-404e-9ba9-ef0be8c84783" />

```sql
select * from Employee
where age < (select avg(age) from Employee
where income>250000);
```

**Output:**

<img width="1205" height="660" alt="image" src="https://github.com/user-attachments/assets/cd6ee525-3149-40b0-af9b-c74764452a79" />

**Question 3**
---
<img width="1198" height="725" alt="image" src="https://github.com/user-attachments/assets/ec4c652c-b786-4e38-ab90-00db52f377eb" />

```sql
select t.student_name, t.grade from GRADES t
JOIN (
    SELECT subject , min(grade) as min_grade from GRADES
    GROUP BY subject
) t2
ON t.subject=t2.subject and t.grade=t2.min_grade;
```

**Output:**

<img width="1198" height="558" alt="image" src="https://github.com/user-attachments/assets/6bb7adaf-bafa-4f8f-bf76-4d232c5c66a1" />

**Question 4**
---
<img width="1197" height="616" alt="image" src="https://github.com/user-attachments/assets/12746115-d8bd-4eee-a29a-7acae2286fc5" />

```sql
select t.* from customer t
JOIN (
    select city,max(id) from customer
    
) t2
on t.city != t2.city;
```

**Output:**

<img width="1198" height="628" alt="image" src="https://github.com/user-attachments/assets/dfd02e81-5722-47de-986c-181b85ccff86" />

**Question 5**
---
<img width="1198" height="539" alt="image" src="https://github.com/user-attachments/assets/fcce18a7-16bb-429f-b094-7e235792d2bf" />

```sql
select medication_id as medic, medication_name, dosage from Medications 
where dosage = (select min(dosage) from Medications);
```

**Output:**

<img width="1194" height="519" alt="image" src="https://github.com/user-attachments/assets/400792bc-20b3-4808-b3aa-504976b6f831" />

**Question 6**
---
<img width="1196" height="654" alt="image" src="https://github.com/user-attachments/assets/8aac23ae-3552-4c1b-890a-17118d22d490" />

```sql
select t.name from customer t
join (
    select phone,count(id),name from customer
    group by phone
    having count(id)=1
) t2
on t.name=t2.name;
```

**Output:**

<img width="1194" height="582" alt="image" src="https://github.com/user-attachments/assets/7a24f6fc-8675-47a0-881b-59d9cadcddf8" />

**Question 7**
---
<img width="1199" height="561" alt="image" src="https://github.com/user-attachments/assets/4680986d-2245-45db-85b3-72c86d0e5cf2" />

```sql
select t1.ord_no, t1.purch_amt, t1.ord_date, t1.salesman_id from orders t1
JOIN (
    select salesman_id, max(commission) from salesman
) t2
on t1.salesman_id=t2.salesman_id;
```

**Output:**

<img width="1199" height="608" alt="image" src="https://github.com/user-attachments/assets/b0a6db59-c69a-4051-8d3c-39ea4a52ee2e" />


**Question 8**
---
<img width="1200" height="712" alt="image" src="https://github.com/user-attachments/assets/1db32483-81d3-4bb1-b150-2ad683123ba4" />

```sql
select * from Orders
where salesman_id in (select salesman_id from Salesman where name = 'Paul Adam');
```

**Output:**

<img width="1198" height="534" alt="image" src="https://github.com/user-attachments/assets/4a3601eb-de91-4ca1-87cd-48c2edcc474d" />

**Question 9**
---
<img width="1195" height="751" alt="image" src="https://github.com/user-attachments/assets/4baacbc8-ddec-44c2-afce-ae41ef7cd12f" />

```sql
select * from CUSTOMERS
WHERE SALARY <2500;
```

**Output:**

<img width="1199" height="594" alt="image" src="https://github.com/user-attachments/assets/a33ccc8b-79b3-4761-8d08-40ad36fe929e" />

**Question 10**
---
<img width="1198" height="745" alt="image" src="https://github.com/user-attachments/assets/3a18ee1f-79e8-43f4-9ad7-6a887ef6ff78" />

```sql
select commission from salesman
where salesman_id in (select salesman_id from customer
where city = 'Paris');
```

**Output:**

<img width="1197" height="453" alt="image" src="https://github.com/user-attachments/assets/6aaf7466-8f6e-4a81-b4f7-e7e9b8697455" />

## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
