# Experiment No: 2

## Title: Implementation of DML commands of SQL with suitable examples

- Insert table
- Update table
- Delete table

## Objective:
- To understand the different issues involved in the design and implementation of a database system
- To understand and use data manipulation language to query, update, and manage a database

## Code:

### University Management System:

```sql
mysql> create database UMS;
Query OK, 1 row affected (0.02 sec)

mysql> use UMS;
Database changed

mysql> create table Department(Dept_ID char(3) primary key, Dept_Name char(30) NOT NULL);
Query OK, 0 rows affected (0.05 sec)

mysql> describe Department;
+-----------+----------+------+-----+---------+-------+
| Field     | Type     | Null | Key | Default | Extra |
+-----------+----------+------+-----+---------+-------+
| Dept_ID   | char(3)  | NO   | PRI | NULL    |       |
| Dept_Name | char(30) | NO   |     | NULL    |       |
+-----------+----------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> create table Student(Student_ID int(3) primary key, Name char(10), Dept_ID char(3), GPA float(3), foreign key (Dept_ID) references Department(Dept_ID));
Query OK, 0 rows affected, 1 warning (0.03 sec)

mysql> describe Student;
+------------+----------+------+-----+---------+-------+
| Field      | Type     | Null | Key | Default | Extra |
+------------+----------+------+-----+---------+-------+
| Student_ID | int      | NO   | PRI | NULL    |       |
| Name       | char(10) | YES  |     | NULL    |       |
| Dept_ID    | char(3)  | YES  | MUL | NULL    |       |
| GPA        | float    | YES  |     | NULL    |       |
+------------+----------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> insert into Department values('AI', 'Artificial Intelligence');
Query OK, 1 row affected (0.01 sec)

mysql> insert into Department values('CSE', 'Computer Science Engineering');
Query OK, 1 row affected (0.00 sec)

mysql> insert into Department values('IoT', 'Internet of Things');
Query OK, 1 row affected (0.00 sec)

mysql> select * from Department;
+---------+------------------------------+
| Dept_ID | Dept_Name                    |
+---------+------------------------------+
| AI      | Artificial Intelligence      |
| CSE     | Computer Science Engineering |
| IoT     | Internet of Things           |
+---------+------------------------------+
3 rows in set (0.00 sec)

mysql> insert into Student values('101','Snehal','IoT', '9.0');
Query OK, 1 row affected (0.00 sec)

mysql> insert into Student values('102','Abhiroop','AI', '9.38');
Query OK, 1 row affected (0.00 sec)

mysql> insert into Student values('103','Kinshuk','CSE','9.75');
Query OK, 1 row affected (0.00 sec)

mysql> insert into Student values('104','Sanskriti','IoT','8.8');
Query OK, 1 row affected (0.00 sec)

mysql> insert into Student values('105','Subhajit','CSE','9.85');
Query OK, 1 row affected (0.00 sec)

mysql> select * from Student;
+------------+-----------+---------+------+
| Student_ID | Name      | Dept_ID | GPA  |
+------------+-----------+---------+------+
|        101 | Snehal    | IoT     |    9 |
|        102 | Abhiroop  | AI      | 9.38 |
|        103 | Kinshuk   | CSE     | 9.75 |
|        104 | Sanskriti | IoT     |  8.8 |
|        105 | Subhajit  | CSE     | 9.85 |
+------------+-----------+---------+------+

mysql> select Name from Student where GPA>9.5;
+----------+
| Name     |
+----------+
| Kinshuk  |
| Subhajit |
+----------+
2 rows in set (0.00 sec)

mysql> select Name from Student where Dept_ID='AI';
+----------+
| Name     |
+----------+
| Abhiroop |
+----------+
1 row in set (0.00 sec)

mysql> delete from Student where Dept_ID='AI';
Query OK, 1 row affected (0.01 sec)

mysql> select * from Student;
+------------+-----------+---------+------+
| Student_ID | Name      | Dept_ID | GPA  |
+------------+-----------+---------+------+
|        101 | Snehal    | IoT     |    9 |
|        103 | Kinshuk   | CSE     | 9.75 |
|        104 | Sanskriti | IoT     |  8.8 |
|        105 | Subhajit  | CSE     | 9.85 |
+------------+-----------+---------+------+
4 rows in set (0.00 sec)

mysql> select distinct Dept_ID from Student;
+---------+
| Dept_ID |
+---------+
| CSE     |
| IoT     |
+---------+
2 rows in set (0.00 sec)
```
