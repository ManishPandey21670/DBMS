###1.Display empno, ename, deptno from employee table. Instead of displaying department numbers display the related department name (Use decode function).
```SQL
MariaDB [manish]> SELECT EMPNO,
    ->        ENAME,
    ->        DEPTNO,
    ->        CASE
    ->            WHEN DEPTNO = 10 THEN 'ACCOUNTING'
    ->            WHEN DEPTNO = 20 THEN 'RESEARCH'
    ->            WHEN DEPTNO = 30 THEN 'SALES'
    ->            WHEN DEPTNO = 40 THEN 'OPERATIONS'
    ->            ELSE 'UNKNOWN'
    ->        END AS DEPT_NAME
    -> FROM employee;
```
+-------+--------+--------+------------+
| EMPNO | ENAME  | DEPTNO | DEPT_NAME  |
+-------+--------+--------+------------+
|  7369 | SMITH  |     20 | RESEARCH   |
|  7499 | ALLEN  |     30 | SALES      |
|  7521 | WARD   |     30 | SALES      |
|  7566 | JONES  |     20 | RESEARCH   |
|  7654 | MARTIN |     30 | SALES      |
|  7698 | BLAKE  |     30 | SALES      |
|  7782 | CLARK  |     10 | ACCOUNTING |
|  7788 | SCOTT  |     20 | RESEARCH   |
|  7839 | KING   |     10 | ACCOUNTING |
|  7844 | TURNER |     30 | SALES      |
|  7876 | ADAMS  |     20 | RESEARCH   |
|  7900 | JAMES  |     30 | SALES      |
|  7902 | FORD   |     20 | RESEARCH   |
|  7934 | MILLER |     10 | ACCOUNTING |
+-------+--------+--------+------------+
14 rows in set (0.001 sec)

###2.Display your age in days.
```SQL
MariaDB [manish]> SELECT DATEDIFF(CURDATE(), '2004-08-15') AS AGE_IN_DAYS;
```
+-------------+
| AGE_IN_DAYS |
+-------------+
|        7851 |
+-------------+
1 row in set (0.001 sec)

###3.Display your age in months.
```SQL
MariaDB [manish]> SELECT TIMESTAMPDIFF(MONTH, '2004-08-15', CURDATE()) AS AGE_IN_MONTHS;
```
+---------------+
| AGE_IN_MONTHS |
+---------------+
|           257 |
+---------------+
1 row in set (0.001 sec)

###4.Display the current date as 15th August Friday Nineteen Ninety-Seven.
```SQL
MariaDB [manish]> SELECT DATE_FORMAT(NOW(), '%D %M %W %Y') AS CURRENT_DATE_FORMAT;
```
+-----------------------------+
| CURRENT_DATE_FORMAT         |
+-----------------------------+
| 12th February Thursday 2026 |
+-----------------------------+
1 row in set (0.001 sec)

###5.Display the following output for each row from employee table.
```SQL
MariaDB [manish]> SELECT CONCAT(ENAME,
    ->               ' has joined the company on ',
    ->               DATE_FORMAT(HIREDATE, '%W %D %M %Y')) AS MESSAGE
    -> FROM employee;
```
+--------------------------------------------------------------+
| MESSAGE                                                      |
+--------------------------------------------------------------+
| SMITH has joined the company on Wednesday 17th December 1980 |
| ALLEN has joined the company on Friday 20th February 1981    |
| WARD has joined the company on Sunday 22nd February 1981     |
| JONES has joined the company on Thursday 2nd April 1981      |
| MARTIN has joined the company on Monday 28th September 1981  |
| BLAKE has joined the company on Friday 1st May 1981          |
| CLARK has joined the company on Tuesday 9th June 1981        |
| SCOTT has joined the company on Thursday 9th December 1982   |
| KING has joined the company on Tuesday 17th November 1981    |
| TURNER has joined the company on Tuesday 8th September 1981  |
| ADAMS has joined the company on Wednesday 12th January 1983  |
| JAMES has joined the company on Thursday 3rd December 1981   |
| FORD has joined the company on Thursday 3rd December 1981    |
| MILLER has joined the company on Saturday 23rd January 1982  |
+--------------------------------------------------------------+
14 rows in set (0.001 sec)

