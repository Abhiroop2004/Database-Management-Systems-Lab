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

mysql> create table Student(Student_ID int(3) primary key, Name char(10), Dept_ID char(3), GPA float(3),
foreign key (Dept_ID) references Department(Dept_ID));
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

### LAB PRACTICE ASSIGNMENT
Create a table EMPLOYEE with following schema: <br>
(Emp_no, E_name, E_address, E_ph_no, Dept_no, Dept_name,Job_id , Salary)

```sql
mysql> create table Employee(Emp_no int primary key, E_name char(20), E_adress char(20), E_ph_no int,
Dept_no char(3), Dept_name char(10), Job_id char(5), Salary int);
Query OK, 0 rows affected (0.02 sec)

mysql> describe Employee;
+-----------+----------+------+-----+---------+-------+
| Field     | Type     | Null | Key | Default | Extra |
+-----------+----------+------+-----+---------+-------+
| Emp_no    | int      | NO   | PRI | NULL    |       |
| E_name    | char(20) | YES  |     | NULL    |       |
| E_adress  | char(20) | YES  |     | NULL    |       |
| E_ph_no   | int      | YES  |     | NULL    |       |
| Dept_no   | char(3)  | YES  |     | NULL    |       |
| Dept_name | char(10) | YES  |     | NULL    |       |
| Job_id    | char(5)  | YES  |     | NULL    |       |
| Salary    | int      | YES  |     | NULL    |       |
+-----------+----------+------+-----+---------+-------+
8 rows in set (0.00 sec)
```
### Question 1
Insert at least 5 rows in the table.

```sql
mysql> insert into Employee values(101, 'Abhiroop', 'Kolkata', 'abhi@gmail.com', 12435836, 'D5', 'Research','R2',80000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(104, 'Ravi', 'Asansol', 'ravi@gmail.com', 23423542, 'D10', 'Mech','M5',50000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(106, 'James', 'Pune', 'james@gmail.com', 77563552, 'D10', 'Mech','M4',60000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(112, 'Vaibhav', 'Noida', 'vbv1@gmail.com', 3256834, 'D6', 'Sales','S4',45000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(152, 'Megha', 'Chandigarh', 'megha@gmail.com', 31246572, 'D6', 'Sales','S2',75000);
Query OK, 1 row affected (0.00 sec)
```

### Question 2
Display all the information of EMP table.

```sql
mysql> select * from Employee;
+--------+----------+------------+-----------------+----------+---------+-----------+--------+--------+
| Emp_no | E_name   | E_adress   | E_email         | E_ph_no  | Dept_no | Dept_name | Job_id | Salary |
+--------+----------+------------+-----------------+----------+---------+-----------+--------+--------+
|    101 | Abhiroop | Kolkata    | abhi@gmail.com  | 12435836 | D5      | Research  | R2     |  80000 |
|    104 | Ravi     | Asansol    | ravi@gmail.com  | 23423542 | D10     | Mech      | M5     |  50000 |
|    106 | James    | Pune       | james@gmail.com | 77563552 | D10     | Mech      | M4     |  60000 |
|    112 | Vaibhav  | Noida      | vbv1@gmail.com  |  3256834 | D6      | Sales     | S4     |  45000 |
|    152 | Megha    | Chandigarh | megha@gmail.com | 31246572 | D6      | Sales     | S2     |  75000 |
+--------+----------+------------+-----------------+----------+---------+-----------+--------+--------+
5 rows in set (0.00 sec)
```

### Question 3
Display the record of each employee who works in department D10

```sql
mysql> select * from Employee where Dept_no='D10';
+--------+--------+----------+-----------------+----------+---------+-----------+--------+--------+
| Emp_no | E_name | E_adress | E_email         | E_ph_no  | Dept_no | Dept_name | Job_id | Salary |
+--------+--------+----------+-----------------+----------+---------+-----------+--------+--------+
|    104 | Ravi   | Asansol  | ravi@gmail.com  | 23423542 | D10     | Mech      | M5     |  50000 |
|    106 | James  | Pune     | james@gmail.com | 77563552 | D10     | Mech      | M4     |  60000 |
+--------+--------+----------+-----------------+----------+---------+-----------+--------+--------+
2 rows in set (0.00 sec)
```

### Question 4
Update the city of Emp_no-12 with current city as Nagpur 
```sql
mysql> update Employee set E_adress='Nagpur' where Emp_no=112;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from Employee;
+--------+----------+------------+-----------------+----------+---------+-----------+--------+--------+
| Emp_no | E_name   | E_adress   | E_email         | E_ph_no  | Dept_no | Dept_name | Job_id | Salary |
+--------+----------+------------+-----------------+----------+---------+-----------+--------+--------+
|    101 | Abhiroop | Kolkata    | abhi@gmail.com  | 12435836 | D5      | Research  | R2     |  80000 |
|    104 | Ravi     | Asansol    | ravi@gmail.com  | 23423542 | D10     | Mech      | M5     |  50000 |
|    106 | James    | Pune       | james@gmail.com | 77563552 | D10     | Mech      | M4     |  60000 |
|    112 | Vaibhav  | Nagpur     | vbv1@gmail.com  |  3256834 | D6      | Sales     | S4     |  45000 |
|    152 | Megha    | Chandigarh | megha@gmail.com | 31246572 | D6      | Sales     | S2     |  75000 |
+--------+----------+------------+-----------------+----------+---------+-----------+--------+--------+
5 rows in set (0.00 sec)
```

### Question 5
Display the details of Employee who works in department MECH.
```sql
mysql> select * from Employee where Dept_name='Mech';
+--------+--------+----------+-----------------+----------+---------+-----------+--------+--------+
| Emp_no | E_name | E_adress | E_email         | E_ph_no  | Dept_no | Dept_name | Job_id | Salary |
+--------+--------+----------+-----------------+----------+---------+-----------+--------+--------+
|    104 | Ravi   | Asansol  | ravi@gmail.com  | 23423542 | D10     | Mech      | M5     |  50000 |
|    106 | James  | Pune     | james@gmail.com | 77563552 | D10     | Mech      | M4     |  60000 |
+--------+--------+----------+-----------------+----------+---------+-----------+--------+--------+
2 rows in set (0.00 sec)
```

### Question 6
Delete the email_id of employee James.
```sql
mysql> select E_email from Employee where E_name='James';
+-----------------+
| E_email         |
+-----------------+
| james@gmail.com |
+-----------------+
1 row in set (0.00 sec)
```

### Question 7
Display the complete record of employees working in SALES Department

```sql
mysql> select * from Employee where Dept_name='Sales';
+--------+---------+------------+-----------------+----------+---------+-----------+--------+--------+
| Emp_no | E_name  | E_adress   | E_email         | E_ph_no  | Dept_no | Dept_name | Job_id | Salary |
+--------+---------+------------+-----------------+----------+---------+-----------+--------+--------+
|    112 | Vaibhav | Nagpur     | vbv1@gmail.com  |  3256834 | D6      | Sales     | S4     |  45000 |
|    152 | Megha   | Chandigarh | megha@gmail.com | 31246572 | D6      | Sales     | S2     |  75000 |
+--------+---------+------------+-----------------+----------+---------+-----------+--------+--------+
2 rows in set (0.00 sec)
```
