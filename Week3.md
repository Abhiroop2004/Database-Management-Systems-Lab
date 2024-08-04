# Title: Implementation of different types of functions with suitable examples

-  Number Function
- Aggregate Function
- Character Function
- Conversion Function
- Date Function

## Code: 
### Examples
```sql
mysql> select abs(-50);
+----------+
| abs(-50) |
+----------+
|       50 |
+----------+
1 row in set (0.00 sec)

mysql> select exp(4);
+--------------------+
| exp(4)             |
+--------------------+
| 54.598150033144236 |
+--------------------+
1 row in set (0.00 sec)

mysql> select power(3,3);
+------------+
| power(3,3) |
+------------+
|         27 |
+------------+
1 row in set (0.00 sec)

mysql> select mod(20,30);
+------------+
| mod(20,30) |
+------------+
|         20 |
+------------+
1 row in set (0.00 sec)

mysql> select round('234.55826',2);
+----------------------+
| round('234.55826',2) |
+----------------------+
|               234.56 |
+----------------------+
1 row in set (0.00 sec)

mysql> select sqrt(225);
+-----------+
| sqrt(225) |
+-----------+
|        15 |
+-----------+
1 row in set (0.00 sec)

mysql> select * from Employee;
+--------+----------+------------+-----------------+---------+-----------+--------+--------+
| Emp_no | E_name   | E_address  | E_email         | Dept_no | Dept_name | Job_id | Salary |
+--------+----------+------------+-----------------+---------+-----------+--------+--------+
|    101 | Abhiroop | Kolkata    | abhi@gmail.com  | D5      | Research  | R2     |  80000 |
|    104 | Ravi     | Asansol    | ravi@gmail.com  | D10     | Mech      | M5     |  50000 |
|    106 | James    | Pune       | james@gmail.com | D10     | Mech      | M4     |  60000 |
|    112 | Vaibhav  | Noida      | vbv1@gmail.com  | D6      | Sales     | S4     |  45000 |
|    152 | Megha    | Chandigarh | megha@gmail.com | D6      | Sales     | S2     |  75000 |
+--------+----------+------------+-----------------+---------+-----------+--------+--------+
5 rows in set (0.00 sec)

mysql> select count(Salary) from Employee;
+---------------+
| count(Salary) |
+---------------+
|             5 |
+---------------+
1 row in set (0.01 sec)

mysql> select sum(Salary) from Employee;
+-------------+
| sum(Salary) |
+-------------+
|      310000 |
+-------------+
1 row in set (0.00 sec)

mysql> select avg(salary) from Employee;
+-------------+
| avg(salary) |
+-------------+
|  62000.0000 |
+-------------+
1 row in set (0.00 sec)

mysql> select max(salary) from Employee;
+-------------+
| max(salary) |
+-------------+
|       80000 |
+-------------+
1 row in set (0.00 sec)

mysql> select Dept_no, max(salary) from Employee group by Dept_no;
+---------+-------------+
| Dept_no | max(salary) |
+---------+-------------+
| D5      |       80000 |
| D10     |       60000 |
| D6      |       75000 |
+---------+-------------+
3 rows in set (0.00 sec)

mysql> select E_name from Employee where salary=(select min(salary) from Employee);
+---------+
| E_name  |
+---------+
| Vaibhav |
+---------+
1 row in set (0.00 sec)

mysql> select lower("Hello");
+----------------+
| lower("Hello") |
+----------------+
| hello          |
+----------------+
1 row in set (0.00 sec)

mysql> select upper("hello");
+----------------+
| upper("hello") |
+----------------+
| HELLO          |
+----------------+
1 row in set (0.00 sec)

mysql> select ltrim("  cseit");
+------------------+
| ltrim("  cseit") |
+------------------+
| cseit            |
+------------------+
1 row in set (0.00 sec)

mysql> select replace('jack and jue','j','bl');
+----------------------------------+
| replace('jack and jue','j','bl') |
+----------------------------------+
| black and blue                   |
+----------------------------------+
1 row in set (0.00 sec)

mysql> select concat('Hello ','World','!');
+------------------------------+
| concat('Hello ','World','!') |
+------------------------------+
| Hello World!                 |
+------------------------------+
1 row in set (0.00 sec)

mysql> select lpad('ORACLE',15,'*');
+-----------------------+
| lpad('ORACLE',15,'*') |
+-----------------------+
| *********ORACLE       |
+-----------------------+
1 row in set (0.00 sec)

mysql> select rpad('ORACLE',15,'*');
+-----------------------+
| rpad('ORACLE',15,'*') |
+-----------------------+
| ORACLE*********       |
+-----------------------+
1 row in set (0.00 sec)

mysql> select substr('ADCDEFGHIJ',3,5);
+--------------------------+
| substr('ADCDEFGHIJ',3,5) |
+--------------------------+
| CDEFG                    |
+--------------------------+
1 row in set (0.00 sec)

mysql> select sysdate();
+---------------------+
| sysdate()           |
+---------------------+
| 2024-08-04 20:15:23 |
+---------------------+
1 row in set (0.00 sec)

mysql> select greatest('5-Jan-23','10-Jan-20');
+----------------------------------+
| greatest('5-Jan-23','10-Jan-20') |
+----------------------------------+
| 5-Jan-23                         |
+----------------------------------+
1 row in set (0.00 sec)
```

### LAB PRACTICE ASSIGNMENT

Create a table EMPLOYEE with the following schema:
(Emp_no, E_name, E_address, E_ph_no, Dept_no, Dept_name,Job_id, Designation , Salary)

