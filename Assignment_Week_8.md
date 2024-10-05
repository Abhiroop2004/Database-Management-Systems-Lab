# Title : Study & Implementation of different types of constraints
## Objective:
- To practice and implement constraints

### Lab Practice Assignment:
1. Create a table called EMP with the following structure.
Name Type
EMPNO NUMBER (6)
ENAME VARCHAR2 (20)
JOB VARCHAR2 (10)
DEPTNO NUMBER (3)
SAL NUMBER (7,2)
Allow NULL for all columns except ename and job

```sql
mysql> create table EMP(
    -> empno numeric(6), ename varchar(20) not null,
    -> job varchar(10) not null, deptno numeric(3),
    -> sal numeric(7,2));
Query OK, 0 rows affected (0.02 sec)

mysql> describe EMP;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| empno  | decimal(6,0) | YES  |     | NULL    |       |
| ename  | varchar(20)  | NO   |     | NULL    |       |
| job    | varchar(10)  | NO   |     | NULL    |       |
| deptno | decimal(3,0) | YES  |     | NULL    |       |
| sal    | decimal(7,2) | YES  |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

```

2. Add constraints to check, while entering the empno value (i.e) empno > 100.
```sql
mysql> alter table EMP add constraint check (empno > 100);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

3. Define the field DEPTNO as unique.
```sql
mysql> alter table EMP add constraint unique (deptno);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

4. Create a primary key constraint for the table(EMPNO).
```sql
mysql> alter table EMP add constraint primary key (empno);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

5. Write queries to implement and practice constraints.
```sql
mysql> alter table EMP add constraint min_sal check (sal > 10000);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> alter table EMP drop constraint min_sal;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe EMP;
+--------+--------------+------+-----+---------+-------+
| Field  | Type         | Null | Key | Default | Extra |
+--------+--------------+------+-----+---------+-------+
| empno  | decimal(6,0) | NO   | PRI | NULL    |       |
| ename  | varchar(20)  | NO   |     | NULL    |       |
| job    | varchar(10)  | NO   |     | NULL    |       |
| deptno | decimal(3,0) | YES  | UNI | NULL    |       |
| sal    | decimal(7,2) | YES  |     | NULL    |       |
+--------+--------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```