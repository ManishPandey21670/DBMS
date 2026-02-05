```sql
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
6 rows in set (0.004 sec)
```
USING manish DATABASE:
```SQL
MariaDB [(none)]> USE manish;
Database changed
MariaDB [manish]> SHOW TABLES;
+------------------+
| Tables_in_manish |
+------------------+
| department       |
| employee         |
+------------------+
2 rows in set (0.001 sec)
```
1.List all distinct job in employee
```SQL
MariaDB [manish]> SELECT DISTINCT JOB
    -> FROM employee;
```
+-----------+
| JOB       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set (0.013 sec)
2.List all information about employee in department number 30.
```sql
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE DEPTNO = 30;
```
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |  950 | NULL |     30 |
+-------+--------+----------+------+------------+------+------+--------+
6 rows in set (0.032 sec)

3.Find all department number with department names greater than 20.
```SQL
MariaDB [manish]> SELECT DISTINCT DEPTNO
    -> FROM employee
    -> WHERE DEPTNO > 20;
```
+--------+
| DEPTNO |
+--------+
|     30 |
+--------+
1 row in set (0.002 sec)

4.Find all information about all the managers as well as the c;erks in department 30.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE DEPTNO =30
    -> AND JOB IN ('MANAGER','CLERK');
```
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
|  7698 | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850 | NULL |     30 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 |  950 | NULL |     30 |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set (0.001 sec)

5.List the employee name,employee numbers,and department of all clerks.
```SQL
MariaDB [manish]> SELECT ENAME,EMPNO,DEPTNO
    -> FROM employee
    -> WHERE JOB ='CLERK';
```
+--------+-------+--------+
| ENAME  | EMPNO | DEPTNO |
+--------+-------+--------+
| SMITH  |  7369 |     20 |
| ADAMS  |  7876 |     20 |
| JAMES  |  7900 |     30 |
| MILLER |  7934 |     10 |
+--------+-------+--------+
4 rows in set (0.001 sec)

6.Find all managers not in department 30.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE JOB ='MANAGER'
    -> AND DEPTNO <> 30;
```
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
|  7566 | JONES | MANAGER | 7839 | 1981-04-02 | 2975 | NULL |     20 |
|  7782 | CLARK | MANAGER | 7839 | 1981-06-09 | 2450 | NULL |     10 |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set (0.031 sec)

7.List information about all employees in department 10 who are not managers and clerks.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE DEPTNO =10
    -> AND JOB NOT IN ('MANAGER','CLERK');
```
+-------+-------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+-----------+------+------------+------+------+--------+
|  7839 | KING  | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL |     10 |
+-------+-------+-----------+------+------------+------+------+--------+
1 row in set (0.002 sec)

8.Find employees and jobs earning  between 1200 and 1400.
```SQL
MariaDB [manish]> SELECT ENAME,JOB,SAL
    -> FROM employee
    -> WHERE SAL BETWEEN 1200 AND 1400;
```
+--------+----------+------+
| ENAME  | JOB      | SAL  |
+--------+----------+------+
| WARD   | SALESMAN | 1250 |
| MARTIN | SALESMAN | 1250 |
| MILLER | CLERK    | 1300 |
+--------+----------+------+
3 rows in set (0.001 sec)

9.List name and department number of employee who are clerks, analyst or salesman.
```SQL
MariaDB [manish]> SELECT ENAME,DEPTNO
    -> FROM employee
    -> WHERE JOB IN('CLERK','ANALYST','SALESMAN');
```
+--------+--------+
| ENAME  | DEPTNO |
+--------+--------+
| SMITH  |     20 |
| ALLEN  |     30 |
| WARD   |     30 |
| MARTIN |     30 |
| SCOTT  |     20 |
| TURNER |     30 |
| ADAMS  |     20 |
| JAMES  |     30 |
| FORD   |     20 |
| MILLER |     10 |
+--------+--------+
10 rows in set (0.001 sec)

10.List name and department numabers of employee who names began with M.
```SQL
MariaDB [manish]> SELECT ENAME,DEPTNO
    -> FROM employee
    -> WHERE ENAME LIKE 'M%';
```
+--------+--------+
| ENAME  | DEPTNO |
+--------+--------+
| MARTIN |     30 |
| MILLER |     10 |
+--------+--------+
2 rows in set (0.001 sec)