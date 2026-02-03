```SQL
MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| manish             |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
6 rows in set (0.001 sec)
```
```SQL
MariaDB [(none)]> USE manish;
Database changed
```
CREATING DEPARTMENT:
```SQL
MariaDB [manish]> CREATE TABLE DEPARTMENT(
    ->  DEPTNO INT(2) PRIMARY KEY,
    ->  DNAME VARCHAR(15) NOT NULL);
Query OK, 0 rows affected (0.044 sec)
```
DESCRIBING DEPARTMENT TABLE:
```SQL
MariaDB [manish]> DESC DEPARTMENT;
```
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| DEPTNO | int(2)      | NO   | PRI | NULL    |       |
| DNAME  | varchar(15) | NO   |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
2 rows in set (0.059 sec)

INSERTING VALUE IN DEPARTMENT TABLE:
```SQL
MariaDB [manish]> INSERT INTO DEPARTMENT
    -> VALUES(10,"research"),
    -> (20,"accounting"),
    -> (30,"sales"),
    -> (40,"operations");
Query OK, 4 rows affected (0.005 sec)
Records: 4  Duplicates: 0  Warnings: 0
```
DISPLAYING DEPARTMENT TABLE:
```SQL
MariaDB [manish]> SELECT * FROM DEPARTMENT;
```
+--------+------------+
| DEPTNO | DNAME      |
+--------+------------+
|     10 | research   |
|     20 | accounting |
|     30 | sales      |
|     40 | operations |
+--------+------------+
4 rows in set (0.001 sec)

CREATING EMPLOYEE TABLE:
```SQL
MariaDB [manish]> CREATE TABLE EMPLOYEE(
    -> EMPNO INT(4) PRIMARY KEY,
    -> ENAME VARCHAR(20) NOT NULL,
    -> JOB VARCHAR(20),
    -> MGR INT(4),
    -> HIREDATE DATE,
    -> SAL INT(10),
    -> COMM INT(7),
    -> DEPTNO INT(2),
    -> FOREIGN KEY(DEPTNO) REFERENCES DEPARTMENT(DEPTNO)
    -> );
Query OK, 0 rows affected (0.047 sec)
```
DESCRIBING EMPLOYEE TABLE:
```SQL
MariaDB [manish]> DESC EMPLOYEE;
```
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| EMPNO    | int(4)      | NO   | PRI | NULL    |       |
| ENAME    | varchar(20) | NO   |     | NULL    |       |
| JOB      | varchar(20) | YES  |     | NULL    |       |
| MGR      | int(4)      | YES  |     | NULL    |       |
| HIREDATE | date        | YES  |     | NULL    |       |
| SAL      | int(10)     | YES  |     | NULL    |       |
| COMM     | int(7)      | YES  |     | NULL    |       |
| DEPTNO   | int(2)      | YES  | MUL | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.070 sec)

INSERTING VALUES IN EMPLOYEE TABLE:
```SQL
MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
Query OK, 1 row affected (0.003 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,300,30);
Query OK, 1 row affected (0.004 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20);
Query OK, 1 row affected (0.003 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30);
Query OK, 1 row affected (0.002 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30);
Query OK, 1 row affected (0.003 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,10);
Query OK, 1 row affected (0.002 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,20);
Query OK, 1 row affected (0.003 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,10);
Query OK, 1 row affected (0.003 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30);
Query OK, 1 row affected (0.003 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7876,'ADAMS','CLERK',7788,'1983-01-12',1100,NULL,20);
Query OK, 1 row affected (0.004 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30);
Query OK, 1 row affected (0.002 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20);
Query OK, 1 row affected (0.004 sec)

MariaDB [manish]> INSERT INTO EMPLOYEE VALUES (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
Query OK, 1 row affected (0.006 sec)
```
DISPLAYING EMPLOYEE TABLE:
```SQL
MariaDB [manish]> SELECT * FROM EMPLOYEE;
```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.002 sec)

1.CREATING EMPLOYEE_MASTER TABLE WITH DATA USING EMPLOYEE TABLE:
```SQL
MariaDB [manish]>  CREATE TABLE EMPLOYEE_MASTER AS
    ->  SELECT * FROM EMPLOYEE;
Query OK, 14 rows affected (0.050 sec)
Records: 14  Duplicates: 0  Warnings: 0
```
```SQL
MariaDB [manish]> SELECT * FROM EMPLOYEE;
```
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.001 sec)

2.DELETING ALL RECORD INTO EMPLOYEE_MASTER WHOSE DEPTNO IS 10.
```SQL
MariaDB [manish]> DELETE FROM EMPLOYEE_MASTER
    ->  WHERE DEPTNO=10;
Query OK, 3 rows affected (0.033 sec)
MariaDB [manish]> SELECT * FROM EMPLOYEE_MASTER;
```
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 1980-12-17 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3000 | NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3000 | NULL |     20 |
+-------+--------+----------+------+------------+------+------+--------+
11 rows in set (0.001 sec)

3.UPDATING 10% IN HIS SALARY OF DEPTNO 20 INTO EMPLOYEE_MASTER TABLE:

```SQL
MariaDB [manish]> UPDATE EMPLOYEE_MASTER
    -> SET SAL= SAL+(SAL*.10)
    -> WHERE DEPTNO=20;
Query OK, 5 rows affected (0.034 sec)
Rows matched: 5  Changed: 5  Warnings: 0
MariaDB [manish]> SELECT * FROM EMPLOYEE_MASTER;
```
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 1980-12-17 |  880 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 | 3273 | NULL |     20 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3300 | NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1210 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 | 3300 | NULL |     20 |
+-------+--------+----------+------+------------+------+------+--------+
11 rows in set (0.001 sec)

4.ALTERING SAL WITH SIZE 10,2 IN EMPLOYEE_TABLE:
```SQL
MariaDB [manish]> ALTER TABLE EMPLOYEE_MASTER
    -> MODIFY SAL DECIMAL(10,2);
Query OK, 11 rows affected (0.094 sec)
Records: 11  Duplicates: 0  Warnings: 0
MariaDB [manish]> SELECT * FROM EMPLOYEE_MASTER;
```
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
11 rows in set (0.003 sec)

DROPING EMPLOYEE MASTER TABLE:
```SQL
MariaDB [manish]> DROP TABLE EMPLOYEE_MASTER;
Query OK, 0 rows affected (0.013 sec)
```