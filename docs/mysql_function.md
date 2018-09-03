# 函数

## FROM_UNIXTIME 时间戳转换为日期

```
SELECT *, FROM_UNIXTIME(`create_time`) FROM `tb_user_sub_task_history` WHERE `task_id` = 195
```



