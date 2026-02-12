in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'DATABAES' at line 1
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
6 rows in set (0.070 sec)

MariaDB [(none)]> SHOW TABLES;
ERROR 1046 (3D000): No database selected
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

MariaDB [manish]> SELCT *FROM employee;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'SELCT *FROM employee' at line 1
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
14 rows in set (0.094 sec)

MariaDB [manish]> SELECT * FROM department;
+--------+------------+
| DEPTNO | DNAME      |
+--------+------------+
|     10 | research   |
|     20 | accounting |
|     30 | sales      |
|     40 | operations |
+--------+------------+
4 rows in set (0.037 sec)

MariaDB [manish]> SELECT COUNT;
ERROR 1054 (42S22): Unknown column 'COUNT' in 'field list'
MariaDB [manish]> SELECT COUNT(*) AS total_employees
    -> FROM employee;
+-----------------+
| total_employees |
+-----------------+
|              14 |
+-----------------+
1 row in set (0.031 sec)

MariaDB [manish]> SELECT SUM(sal) AS total_salary
    -> FROM employee;
+--------------+
| total_salary |
+--------------+
|         7943 |
+--------------+
1 row in set (0.001 sec)

MariaDB [manish]> SELECT MAX(sal) AS maximum_salary
    -> FROM employee;
+----------------+
| maximum_salary |
+----------------+
|           1600 |
+----------------+
1 row in set (0.001 sec)

MariaDB [manish]> SELECT MIN(sal) AS minimum_salary
    -> FROM employee;
+----------------+
| minimum_salary |
+----------------+
|             80 |
+----------------+
1 row in set (0.002 sec)

MariaDB [manish]> SELECT AVG(sal) AS average_salary
    -> FROM employee;
+----------------+
| average_salary |
+----------------+
|       567.3571 |
+----------------+
1 row in set (0.001 sec)

MariaDB [manish]> SELECT MAX(sal) AS max_clerk_salary
    -> FROM employee
    -> WHERE job = 'CLERK';
+------------------+
| max_clerk_salary |
+------------------+
|              130 |
+------------------+
1 row in set (0.002 sec)

MariaDB [manish]> SELECT MAX(sal) AS max_dept20_salary
    -> FROM employee
    -> WHERE deptno = 20;
+-------------------+
| max_dept20_salary |
+-------------------+
|               300 |
+-------------------+
1 row in set (0.002 sec)

MariaDB [manish]> SELECT MIN(sal) AS min_salesman_salary
    -> FROM employee
    -> WHERE job = 'SALESMAN';
+---------------------+
| min_salesman_salary |
+---------------------+
|                1250 |
+---------------------+
1 row in set (0.002 sec)

MariaDB [manish]> SELECT AVG(sal) AS avg_manager_salary
    -> FROM employee
    -> WHERE job = 'MANAGER';
+--------------------+
| avg_manager_salary |
+--------------------+
|           276.0000 |
+--------------------+
1 row in set (0.001 sec)

MariaDB [manish]> SELECT SUM(sal) AS total_analyst_salary
    -> FROM employee
    -> WHERE job = 'ANALYST'
    -> AND deptno = 40;
+----------------------+
| total_analyst_salary |
+----------------------+
|                 NULL |
+----------------------+
1 row in set (0.013 sec)

MariaDB [manish]> SELECT UPPER(ename) AS employee_name
    -> FROM employee;
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

MariaDB [manish]> SELECT LOWER(ename) AS employee_name
    -> FROM employee;
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

MariaDB [manish]> SELECT INITCAP(ename) AS employee_name
    -> FROM employee;
ERROR 1305 (42000): FUNCTION manish.INITCAP does not exist
MariaDB [manish]> SELECT CONCAT(UPPER(LEFT(ename,1)), LOWER(SUBSTRING(ename,2))) AS employee_name
    -> FROM employee;
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

MariaDB [manish]> SELECT LENGTH('MANISH') AS name_length;
+-------------+
| name_length |
+-------------+
|           6 |
+-------------+
1 row in set (0.001 sec)

MariaDB [manish]> SELECT ename, LENGTH(ename) AS name_length
    -> FROM employee;
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