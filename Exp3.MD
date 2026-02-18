###1.List all employees and jobs in Department 30 in descending order by salary.
```SQL
MariaDB [manish]> SELECT ENAME,JOB,SAL
    -> FROM employee
    -> WHERE DEPTNO=30
    -> ORDER BY SAL DESC;
```
+--------+----------+------+
| ENAME  | JOB      | SAL  |
+--------+----------+------+
| ALLEN  | SALESMAN | 1600 |
| TURNER | SALESMAN | 1500 |
| WARD   | SALESMAN | 1250 |
| MARTIN | SALESMAN | 1250 |
| BLAKE  | MANAGER  |  285 |
| JAMES  | CLERK    |   95 |
+--------+----------+------+
6 rows in set (0.002 sec)

###2.List job and Department Number of employees whose name are five letters long begin with “A” and end with “N”.
```SQL
MariaDB [manish]> SELECT JOB, DEPTNO
    -> FROM employee
    -> WHERE ENAME LIKE 'A___N';
```
+----------+--------+
| JOB      | DEPTNO |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+
1 row in set (0.001 sec)

###3.Display the name of employees whose name start with alphabet S.
```SQL
MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE ENAME LIKE 'S%';
```
+-------+
| ENAME |
+-------+
| SMITH |
| SCOTT |
+-------+
2 rows in set (0.001 sec)

###5.Display the names of employees working in department number 10 or 20 or 40 or employees working as clerks, salesman or analyst.
```SQL
MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE DEPTNO IN(10,20,30)
    -> AND JOB IN ('CLERK','SALESMAN','ANALYST');
```
+--------+
| ENAME  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| MARTIN |
| SCOTT  |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
10 rows in set (0.001 sec)

###6.Display employee number and names for employees who earn commission.
```SQL
MariaDB [manish]> SELECT EMPNO,ENAME
    -> FROM employee
    -> WHERE COMM IS NOT NULL
    -> AND COMM>0;
```
+-------+--------+
| EMPNO | ENAME  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
+-------+--------+
3 rows in set (0.001 sec)

###7.Display employee number and total salary for each employee.
```SQL
MariaDB [manish]> SELECT EMPNO,
    -> (SAL+IFNULL(COMM,0)) AS TOTAL_SALARY
    -> FROM employee;
```
+-------+--------------+
| EMPNO | TOTAL_SALARY |
+-------+--------------+
|  7369 |           80 |
|  7499 |         1900 |
|  7521 |         1550 |
|  7566 |          298 |
|  7654 |         2650 |
|  7698 |          285 |
|  7782 |          245 |
|  7788 |          300 |
|  7839 |          500 |
|  7844 |         1500 |
|  7876 |          110 |
|  7900 |           95 |
|  7902 |          300 |
|  7934 |          130 |
+-------+--------------+
14 rows in set (0.001 sec)

###8.Display employee number and annual salary for each employee.
```SQL
MariaDB [manish]> SELECT EMPNO,
    ->  ENAME,
    ->  SAL * 12 AS ANNUAL_SALARY
    -> FROM employee;
```
+-------+--------+---------------+
| EMPNO | ENAME  | ANNUAL_SALARY |
+-------+--------+---------------+
|  7369 | SMITH  |           960 |
|  7499 | ALLEN  |         19200 |
|  7521 | WARD   |         15000 |
|  7566 | JONES  |          3576 |
|  7654 | MARTIN |         15000 |
|  7698 | BLAKE  |          3420 |
|  7782 | CLARK  |          2940 |
|  7788 | SCOTT  |          3600 |
|  7839 | KING   |          6000 |
|  7844 | TURNER |         18000 |
|  7876 | ADAMS  |          1320 |
|  7900 | JAMES  |          1140 |
|  7902 | FORD   |          3600 |
|  7934 | MILLER |          1560 |
+-------+--------+---------------+
14 rows in set (0.001 sec)

###9.Display the names of all employees working as clerks and drawing a salary more than 3,000.
```SQL
MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE JOB ='CLERK'
    -> AND SAL>3000;
```
Empty set (0.001 sec)

###10.Display the names of employees who are working as clerk, salesman or analyst and drawing a salary more than 3,000.
```SQL
MariaDB [manish]> SELECT ENAME
    -> FROM employee
    -> WHERE JOB IN ('CLERK','SALESMAN','ANALYST')
    -> AND SAL>3000;
```
Empty set (0.001 sec)