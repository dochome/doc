MySQL 使用基础
==============

> 参见 [http://www.runoob.com/mysql/mysql-tutorial.html](http://www.runoob.com/mysql/mysql-tutorial.html)

1 使用注意事项
--------------

### 1.1 字符集推荐使用 `utf8mb4` 而不是 `utf8`。

### 1.2 数据类型

* 数值类型表

类型|大小（字节）|范围（有符号）|范围（无符号）|用途
----|----|--------------|--------------|----
TINYINT|1|(-128，127)|(0，255)|超小整数
SMALLINT|2|(-32768，32767)|(0，65535)|小整数
MEDIUMINT|3|(-8388608，8388607)|(0，16777215)|较大整数
INT|4|(-2147483648，2147483647)|(0，4294967295)|大整数
BIGINT|8|(-9233372036854775808，9223372036854775807)|(0，18446744073709551615)|超大整数
FLOAT|4|||单精度浮点数
DOUBLE|8|||双精度浮点数
DECIMAL||依赖于M和D的值|依赖于M和D的值|小数

### 1.3 创建用户

```sql
create user '$user'@'localhost' identified by '$password';
grant all on *.* to '$user'@'localhost';
flush privileges;
```

### 1.4 创建/删除数据库和表

* 创建/删除数据库

```sql
-- 如果数据库不存在则创建数据库
create database if not exists `$database_name`;

-- 如果数据库存在则删除数据库
drop database if exists `$database_name`;
```

* 创建/删除表

在选择 engine 时通常使用 `InnoDB`，但是有时也会选用 `MyISAM`。

```sql
-- 如果表不存在则创建表
create table if not exists `$table_name` (
	`id` bigint auto_increment comment '自动增长ID',
	`name` varchar(32) not null comment '名字',
	`age` smallint null comment '年龄',
	`created_at` datetime not null default CURRENT_TIMESTAMP comment '创建时间',
	index(`name`),
	primary key(`id`) -- 主键
) engine=InnoDB default charset=utf8mb4;

-- 如果表存在则删除表
drop table if exists `$table_name`;
```
