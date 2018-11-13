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

## 表 - 清空表

```
TRUNCATE tb_main_task;
```


## 表 - 删除表

```
DROP TABLE tb_main_task;
```


## 表 - 修改表名

```
RENAME TABLE `tb_user2` TO `tb_user`;
```


## 表 - 增加字段

**在所有表字段之后增加字段**

```
ALTER TABLE think_data ADD status tinyint(2) NOT NULL DEFAULT '0' COMMENT '状态';
```

**在特定字段之后增加字段**

```
ALTER TABLE `tb_growth_user_sub_task_history` ADD `appid` VARCHAR(128) NOT NULL DEFAULT '' COMMENT  'appid' AFTER  `query`;
```


## 表 - 删除字段

```
ALTER TABLE `tb_growth_user_main_task_history` DROP `task_circle_times`;
```


## 表 - 增加索引

增加单个索引

```
ALTER TABLE `tb_main_task` ADD INDEX (`task_category`);
```

增加多个索引

```
ALTER TABLE `tb_main_task`
ADD INDEX (`task_category`),
ADD INDEX (`create_user`),
ADD INDEX (`status`),
ADD INDEX (`is_del`);
```

增加联合索引

```
ALTER TABLE `tb_demo` ADD INDEX idx_task_id_user_id(`task_id`, `user_id`);
```


## 表 - 删除索引

```
ALTER TABLE `tb_main_task` DROP INDEX `task_category`;
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


## 操作 - 字段值基于原始值变化

```
UPDATE tb_growth_user SET growth_value = growth_value + 100 WHERE (is_del = 0) AND (user_id = '31100686');
```


## 权限 - 增加权限

账号在所有机器上登录都具有所有操作权限

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
```


## 权限 - 查看权限

查看账号在所有机器上登录都具有的操作权限

```
mysql> show grants for root@'%';
+-------------------------------------------------------------+
| Grants for root@%                                           |
+-------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION |
+-------------------------------------------------------------+
1 row in set (0.00 sec)
```



