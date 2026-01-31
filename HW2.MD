CREATING TABLE
```SQL
MariaDB [IILM]> CREATE TABLE movie(
    -> MovieID INT PRIMARY KEY,
    -> MovieName VARCHAR(50) NOT NULL,
    -> Category VARCHAR(50) NOT NULL,
    -> ReleaseDate DATE,
    -> ProductionCost INT NOT NULL,
    -> BusinessCost INT);
Query OK, 0 rows affected (0.050 sec)
```
DESCRIBING TABLE
```SQL
MariaDB [IILM]> DESC movie;
```
```SQL
+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| MovieID        | int(11)     | NO   | PRI | NULL    |       |
| MovieName      | varchar(50) | NO   |     | NULL    |       |
| Category       | varchar(50) | NO   |     | NULL    |       |
| ReleaseDate    | date        | YES  |     | NULL    |       |
| ProductionCost | int(11)     | NO   |     | NULL    |       |
| BusinessCost   | int(11)     | YES  |     | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
6 rows in set (0.061 sec)
```
INSERTING INTO TABLE
```SQL


MariaDB [IILM]> INSERT INTO movie(
    -> VALUES(001,"Hindu_Movie","Musical","2018-04-23",124500,130000),
    -> (002,"Tamil_Movie","Action","2016-05-17",112000,118000),
    -> (003,"Englis_Movie","Horror","2017-08-06",245000,360000),
    -> (004,"Bengali_Movie","Adventure","2017-01-04",72000,100000),
    -> (005,"Telugu_Movie","Action",NULL,100000,NULL),
    -> (006,"Punjabi_Movie","Comedy",NULL,30500,NULL));
Query OK, 6 rows affected (0.035 sec)
Records: 6  Duplicates: 0  Warnings: 0
```
VIEWING TUPLES OF TABLE
```SQL
MariaDB [IILM]> SELECT * FROM movie;
```
```SQL
| MovieID | MovieName     | Category  | ReleaseDate | ProductionCost | BusinessCost |
+---------+---------------+-----------+-------------+----------------+--------------+
|       1 | Hindu_Movie   | Musical   | 2018-04-23  |         124500 |       130000 |
|       2 | Tamil_Movie   | Action    | 2016-05-17  |         112000 |       118000 |
|       3 | Englis_Movie  | Horror    | 2017-08-06  |         245000 |       360000 |
|       4 | Bengali_Movie | Adventure | 2017-01-04  |          72000 |       100000 |
|       5 | Telugu_Movie  | Action    | NULL        |         100000 |         NULL |
|       6 | Punjabi_Movie | Comedy    | NULL        |          30500 |         NULL |
+---------+---------------+-----------+-------------+----------------+--------------+
6 rows in set (0.001 sec)
```
```SQL
MariaDB [IILM]> SELECT MovieID,MovieName,BusinessCost
    -> FROM movie;   
```
```SQL
+---------+---------------+--------------+
| MovieID | MovieName     | BusinessCost |
+---------+---------------+--------------+
|       1 | Hindu_Movie   |       130000 |
|       2 | Tamil_Movie   |       118000 |
|       3 | Englis_Movie  |       360000 |
|       4 | Bengali_Movie |       100000 |
|       5 | Telugu_Movie  |         NULL |
|       6 | Punjabi_Movie |         NULL |
+---------+---------------+--------------+
6 rows in set (0.001 sec)
```
```SQL
MariaDB [IILM]> SELECT DISTINCT Category
    -> FROM movie;
```

```SQL
+-----------+
| Category  |
+-----------+
| Musical   |
| Action    |
| Horror    |
| Adventure |
| Comedy    |
+-----------+
5 rows in set (0.001 sec)
```
```SQL
MariaDB [IILM]> SELECT MovieID,
    -> MovieName,
    -> (BusinessCost-ProductionCost) AS NetProfit
    -> FROM movie;       
```
```SQL
+---------+---------------+-----------+
| MovieID | MovieName     | NetProfit |
+---------+---------------+-----------+
|       1 | Hindu_Movie   |      5500 |
|       2 | Tamil_Movie   |      6000 |
|       3 | Englis_Movie  |    115000 |
|       4 | Bengali_Movie |     28000 |
|       5 | Telugu_Movie  |      NULL |
|       6 | Punjabi_Movie |      NULL |
+---------+---------------+-----------+
6 rows in set (0.001 sec)
```
```SQL
MariaDB [IILM]> SELECT MovieID, MovieName, ProductionCost
    -> FROM movie
    -> WHERE ProductionCost>80000
    -> AND ProductionCost<125000;
```
```SQL
+---------+--------------+----------------+
| MovieID | MovieName    | ProductionCost |
+---------+--------------+----------------+
|       1 | Hindu_Movie  |         124500 |
|       2 | Tamil_Movie  |         112000 |
|       5 | Telugu_Movie |         100000 |
+---------+--------------+----------------+
3 rows in set (0.001 sec)
```
```SQL
MariaDB [IILM]> SELECT MovieID,MovieName, Category
    -> FROM movie
    -> WHERE Category='Comedy'
    -> OR Category='Action';
```
```SQL
+---------+---------------+----------+
| MovieID | MovieName     | Category |
+---------+---------------+----------+
|       2 | Tamil_Movie   | Action   |
|       5 | Telugu_Movie  | Action   |
|       6 | Punjabi_Movie | Comedy   |
+---------+---------------+----------+
3 rows in set (0.001 sec)
```

```SQL
MariaDB [IILM]> SELECT MovieID, MovieName
    -> FROM movie
    -> WHERE ReleaseDate IS NULL;
+---------+---------------+
| MovieID | MovieName     |
+---------+---------------+
|       5 | Telugu_Movie  |
|       6 | Punjabi_Movie |
+---------+---------------+
2 rows in set (0.001 sec)
