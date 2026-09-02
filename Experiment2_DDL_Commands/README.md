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
<img width="838" height="487" alt="image" src="https://github.com/user-attachments/assets/35973666-4746-46e8-b023-b1969341c42b" />

## CODE
```sql
ALTER TABLE Companies ADD designation  varchar(50);
ALTER TABLE Companies ADD net_salary number; 
ALTER TABLE Companies ADD dob date;
```

**Output:**

<img width="978" height="374" alt="image" src="https://github.com/user-attachments/assets/4f743bb8-4a0b-4f86-8e15-65f761e1aa35" />


**Question 2**
<img width="862" height="306" alt="image" src="https://github.com/user-attachments/assets/78719b35-dc38-4d18-99e9-b23f7647588f" />


```sql
INSERT INTO Employee(EmployeeID,Name,Position) VALUES(4,'Emily White','Analyst');
```

**Output:**

<img width="899" height="258" alt="image" src="https://github.com/user-attachments/assets/f988bfc4-8f8a-47bc-8df7-a5ac1ee195a0" />



**Question 3**
<img width="702" height="410" alt="image" src="https://github.com/user-attachments/assets/ba586836-36b3-4e0b-9e75-88bf51445b2a" />


```sql
create table products(
product_id integer primary key,
product_name text not null,
list_price decimal(10,2) not null,
discount decimal(10,2) default 0 not null ,
check(discount>=0),
check(list_price>=0),
check(list_price>=discount)
);
```

**Output:**

![Output3](output.png)

**Question 4**
<img width="692" height="282" alt="image" src="https://github.com/user-attachments/assets/f2dab9b1-b2a4-4f42-a442-9895df7c2a6a" />


```sql
insert into Books(ISBN, Title, Author, Publisher, YearPublished)select ISBN, Title, Author, Publisher, YearPublished from Out_of_print_books;
```

**Output:**
<img width="669" height="241" alt="image" src="https://github.com/user-attachments/assets/ab2085d6-a9ab-46ee-9a9c-dc40a3af0701" />


**Question 5**
<img width="681" height="438" alt="image" src="https://github.com/user-attachments/assets/5cb45841-b214-4a8e-8891-da66d0b318c4" />


```sql
insert into Customers( CustomerID ,Name,Address,City ,ZipCode)values(306,'Diana Prince' ,'Themyscira',null,null),(307, 'Bruce Wayne', 'Wayne Mano','Gotham',10007),
(308,'Peter Parker','Queens',null,11375);
```

**Output:**

<img width="678" height="238" alt="image" src="https://github.com/user-attachments/assets/ef329611-5237-46e3-9b5a-85f30b202023" />


**Question 6**
<img width="691" height="386" alt="image" src="https://github.com/user-attachments/assets/ac2570c4-fdb5-4110-a732-b345886635fd" />


```sql
create table item( 
item_id text primary key,
item_desc text not null,
rate integer not null,
icom_id varchar(4),
foreign key(icom_id)references company(com_id) 
on update set null
on delete set null
);

```

**Output:**

<img width="684" height="306" alt="image" src="https://github.com/user-attachments/assets/822b98f4-affd-42a1-808f-5651c46c4373" />


**Question 7**

<img width="680" height="343" alt="image" src="https://github.com/user-attachments/assets/a5f71a66-5b29-4572-9fce-82b09b93e16d" />


```sql
alter table Employees add salary INTEGER check(salary>0);
```

**Output:**

<img width="681" height="286" alt="image" src="https://github.com/user-attachments/assets/2ab03dc2-44ce-4316-b26d-b8d116dcca46" />


**Question 8**

<img width="687" height="374" alt="image" src="https://github.com/user-attachments/assets/0bda1d18-8546-4dbd-b2c2-1852f5997696" />


```sql
create table products(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);

```

**Output:**


<img width="674" height="265" alt="image" src="https://github.com/user-attachments/assets/8732ba3e-92f2-46d1-8b4d-b6e524760c43" />


**Question 9**

<img width="705" height="288" alt="image" src="https://github.com/user-attachments/assets/81fae7a5-0cd8-481e-9670-8d40cb01b8ec" />


```sql
create table jobs(job_id integer, job_title text default '', min_salary integer default 8000, max_salary integer default null); 
```

**Output:**

<img width="682" height="348" alt="image" src="https://github.com/user-attachments/assets/a7c374d1-88f1-4cf5-a579-8db02cc8a5e9" />


**Question 10**

<img width="685" height="377" alt="image" src="https://github.com/user-attachments/assets/20e47483-f6b2-41fa-a4ca-dd5cab2c29be" />


```sql
create table Invoices(
InvoiceID integer primary key,
InvoiceDate date,
Amount real check(Amount>0),
DueDate date check(DueDate>InvoiceDate),
OrderID integer,
foreign key(OrderID)References Orders(OrderID)
);
```

**Output:**


<img width="690" height="258" alt="image" src="https://github.com/user-attachments/assets/2c164db9-fbba-41f2-ab15-8c643bc9ae43" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
