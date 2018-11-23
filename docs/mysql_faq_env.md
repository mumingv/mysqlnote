# 环境FAQ

## tmpdir空间不足导致无法执行命令？

**问题现象**

```
mysql> desc tb_growth_user;
ERROR 1030 (HY000): Got error 28 from storage engine
```

**问题原因**

临时目录空间不足。

```
mysql> show variables like 'tmpdir';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| tmpdir        | /tmp  |
+---------------+-------+
```
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/tmp                   20G   19G  5.7M 100% /home/linux/V2-0.0.10-opt/tmp
```

**解决方法**

修改my.cnf配置文件并重启mysql。

```
tmpdir = /home/users/mumingv/.jumbo/var/lib/mysql/tmp
```
```
$ mysqladmin shutdown -uroot -pxxx
$ ~/.jumbo/bin/mysqld_safe &
```