```sql
mysql> create table Employee(Emp_no int primary key, E_name char(20), E_adress char(20), E_ph_no int,
Dept_no int, Dept_name char(10), Job_id char(5), Join_date date, Designation char(10), Salary int);
Query OK, 0 rows affected (0.03 sec)

mysql> describe Employee;
+-------------+----------+------+-----+---------+-------+
| Field       | Type     | Null | Key | Default | Extra |
+-------------+----------+------+-----+---------+-------+
| Emp_no      | int      | NO   | PRI | NULL    |       |
| E_name      | char(20) | YES  |     | NULL    |       |
| E_adress    | char(20) | YES  |     | NULL    |       |
| E_ph_no     | int      | YES  |     | NULL    |       |
| Dept_no     | int      | YES  |     | NULL    |       |
| Dept_name   | char(10) | YES  |     | NULL    |       |
| Job_id      | char(5)  | YES  |     | NULL    |       |
| Join_date   | date     | YES  |     | NULL    |       |
| Designation | char(10) | YES  |     | NULL    |       |
| Salary      | int      | YES  |     | NULL    |       |
+-------------+----------+------+-----+---------+-------+
10 rows in set (0.01 sec)
```

1. List the E_no, E_name, Salary of all employees working for MANAGER.
```sql
mysql> insert into Employee values(101, 'Abhiroop', 'Kolkata', 12435836, '10', 'Research', '110', '2022-08-05', 'Scientist', 80000);
Query OK, 1 row affected (0.01 sec)

mysql> insert into Employee values(104, 'Ravi', 'Asansol', 2354234, 20, 'Mech', '105', '1992-06-05', 'CLERK', 70000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(106, 'Sames', 'Pune', 2346248, 12, 'Mech', '102', '1980-06-05', 'MANAGER', 110000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(116, 'Harrison', 'Noida', 5452948, 10, 'Sales', '103', '1990-06-02', 'ANALYST', 60000);
Query OK, 1 row affected (0.00 sec)

mysql> insert into Employee values(126, 'Sen', 'Mumbai', 521300, 11, 'IT', '103', '1985-06-02', 'Lead', 100000);
Query OK, 1 row affected (0.00 sec)

mysql> select Emo_no, E_name, Salary from Employee;
+--------+----------+--------+
| Emp_no | E_name   | Salary |
+--------+----------+--------+
|    101 | Abhiroop |  80000 |
|    104 | Ravi     |  70000 |
|    106 | Sames    | 110000 |
|    116 | Harrison |  60000 |
|    126 | Sen      | 100000 |
+--------+----------+--------+
5 rows in set (0.00 sec)
```
2. Display all the details of the employee whose salary is more than the Sal of any IT PROFF..
```sql
mysql> select * from Employee where Designation !='Manager';
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    116 | Harrison | Noida    |  5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
4 rows in set (0.00 sec)
```
3. List the employees in the ascending order of Designations of those joined after 1981.
```sql
mysql> select * from employee where Join_date>'1981-01-01' order by Join_date;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
|    116 | Harrison | Noida    |  5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
4 rows in set (0.00 sec)
```
4. List the employees along with their Experience and Daily Salary.
```sql
mysql> select current_date - Join_date as Experience, Salary/365 from Employee;
+------------+------------+
| Experience | Salary/365 |
+------------+------------+
|      19924 |   219.1781 |
|     320124 |   191.7808 |
|     440124 |   301.3699 |
|     340127 |   164.3836 |
|     390127 |   273.9726 |
+------------+------------+
5 rows in set (0.00 sec)
```
5. List the employees who are either ‘CLERK’ or ‘ANALYST’ .
```sql
mysql> select * from employee where Designation='ANALYST' or Designation='CLERK';
+--------+----------+----------+---------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+---------+---------+-----------+--------+------------+-------------+--------+
|    104 | Ravi     | Asansol  | 2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    116 | Harrison | Noida    | 5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
+--------+----------+----------+---------+---------+-----------+--------+------------+-------------+--------+
2 rows in set (0.00 sec)
```
6. List the employees who joined on 1-MAY-81, 3-DEC-81, 17-DEC-81,19-JAN-80 .
```sql
mysql> select * from employee where Join_date='1992-06-05' or Join_date='1980-06-05';
+--------+--------+----------+---------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name | E_adress | E_ph_no | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+--------+----------+---------+---------+-----------+--------+------------+-------------+--------+
|    104 | Ravi   | Asansol  | 2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames  | Pune     | 2346248 |      12 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
+--------+--------+----------+---------+---------+-----------+--------+------------+-------------+--------+
2 rows in set (0.00 sec)
```
7. List the employees who are working for the Deptno 10 or20.
```sql
mysql> select * from employee where Dept_no=10 or Dept_no=20;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    116 | Harrison | Noida    |  5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
3 rows in set (0.00 sec)
```
8. List the Enames those are starting with ‘S’ .
```sql
mysql> select E_name from employee where E_name like 'S%';
+--------+
| E_name |
+--------+
| Sames  |
| Sen    |
+--------+
2 rows in set (0.00 sec)
```
9. Display the name as well as the first five characters of name(s) starting with ‘H’
```sql
mysql> select E_name,left(E_name, 5)  from employee where E_name like 'H%';
+----------+-----------------+
| E_name   | left(E_name, 5) |
+----------+-----------------+
| Harrison | Harri           |
+----------+-----------------+
1 row in set (0.00 sec)
```

10. List all the emps except ‘PRESIDENT’ & ‘MGR” in asc order of Salaries.
```sql
mysql> select * from employee where Designation != 'PRESIDENT' and Designation != 'MGR' order by  Salary;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    116 | Harrison | Noida    |  5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
|    106 | Sames    | Pune     |  2346248 |      12 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
5 rows in set (0.00 sec)
```  
