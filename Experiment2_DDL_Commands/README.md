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
<img width="1206" height="446" alt="image" src="https://github.com/user-attachments/assets/c8fba104-6e1c-4706-a467-8e2255e672d5" />

```sql
CREATE TABLE Locations(
    LocationID INTEGER,
    LocationName TEXT,
    Address TEXT
);
```
**Output:**

<img width="1207" height="505" alt="image" src="https://github.com/user-attachments/assets/be8f3e90-adec-4d70-8f45-fe8b11dd1210" />


**Question 2**
---
<img width="1200" height="532" alt="image" src="https://github.com/user-attachments/assets/9f393f5b-7a3c-4749-9711-889701bc9551" />


```sql
INSERT INTO Student_details 
SELECT * FROM Archived_students;
```

**Output:**
<img width="1204" height="410" alt="image" src="https://github.com/user-attachments/assets/bbc861d9-662b-4e1b-9695-f9dbdd418118" />


**Question 3**
---
<img width="1195" height="453" alt="image" src="https://github.com/user-attachments/assets/2ac38821-a617-4286-9c1c-bb5b7e6f2272" />


```sql
CREATE TABLE Members(
    MemberID INTEGER,
    MemberName TEXT,
    JoinDate DATE
);
```

**Output:**

<img width="1201" height="503" alt="image" src="https://github.com/user-attachments/assets/a9fa4cec-9eb0-4fcf-a2ec-e3523f96f18a" />


**Question 4**
---
<img width="1201" height="554" alt="image" src="https://github.com/user-attachments/assets/d11cb946-8de4-4bd9-a061-ca840742e59a" />

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) VALUES
(306,"Diana Prince","Themyscira",NULL,NULL),
(307,"Bruce Wayne","Wayne Mano","Gotham",10007),
(308,"Peter Parker","Queens",NULL,11375);
```

**Output:**

<img width="1203" height="411" alt="image" src="https://github.com/user-attachments/assets/25300900-019b-4b85-89f0-3c289e13f093" />

**Question 5**
---
<img width="1201" height="489" alt="image" src="https://github.com/user-attachments/assets/ce48ced0-04e2-4e19-9e38-68ee1b89d2d5" />

```sql
INSERT INTO Customers(CustomerID,Name,Address) values (304,"Peter Parker","Spider St");
```

**Output:**
<img width="1202" height="451" alt="image" src="https://github.com/user-attachments/assets/4c518ce7-67dd-423d-8536-1a60c9bbe74b" />


**Question 6**
---
<img width="1204" height="447" alt="image" src="https://github.com/user-attachments/assets/397eb1a1-a734-470e-9832-c83f48606379" />

```sql
ALTER TABLE Employees
ADD salary INTEGER CHECK(salary>0);
```

**Output:**

<img width="1202" height="410" alt="image" src="https://github.com/user-attachments/assets/723d78e6-2d04-4320-b75d-891cbb75d275" />

**Question 7**
---
<img width="1201" height="399" alt="image" src="https://github.com/user-attachments/assets/aba16bd2-b29a-41a3-b6c2-39cc6b1e1cca" />

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY(ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**
<img width="1195" height="393" alt="image" src="https://github.com/user-attachments/assets/cdb0f0b6-8fef-4b5f-92f9-041d2b614579" />

**Question 8**
---
<img width="1201" height="513" alt="image" src="https://github.com/user-attachments/assets/87a53a05-101d-4fa0-8578-4730d59d59d5" />

```sql
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK(length(icom_id)=4),
    FOREIGN KEY(icom_id) REFERENCES company(com_id)
    ON UPDATE CASCADE
    ON DELETE CASCADE
);
```

**Output:**

<img width="1195" height="476" alt="image" src="https://github.com/user-attachments/assets/cad1ab87-9ac4-40ca-b581-7b5c7ff805f9" />


**Question 9**
---
<img width="1201" height="475" alt="image" src="https://github.com/user-attachments/assets/6518124b-cd47-4f86-a947-96dadd6c008a" />


```sql
ALTER TABLE employee
RENAME COLUMN id TO employee_id;
```

**Output:**
<img width="1207" height="375" alt="image" src="https://github.com/user-attachments/assets/6d98498c-e899-499b-8c92-85eab3e42eb1" />


**Question 10**
---
<img width="1207" height="480" alt="image" src="https://github.com/user-attachments/assets/daada4de-17f5-4ea8-b30b-57b8d5271dfb" />


```sql
CREATE TABLE contacts(
    contact_id integer primary key,
    first_name text not null,
    last_name text not null,
    email text,
    phone text not null check(length(phone)>=10)
);
```

**Output:**
<img width="1206" height="442" alt="image" src="https://github.com/user-attachments/assets/31ca80f5-edd7-4bfb-91a8-6a29d9688a18" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
