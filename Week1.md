# Experiment No: 1

## Title: Implementation of DDL commands of SQL with suitable examples

- Create table
- Alter table
- Drop Table

## Objective:
- To understand the different issues involved in the design and implementation of a database system
- To understand and use data definition language to write query for a database

## Code:
### Question 1
Create a table EMPLOYEE with following schema:<br>
(Emp_no, E_name, E_address, E_ph_no, Dept_no, Dept_name,Job_id , Salary)

```sql
mysql> create table Employee
(Emp_no int primary key, E_name char(20), E_adress char(20),
E_ph_no int, Dept_no int, Dept_name char(10), Job_id char(10), Salary int);
Query OK, 0 rows affected (0.02 sec)

mysql> describe Employee;
+-----------+----------+------+-----+---------+-------+
| Field     | Type     | Null | Key | Default | Extra |
+-----------+----------+------+-----+---------+-------+
| Emp_no    | int      | NO   | PRI | NULL    |       |
| E_name    | char(20) | YES  |     | NULL    |       |
| E_adress  | char(20) | YES  |     | NULL    |       |
| E_ph_no   | int      | YES  |     | NULL    |       |
| Dept_no   | int      | YES  |     | NULL    |       |
| Dept_name | char(10) | YES  |     | NULL    |       |
| Job_id    | char(10) | YES  |     | NULL    |       |
| Salary    | int      | YES  |     | NULL    |       |
+-----------+----------+------+-----+---------+-------+
8 rows in set (0.00 sec)
```
### Question 2
Add a new column; HIREDATE to the existing relation.
```sql
mysql> alter table Employee add HireDate date;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

### Question 3
Change the datatype of JOB_ID from char to varchar2.
```sql
mysql> alter table Employee modify Job_id varchar(10);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

### Question 4
Change the name of column/field Emp_no to E_no.
```sql
mysql> alter table Employee rename column Emp_no to E_no;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

### Question 5
Modify the column width of the job field of emp table
```sql
mysql> alter table Employee modify Job_id varchar(20);
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0
```
### Final Table->
```sql
mysql> describe Employee;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| E_no      | int         | NO   | PRI | NULL    |       |
| E_name    | char(20)    | YES  |     | NULL    |       |
| E_adress  | char(20)    | YES  |     | NULL    |       |
| E_ph_no   | int         | YES  |     | NULL    |       |
| Dept_no   | int         | YES  |     | NULL    |       |
| Dept_name | char(10)    | YES  |     | NULL    |       |
| Job_id    | varchar(20) | YES  |     | NULL    |       |
| Salary    | int         | YES  |     | NULL    |       |
| HireDate  | date        | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
9 rows in set (0.00 sec)
```
