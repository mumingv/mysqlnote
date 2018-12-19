# MAC安装MySQL

## 下载安装

**下载**

最新版本：https://dev.mysql.com/downloads/mysql/

5.7版本：https://dev.mysql.com/downloads/mysql/5.7.html#downloads

注：本文使用Mysql5.7版本。


**安装**

双击安装即可，安装成功后会提供一个root的默认密码，该密码也可以在通知中心查看。

注：MySQL的安装命令为`/usr/local/mysql/`。


## 配置启动

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



