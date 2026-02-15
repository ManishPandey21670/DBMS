```SQL
MariaDB [(none)]> SHOW DATABASES;
```
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
6 rows in set (0.070 sec)

```SQL
MariaDB [(none)]> USE manish;
Database changed
MariaDB [manish]> SHOW TABLES;
```
+------------------+
| Tables_in_manish |
+------------------+
| department       |
| employee         |
+------------------+
2 rows in set (0.001 sec)

###1.Display the total number of employee working in the company.
```SQL
MariaDB [manish]> SELECT COUNT(*) AS total_employees
    -> FROM employee;
```
+-----------------+
| total_employees |
+-----------------+
|              14 |
+-----------------+
1 row in set (0.031 sec)

###2.Display the total salary being paid to all employees.
```SQL
MariaDB [manish]> SELECT SUM(sal) AS total_salary
    -> FROM employee;
```
+--------------+
| total_salary |
+--------------+
|         7943 |
+--------------+
1 row in set (0.001 sec)

###3.Display the maximum salary from employee table.
```SQL
MariaDB [manish]> SELECT MAX(sal) AS maximum_salary
    -> FROM employee;
```
+----------------+
| maximum_salary |
+----------------+
|           1600 |
+----------------+
1 row in set (0.001 sec)

###4.Display the minimum salary from employee table.
```SQL
MariaDB [manish]> SELECT MIN(sal) AS minimum_salary
    -> FROM employee;
```
+----------------+
| minimum_salary |
+----------------+
|             80 |
+----------------+
1 row in set (0.002 sec)

###5.Display the average salary from employee table.
```SQL
MariaDB [manish]> SELECT AVG(sal) AS average_salary
    -> FROM employee;
```
+----------------+
| average_salary |
+----------------+
|       567.3571 |
+----------------+
1 row in set (0.001 sec)

###6.Display the maximum salary being paid to clerk.
```SQL
MariaDB [manish]> SELECT MAX(sal) AS max_clerk_salary
    -> FROM employee
    -> WHERE job = 'CLERK';
```
+------------------+
| max_clerk_salary |
+------------------+
|              130 |
+------------------+
1 row in set (0.002 sec)

###7.Display the maximum salary being paid in dept no 20.
```SQL
MariaDB [manish]> SELECT MAX(sal) AS max_dept20_salary
    -> FROM employee
    -> WHERE deptno = 20;
```
+-------------------+
| max_dept20_salary |
+-------------------+
|               300 |
+-------------------+
1 row in set (0.002 sec)

###8.Display the minimum salary paid to any salesman.
```SQL
MariaDB [manish]> SELECT MIN(sal) AS min_salesman_salary
    -> FROM employee
    -> WHERE job = 'SALESMAN';
```
+---------------------+
| min_salesman_salary |
+---------------------+
|                1250 |
+---------------------+
1 row in set (0.002 sec)

###9.Display the average salary drawn by managers.
```SQL
MariaDB [manish]> SELECT AVG(sal) AS avg_manager_salary
    -> FROM employee
    -> WHERE job = 'MANAGER';
```
+--------------------+
| avg_manager_salary |
+--------------------+
|           276.0000 |
+--------------------+
1 row in set (0.001 sec)

###10.Display the total salary drawn by analyst working in dept no 40.
```SQL
MariaDB [manish]> SELECT SUM(sal) AS total_analyst_salary
    -> FROM employee
    -> WHERE job = 'ANALYST'
    -> AND deptno = 40;
```
+----------------------+
| total_analyst_salary |
+----------------------+
|                 NULL |
+----------------------+
1 row in set (0.013 sec)

###11.Display the names of the employee in Uppercase.
```SQL
MariaDB [manish]> SELECT UPPER(ename) AS employee_name
    -> FROM employee;
```
+---------------+
| employee_name |
+---------------+
| SMITH         |
| ALLEN         |
| WARD          |
| JONES         |
| MARTIN        |
| BLAKE         |
| CLARK         |
| SCOTT         |
| KING          |
| TURNER        |
| ADAMS         |
| JAMES         |
| FORD          |
| MILLER        |
+---------------+
14 rows in set (0.002 sec)

###12.Display the names of the employee in Lowercase.
```SQL
MariaDB [manish]> SELECT LOWER(ename) AS employee_name
    -> FROM employee;
```
+---------------+
| employee_name |
+---------------+
| smith         |
| allen         |
| ward          |
| jones         |
| martin        |
| blake         |
| clark         |
| scott         |
| king          |
| turner        |
| adams         |
| james         |
| ford          |
| miller        |
+---------------+
14 rows in set (0.002 sec)

###13.Display the names of the employee in Proper case.
```SQL
MariaDB [manish]> SELECT CONCAT(UPPER(LEFT(ename,1)), LOWER(SUBSTRING(ename,2))) AS employee_name
    -> FROM employee;
```
+---------------+
| employee_name |
+---------------+
| Smith         |
| Allen         |
| Ward          |
| Jones         |
| Martin        |
| Blake         |
| Clark         |
| Scott         |
| King          |
| Turner        |
| Adams         |
| James         |
| Ford          |
| Miller        |
+---------------+
14 rows in set (0.001 sec)

###14.Display the length of Your name using appropriate function.
```SQL
MariaDB [manish]> SELECT LENGTH('MANISH') AS name_length;
```
+-------------+
| name_length |
+-------------+
|           6 |
+-------------+
1 row in set (0.001 sec)

###15.Display the length of all the employee names.
```SQL
MariaDB [manish]> SELECT ename, LENGTH(ename) AS name_length
    -> FROM employee;
```
+--------+-------------+
| ename  | name_length |
+--------+-------------+
| SMITH  |           5 |
| ALLEN  |           5 |
| WARD   |           4 |
| JONES  |           5 |
| MARTIN |           6 |
| BLAKE  |           5 |
| CLARK  |           5 |
| SCOTT  |           5 |
| KING   |           4 |
| TURNER |           6 |
| ADAMS  |           5 |
| JAMES  |           5 |
| FORD   |           4 |
| MILLER |           6 |
+--------+-------------+
14 rows in set (0.001 sec)