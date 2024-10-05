# Title: Study & Implementation of
- Sub queries
- Views

## Objective:
– To perform nested Queries and joining Queries using DML command

– To understand the implementation of views.

### Lab Practice Assignment:
Consider the following schema:
    Sailors (sid, sname, rating, age)
    Boats (bid, bname, color)
    Reserves (sid, bid, day(date))

```sql
mysql> create table Sailors (sid int primary key, sname char(10), rating int, age int);
Query OK, 0 rows affected (0.10 sec)

mysql> create table Boats (bid int primary key, bname char(10), color char(10));
Query OK, 0 rows affected (0.03 sec)

mysql> create table Reserves (sid int, bid int, day date,
    -> foreign key (sid) references Sailors (sid), foreign key (bid) references Boats (bid));
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
**Write subquery statement for the following queries.**

1. Find all information of sailors who have reserved boat number 101.
```sql
mysql> select * from sailors where sid in (select sid from reserves where bid = 101);
+-----+-------+--------+------+
| sid | sname | rating | age  |
+-----+-------+--------+------+
| 105 | Bob   |      4 |   22 |
+-----+-------+--------+------+
1 row in set (0.00 sec)
```
2. Find the name of boat reserved by Bob.
```sql
mysql> select bname from boats where bid in(
    -> select bid from reserves where sid =
    -> (select sid from sailors where sname = 'Bob'));
+--------+
| bname  |
+--------+
| Utopia |
+--------+
1 row in set (0.00 sec)
```
3. Find the names of sailors who have reserved a red boat, and list in the order of age.
```sql
mysql> select sname from sailors where sid in
    -> (select sid from reserves where bid in
    -> (select bid from boats where color ='red'))
    -> order by age;
+-------+
| sname |
+-------+
| Bob   |
+-------+
1 row in set (0.00 sec)
```
4. Find the names of sailors who have reserved at least one boat
```sql
mysql> select sname from sailors
    -> where sid in
    -> (select distinct sid from Reserves);
+-------+
| sname |
+-------+
| Tim   |
| Bob   |
| Nabab |
| Lim   |
+-------+
4 rows in set (0.00 sec)
```
5. Find the ids and names of sailors who have reserved two different boats on the same day.
```sql
mysql> select sid, sname from sailors
    -> where sid in( select sid
    -> from reserves R1 where exists(
    -> select 1 from reserves R2 where R1.sid = R2.sid
    -> and R1.bid <> R2.bid and R1.day = R2.day));
+-----+-------+
| sid | sname |
+-----+-------+
| 111 | Nabab |
+-----+-------+
1 row in set (0.00 sec)
```
6. Find the ids of sailors who have reserved a red boat or a green boat
```sql
mysql> select sid from sailors where sid in
    -> (select sid from reserves where bid in
    -> (select bid from boats where color in ('Red', 'Green')));
+-----+
| sid |
+-----+
| 105 |
| 111 |
+-----+
2 rows in set (0.00 sec)
```
7. Find the name and the age of the youngest sailor.
```sql
mysql> select sname, age from sailors
    -> where age = ( select min(age) from sailors);
+-------+------+
| sname | age  |
+-------+------+
| Bob   |   22 |
+-------+------+
1 row in set (0.00 sec)
```
8. Count the number of different sailor names.
```sql
mysql> select count(distinct sname) as Number_of_Sailor_Names from sailors;
+------------------------+
| Number_of_Sailor_Names |
+------------------------+
|                      4 |
+------------------------+
1 row in set (0.00 sec)
```
9. Find the average age of sailors for each rating level.
```sql
mysql> select rating, avg(age) as average_age
    -> from sailors where rating in ( select distinct rating from sailors)
    -> group by rating;
+--------+-------------+
| rating | average_age |
+--------+-------------+
|      3 |     25.0000 |
|      4 |     22.5000 |
|      2 |     26.0000 |
+--------+-------------+
3 rows in set (0.00 sec)
```
10. Find the average age of sailors for each rating level that has at least two sailors.
```sql
mysql> select rating, avg(age) as avg_age from sailors
    -> where rating in (select rating from sailors group by rating
    -> having count(sid) >= 2) group by rating;
+--------+---------+
| rating | avg_age |
+--------+---------+
|      4 | 22.5000 |
+--------+---------+
1 row in set (0.00 sec)
```
