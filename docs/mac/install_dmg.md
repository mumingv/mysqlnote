# MAC安装MySQL（DMG方式）

## 下载安装

**下载**

最新版本：https://dev.mysql.com/downloads/mysql/

5.7版本：https://dev.mysql.com/downloads/mysql/5.7.html#downloads

注：本文使用Mysql5.7版本。


**安装**

双击安装即可，安装成功后会提供一个root的默认密码，该密码也可以在通知中心查看。

**安装后的目录结构**

MySQL的所有程序和数据均在目录`/usr/local/mysql/`下，pid文件在目录`/usr/local/mysql/data/`下。

```
$ ll /usr/local/ | grep mysql
lrwxr-xr-x   1 _mysql    _mysql    30  9 14 17:07 mysql -> mysql-5.7.27-macos10.14-x86_64
drwxr-xr-x  13 _mysql    _mysql   416  9 14 17:07 mysql-5.7.27-macos10.14-x86_64
```
```
$ ll /usr/local/mysql/
total 48
-rwxr-xr-x   1 _mysql  _mysql  17987  6 10 22:43 COPYING
-rwxr-xr-x   1 _mysql  _mysql   2478  6 10 22:43 README
drwxr-xr-x  40 _mysql  _mysql   1280  6 10 23:16 bin
drwxr-xr-x  14 _mysql  _mysql    448  9 14 17:36 data
drwxr-xr-x   5 _mysql  _mysql    160  6 10 23:15 docs
drwxr-xr-x  50 _mysql  _mysql   1600  6 10 23:15 include
drwxr-xr-x   3 _mysql  _mysql     96  9 14 17:24 keyring
drwxr-xr-x  11 _mysql  _mysql    352  9 14 17:07 lib
drwxr-xr-x   4 _mysql  _mysql    128  6 10 23:15 man
drwxr-xr-x  39 _mysql  _mysql   1248  6 10 23:15 share
drwxr-xr-x   6 _mysql  _mysql    192  6 10 23:15 support-files
```
```
$ ll /usr/local/mysql/data/
total 245896
-rwxr-xr-x    1 _mysql  _mysql     44931  9 14 17:36 00000065432i.err
-rw-r-----    1 _mysql  _mysql         4  9 14 17:36 00000065432i.pid
-rwxr-xr-x    1 _mysql  _mysql        56  9 14 17:07 auto.cnf
-rw-r-----    1 _mysql  _mysql       294  9 14 17:36 ib_buffer_pool
-rwxr-xr-x    1 _mysql  _mysql  50331648  9 14 17:36 ib_logfile0
-rwxr-xr-x    1 _mysql  _mysql  50331648  9 14 17:07 ib_logfile1
-rwxr-xr-x    1 _mysql  _mysql  12582912  9 14 17:36 ibdata1
-rw-r-----    1 _mysql  _mysql  12582912  9 14 17:36 ibtmp1
drwxr-xr-x   77 _mysql  _mysql      2464  9 14 17:07 mysql
-rw-r-----    1 _mysql  _mysql      8544  9 14 17:31 mysqld.local.err
drwxr-xr-x   90 _mysql  _mysql      2880  9 14 17:07 performance_schema
drwxr-xr-x  108 _mysql  _mysql      3456  9 14 17:07 sys
```


## 配置启动

### 方式一：在「系统偏好设置」中启动（推荐）

### 方式二：通过命令启动

**配置PATH**

```
$ vim ~/.bash_profile
export PATH=$PATH:/usr/local/mysql/bin
$ source ~/.bash_profile
```

**启动**

```
sudo /usr/local/mysql/support-files/mysql.server start
```


## 修改root密码

```
$ mysql -uroot -p
...
mysql> set password = password('12345678');
```



