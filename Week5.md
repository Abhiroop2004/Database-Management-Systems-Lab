# Experiment No: 5
```
mysql> create table Sailors (sid int primary key, sname char(10), rating int, age int);
Query OK, 0 rows affected (0.10 sec)

mysql> create table Boats (bid int primary key, bname char(10), color char(10));
Query OK, 0 rows affected (0.03 sec)

mysql> create table Reserves (sid int, bid int, day date, foreign key (sid) references Sailors (sid), foreign key (bid) references Boats (bid));
Query OK, 0 rows affected (0.05 sec)

mysql> insert into Sailors values
    -> (100, 'Tim', 3 , 25),
    -> (105, 'Bob', 4, 22),
    -> (111, 'Nabab', 2, 26),
    -> (130, 'Lim', 4, 23);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> select * from Sailors;
+-----+-------+--------+------+
| sid | sname | rating | age  |
+-----+-------+--------+------+
| 100 | Tim   |      3 |   25 |
| 105 | Bob   |      4 |   22 |
| 111 | Nabab |      2 |   26 |
| 130 | Lim   |      4 |   23 |
+-----+-------+--------+------+
4 rows in set (0.01 sec)

mysql> insert into boats values (101,'Utopia', 'red');
Query OK, 1 row affected (0.01 sec)

mysql> insert into boats values(81,'Wonder', 'blue');
Query OK, 1 row affected (0.01 sec)

mysql> insert into boats values(71,'Harmony', 'white');
Query OK, 1 row affected (0.01 sec)

mysql> insert into boats values(51,'Oasis', 'green');
Query OK, 1 row affected (0.01 sec)

mysql> select * from boats;
+-----+---------+-------+
| bid | bname   | color |
+-----+---------+-------+
|  51 | Oasis   | green |
|  71 | Harmony | white |
|  81 | Wonder  | blue  |
| 101 | Utopia  | red   |
+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> insert into reserves values (100, 71, '24-08-20');
Query OK, 1 row affected (0.01 sec)

mysql> insert into reserves values(111, 51, '24-08-21');
Query OK, 1 row affected (0.01 sec)

mysql> insert into reserves values(130, 81, '24-08-25');
Query OK, 1 row affected (0.00 sec)

mysql> insert into reserves values(105, 101, '24-08-25');
Query OK, 1 row affected (0.00 sec)

mysql> select * from reserves;
+------+------+------------+
| sid  | bid  | day        |
+------+------+------------+
|  100 |   71 | 2024-08-20 |
|  111 |   51 | 2024-08-21 |
|  130 |   81 | 2024-08-25 |
|  105 |  101 | 2024-08-25 |
+------+------+------------+
4 rows in set (0.00 sec)
```