###6.Scott has joined the company on Wednesday 13th August Nineteen Ninety.
```SQL
MariaDB [manish]> SELECT CONCAT(ENAME,
    ->               ' has joined the company on ',
    ->               DATE_FORMAT(HIREDATE, '%W %D %M %Y')) AS MESSAGE
    -> FROM employee
    -> WHERE ENAME = 'SCOTT';
```
+------------------------------------------------------------+
| MESSAGE                                                    |
+------------------------------------------------------------+
| SCOTT has joined the company on Thursday 9th December 1982 |
+------------------------------------------------------------+
1 row in set (0.004 sec)

###7.Find the date for nearest Saturday after current date.
```SQL
MariaDB [manish]> SELECT DATE_ADD(CURDATE(),
    ->        INTERVAL (7 - WEEKDAY(CURDATE()) + 5) % 7 DAY)
    -> AS NEXT_SATURDAY;
```
+---------------+
| NEXT_SATURDAY |
+---------------+
| 2026-02-14    |
+---------------+
1 row in set (0.001 sec)

###8.Display current time.
```SQL
MariaDB [manish]> SELECT NOW();
```
+---------------------+
| NOW()               |
+---------------------+
| 2026-02-12 16:45:13 |
+---------------------+
1 row in set (0.001 sec)

###9.Display the date three months before the current date.
```SQL
MariaDB [manish]> SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH)
    -> AS THREE_MONTHS_BEFORE;
```
+---------------------+
| THREE_MONTHS_BEFORE |
+---------------------+
| 2025-11-12          |
+---------------------+
1 row in set (0.000 sec)

###10.Display those employees who joined in the company in the month of Dec.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE MONTH(HIREDATE) = 12;
```
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
|  7369 | SMITH | CLERK   | 7902 | 1980-12-17 |   80 | NULL |     20 |
|  7788 | SCOTT | ANALYST | 7566 | 1982-12-09 |  300 | NULL |     20 |
|  7900 | JAMES | CLERK   | 7698 | 1981-12-03 |   95 | NULL |     30 |
|  7902 | FORD  | ANALYST | 7566 | 1981-12-03 |  300 | NULL |     20 |
+-------+-------+---------+------+------------+------+------+--------+
4 rows in set (0.001 sec)

###11.Display those employees whose first 2 characters from hire date - last 2 characters of salary.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE RIGHT(DAY(HIREDATE), 2) =
    ->       RIGHT(SAL, 2);
```
Empty set (0.003 sec)

###12.Display those employees whose 10% of salary is equal to the year of joining.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE SAL * 0.10 =
    ->       YEAR(HIREDATE);
```
Empty set (0.002 sec)

###13.Display those employees who joined the company before 15 of the months.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE DAY(HIREDATE) < 15;
```
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
|  7566 | JONES  | MANAGER  | 7839 | 1981-04-02 |  298 | NULL |     20 |
|  7698 | BLAKE  | MANAGER  | 7839 | 1981-05-01 |  285 | NULL |     30 |
|  7782 | CLARK  | MANAGER  | 7839 | 1981-06-09 |  245 | NULL |     10 |
|  7788 | SCOTT  | ANALYST  | 7566 | 1982-12-09 |  300 | NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 1983-01-12 |  110 | NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 1981-12-03 |   95 | NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 1981-12-03 |  300 | NULL |     20 |
+-------+--------+----------+------+------------+------+------+--------+
8 rows in set (0.001 sec)

###14.Display those employees who has joined before 15th of the month.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE HIREDATE < DATE_SUB(CURDATE(), INTERVAL 15 MONTH);
```
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
14 rows in set (0.002 sec)

###15.Display those employees whose joining DATE is available in deptno.
```SQL
MariaDB [manish]> SELECT *
    -> FROM employee
    -> WHERE HIREDATE IS NOT NULL;
```
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