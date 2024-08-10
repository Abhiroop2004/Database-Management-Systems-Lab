# Title: Implementation of different types of operators in SQL

- Arithmetic Operator
- Logical Operator
- Comparison Operator
- Special Operator
- Set Operator
## Objective:
To learn different types of operators.
## Code
### Examples
```sql
mysql> select * from employee;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames    | Pune     |  2346248 |      12 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
|    116 | Harrison | Noida    |  5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
5 rows in set (0.02 sec)

mysql> select Salary+1000 from employee;
+-------------+
| Salary+1000 |
+-------------+
|       81000 |
|       71000 |
|      111000 |
|       61000 |
|      101000 |
+-------------+
5 rows in set (0.00 sec)

mysql> select Salary-1000 from employee;
+-------------+
| Salary-1000 |
+-------------+
|       79000 |
|       69000 |
|      109000 |
|       59000 |
|       99000 |
+-------------+
5 rows in set (0.00 sec)

mysql> select Salary*12 as Yearly_Salary from employee;
+---------------+
| Yearly_Salary |
+---------------+
|        960000 |
|        840000 |
|       1320000 |
|        720000 |
|       1200000 |
+---------------+
5 rows in set (0.00 sec)

mysql> select Salary/30 as Daily_Salary from employee;
+--------------+
| Daily_Salary |
+--------------+
|    2666.6667 |
|    2333.3333 |
|    3666.6667 |
|    2000.0000 |
|    3333.3333 |
+--------------+
5 rows in set (0.00 sec)

mysql> select power(Salary,2) from employee;
+-----------------+
| power(Salary,2) |
+-----------------+
|      6400000000 |
|      4900000000 |
|     12100000000 |
|      3600000000 |
|     10000000000 |
+-----------------+
5 rows in set (0.00 sec)

mysql> select Salary%12 from employee;
+-----------+
| Salary%12 |
+-----------+
|         8 |
|         4 |
|         8 |
|         0 |
|         4 |
+-----------+
5 rows in set (0.00 sec)

mysql> select E_name,Salary from employee where Salary>100000 and Dept_name='Mech';
+--------+--------+
| E_name | Salary |
+--------+--------+
| Sames  | 110000 |
+--------+--------+
1 row in set (0.00 sec)

mysql> select E_name,Salary from employee where Salary<80000 or Dept_name='Research';
+----------+--------+
| E_name   | Salary |
+----------+--------+
| Abhiroop |  80000 |
| Ravi     |  70000 |
| Harrison |  60000 |
+----------+--------+
3 rows in set (0.00 sec)

mysql> select E_name,Salary from employee where Dept_name<>'Mech';
+----------+--------+
| E_name   | Salary |
+----------+--------+
| Abhiroop |  80000 |
| Harrison |  60000 |
| Sen      | 100000 |
+----------+--------+
3 rows in set (0.00 sec)

mysql> select E_name,Salary from employee where Salary between 70000 and 100000;
+----------+--------+
| E_name   | Salary |
+----------+--------+
| Abhiroop |  80000 |
| Ravi     |  70000 |
| Sen      | 100000 |
+----------+--------+
3 rows in set (0.00 sec)

mysql> insert into Employee values(111, 'Han', 'Patna', 831656, '11', 'IT', '115', '2002-08-05', NULL, 65000);
Query OK, 1 row affected (0.01 sec)

mysql> select * from employee;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames    | Pune     |  2346248 |      12 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
|    111 | Han      | Patna    |   831656 |      11 | IT        | 115    | 2002-08-05 | NULL        |  65000 |
|    116 | Harrison | Noida    |  5452948 |      10 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
6 rows in set (0.00 sec)

mysql> select E_name from employee where Designation is null;
+--------+
| E_name |
+--------+
| Han    |
+--------+
1 row in set (0.00 sec)

mysql> select E_name, Designation from employee where Dept_name = all (select Dept_name from employee where Dept_name='Mech');
+--------+-------------+
| E_name | Designation |
+--------+-------------+
| Ravi   | CLERK       |
| Sames  | MANAGER     |
+--------+-------------+
2 rows in set (0.00 sec)

mysql> select E_name, Designation from employee where Join_date = any (select Join_date from employee where salary>=100000);
+--------+-------------+
| E_name | Designation |
+--------+-------------+
| Sames  | MANAGER     |
| Sen    | Lead        |
+--------+-------------+
2 rows in set (0.00 sec)

mysql> select E_name, Designation from employee where E_name like '%r%';
+----------+-------------+
| E_name   | Designation |
+----------+-------------+
| Abhiroop | Scientist   |
| Ravi     | CLERK       |
| Harrison | ANALYST     |
+----------+-------------+
3 rows in set (0.00 sec)

mysql> select E_name, Designation from employee where E_adress in ('Mumbai', 'Delhi', 'Chennai', 'Kolkata');
+----------+-------------+
| E_name   | Designation |
+----------+-------------+
| Abhiroop | Scientist   |
| Sen      | Lead        |
+----------+-------------+
2 rows in set (0.00 sec)

mysql> select Emp_no, E_name from employee where salary<70000 union select Emp_no, E_name from employee where salary>100000;
+--------+----------+
| Emp_no | E_name   |
+--------+----------+
|    111 | Han      |
|    116 | Harrison |
|    106 | Sames    |
+--------+----------+
3 rows in set (0.00 sec)

mysql> select Emp_no, E_name from employee where salary<70000 intersect select Emp_no, E_name from employee where Dept_name='IT';
+--------+--------+
| Emp_no | E_name |
+--------+--------+
|    111 | Han    |
+--------+--------+
1 row in set (0.00 sec)

mysql> select Emp_no, E_name from employee where salary<70000 except select Emp_no, E_name from employee where Dept_name='IT';
+--------+----------+
| Emp_no | E_name   |
+--------+----------+
|    116 | Harrison |
+--------+----------+
1 row in set (0.00 sec)
```

