# 操作

## 表 - 显示数据库的所有表

```
use demo;
show tables;
```
```
show tables from demo;
```

## 表 - 创建表

```
CREATE TABLE IF NOT EXISTS `think_data`(
    `id` int(8) unsigned NOT NULL AUTO_INCREMENT,
    `name` varchar(255) NOT NULL COMMENT '名称',
    `status` tinyint(2) NOT NULL DEFAULT '0' COMMENT '状态',
    PRIMARY KEY (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=utf8;
```


## 表 - 修改表名

```
RENAME TABLE `tb_user2` TO `tb_user`;
```


## 表 - 增加字段

```
ALTER TABLE think_data ADD status tinyint(2) NOT NULL DEFAULT '0' COMMENT '状态';
```


## 表 - 增加记录

```
INSERT INTO `think_data_2`(`id`,`name`,`status`) VALUES (1,'thinkphp',1),(2,'onethink',1),(3,'topthink',1);
```
```
INSERT INTO `think_data_2`(`id`,`name`,`status`) VALUES
(1,'thinkphp',1),
(2,'onethink',1),
(3,'topthink',1);
```


## 表 - 清空表记录

```
RUNCATE TABLE think_data;
```




