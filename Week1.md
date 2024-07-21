# Experiment No: 1

## Title: Implementation of DDL commands of SQL with suitable examples

- Create table
- Alter table
- Drop Table

## Objective:
- To understand the different issues involved in the design and implementation of a database system
- To understand and use data definition language to write query for a database

## Code:

```sql
mysql> create table Employee (Emp_no int primary key, E_name char(20), E_adress char(20), E_ph_no int, Dept_no int, Dept_name char(10), Job_id char(10), Salary int);
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
