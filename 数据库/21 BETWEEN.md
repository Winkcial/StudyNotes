BETWEEN 操作符用于选取介于两个值之间的数据范围内的值。
这些值可以是数值、文本或者日期。



SQL BETWEEN 语法

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

下面的 SQL 语句选取 alexa 介于 1 和 20 之间的所有网站：

```
mysql> select * from websites;
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
|  1 | Google       | https://www.google.cm/    |     1 | USA     |
|  2 | 淘宝         | https://www.taobao.com/   |    13 | CN      |
|  3 | 菜鸟教程     | http://www.runoob.com/    |  4689 | CN      |
|  4 | 微博         | http://weibo.com/         |    20 | CN      |
|  5 | Facebook     | https://www.facebook.com/ |     3 | USA     |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.01 sec)

mysql> select * from websites where alexa between 1 and 20;
+----+----------+---------------------------+-------+---------+
| id | name     | url                       | alexa | country |
+----+----------+---------------------------+-------+---------+
|  1 | Google   | https://www.google.cm/    |     1 | USA     |
|  2 | 淘宝     | https://www.taobao.com/   |    13 | CN      |
|  4 | 微博     | http://weibo.com/         |    20 | CN      |
|  5 | Facebook | https://www.facebook.com/ |     3 | USA     |
+----+----------+---------------------------+-------+---------+
4 rows in set (0.00 sec)
```

如果想查询在范围外的数据就加上NOT，下面是一个例子

```
mysql> select * from websites where alexa not between 1 and 20;
+----+--------------+------------------------+-------+---------+
| id | name         | url                    | alexa | country |
+----+--------------+------------------------+-------+---------+
|  3 | 菜鸟教程     | http://www.runoob.com/ |  4689 | CN      |
+----+--------------+------------------------+-------+---------+
1 row in set (0.00 sec)
```

下面的 SQL 语句选取 alexa 介于 1 和 20 之间但 country 不为 USA 和 IND 的所有网站：

```
mysql> select * from websites where (alexa between 1 and 20)
    -> and 
    -> country not in ('USA','IND');
+----+--------+-------------------------+-------+---------+
| id | name   | url                     | alexa | country |
+----+--------+-------------------------+-------+---------+
|  2 | 淘宝   | https://www.taobao.com/ |    13 | CN      |
|  4 | 微博   | http://weibo.com/       |    20 | CN      |
+----+--------+-------------------------+-------+---------+
2 rows in set (0.00 sec)
```

带有文本值的 BETWEEN 操作符实例

下面的 SQL 语句选取 name 以介于 'A' 和 'H' 之间字母开始的所有网站：

```
mysql> select * from websites where name between 'A' and 'H';
+----+----------+---------------------------+-------+---------+
| id | name     | url                       | alexa | country |
+----+----------+---------------------------+-------+---------+
|  1 | Google   | https://www.google.cm/    |     1 | USA     |
|  5 | Facebook | https://www.facebook.com/ |     3 | USA     |
+----+----------+---------------------------+-------+---------+
2 rows in set (0.00 sec)
```

下面是 "access_log" 网站访问记录表的数据，其中：

- aid：为自增 id。
- site_id：为对应 websites表的网站 id。
- count：访问次数。
- date：为访问日期。


下面对于表access_log查询日期在2016/5/16到2016/5/17日之间所有的数据

```
mysql> select * from access_log where date between '2016-05-16' and '2016-05-17';
+-----+---------+-------+------------+
| aid | site_id | count | date       |
+-----+---------+-------+------------+
|   8 |       5 |   545 | 2016-05-16 |
|   9 |       3 |   201 | 2016-05-17 |
+-----+---------+-------+------------+
2 rows in set (0.00 sec)
```

补充

- 请注意，在不同的数据库中，BETWEEN 操作符会产生不同的结果！
- 在某些数据库中，BETWEEN 选取介于两个值之间但不包括两个测试值的字段。
- 在某些数据库中，BETWEEN 选取介于两个值之间且包括两个测试值的字段。
- 在某些数据库中，BETWEEN 选取介于两个值之间且包括第一个测试值但不包括最后一个测试值的字段。

因此，请检查您的数据库是如何处理 BETWEEN 操作符！


