# Experiment 3: DML Commands

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
--
<img width="1207" height="672" alt="image" src="https://github.com/user-attachments/assets/26f5fd39-729a-4b54-9a48-ac98a048ac5b" />

```sql
SELECT customer_id, cust_name, city, grade, salesman_id FROM customer WHERE grade IS NULL;
```

**Output:**

<img width="1202" height="548" alt="image" src="https://github.com/user-attachments/assets/2153f5db-c963-4913-b5a4-48da57c39cb6" />

**Question 2**
---
<img width="1203" height="354" alt="image" src="https://github.com/user-attachments/assets/7dfed1fa-bfbb-40f7-ae67-49114b5bee7b" />

```sql
UPDATE Products
SET sell_price=sell_price*1.1
WHERE category = "Bakery";
```

**Output:**
<img width="1208" height="659" alt="image" src="https://github.com/user-attachments/assets/969a1e47-3602-45d9-b1ba-4ce7c7ac3922" />

**Question 3**
---
<img width="1206" height="718" alt="image" src="https://github.com/user-attachments/assets/73072ebb-adef-4246-bd48-80b45a6cd908" />

```sql
UPDATE Employees
SET salary=salary*2
WHERE job_id LIKE '%MAN';
```

**Output:**
<img width="1198" height="465" alt="image" src="https://github.com/user-attachments/assets/a3256816-26e3-4c3f-ad07-95294984225f" />

**Question 4**
---
<img width="1202" height="631" alt="image" src="https://github.com/user-attachments/assets/11bceab2-d23c-44e7-b0ed-6f2c6873b7c3" />

```sql
UPDATE Products
SET sell_price=sell_price*1.15
WHERE quantity < 50 AND supplier_id = 10;
```

**Output:**
<img width="1209" height="626" alt="image" src="https://github.com/user-attachments/assets/ec482cd0-d921-42b0-aa33-4b32c48112d8" />

**Question 5**
---
<img width="1189" height="602" alt="image" src="https://github.com/user-attachments/assets/dfa1f55e-8839-4b6f-90e4-3dded62d5c4b" />

```sql
select EmpFname || " " || EmpLname as FullName from EmployeeInfo;
```

**Output:**
<img width="1207" height="442" alt="image" src="https://github.com/user-attachments/assets/8fb199d8-bd43-4fdb-8fe8-998547d9d25c" />

**Question 6**
---
<img width="1199" height="686" alt="image" src="https://github.com/user-attachments/assets/9c5f50cb-8353-4969-9877-2c3f7dddb543" />

```sql
select salesman_id,name,city,commission from salesman
where city not in ('Paris','Rome');
```

**Output:**

<img width="1200" height="500" alt="image" src="https://github.com/user-attachments/assets/7c33776d-d9b3-4450-b394-ea81418dc2a1" />

**Question 7**
---
<img width="1185" height="690" alt="image" src="https://github.com/user-attachments/assets/087778cf-ef17-4619-b561-62bff3935093" />

```sql
select * from emp
where hiredate between "2022-01-01" and "2022-12-31";
```

**Output:**

<img width="1200" height="471" alt="image" src="https://github.com/user-attachments/assets/6e95f0ee-7c37-406c-bb54-53d20fc06c4a" />

**Question 8**
---
<img width="1206" height="592" alt="image" src="https://github.com/user-attachments/assets/d5dcdb08-f8c5-4d8c-94dc-2ebf4914c119" />

```sql
UPDATE products
set reorder_lvl =reorder_lvl*1.3
where category='Food' and quantity < 0.5*reorder_lvl;
```

**Output:**

<img width="1201" height="528" alt="image" src="https://github.com/user-attachments/assets/c912150b-e20e-4e1e-92f7-c1f29a2a5c99" />

**Question 9**
---
<img width="1207" height="540" alt="image" src="https://github.com/user-attachments/assets/fb7cf4e7-eaec-4653-9371-7e123d492a38" />

```sql
Delete from Customer
where GRADE%2!=0;
```

**Output:**

<img width="1205" height="545" alt="image" src="https://github.com/user-attachments/assets/b22b9a2c-06d5-411e-94ca-f28d235b7884" />

**Question 10**
---
<img width="1212" height="755" alt="image" src="https://github.com/user-attachments/assets/3081c836-469d-440b-9fb6-329dc4a95362" />

```sql
Update emp
set hiredate='1981-11-17'
where ename='TURNER';
select ename, cast((julianday('2024-08-30')-julianday(hiredate))/365 as INTEGER) AS Tenure
from emp;
```

**Output:**

<img width="1206" height="497" alt="image" src="https://github.com/user-attachments/assets/da8fa2e0-9575-40c8-9d16-d8c1a9977197" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
