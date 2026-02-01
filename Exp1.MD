```SQL
MariaDB [iilm]> CREATE TABLE DEPARTMENT;
ERROR 1113 (42000): A table must have at least 1 column
MariaDB [iilm]> CREATE TABLE DEPARTMENT(
    -> DEPTNO INT(2) PRIMARY KEY,
    -> DNAME VARCHAR(15) NOT NULL);
Query OK, 0 rows affected (0.048 sec)
```
```SQL
MariaDB [iilm]> INSERT INTO DEPARTMENT(
    -> VALUES(10,"RESEARCH"),
    -> (20,"ACCOUNTING"),
    -> (30,"SALES"),
    -> (40,"OPERATIONS"));
Query OK, 4 rows affected (0.132 sec)
Records: 4  Duplicates: 0  Warnings: 0
```
```SQL
MariaDB [iilm]> CREATE TABLE EMPLOYEE (
    ->     EMPNO INT PRIMARY KEY,
    ->     ENAME VARCHAR(20) NOT NULL,
    ->     JOB VARCHAR(20),
    ->     MGR INT,
    ->     HIREDATE DATE,
    ->     SAL INT,
    ->     COMM INT,
    ->     DEPTNO INT,
    ->     FOREIGN KEY (DEPTNO) REFERENCES DEPARTMENT(DEPTNO)
    -> );
Query OK, 0 rows affected (0.076 sec)
```
```SQL
MariaDB [iilm]> INSERT INTO EMPLOYEE(
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '' at line 1
MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20);
Query OK, 1 row affected (0.006 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
Query OK, 1 row affected (0.004 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,300,30);
Query OK, 1 row affected (0.005 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20);
Query OK, 1 row affected (0.005 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30);
Query OK, 1 row affected (0.005 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30);
Query OK, 1 row affected (0.004 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,10);
Query OK, 1 row affected (0.005 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,20);
Query OK, 1 row affected (0.002 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,10);
Query OK, 1 row affected (0.003 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30);
Query OK, 1 row affected (0.003 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7876,'ADAMS','CLERK',7788,'1983-01-12',1100,NULL,20);
Query OK, 1 row affected (0.003 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30);
Query OK, 1 row affected (0.003 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20);
Query OK, 1 row affected (0.007 sec)

MariaDB [iilm]> INSERT INTO EMPLOYEE VALUES (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
Query OK, 1 row affected (0.004 sec)
```
```SQL

MariaDB [iilm]> CREATE TABLE EMPLOYEE_MASTER AS
    -> SELECT * FROM EMPLOYEE;
Query OK, 14 rows affected (0.060 sec)
Records: 14  Duplicates: 0  Warnings: 0
```
```SQL

MariaDB [iilm]> DELETE FROM EMPLOYEE_MASTER
    -> WHERE DEPTNO=10;
Query OK, 3 rows affected (0.034 sec)
```
```SQL 
MariaDB [iilm]> UPDATE EMPLOYEE_MASTER
    -> SET SAL = SAL + (SAL * 0.10)
    -> WHERE DEPTNO = 20;
Query OK, 5 rows affected (0.034 sec)
Rows matched: 5  Changed: 5  Warnings: 0
```
```SQL
MariaDB [iilm]> ALTER TABLE EMPLOYEE_MASTER
    -> MODIFY SAL DECIMAL(10,2);
Query OK, 11 rows affected (0.095 sec)
Records: 11  Duplicates: 0  Warnings: 0
```
```SQL
MariaDB [iilm]> SELECT * FROM EMPLOYEE_MASTER;
```
```SQL
+-------+--------+----------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+----------+------+------------+---------+------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 1980-12-17 |  880.00 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600.00 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250.00 |  300 |     30 |
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 3273.00 | NULL |     20 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250.00 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850.00 | NULL |     30 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3300.00 | NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500.00 |    0 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1210.00 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950.00 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3300.00 | NULL |     20 |
+-------+--------+----------+------+------------+---------+------+--------+
11 rows in set (0.002 sec)
```
```SQL

MariaDB [iilm]> DROP TABLE EMPLOYEE_MASTER;
Query OK, 0 rows affected (0.044 sec)

MariaDB [iilm]> SHOW TABLES;
+-----------------+
| Tables_in_iilm  |
+-----------------+
| department      |
| employee        |
| movie           |
| student_details |
+-----------------+
4 rows in set (0.001 sec)