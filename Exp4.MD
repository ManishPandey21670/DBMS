
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
6 rows in set (0.107 sec)

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

MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE HIREDATE <'1980-06-30'
    -> OR HIREDATE > '1981-12-31';
+-------+--------+---------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+---------+------+------------+------+------+--------+
|  7788 | SCOTT  | ANALYST | 7566 | 1982-12-09 | 3000 | NULL |     20 |
|  7876 | ADAMS  | CLERK   | 7788 | 1983-01-12 | 1100 | NULL |     20 |
|  7934 | MILLER | CLERK   | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+-------+--------+---------+------+------------+------+------+--------+
3 rows in set (0.078 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE ENAME LIKE '_A%';
+--------+
| ENAME  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE LENGTH(ENAME)=5;
+-------+
| ENAME |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+
8 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME,JOB
    -> FROM employee
    -> WHERE JOB NOT IN ('SALESMAN','CLERK','ANALYST');
+-------+-----------+
| ENAME | JOB       |
+-------+-----------+
| JONES | MANAGER   |
| BLAKE | MANAGER   |
| CLARK | MANAGER   |
| KING  | PRESIDENT |
+-------+-----------+
4 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME, SAL*12 AS ANNUAL_SALARY
    -> FROM employee
    -> ORDER BY SAL DESC;
+--------+---------------+
| ENAME  | ANNUAL_SALARY |
+--------+---------------+
| KING   |         60000 |
| SCOTT  |         36000 |
| FORD   |         36000 |
| JONES  |         35700 |
| BLAKE  |         34200 |
| CLARK  |         29400 |
| ALLEN  |         19200 |
| TURNER |         18000 |
| MILLER |         15600 |
| MARTIN |         15000 |
| WARD   |         15000 |
| ADAMS  |         13200 |
| JAMES  |         11400 |
| SMITH  |          9600 |
+--------+---------------+
14 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME,
    -> SAL,
    -> SAL*0.15 AS HRA,
    -> SAL*0.10 AS DA,
    -> SAL*0.05 AS PF,
    -> (SAL+(SAL*0.15)+(SAL*0.10)-(SAL*0.05)) AS TOTAL_SALARY,
    -> FROM employee
    -> ORDER BY TOTAL_SALARY;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'FROM employee
ORDER BY TOTAL_SALARY' at line 7
MariaDB [manish]> SELECT ENAME,
    -> SAL,
    -> SAL*0.15 AS HRA,
    -> SAL*0.10 AS DA,
    -> SAL*0.05 AS PF,
    -> (SAL+(SAL*0.15)+(SAL*0.10)-(SAL*0.05)) AS TOTAL_SALARY
    -> FROM employee
    -> ORDER BY TOTAL_SALARY;
+--------+------+--------+--------+--------+--------------+
| ENAME  | SAL  | HRA    | DA     | PF     | TOTAL_SALARY |
+--------+------+--------+--------+--------+--------------+
| SMITH  |  800 | 120.00 |  80.00 |  40.00 |       960.00 |
| JAMES  |  950 | 142.50 |  95.00 |  47.50 |      1140.00 |
| ADAMS  | 1100 | 165.00 | 110.00 |  55.00 |      1320.00 |
| WARD   | 1250 | 187.50 | 125.00 |  62.50 |      1500.00 |
| MARTIN | 1250 | 187.50 | 125.00 |  62.50 |      1500.00 |
| MILLER | 1300 | 195.00 | 130.00 |  65.00 |      1560.00 |
| TURNER | 1500 | 225.00 | 150.00 |  75.00 |      1800.00 |
| ALLEN  | 1600 | 240.00 | 160.00 |  80.00 |      1920.00 |
| CLARK  | 2450 | 367.50 | 245.00 | 122.50 |      2940.00 |
| BLAKE  | 2850 | 427.50 | 285.00 | 142.50 |      3420.00 |
| JONES  | 2975 | 446.25 | 297.50 | 148.75 |      3570.00 |
| FORD   | 3000 | 450.00 | 300.00 | 150.00 |      3600.00 |
| SCOTT  | 3000 | 450.00 | 300.00 | 150.00 |      3600.00 |
| KING   | 5000 | 750.00 | 500.00 | 250.00 |      6000.00 |
+--------+------+--------+--------+--------+--------------+
14 rows in set (0.001 sec)

MariaDB [manish]> UPDATE employee
    -> SET SAL =SAL*.10
    -> WHERE COMM IS NULL;
Query OK, 10 rows affected (0.003 sec)
Rows matched: 10  Changed: 10  Warnings: 0

MariaDB [manish]> SELECT *FROM employee;
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |   80 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 |  298 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 |  285 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 |  245 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 |  300 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 |  500 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 |  110 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |   95 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 |  300 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 |  130 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.001 sec)

MariaDB [manish]> SELECT ENAME,SAL, SAL*1.20 AS
    -> INCREMENTED_SALARY
    -> FROM employee
    -> WHERE SAL*1.20>3000;
Empty set (0.001 sec)

MariaDB [manish]> SELECT ENAME,SAL
    -> FROM employee
    -> WHERE SAL>=100;
+--------+------+
| ENAME  | SAL  |
+--------+------+
| ALLEN  | 1600 |
| WARD   | 1250 |
| JONES  |  298 |
| MARTIN | 1250 |
| BLAKE  |  285 |
| CLARK  |  245 |
| SCOTT  |  300 |
| KING   |  500 |
| TURNER | 1500 |
| ADAMS  |  110 |
| FORD   |  300 |
| MILLER |  130 |
+--------+------+
12 rows in set (0.001 sec)