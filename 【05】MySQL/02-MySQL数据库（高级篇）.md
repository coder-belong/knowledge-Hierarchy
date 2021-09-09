# 一、事务

## 1.1 事务的简介

- 什么是**事务**？
    - 当一个业务逻辑需要多个SQL语句完成时，如果其中某条SQL语句出错，则希望整个操作都退回
    - 这些SQL操作作为一个整体一起向系统提交，**要么都执行**、**要么都不执行**
    - 事务是**一组不可再分割**的**操作集合**



## 1.2 事务的**四大特性**

>事务必须满足以下四大特性
>

1. 原子性：事务中包含的全部操作**要么全部完成**，**要么都不执行**
2. 一致性：
    - 当数据库只包含成功事务提交的结果时，就说数据库处于**一致性**状态
    - 如果数据库系统运行中有些事务尚未完成就被迫中断，这些未完成事务会有一部分已写入物理数据库，这时数据库就处于一种**不一致的状态**。
3. 隔离性：事务的执行**不受其它事务干扰**。即一个事务内部的操作对其它并发事务是隔离的
4. 持续性：也称永久性，指一个事务一旦提交，它对数据库中的数据的**改变就应该是永久性**的





## 1.3 事务的使用

>要求：**表的类型**必须是**innodb**或**bdb**类型，才可以对数据表使用事务
>

- 创建表：

    - ```mysql
        # 建一个支持事务的数据表
        create table if not exists `affair`(
        	`id` int primary key auto_increment,
        	`name` varchar(10) not null,
        	`age` int not null
        );
        
        -- 修改表类型
        alter table `affair` engine = innodb;
        ```

        

>***在 MySQL 默认设置下，每条SQL语句都是自动提交的，即执行 SQL语句后就会马上执行 COMMIT 操作***

- **当执行commit后，数据库就会被相对应的SQL语句进行修改**

- 因此要开启一个事务前必须执行命令`set autocommit = 0;`，用来***禁止SQL语句的自动提交***

- 使用**事务语句**

    - ```mysql
        -- 以下SQL语句如果有一条执行失败，则全部SQL语句都不执行
        -- 注：开启事务前必须取消MySQL的自动提交
        set autocommit = 0;
        begin;  # 开启事务
            insert into `affair`(id, name, age) values(4, '张三', 18);
            insert into `affair`(id, name, age) values(3, '张三', 18);
            insert into `affair`(id, name, age) values(3, '张三', 18);
            insert into `affair`(id, name, age) values(5, '张三', 18);
        commit; # 只有全部SQL都成功了才进行提交去修改数据库
        
        begin;
        	SQL语句
        rollback; # 使事务中的SQL语句无效
        ```

    

>注：在**不使用事务时**，如果希望SQL语句能够立马更改数据库，则需要执行命令`set autocommit = 1;`

```mysql
-- 在不使用事务时，需要开启自动提交,MySQL默认配置是自动提交的
set autocommit = 1;
insert into `affair`(id, name, age) values(13, '张三', 18);
insert into `affair`(id, name, age) values(14, '张三', 18);
insert into `affair`(id, name, age) values(15, '张三', 18);
```



































































































































































































































































