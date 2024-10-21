# Title : Study and Implementation of Rollback, Commit, Save point.

### Objective: 
- To understand the concept of administrative commands

### Lab Practice Assignment:
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
6 rows in set (0.03 sec)
```

2. Write a query to implement the rollback.

```sql
mysql> insert into employee values (120, 'Snehal', 'Siliguri', 54764567, 11, 'IT', 112, '2022-05-11', 'Head', 130000);
Query OK, 1 row affected (0.01 sec)

mysql> select * from employee;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames    | Pune     |  2346248 |      20 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
|    111 | Han      | Patna    |   831656 |      11 | IT        | 115    | 2002-08-05 | NULL        |  65000 |
|    116 | Harrison | Noida    |  5452948 |      12 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    120 | Snehal   | Siliguri | 54764567 |      11 | IT        | 112    | 2022-05-11 | Head        | 130000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
7 rows in set (0.00 sec)

mysql> set autocommit=0;
Query OK, 0 rows affected (0.00 sec)

mysql> Delete from employee where Designation='Head';
Query OK, 1 row affected (0.00 sec)

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

mysql> ROLLBACK;
Query OK, 0 rows affected (0.00 sec)

mysql> select * from employee;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames    | Pune     |  2346248 |      20 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
|    111 | Han      | Patna    |   831656 |      11 | IT        | 115    | 2002-08-05 | NULL        |  65000 |
|    116 | Harrison | Noida    |  5452948 |      12 | Sales     | 103    | 1990-06-02 | ANALYST     |  60000 |
|    120 | Snehal   | Siliguri | 54764567 |      11 | IT        | 112    | 2022-05-11 | Head        | 130000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
7 rows in set (0.00 sec)
```

3. Write a query to implement the commit. 

```sql
mysql> Delete from employee where Designation='Head';
Query OK, 1 row affected (0.00 sec)

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

mysql> COMMIT;
Query OK, 0 rows affected (0.00 sec)

mysql> ROLLBACK;
Query OK, 0 rows affected (0.00 sec)

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
```

1. Write a query to implement the save point. 

```sql
mysql> savepoint abc;
Query OK, 0 rows affected (0.00 sec)

mysql> Delete from employee where Job_id=115;
Query OK, 1 row affected (0.00 sec)

mysql> Delete from employee where Designation='ANALYST';
Query OK, 1 row affected (0.00 sec)

mysql> select * from employee;
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
| Emp_no | E_name   | E_adress | E_ph_no  | Dept_no | Dept_name | Job_id | Join_date  | Designation | Salary |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
|    101 | Abhiroop | Kolkata  | 12435836 |      10 | Research  | 110    | 2022-08-05 | Scientist   |  80000 |
|    104 | Ravi     | Asansol  |  2354234 |      20 | Mech      | 105    | 1992-06-05 | CLERK       |  70000 |
|    106 | Sames    | Pune     |  2346248 |      20 | Mech      | 102    | 1980-06-05 | MANAGER     | 110000 |
|    126 | Sen      | Mumbai   |   521300 |      11 | IT        | 103    | 1985-06-02 | Lead        | 100000 |
+--------+----------+----------+----------+---------+-----------+--------+------------+-------------+--------+
4 rows in set (0.00 sec)

mysql> rollback to savepoint abc;
Query OK, 0 rows affected (0.00 sec)

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
6 rows in set (0.00 s)

mysql> set autocommit=1;
Query OK, 0 rows affected (0.00 sec)
```