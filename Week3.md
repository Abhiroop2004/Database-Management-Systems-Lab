# Title: Implementation of different types of functions with suitable examples

-Number Function
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
