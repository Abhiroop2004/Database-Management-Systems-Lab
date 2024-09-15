# Title: Study & Implementation of
- Group by & Having Clause
- Order by Clause
- Indexing


## Objective:
To learn the concept of group functions

### Lab Practice Assignment:
```sql
mysql> CREATE TABLE departments (
    ->     dept_id INT PRIMARY KEY,
    ->     dept_name VARCHAR(50));
Query OK, 0 rows affected (0.22 sec)


mysql> INSERT INTO departments values (1, 'Finance'), (2, 'Engineering'), (3, 'Sales');
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0


mysql> CREATE TABLE employees (
    ->     emp_id INT PRIMARY KEY,
    ->     emp_name VARCHAR(20),
    ->     salary INT,
    ->     job_category VARCHAR(20),
    ->     manager_id INT,
    ->     dept_id INT,
    ->     FOREIGN KEY (dept_id) REFERENCES departments(dept_id),
    ->     FOREIGN KEY (manager_id) REFERENCES employees(emp_id) ON DELETE SET NULL
    -> );
Query OK, 0 rows affected (0.10 sec)


mysql> INSERT INTO employees (emp_id, emp_name, salary, job_category, manager_id, dept_id)
    -> VALUES
    -> (103, 'Mark Johnson', 22000.00, 'Manager', NULL, 1),
    -> (104, 'Sarah Davis', 19000.00, 'Accountant', 103, 1),
    -> (105, 'Michael Brown', 25000.00, 'Manager', NULL, 2),
    -> (106, 'Laura Wilson', 17000.00, 'Engineer', 105, 2),
    -> (107, 'James White', 16000.00, 'Engineer', 105, 2),
    -> (110, 'Sophia Martinez', 24000.00, 'Sales Executive', NULL, 3);
Query OK, 6 rows affected (0.01 sec)
Records: 6  Duplicates: 0  Warnings: 0
```

1. Display total salary spent for each job category.
```sql
mysql> SELECT job_category, SUM(salary) AS total_salary FROM employees GROUP BY job_category;
+-----------------+--------------+
| job_category    | total_salary |
+-----------------+--------------+
| Manager         |        47000 |
| Accountant      |        19000 |
| Engineer        |        33000 |
| Sales Executive |        24000 |
+-----------------+--------------+
4 rows in set (0.01 sec)
```

2. Display lowest paid employee details under each manager.
```sql
mysql> SELECT * from employees e WHERE salary=(SELECT MIN(salary)
    -> FROM employees WHERE manager_id=e.manager_id) ORDER BY manager_id;
+--------+-------------+--------+--------------+------------+---------+
| emp_id | emp_name    | salary | job_category | manager_id | dept_id |
+--------+-------------+--------+--------------+------------+---------+
|    104 | Sarah Davis |  19000 | Accountant   |        103 |       1 |
|    107 | James White |  16000 | Engineer     |        105 |       2 |
+--------+-------------+--------+--------------+------------+---------+
2 rows in set (0.01 sec)
```

3. Display number of employees working in each department and their department name
```sql
mysql> SELECT d.dept_name, COUNT(e.emp_id) AS no_employees FROM employees e
    -> JOIN departments d WHERE e.dept_id = d.dept_id GROUP BY d.dept_name;
+-------------+--------------+
| dept_name   | no_employees |
+-------------+--------------+
| Finance     |            2 |
| Engineering |            3 |
| Sales       |            1 |
+-------------+--------------+
3 rows in set (0.00 sec)
```

4. Display the details of employees sorting the salary in increasing order.
```sql
mysql> SELECT * FROM employees ORDER BY salary;
+--------+-----------------+--------+-----------------+------------+---------+
| emp_id | emp_name        | salary | job_category    | manager_id | dept_id |
+--------+-----------------+--------+-----------------+------------+---------+
|    107 | James White     |  16000 | Engineer        |        105 |       2 |
|    106 | Laura Wilson    |  17000 | Engineer        |        105 |       2 |
|    104 | Sarah Davis     |  19000 | Accountant      |        103 |       1 |
|    103 | Mark Johnson    |  22000 | Manager         |       NULL |       1 |
|    110 | Sophia Martinez |  24000 | Sales Executive |       NULL |       3 |
|    105 | Michael Brown   |  25000 | Manager         |       NULL |       2 |
+--------+-----------------+--------+-----------------+------------+---------+
6 rows in set (0.00 sec)
```

5. Show the record of employee earning salary greater than 16000 in each department
```sql
mysql> SELECT e.* FROM employees e JOIN departments d ON e.dept_id = d.dept_id
    -> WHERE salary > 16000 ORDER BY dept_name;
+--------+-----------------+--------+-----------------+------------+---------+
| emp_id | emp_name        | salary | job_category    | manager_id | dept_id |
+--------+-----------------+--------+-----------------+------------+---------+
|    105 | Michael Brown   |  25000 | Manager         |       NULL |       2 |
|    106 | Laura Wilson    |  17000 | Engineer        |        105 |       2 |
|    103 | Mark Johnson    |  22000 | Manager         |       NULL |       1 |
|    104 | Sarah Davis     |  19000 | Accountant      |        103 |       1 |
|    110 | Sophia Martinez |  24000 | Sales Executive |       NULL |       3 |
+--------+-----------------+--------+-----------------+------------+---------+
5 rows in set (0.00 sec)
```
