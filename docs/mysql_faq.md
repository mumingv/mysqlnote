# FAQ

## Mysql搭建了两套数据库分别使用不同的端口，如何在启动第二套数据库时制定配置文件？

第一套数据库启动时，使用`--defaults-file`参数指定配置文件；第二套数据库启动时，需要使用`--defaults-extra-file`参数指定配置文件。如下所示：

```
$ ./.jumbo/bin/mysqld_safe --defaults-extra-file=/home/work/data/mysql_8307/my.cnf  --datadir=/home/work/data/mysql_8307/data &
```

配置文件参考：[my.cnf](http://localhost/mnote/backup/mysql/my.cnf/my.cnf.enrich)。


## 运行脚本时提示活动连接数超过最大值？

报错如下：

```
PHP Warning:  mysqli::real_connect(): (42000/1203): User edurd_wr already has more than 'max_user_connections' active connections in ...
```

解决方法：待完善。


## 时间类型DATETIME和TIMESTAMP的区别？

DATETIME是本地时间，不会随时区的变化而变化；TIMESTAMP也是本地时间，但其会随时区的变化而变化。

示例如下：

```
mysql> create table datedemo(mydatetime datetime,mytimestamp timestamp);
mysql> insert into datedemo values ((now()), (now()));
mysql> select * from datedemo;                        
+---------------------+---------------------+
| mydatetime          | mytimestamp         |
+---------------------+---------------------+
| 2018-03-29 17:08:30 | 2018-03-29 17:08:30 |
+---------------------+---------------------+
mysql> set time_zone = '+10:00';         
mysql> flush privileges;
mysql> show variables like '%time_zone%';
+------------------+--------+
| Variable_name    | Value  |
+------------------+--------+
| system_time_zone | CST    |
| time_zone        | +10:00 |
+------------------+--------+
mysql> select * from datedemo;
+---------------------+---------------------+
| mydatetime          | mytimestamp         |
+---------------------+---------------------+
| 2018-03-29 17:08:30 | 2018-03-29 19:08:30 |
| 2018-03-29 17:14:49 | 2018-03-29 19:14:49 |
+---------------------+---------------------+
```

