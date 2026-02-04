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
6 rows in set (0.002 sec)

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

MariaDB [manish]> SELECT ENAME,JOB,SAL
    -> FROM EMP
    -> WHERE DEPTNO =30
    -> ORDER BY SAL DESC;
ERROR 1146 (42S02): Table 'manish.emp' doesn't exist
MariaDB [manish]> SELECT ENAME,JOB,SAL
    -> FROM employee
    -> WHERE DEPTNO =30
    -> ORDER BY SAL DESC;
+--------+----------+------+
| ENAME  | JOB      | SAL  |
+--------+----------+------+
| BLAKE  | MANAGER  | 2850 |
| ALLEN  | SALESMAN | 1600 |
| TURNER | SALESMAN | 1500 |
| WARD   | SALESMAN | 1250 |
| MARTIN | SALESMAN | 1250 |
| JAMES  | CLERK    |  950 |
+--------+----------+------+
6 rows in set (0.001 sec)

MariaDB [manish]> SELECT JOB,DEPTNO
    -> FROM employee
    -> WHERE ENAME LIKE 'A___N';
+----------+--------+
| JOB      | DEPTNO |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+
1 row in set (0.001 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE ENAME LIKE 'S%';
+-------+
| ENAME |
+-------+
| SMITH |
| SCOTT |
+-------+
2 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE ENAME LIKE '%S';
+-------+
| ENAME |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+
3 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE DEPTNO IN (10,20,40)
    -> OR JOB IN ('CLERK','SALESMAN','ANALYST');
+--------+
| ENAME  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
13 rows in set (0.001 sec)

MariaDB [manish]> SELECT EMPNO,ENAME
    -> FROM employee
    -> WHERE COMM IS NOT NULL
    -> AND COMM>0;
+-------+--------+
| EMPNO | ENAME  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
+-------+--------+
3 rows in set (0.001 sec)

MariaDB [manish]> SELECT EMPNO
    -> ENAME,
    -> SAL+NVL(COMM, 0) AS
    -> TOTAL_SALARY
    -> FROM employee;
+-------+--------------+
| ENAME | TOTAL_SALARY |
+-------+--------------+
|  7369 |          800 |
|  7499 |         1900 |
|  7521 |         1550 |
|  7566 |         2975 |
|  7654 |         2650 |
|  7698 |         2850 |
|  7782 |         2450 |
|  7788 |         3000 |
|  7839 |         5000 |
|  7844 |         1500 |
|  7876 |         1100 |
|  7900 |          950 |
|  7902 |         3000 |
|  7934 |         1300 |
+-------+--------------+
14 rows in set (0.001 sec)

MariaDB [manish]> SELECT EMPNO,ENAME
    -> SAL*12 AS ANNUAL
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '*12 AS ANNUAL' at line 2
MariaDB [manish]> SELECT EMPNO,ENAME
    -> SAL*12 AS ANNUAL_SALARY
    -> FROM employee;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '*12 AS ANNUAL_SALARY
FROM employee' at line 2
MariaDB [manish]> SELECT EMPNO,ENAME,
    -> SAL*12 AS ANNUAL_SALARY,
    -> FROM employee;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'FROM employee' at line 3
MariaDB [manish]> SELECT EMPNO,
    -> ENAME,
    -> SAL * 12 AS ANNUAL_SALARY
    -> FROM employee;
+-------+--------+---------------+
| EMPNO | ENAME  | ANNUAL_SALARY |
+-------+--------+---------------+
|  7369 | SMITH  |          9600 |
|  7499 | ALLEN  |         19200 |
|  7521 | WARD   |         15000 |
|  7566 | JONES  |         35700 |
|  7654 | MARTIN |         15000 |
|  7698 | BLAKE  |         34200 |
|  7782 | CLARK  |         29400 |
|  7788 | SCOTT  |         36000 |
|  7839 | KING   |         60000 |
|  7844 | TURNER |         18000 |
|  7876 | ADAMS  |         13200 |
|  7900 | JAMES  |         11400 |
|  7902 | FORD   |         36000 |
|  7934 | MILLER |         15600 |
+-------+--------+---------------+
14 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employeee
    -> WHERE JOB ='CLERK'
    -> AND SAL >3000;
ERROR 1146 (42S02): Table 'manish.employeee' doesn't exist
MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE JOB ='CLERK'
    -> AND SAL >3000;
Empty set (0.001 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE JOB IN ('CLERK',SALESMAN','ANALYST')
    '> AND SAL >3000;
    '> AND SAL >3000;
    '> WHERE JOB IN ('CLERK',SALESMAN','ANALYST');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '','ANALYST')
AND SAL >3000;
AND SAL >3000;
WHERE JOB IN ('CLERK',SALESMAN','A...' at line 3
MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE JOB IN ('CLERK','SALESMAN','ANALYST')
    -> AND SAL >3000;
Empty set (0.001 sec)