### LAB PRACTICE ASSIGNMENT:

```sql
mysql> select * from employee;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames    | Pune     |  2346248 |      20 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
|    111 | Han      | Patna    |   831656 |      11 | IT        | 115    | 2002-08-05 | NULL        |  65000 |
|    116 | Harrison | Noida    |  5452948 |      12 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
6 rows in set (0.00 sec)


mysql> insert into department values(10, 'Research');
Query OK, 1 row affected (0.01 sec)

mysql> insert into department values(20, 'Mech');
Query OK, 1 row affected (0.00 sec)

mysql> insert into department values(11, 'IT');
Query OK, 1 row affected (0.00 sec)

mysql> insert into department values(15, 'HR');
Query OK, 1 row affected (0.00 sec)

mysql> select * from department;
+---------+-----------+
| Dept_no | Dept_name |
+---------+-----------+
|      10 | Research  |
|      11 | IT        |
|      15 | HR        |
|      20 | Mech      |
+---------+-----------+
4 rows in set (0.00 sec)
```
1. Display all the dept numbers available with the dept and emp tables avoiding duplicates
```sql
mysql> select Dept_no from department union select Dept_no from Employee;
+---------+
| Dept_no |
+---------+
|      10 |
|      11 |
|      15 |
|      20 |
|      12 |
+---------+
5 rows in set (0.00 sec)
```
2. Display all the dept numbers available with the dept and emp tables.
```sql
mysql> select Dept_no from department union all select Dept_no from Employee;
+---------+
| Dept_no |
+---------+
|      10 |
|      11 |
|      15 |
|      20 |
|      10 |
|      20 |
|      11 |
|      12 |
+---------+
3 rows in set (0.00 sec)
```

3. Display all the dept numbers available in emp and not in dept tables and vice versa.
```sql
mysql> select Dept_no from department except select Dept_no from Employee;
+---------+
| Dept_no |
+---------+
|      15 |
+---------+
1 row in set (0.00 sec)

mysql> select Dept_no from Employee except select Dept_no from department;
+---------+
| Dept_no |
+---------+
|      12 |
+---------+
1 row in set (0.00 sec)
```
