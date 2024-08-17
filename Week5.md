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

mysql> insert into reserves values(111, 81, '24-08-21');
Query OK, 1 row affected (0.00 sec)

mysql> select * from reserves;
+------+------+------------+
| sid  | bid  | day        |
+------+------+------------+
|  100 |   71 | 2024-08-20 |
|  111 |   51 | 2024-08-21 |
|  130 |   81 | 2024-08-25 |
|  105 |  101 | 2024-08-25 |
|  111 |   81 | 2024-08-21 |
+------+------+------------+
5 rows in set (0.00 sec)

```

```
mysql> select * from Sailors s join reserves r on s.sid=r.sid where r.bid = 101;
+-----+-------+--------+------+------+------+------------+
| sid | sname | rating | age  | sid  | bid  | day        |
+-----+-------+--------+------+------+------+------------+
| 105 | Bob   |      4 |   22 |  105 |  101 | 2024-08-25 |
+-----+-------+--------+------+------+------+------------+
1 row in set (0.01 sec)

mysql> select b.bname from boats b join reserves r on b.bid = r.bid
    -> join sailors s on r.sid = s.sid where s.sname = 'Bob';
+--------+
| bname  |
+--------+
| Utopia |
+--------+
1 row in set (0.00 sec)

mysql> select s.sname from sailors s
    -> join reserves r on s.sid = r.sid join boats b on r.bid = b.bid
    -> where b.color = 'red'
    -> order by s.age;
+-------+
| sname |
+-------+
| Bob   |
+-------+
1 row in set (0.01 sec)

mysql> select distinct s.sname from sailors s join reserves r on s.sid = r.sid;
+-------+
| sname |
+-------+
| Tim   |
| Bob   |
| Nabab |
| Lim   |
+-------+
4 rows in set (0.01 sec)

mysql> select distinct s.sid, s.sname from sailors s
    -> join reserves r1 on s.sid = r1.sid join reserves r2 on s.sid = r2.sid
    -> where r1.day = r2.day and r1.bid <> r2.bid;
+-----+-------+
| sid | sname |
+-----+-------+
| 111 | Nabab |
+-----+-------+
1 row in set (0.00 sec)

mysql> select distinct s.sid from sailors s
    -> join reserves r on s.sid = r.sid
    -> join boats b on r.bid = b.bid
    -> where b.color in ('red', 'green');
+-----+
| sid |
+-----+
| 111 |
| 105 |
+-----+
2 rows in set (0.00 sec)

mysql> select s.sname, s.age
    -> from sailors s
    -> where s.age = (select min(age) from sailors);
+-------+------+
| sname | age  |
+-------+------+
| Bob   |   22 |
+-------+------+
1 row in set (0.01 sec)

mysql> select count(distinct sname) as Number_of_Sailor_Names
    -> from sailors;
+------------------------+
| Number_of_Sailor_Names |
+------------------------+
|                      4 |
+------------------------+
1 row in set (0.00 sec)

mysql> select rating, AVG(age) as average_age
    -> from sailors
    -> group by rating;
+--------+-------------+
| rating | average_age |
+--------+-------------+
|      3 |     25.0000 |
|      4 |     22.5000 |
|      2 |     26.0000 |
+--------+-------------+
3 rows in set (0.00 sec)

mysql> select rating, avg(age) as avg_age from sailors group by rating
    -> having count(sid) >= 2;
+--------+---------+
| rating | avg_age |
+--------+---------+
|      4 | 22.5000 |
+--------+---------+
1 row in set (0.00 sec)
```
