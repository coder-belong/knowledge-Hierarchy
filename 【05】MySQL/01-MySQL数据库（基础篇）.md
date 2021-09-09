#  一、数据库介绍



## 1.1 数据库概述

- 什么是**数据库**？

    - **数据库(DataBase)**  是按照一定的数据结构来组织、存储和管理数据的**仓库**。

      ​    

- 为什么需要**数据库**？

    - 任何的软件系统都需要存放大量的数据，这些数据通常是非常复杂和庞大的： 

        - 比如用户信息包括姓名、年龄、性别、地址、身份证号、出生日期等等
        - 比如商品信息包括商品的名称、描述、价格（原价）、分类标签、商品图片等等； 

    -  那么这些信息不能直接存储到文件中吗？可以，但是文件系统有很多的缺点： 

        -  很难以合适的方式组织数据（多张表之间的关系合理组织）

        - 无法对数据进行增删改查中的复杂操作

        - 等等... 

            

- 数据库通俗来讲就是一个**存储数据的仓库**，数据库本质上就是**一个软件**、一个**程序**。

    

    

## 1.2 常见的的数据库

- 通常我们将**数据库**划分成两类：**关系型数据库**和**非关系型数据库**

    

- **关系型数据库**：MySQL、Oracle、DB2、SQL Server等
  
    -  存储特点：结构化数据集，由**行和列**组合而成的**二维表**结构的数据。
    - 数据表之间相互关联起来，形成一对一、一对多、多对对等关系
    - 之后可以利用SQL语句在多张表中查询我们所需的数据
    -  支持事务，对数据的访问更加的安全



- **非关系型数据库**：MongoDB、Redis、Memcached、HBse等
    - 非关系型数据库的英文其实是Not only SQL，也简称为NoSQL
    - 存储特点：键值对形式的非结构化数据**集合**，并且查询的过程中不需要经过SQL解析，所以性能更高
    - 存储数据也会更加自由（可以直接将json对象塞入到数据库中）
    - NoSQL通常不支持事物



- 如何在开发中选择他们呢？
    -  目前在公司进行后端开发（Node、Java、Go等），还是以**关系型数据库**为主
    - 在**爬取**大量的数据进行存储时，用到**非关系型数据库**会比较常见





## 1.3 DB、DBMS、SQL三者之间的关系

- **数据库**（DB）是长期存储在计算机内、有组织的、统一管理的相关数据的集合。

- **数据库管理系统**（DBMS）是用于管理数据库的**软件**，它对数据库进行统一的管理和控制，以保证数据库的安全性和完整性。

- **SQL**是一种结构化**查询语言**，与**数据库通讯的语言**



<img src="images/05-MongoDB 数据库.assets/image-20201025153440728.png" alt="image-20201025153440728" style="zoom:50%;" />









## 1.4 数据库与后端语言的关系

- **后端语言可以操作数据库的数据**，对其数据进行**增删改查**的操作

    <img src="images/05-MongoDB 数据库.assets/image-20201025155315477.png" alt="image-20201025155315477" style="zoom:50%;" />





- 前端、后端、数据库 三者之间的**交互流程图**

    <img src="images/05-MongoDB 数据库.assets/image-20201025160003967.png" alt="image-20201025160003967" style="zoom:50%;" />



- 现在**遵循前后端分离原则**，前端需要向后端发送请求，**后端需要在数据库中拿数据响应给前端**，然后前端根据数据对页面进行渲染





# 二、邂逅MySQL

## 2.1 认识MySQL

- 什么是`MySQL`?
    - `MySQL` 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是**最好的关系数据库管理系统应用软件**之一。

- `MySQL` 支持多种语言。这些编程语言包括 C、C++、Python、Java、Node 和 PHP 等。



- MySQL中的**数据组织**方式
    - **MySQL服务**中包含了`多个数据库`
    - **每个数据库**中包含了`多个数据表`
    - **每个数据表**里有`多条数据`
    - 一般情况下，每一个项目里用到的**数据库**就只有**一个**

<img src="images/04-MySQL数据库.assets/image-20210720221505502.png" alt="image-20210720221505502" style="zoom:50%;" />





## 2.2 RDBMS 相关概念

- 关系型数据库管理系统 = **RDBMS**

- **数据库：**数据库是一些**关联表的集合**。
- **数据表：**数据库中的表看起来像一个简单的**电子表格**。
- **列：** 一列(数据元素) **包含了相同的数据**
- **行：**一行（或**记录**）是**一组相关的数据**
- **主键**：主键是唯一的。**一个数据表中只能包含一个主键**。你可以使用主键来查询数据。
- **外键：**外键用于关联两个表。
- 值(value): 行的具体信息, 每个值必须与该列的数据类型相同;
- **键(key)**: 键的值在当前列中具有**唯一性**。

<img src="images/04-MySql数据库.assets/image-20201010112002132.png" alt="image-20201010112002132" style="zoom:50%;" />









## 2.3 MySQL 安装与卸载

### 1. MySQL 安装

- MySQL安装参考教程：https://zhuanlan.zhihu.com/p/37152572

1. 进入MySQL官方网站（https://dev.mysql.com/downloads/installer/）

    <img src="images/04-MySql数据库.assets/image-20201010112930113.png" alt="image-20201010112930113" style="zoom:50%;" />

    <img src="images/04-MySql数据库.assets/image-20201010113120416.png" alt="image-20201010113120416" style="zoom:50%;" />

    <img src="images/04-MySql数据库.assets/image-20201010113348054.png" alt="image-20201010113348054" style="zoom:50%;" />



2. 第一步也可以替换为直接在`前端学习资料\软件安装包\MySql\数据库mysql`下安装5.7版本的MySQL

    <img src="images/04-MySql数据库.assets/image-20201010113446546.png" alt="image-20201010113446546" style="zoom:50%;" />



3. 双击打开MySQL的安装包，开始安装

4. 按下图勾选同意协议，然后下一步

    <img src="images/04-MySql数据库.assets/image-20201010113602233.png" alt="image-20201010113602233" style="zoom:50%;" />



5. 左边界面是安装到了哪一步，下图是选择安装类型，选Server only（只安装mysql），然后点击“next”。

    <img src="images/04-MySql数据库.assets/image-20201010113721428.png" alt="image-20201010113721428" style="zoom:50%;" />

6. 点击Execute开始安装，安装完成后点击next

    <img src="images/04-MySql数据库.assets/image-20201010113806213.png" alt="image-20201010113806213" style="zoom:50%;" />

7. 点击next

    <img src="images/04-MySql数据库.assets/image-20201010113903515.png" alt="image-20201010113903515" style="zoom:50%;" />

8. 默认选第一个，点击“next”继续

    <img src="images/04-MySql数据库.assets/image-20201010113928036.png" alt="image-20201010113928036" style="zoom:50%;" />



9. 默认，继续点击next

    <img src="images/04-MySql数据库.assets/image-20201010114001771.png" alt="image-20201010114001771" style="zoom:50%;" />



10. 设置密码，需要牢记，最好将登陆用户名（是root）和密码（下图的地方设置）记录到其他地方，因为后面要用这个密码连接数据库。**这里我将密码设置为了 123456**，然后点击next

    <img src="images/04-MySql数据库.assets/image-20201010121905251.png" alt="image-20201010121905251" style="zoom:50%;" />



11. 默认点击next继续，如果出现下图红框的警告，表示**要启动的服务名称重复**了，换个其他名称

    <img src="images/04-MySql数据库.assets/image-20201010121954850.png" alt="image-20201010121954850" style="zoom:50%;" />

12. 按下图红框的地方勾选，点击next继续

<img src="images/04-MySql数据库.assets/image-20201010122050679.png" alt="image-20201010122050679" style="zoom:50%;" />



13. 点击执行（Execute）安装

    <img src="images/04-MySql数据库.assets/image-20201010122130337.png" alt="image-20201010122130337" style="zoom:67%;" />



14. 当出现如下界面后，直接点击"Finish"。

    <img src="images/04-MySql数据库.assets/image-20201010122623996.png" alt="image-20201010122623996" style="zoom:50%;" />

    

15. 当出现如下界面后，直接点击"Next"

    <img src="images/04-MySql数据库.assets/image-20201010122704223.png" alt="image-20201010122704223" style="zoom:50%;" />

16. 当出现如下界面后，直接点击"Finish"。完成安装

    <img src="images/04-MySql数据库.assets/image-20201010122746442.png" alt="image-20201010122746442" style="zoom:50%;" />





- 检查MySQL**是否安装成功**

    <img src="images/04-MySql数据库.assets/image-20201010123150608.png" alt="image-20201010123150608" style="zoom:50%;" />

    <img src="images/04-MySql数据库.assets/image-20201010123335471.png" alt="image-20201010123335471" style="zoom:50%;" />

​	

- MySQL**安装目录详解**：

    - `C:\Program Files\MySQL\MySQL Server 5.7`：MySQL数据库这个软件的**安装路径**

        <img src="images/04-MySql数据库.assets/image-20201010124831950.png" alt="image-20201010124831950" style="zoom:50%;" />

        

    - `C:\ProgramData\MySQL\MySQL Server 5.7`：在数据库中创建库、创建表的**数据保存位置**。该文件夹默认是一个**隐藏项目**

        <img src="images/04-MySql数据库.assets/image-20201010125043723.png" alt="image-20201010125043723" style="zoom:50%;" />
    
        



### 2. MySQL 卸载

1. 打开控制面板，将`MySQL`相关的应用全部都卸载掉

2. 打开c盘，将mysql的数据全部清除

    - 删除MySQL文件夹：`C:\ProgramData\MySQL`(隐藏项目)

    - 删除MySQL文件夹：`C:\Program Files\MySQL`
    - 以上两个文件夹都要删除

3. 删除和`MySQL`相关的**系统环境变量**

    <img src="images/04-MySql数据库.assets/image-20201010131035903.png" alt="image-20201010131035903" style="zoom:50%;" />

    

4. windows+R运行“regedit”，打开注册表，删除注册表中MySQL相关目录（**ctrl+f 搜索mysql**）

5. 打开服务，看表中是否有**mysql服务**，没有则说明卸载干净了

6. 如果mysql服务还存在，那么执行以下cmd窗口命令，删除mysql服务

    - ```js
        sc delete mysql
        ```

        



## 2.4 MySQL的基本使用

### 2.4.1 MySQL配置环境变量

- 找到MySQL的**安装目录**：`C\Program Files\MySQL\MySQL Server 5.7`，在该文件夹下的**bin文件夹**中，存储了大量的可执行的**MySQL相关命令**
- 如果我们每次想要执行**MySQL相关命令**，就必须每次切换到其安装目录的bin文件夹下，这样必然麻烦，因此我们可以为其**配置环境变量**，这样就可以直接在CMD窗口中输入MySQL相关命令，并且正常执行



1. 在系统变量中添加**MYSQL_HOME变量**，并写入**MySQL安装目录下的bin文件夹路径**

    <img src="images/04-MySql数据库.assets/image-20201010130103482.png" alt="image-20201010130103482" style="zoom:50%;" />

2. 将**MYSQL_HOME变量**，添加到path系统变量中

    <img src="images/04-MySql数据库.assets/image-20201010130151850.png" alt="image-20201010130151850" style="zoom:50%;" />



3. 打开命令行窗口，执行`mysql -u root -p`命令，该命令用于**连接MySQL数据库**，并且输入MySQL密码

    <img src="images/04-MySql数据库.assets/image-20201010130501099.png" alt="image-20201010130501099" style="zoom:50%;" />

    



### 2.4.2 终端操作 - 连接数据库

- 所有**操作数据库的前提**都是建立在**连接数据库之上**
- 打开命令行窗口，执行`mysql -u root -p `命令

<img src="images/04-MySql数据库.assets/image-20201010130501099.png" alt="image-20201010130501099" style="zoom:50%;" />









### 2.4.3 终端操作 - 显示数据库

- 在与**数据库进行连接后**，执行`show databases;`命令

<img src="images/04-MySQL数据库.assets/image-20210720223652852.png" alt="image-20210720223652852" style="zoom:50%;" />



- MySQL默认存在的数据库（了解）： 
    - infomation_schema：信息数据库，其中包括MySQL在维护的其他数据库、表、 列、访问权限等信息
    - performance_schema：性能数据库，记录着MySQL Server数据库引擎在运行过程中的资源消耗相关的信息
    - mysql：用于存储数据库管理者的用户信息、权限信息以及一些日志信息等
    -  sys：相当于是一个简易版的performance_schema，将性能数据库中的数据汇总成更容易理解的形式



### 2.4.3 终端操作 - 创建数据库 / 表

- 在终端直接创建一个属于自己的新的数据库`coderlong`（一般情况下一个新的项目会对应一个新的数据库）

    - `create database coderlong;`

- 使用我们创建的数据库

    - `use coderlong;`

- 在数据库中，创建一张表

    <img src="images/04-MySQL数据库.assets/image-20210720224445596.png" alt="image-20210720224445596" style="zoom:50%;" />









# 三、 MySQL GUI工具



## 3.1 GUI工具的介绍

- 我们会发现在**终端操作数据库有很多不方便**的地方： 

    - 语句写出来没有高亮，并且不会有任何的提示

    - 复杂的语句分成多行，格式看起来并不美观，很容易出现错误

    - 终端中查看所有的数据库或者表非常的不直观和不方便

        

- 什么是**MySQL GUI**工具？

    - `MySQL`数据库用于存放数据，客户端`MySQL GUI`工具是为了`方便操作数据库`而设计的一种`图形化软件`。

    -  所以在开发中，我们可以使用GUI工具来帮助我们连接上数据库，之后直接在GUI工具中操作就会**非常方便**

        <img src="images/04-MySql数据库.assets/image-20201010132610427.png" alt="image-20201010132610427" style="zoom:50%;" />

        

- 常见**MySQL GUI**工具有很多，目前最好用的是**Navicat**，但是需要破解

>在**Navivat**中的**查询**中可以执行任何我们想要的**终端命令**
>

<img src="images/04-MySQL数据库.assets/image-20210726132744993.png" alt="image-20210726132744993" style="zoom:50%;" />









## 3.2 Navicat的安装

- `Navicat`官网地址：http://www.Navicat.com.cn/products，选择**可以操作MySQL**数据的版本进行下载

    ![image-20201115143656993](images/04-MySQL数据库.assets/image-20201115143656993.png)

    - 一键**傻瓜式进行安装**，一直`next`

    

- **破解**Navicat步骤：

    1. 安装完成后不要打开，先打开Keygen注册机

        <img src="images/04-MySQL数据库.assets/image-20201115162812117.png" alt="image-20201115162812117" style="zoom:50%;" />

    2. 点击Patch

        <img src="images/04-MySQL数据库.assets/image-20201115162849858.png" alt="image-20201115162849858" style="zoom:50%;" />

3. 点击确定。

    <img src="images/04-MySQL数据库.assets/image-20201115162930421.png" alt="image-20201115162930421" style="zoom:50%;" />

4. 点击Generate，自动生成序列号到软件窗口

    <img src="images/04-MySQL数据库.assets/image-20201115162954200.png" alt="image-20201115162954200" style="zoom:50%;" />



5. 打开**Navicat Premium 15**，点击帮助 --> 注册 ，将注册机获取到的序列号复制到激活码中

    <img src="images/04-MySQL数据库.assets/image-20201115163148471.png" alt="image-20201115163148471" style="zoom:50%;" />

6. 点击手动激活

    <img src="images/04-MySQL数据库.assets/image-20201115163213390.png" alt="image-20201115163213390" style="zoom:50%;" />



7. 复制软件窗口中的请求码

    <img src="images/04-MySQL数据库.assets/image-20201115163234667.png" alt="image-20201115163234667" style="zoom:50%;" />



8. 点击Paste粘贴，然后点击Generate自动生成激活码到软件窗口

    <img src="images/04-MySQL数据库.assets/image-20201115163303966.png" alt="image-20201115163303966" style="zoom:50%;" />



9. 点击激活

    <img src="images/04-MySQL数据库.assets/image-20201115163325448.png" alt="image-20201115163325448" style="zoom:50%;" />



- 坑：
    - 如果出现`rsa public key not find`报错信息，可以尝试断网或重装`Navicat15`，然后重复以上步骤
    - **安装完成后不要打开**，先点击Navicat Keygen进行patch，patch完后再打开软件进行激活操作！





## 3.3 Navicat的基本使用



#### 连接MySQL服务

- 使用客户端`Navicat`连接`MySQL`数据库

    

>连接**本地MySQL服务**
>

<img src="images/04-MySql数据库.assets/image-20201010132915075.png" alt="image-20201010132915075" style="zoom:50%;" />





![image-20210720230039192](images/04-MySQL数据库.assets/image-20210720230039192.png)





>连接**远程MySQL服务**
>

1. 在远程服务器上的navicat -> 的查询中**修改连接权限**

    - ```mysql
        # 使⽤mysql数据库
        use mysql;
        
        # 查看user表中，连接权限，默认看到root是localhost
        select host, user from user;
        
        # 修改权限
        update user set host = '%' where user = 'root';
        
        # 刷新MySQL的系统权限相关表
        flush privileges;
        ```

2. 在远程服务器配置 -> 防火墙中**开放3306端口**

<img src="images/01-MySQL数据库（基础篇）.assets/image-20210815105216233.png" alt="image-20210815105216233" style="zoom:50%;" />



3. 在本地服务器上**使用 navicat** 连接**远程服务器的MySQL**服务

    <img src="images/01-MySQL数据库（基础篇）.assets/image-20210815105404971.png" alt="image-20210815105404971" style="zoom:50%;" />





#### 查看数据库

- 使用客户端`Navicat`查看数据库
  
    - <img src="images/04-MySql数据库.assets/image-20201010133104017.png" alt="image-20201010133104017" style="zoom:50%;" />



<img src="images/04-MySQL数据库.assets/image-20201101174223067.png" alt="image-20201101174223067" style="zoom:50%;" />



- **查看数据表**
    - <img src="images/04-MySQL数据库.assets/image-20201101174701488.png" alt="image-20201101174701488" style="zoom:50%;" />











#### 创建数据库 / 数据表

1. 创建数据库：右击MySQL连接，新建数据库，**选择utf-8字符集**，**排序类型默认**

    <img src="images/04-MySQL数据库.assets/image-20210726134745109.png" alt="image-20210726134745109" style="zoom:50%;" />

    

    

2. 创建数据表：点击**数据库 --> 表 --> 新建表**

<img src="images/04-MySQL数据库.assets/image-20201101175051918.png" alt="image-20201101175051918" style="zoom:50%;" />





2. 点击保存后输入表名，就创建成功了一个表

    <img src="images/04-MySQL数据库.assets/image-20201101175137083.png" alt="image-20201101175137083" style="zoom:67%;" />



>创建数据表后记得**保存才会生效**，表名最好以**小写形式**
>





#### 导入数据表

- 使用客户端`Navicat`导入**SQL文件**

    - **SQL文件中可以有大量的SQL语句**，可以用于新建多个表

    <img src="images/04-MySql数据库.assets/image-20201010133835877.png" alt="image-20201010133835877" style="zoom:50%;" />





#### 导出单个数据表

- 选择要导出的**数据表然后右键**，点击转储**SQL文件**

    <img src="images/04-MySQL数据库.assets/image-20201102172454909.png" alt="image-20201102172454909" style="zoom:50%;" />





#### 导出多个数据表

- 可以将**数据库中的所有表导出到一个SQL文件上**

    ​	① 选择数据库 ② 右键转储SQL文件 ③ 选择结构和数据

    <img src="images/04-MySQL数据库.assets/image-20201115164035405.png" alt="image-20201115164035405" style="zoom:50%;" />



<img src="images/04-MySQL数据库.assets/image-20201115164118074.png" alt="image-20201115164118074" style="zoom:50%;" />





#### 修改表格列的宽度

- 右键表格列，显示--> 修改表格列宽

    <img src="images/04-MySQL数据库.assets/image-20201116112048966.png" alt="image-20201116112048966" style="zoom:50%;" />





## 3.4 Navicat偏好设置

- Navicat**常用快捷键**

<img src="images/04-MySQL数据库.assets/image-20210726132632556.png" alt="image-20210726132632556" style="zoom:50%;" />





- **SQL**语句美化

    <img src="images/04-MySQL数据库.assets/image-20210726132744993.png" alt="image-20210726132744993" style="zoom:50%;" />





- **自定义SQL语句颜色**：工具 -> 选项 -> 编辑器

    ![image-20210726134253181](images/04-MySQL数据库.assets/image-20210726134253181.png)

    







# 四、MySQL - 数据类型

## 4.1 数据类型介绍

- 我们知道**不同的数据会划分为不同的数据类型**，在数据库中也是一样： 
- MySQL支持的数据类型有：**数字类型**，**日期和时间类型**，**字符串类型**，**空间类型**和 **JSON数据类型**

<img src="images/04-MySQL数据库.assets/image-20210726143231110.png" alt="image-20210726143231110" style="zoom:50%;" />



>数据类型有很多种，我们只学习开发中**常用的数据类型**
>

>在实际开发中，最**主要用到**的只有**三种数据类型**：**int**   **timestamp**  **varchar**
>





## 4.2 MySQL - 数字类型

- **整数**数字类型：integer，**int**，smallint，tinyint，mediumint，bigint

    ![image-20210726143749659](images/04-MySQL数据库.assets/image-20210726143749659.png)

    

- **浮点**(小数)数字类型：**float**，double（float是4个字节，double是8个字节）

    

- **精确**数字类型：**decimal**，numeric



>开发中**常用的数字类型**就只有：**int float decimal** 这三种
>





## 4.3 MySQL - 日期类型

- **year**：以***yyyy***格式显示值

    - 范围 1901到2155，和 0000

        

- **date**：用于具有日期部分但没有时间部分的值

    - date以格式***yyyy-mm-dd***显示值 ；

    - 支持的范围是 '1000-01-01' 到 '9999-12-31'

        

- **datetime**：用于**包含日期和时间部分**的值：

    - datetime以格式'***yyyy-mm-dd hh:mm:ss***'显示值

    - 支持的范围是1000-01-01 00:00:00到9999-12-31 23:59:59

        

- **timestamp**：用于**包含日期和时间部分**的值：

    - timestamp以格式'***yyyy-mm-dd hh:mm:ss***'显示值；

    - 但是它的范围是utc的时间范围：'1970-01-01 00:00:01'到'2038-01-19 03:14:07'

        

- 另外：**datetime**或**timestamp** 值可以包括在微秒

    - 比如datetime表示的范围可以是'1000-01-01 00:00:00.000000'到'9999-12-31 23:59:59.999999';



>开发中最**常用的日期类型**：**datetime**和 **timestamp**
>





## 4.4 MySQL - 字符串类型

- **char类型**：在创建表时为固定长度，长度可以是0到255之间的任何值

    - 在被查询时，会删除后面的空格

        

-  **varchar类型**：的值是可变长度的字符串，长度可以指定为0到65535之间的值

    - 在被查询时，不会删除后面的空格

        

- **text类型：**用于存储大的字符串类型



>开发中最主要用到的还是 **varchar类型**
>









# 五、MySQL - 表约束

## 5.1 表约束的基本认识

- 什么是**表约束**？

    - **表约束**实际上就是**表中数据**的**限制条件**

        <img src="images/04-MySQL数据库.assets/image-20210726153746084.png" alt="image-20210726153746084" style="zoom:50%;" />

- **表约束**的**作用**
  
    - 表在设计的时候加入约束的目的就是为了**保证表中的记录完整**和**有效性**



- MySQL中的**表约束种类**
    - **非空**约束(not null)
    - **唯一性**约束(unique)
    - **主键**约束(primary key) 
    - **外键**约束(foreign key) 
    - **默认约束**和**递增约束**



## 5.2 主键约束

>数据表设计时**一定要有主键（primary key）**
>

- 一张表中为了区分每一条记录的唯一性，必须有一个字段是**永远不会重复**，并且**不会为空**的，这个字段我们通常会 将它设置为**主键**： 

    - 主键是表中**唯一的索引，不能重复**

    - 并且**必须是NOT NULL**的，如果没有设置 NOT NULL，那么MySQL也会隐式的设置为NOT NULL

        

- 主键**涉及术语**

    - 主键约束
    - 主键字段
    - 主键值

    以上三者关系：表中的某个字段添加主键约束后，该字段为主键字段，主键字段中出现的每一个数据都称为主键值



>建议：开发中主**键字段应该是和业务无关**的，尽量不要使用业务字段来作为主键







## 5.3 唯一性约束

>**unique**约束的字段，**具有唯一性**，**不可重复**，但可**以为null**
>

- 某些字段在开发中我们希望是**唯一**的，**不会重复**的，比如***邮箱***，这个字段我们可以使用`unique`来约束

    - ```mysql
        create table t_user(
        	id int(10),
        	name varchar(32) not null,
        	email varchar(128) unique
        );
        Query OK, 0 rows affected (0.03 sec)
        ```

        





## 5.4 非空约束

>用**not null**约束的字段不能为null值，**必须给定具体的数据**
>

- 创建表，给字段添加非空约束（创建用户表，用户名不能为空）

    - ```mysql
        create table t_user(
        	id int(10),
        	name varchar(32) not null
        );
        Query OK, 0 rows affected (0.08 sec)
        ```

        



## 5.5 创建一个完整的表

- 基于**表约束**创建一个**完整的数据表**

    - ```mysql
        create table if not exists `user`(
          # id字段：int类型 主键 不为空 自动递增
        	`id` int primary key not null auto_increment,
        	# name字段：varchar类型 长度为20 不为空
        	`name` varchar(20) not null,
        	# age字段：int类型  默认值为0
        	`age` int default 0,
        	# telphone字段： varchar类型 长度为20  具有唯一性  默认值为null
        	`telphone` varchar(20) unique default null,
        	`createTime` timestamp
        )
        ```

        

- 创建后的**表结构如下**

    <img src="images/04-MySQL数据库.assets/image-20210726161729231.png" alt="image-20210726161729231" style="zoom:50%;" />





































































































# 六、SQL语句

## 6.1 邂逅SQL语句

### 6.1.1 SQL语句的简介

- 我们希望操作数据库需要有**和数据库沟通的语言**，这个语言就是SQL： 

    -  SQL是Structured Query Language，称之为结构化**查询语言**，简称SQL

    - 使用SQL编写出来的语句，就称之为**SQL语句**

    -  **SQL语句**可以用于对数据库**进行操作**

        

-  事实上，常见的关系型数据库**SQL语句都是比较相似**的，所以你学会了MySQL中的SQL语句，之后去操作比如 Oracle或者其他关系型数据库，也是非常方便的。 

    

- SQL语句的**常用规范**： 

    - 通常**关键字需要以大写为规范**，***不过也可以小写***，比如CREATE、TABLE、SHOW等等
    - 一条语句结束后，需要**以 ; 结尾**
    -  **表名**和**字段**可以**使用``包裹**以用来区分关键字，当然这只是建议
    -  **注释**需要以`#`或`--`开头





- Navicat中**运行选中的SQL语句**

    <img src="images/04-MySQL数据库.assets/image-20210726135412628.png" alt="image-20210726135412628" style="zoom:50%;" />







### 6.1.2 SQL语句的分类

>**常见的SQL语句**我们可以分成**以下四类**：

- **DDL**（Data Definition Language）：数据定义语言

    - 可以通过DDL语句对**数据库**或者**数据表**进行：创建、删除、修改等操作

        

-  **DML**（Data Manipulation Language）：数据操作语言

    - 可以通过DML语句对**数据表**进行：添加、删除、修改等操作

        

- **DQL**（Data Query Language）：数据查询语言

    -  可以通过DQL从**数据库中查询**记录（重点）

        

-  **DCL**（Data Control Language）：数据控制语言

    -  对数据库、表格的权限进行相关访问控制操作



>**新建learn_sql数据表 --> 新建查询 **之后所有的sql语句演练，都会在该**查询**中

![image-20210726131112879](images/04-MySQL数据库.assets/image-20210726131112879.png)





## 6.2 DDL - 数据库 / 表操作

### 6.2.1 DDL - 数据库操作

>为了更方便查看**SQL语句的关键**字，接下来的SQL语句**统一采用小写规范**
>

```mysql
# 查询所有数据库
show databases;

# 选择某个数据库
use test;

# 查看当前正在使用的数据库
select database();

# 创建一个新的数据库 需要刷新后才显示
-- create database douyu; # 基本写法
create database if not exists douyu; # 严谨写法

# 删除数据库
drop database if exists douyu;

# 修改数据库 修改数据库的字符集和排序规则
alter database douyu character set = utf8 collate = utf8_unicode_ci
```



### 6.2.2 DDL - 数据表操作

#### 1. 表的**查询**与**创建**

- ```mysql
    # 查看所有数据表
    show tables;
    
    # 查看某一个表结构
    desc student
    
    # 新建数据表 坑：最后一个字段不能加逗号，否则报错
    create table if not exists `student` (
    	`username` varchar(10),
    	`age` int,
    	`score` int
    );
    ```

    

#### 2. 基于**表约束创建**一个**完整的表**

- ```mysql
    create table if not exists `user`(
      # id字段：int类型 主键 不为空 自动递增
    	`id` int primary key not null auto_increment,
    	# name字段：varchar类型 长度为20 不为空
    	`name` varchar(20) not null,
    	# age字段：int类型  默认值为0
    	`age` int default 0,
    	# telphone字段： varchar类型 长度为20  具有唯一性  默认值为空
    	`telphone` varchar(20) unique default null,
      # createTime：默认值为当前时间
    	`createTime` timestamp default current_timestamp
    )
    ```

    

#### 3. **删除**表

- ```mysql
    drop table student;
    drop table if exists `student`;
    ```

    

#### 4. **修改**表

- ```mysql
    -- 1. 修改表名
    alter table `user` rename to `users`;
    
    -- 2. 添加一个新的字段
    alter table `users` add `updateTime` datetime;
    alter table `users` add `publishTime` datetime;
    
    -- 3. 删除一个字段
    alter table `users` drop `updateTime`;
    
    -- 4. 修改字段的名称
    alter table `users` change `publishTime` `publishDate` date;
    
    -- 5. 修改字段的数据类型
    alter table `users` modify `publishDate` int;
    ```

    

#### 5. 表的**结构复制**

- ```mysql
    # 根据一个表结构去创建另外一张表
    create table `new_user` like `user`;
    ```

    



## 6.3 DML - 数据操作

>**DML**：Data Manipulation Language（**数据操作语言**），在MySQL中**一条数据也称为一条记录**
>



### 6.3.1 添加数据

- 方式一：`insert into 表名 values (值,值)`

    - ```mysql
        -- 1. 一次性插入所有数据
        insert into `user` values (110, 'long', 18, '1561891', '2021-07-26');
        ```

        

- 方式二：`insert into 表名 (字段,字段) values (值,值)`

    - ```mysql
        -- 2. 根据指定字段插入数据，主键id自动递增时可采用该方式
        insert into user (name, age, telphone, createTime)
        						values ('kobe', 88, '231561', '2021-07-26');
        ```

        <img src="images/04-MySQL数据库.assets/image-20210726173920188.png" alt="image-20210726173920188" style="zoom:50%;" />

        

>当主键为**自动递增**时，添加数据时可以缺少主键，因为他会**默认**将主键**自增1**添加**进去**
>



>注：即使**一条记录被删除**了，但是他原来的**主键依旧存在**，因此主键自增时是依据**上一条的主键**
>





### 6.3.2 删除数据

- **删除记录**的SQL语句：`delete from 表名 where 条件`

    - 删除user表中 name字段为‘kobe’的数据

    - ```mysql
        -- 1. 根据字段的值删除指定的数据
        delete from `user` where `name` = 'kobe';
        ```


>注：即使**一条记录被删除**了，但是他原来的**主键依旧存在**，因此主键自增时是依据**上一条的主键**
>



### 6.3.3 更新数据

- 修改**单个字段**的值：`update 表名 set 字段 = 值 where 条件`

    - ```mysql
        # 将 user 表中 id 字段为 116 的记录的 name 字段值修改为了 lul
        update `user` set `name` = 'lul' where `id` = 116
        ```

        

- 修改**多个字段**的值：`update 表名 set 字段 = 值, 字段 = 值 where 条件`

    - ```mysql
        # 将 id 为 116 的记录中的 name 字段改为了 lul， age 字段改为了 18, ,sex = male
        update `user` set `name` = 'lul', `age` = 18, `sex` = 'male' where `id` = 116
        ```

        



### 6.3.4 时间默认值与更新时间

- 设置 `datetime`类型的默认值，**默认值添加记录时的时间**

    - ```mysql
        alter table `user` modify `createTime` datetime default current_timestamp;
        ```

        

- **修改完数据后**，可以显示**最新的更新时间**：

    - ```mysql
        -- 当记录被修改时，updateTime字段会自动被修改为的修改时的时间
        alter table `user` modify `updateTime` datetime 
        										default current_timestamp on update current_timestamp
        ```

        



## 6.4 DQL - 数据查询

>**DQL**：Data Query Language（**数据查询语言**） 
>



- 在学习数据查询之前，我们需要先**准备好一个拥有完整数据的数据表**

  <img src="images/04-MySQL数据库.assets/image-20210727161238533.png" alt="image-20210727161238533" style="zoom:67%;" />
  
  - 然后将json文件进行导入
  
  
  
    

### 6.4.1 基本查询

- 查询表中**所有的字段**以及**所有的数据**：`select * from 表名`

    - ```mysql
        select * from `products`;
        ```

        <img src="images/04-MySQL数据库.assets/image-20210726212615736.png" alt="image-20210726212615736" style="zoom:50%;" />

        

- 查询**指定的字段**以及数据：`select 字段, 字段 from 表名`

    - ```mysql
        select `title`, `price`, `score` from `products`;
        ```

        <img src="images/04-MySQL数据库.assets/image-20210726212631489.png" alt="image-20210726212631489" style="zoom:67%;" />

        

- 对查询结果的字段**起别名**：`select 字段 as 别名, 字段 as 别名 from 表名`

    - ```mysql
        select title as phoneTile, price as phonePrice from `products`;
        ```

        <img src="images/04-MySQL数据库.assets/image-20210726212650105.png" alt="image-20210726212650105" style="zoom:67%;" />





### 6.4.2 条件查询

>在开发中，我们希望**根据条件来筛选我们的数据**，这个时候我们要使用**条件查询**

- **条件查询**的SQL语句：`select * from 表名 where 条件`

    

#### 1. where的**比较运算符**



<img src="images/04-MySQL数据库.assets/image-20210726220459837.png" alt="image-20210726220459837" style="zoom:50%;" />





#### 2. where的**逻辑运算符**

- 关键字：`and  &&`    、    `or  ||`   、  `between ... and .... `   、 `字段 in('值', '值')`

- `between ... and ...`：包含等于

-  `字段 in('值', '值')`：效果与 ***or*** 或 ***||*** 一致

    <img src="images/04-MySQL数据库.assets/image-20210726221715691.png" alt="image-20210726221715691" style="zoom: 50%;" />

    

#### 3. 模糊查询

- **模糊查询**：在**搜索场景**下用的比较多，使用`like`关键字，结合两个特殊的符号：
    - `%`表示**匹配任意个**的任意字符

    - `_`表示**匹配一个**的任意字符

    ```mysql
    -- 3.1 查询所有title字段中以v开头的数据
    select * from `products` where title like 'v%';
    
    -- 3.2 查询所有title字段中有M的数据
    select * from `products` where title like '%M%';
    
    -- 3.3 查询所有title字段中有M在第三个字符的数据
    select * from `products` where title like '__M%';
    ```

    





### 6.4.3 查询结果排序

- 当我们查询到结果的时候，我们希望**将结果按照某种方式进行排序**，这个时候使用的是`order by`关键字
-  `order by`有两个常用的值： 
    - `asc`：**升序**排列
    - `desc`：**降序**排列

- `order by`SQL语句：`select * from 表名 where 条件 order by 字段 asc/desc, 字段 asc/desc`

    - ```mysql
        -- 4.1 升序排序(低 -> 高) 根据 price 字段对查询结果进行 升序排列
        select * from `products` where `price` < 1000 order by price asc;
        
        -- 4.2 降序排序(高 -> 低) 根据 price 字段对查询结果进行 降序排列
        select * from `products` where `price` < 1000 order by price desc;
        ```

        



### 6.4.4 分页查询

- 当数据库中的数据非常多时，一次性查询到所有的结果进行显示是不太现实的：

    -  在真实开发中，我们都会要求用户传入***offset***、***limit***或者***page***等字段

    - 它们的目的是让我们可以在数据库中进行**分页查询**

        

- **分页查询**的SQL语句：`select * from 表名 limit 查询的数量 offset 第几个记录开始查询 `

    - ```mysql
        -- 写法一：limit 查询的数量 offset 第几个记录开始查询
        select * from `products` limit 30 offset 0;
        select * from `products` limit 30 offset 60;
        
        -- 写法二：limit 第几个记录开始查询, 查询的数量
        select * from `products` limit 40, 30;
        -- 表示从第二个记录开始查找（但不包括第二个记录），查询五条记录（3 ~7）
        select * from `products` limit 2, 5
        ```



>坑：分页查询的**参数必须是数字类型**，不能为字符串类型
>





### 6.4.5 聚合函数 和 Group By

#### 1. 聚合函数的使用

>聚合函数表示对**字段值**进行**操作**的函数。作用：为了**快速得到统计数据**

- 常见的聚合函数有：***sum() 、agv()、max()、min()、count***

- 聚合函数的**基本使用**

    <img src="images/04-MySQL数据库.assets/image-20210727122518155.png" alt="image-20210727122518155" style="zoom:50%;" />

    

- 聚合函数的**查询结果**

    <img src="images/04-MySQL数据库.assets/image-20210727122821071.png" alt="image-20210727122821071" style="zoom:50%;" />



- 在一个查询SQL语句中，可以存在**多个聚合函数**，***以逗号进行区分***

    - ```mysql
        select max(price), sum(price) as totalPrice from `products`;
        ```

        <img src="images/04-MySQL数据库.assets/image-20210727123453469.png" alt="image-20210727123453469" style="zoom:50%;" />







#### 2. Group by的使用

- 聚合函数默认将**所有的数据**分成了**一组**：

    - 如果希望将**所有数据划分多个组**：以`brand`字段作为区分，应该怎么来做呢？

    -  这个时候我们可以使用 `GROUP BY`

        

- `Group By`通常和**聚合函数**一起使用

    - 表示按照字段对数据进行分组，**此字段相同的数据会被放到一个组中**

    - 然后再进行聚合函数的计算

        

- ***group by*** 的SQL语法：`select 字段1, 聚合函数 from 表名 group by 字段1`

    - ```mysql
        -- 1. 以 barnd 字段作为分组，查询分组后的最大值和最小值
        select brand, max(price), min(price) from `products` group by brand
        ```

        <img src="images/04-MySQL数据库.assets/image-20210727125357384.png" alt="image-20210727125357384" style="zoom: 67%;" />



- 对**分组 —> 统计后的数据**进行筛选，需要用到关键字`having`

    - `having`后面的条件运算符与`where`的相同

    - ```mysql
        -- 对group by后的数据进行筛选
        select brand, 
        		max(price) as maxPrice, 
        		min(price) as minPrice 
        from `products` group by brand 
        having maxPrice < 4000 && minPrice >600
        ```

        ![image-20210727130723737](images/04-MySQL数据库.assets/image-20210727130723737.png)



- #####  对比where与having

    - `where`是对from后面**指定的表进行数据筛选**，属于对原始数据的筛选
    - `having`是对**group by的结果进行筛选**

    - ```mysql
        -- 查询评论分(score)大于7.5的手机，按照品牌(brand)进行分组
        -- 求出平均价钱(price)   筛选出平均价钱大于3000的数据
        select brand, 
        		avg(price) as avgPrice 
        from `products` where score > 7.5 
        group by brand
        having avgPrice > 3000
        ```

        







# 七、MySQL - 多表查询

## 7.1 多表设计

- 通常**不同数据表的数据之间是有关系**的

    - 比如商品表中，其品牌数据还需要包含其他的信息：比如品牌的官网，品牌的世界排名等等；

    - 如果直接在商品表中去添加品牌相关的信息，会存在一些问题：

        1. ***products***表中应该表示的都是商品相关的数据，应该新建另一张表来表示 ***brand***的数据

        2. 多个商品使用的品牌是一致时，会存在大量的冗余数据；

            

- 所以，我们可以将所有的品牌数据，单独放到一张表中，创建一张品牌的表：

    <img src="images/04-MySQL数据库.assets/image-20210727151404318.png" alt="image-20210727151404318" style="zoom:50%;" />







## 7.2 多表关联(外键约束)

- 如果要把**两张表关联**起来，就需要将**一张表的特定字段(外键)**与**另一张表的主键字段**做关联

    - 注：**外键**一般都是跟**主键**进行关联

    ![image-20210727150715685](images/04-MySQL数据库.assets/image-20210727150715685.png)

    

- **外键约束**SQL语句：`foreign key (特定字段) references 要关联的数据表名 (主键)`

-  在创建表**添加外键约束**，需要在创建表的()最后添加如下语句：

    - ```mysql
        create table if not exists `products`(
        	.....
          brand_id int,
          # 将当前表的 brand_id 字段与 brand 表的 id 字段进行关联
        	foreign key (brand_id) references brand(id)
        );
        ```

        

- 如果是表已经创建好，则需要通过**修改字段类型来添加外键**：

    - ```mysql
        -- 添加一个brand_id字段
        alter table `products` add `brand_id` int;
        
        -- 将brand_id字段修改为外键(用于连接其他数据表的字段)
        alter table `products` add foreign key (brand_id) references brand(id)
        ```

        

- 在添加外键约束后，可在**设计表**中**查看外键**

    ![image-20210727153947378](images/04-MySQL数据库.assets/image-20210727153947378.png)



>当然，在GUI工具里也能直接添加外键，不过为了学习，还是**优先使用SQL语句实现**
>



- 创建好外键后需要设置**外键的值**与**被引用的表的主键**的值**一致**

    <img src="images/04-MySQL数据库.assets/image-20210727155013111.png" alt="image-20210727155013111" style="zoom: 67%;" />







## 7.3 外键存在时更新和删除数据

- 当外键存在时，其外键**引用表的主键**是**无法被修改**和**删除**的，否则会报错

    <img src="images/04-MySQL数据库.assets/image-20210727163220267.png" alt="image-20210727163220267" style="zoom:50%;" />



- 这是因为外键有**更新时**和**删除时**的 **action** 默认是 ***RESTRICT***
    - **RESTRICT**（默认属性）: 当更新或删除**主键**时，会检查该主键是否有关联的外键记录，有的话会报错的， 不允许更新或删除；
    - **NO ACTION**：和RESTRICT一致
    - **CASCADE**：当更新或删除主键时，会检查该主键是否有关联的外键记录，有的话
        -  更新：那么会更新对应的外键记录
        -  删除：那么关联的**外键及其记录**会被一起删除掉
    - **SET NULL**：当更新或删除主键时，会检查该主键是否有关联的外键记录，有的话，**将对应的值设置为 NULL**

<img src="images/04-MySQL数据库.assets/image-20210727164215898.png" alt="image-20210727164215898" style="zoom:50%;" />





- 使用SQL语句来**修改外键**的 ***action***

    - ```mysql
        -- 3.1 获取外键名称
        show create table `products`;
        
        -- 3.2 根据外键名称删除
        alter table `products` drop foreign key products_ibfk_1;
        
        -- 3.3 添加新的外键并添加新的action
        alter table `products` add foreign key (brand_id) references brand (id)
        																									on update cascade 
        																									on delete restrict;
        ```

        

>注：外键的**引用表**无法被删除，如果希望删除，那么需要**先删除外键**
>







## 7.4 多表查询 - 默认查询结果

- 在查询多张表时，其查询结果为 **笛卡尔乘积**
    - 也就是说第一张表中每一个条数据，都会和第二张表中的每一条数据结合一次
    - 第一张表的108条 * 第二张表的6条数据
    -  这个结果称为 笛卡尔乘积

<img src="images/04-MySQL数据库.assets/image-20210727180749750.png" alt="image-20210727180749750" style="zoom:50%;" />



- 如何对多表查询的默认结果**进行筛选**？

    - 使用 where 关键字：`where 表名.外键 = 表名.主键`

    - ```mysql
        select * from `products`, `brand` where `products`.brand_id = `brand`.id;
        ```

        <img src="images/04-MySQL数据库.assets/image-20210728102448874.png" alt="image-20210728102448874" style="zoom: 67%;" />





## 7.5 多表查询 - SQL_JOIN

### 7.5.1 SQL_JOIN介绍

>当需要对**有关系**的**多张表进行查询**时，需要使用连接 **join** 关键字
>

- **多表查询分类**如下：

    - 表A **inner join** 表B：只显示表A和表B关联的数据
    - 表A **left join** 表B：以表A为主。显示表A的全部数据，表B只会展示与表A关联的数据，如果表B没有对应的数据，则为NULL
    - 表A **right join** 表B：以表B为主。显示表B的全部数据，表A只会展示与表B关联的数据，如果表A没有对应的数据，则为NULL

    

<img src="images/04-MySQL数据库.assets/image-20210727202430714.png" alt="image-20210727202430714" style="zoom: 67%;" />







### 7.5.2 左连接(最常用)

- **左连接**全称是**左外连接**，是**外连接**中的一种，也是**开发中使用最多的情况**

    - **以左表为主**。显示**左表**的全部数据，右表只会展示与左表关联的数据，如果**右表**没有对应的数据，则为NULL

    - **左连接**又分为下图**两种情况**

    <img src="images/04-MySQL数据库.assets/image-20210728104741526.png" alt="image-20210728104741526" style="zoom:50%;" />

    

- 情况一：(常见)

    - 左表（A)的记录将会全部表示出来，而右表（B)只会显示**符合搜索条件的记录**（比如：**A.aID = B.bID**).

    - ```mysql
        -- 表A left join 表B on 表A.外键 = 表B.主键
        select * from A left join B on A.aID = B.bID
        ```

        <img src="images/04-MySQL数据库.assets/image-20210728105256529.png" alt="image-20210728105256529" style="zoom:50%;" />

    

- 情况二(少见)：**以左表为主**，展示左表**与右表没有关联的数据**

    - ```mysql
        -- 表A left join 表B on 表A.外键 = 表B.主键 where 表B.主键 is null
        select * from A left join B on A.aID = B.bID where B.bid is null
        ```

        <img src="images/04-MySQL数据库.assets/image-20210728110324544.png" alt="image-20210728110324544" style="zoom:50%;" />





### 7.5.3 右连接

- 右连接**在开发中并没有左连接常用**
    - **以右表为主**。显示**右表**的全部数据，左表只会展示与右表关联的数据，如果**左表**没有对应的数据，则为NULL

<img src="images/04-MySQL数据库.assets/image-20210728110620806.png" alt="image-20210728110620806" style="zoom:50%;" />



- 情况一：

    - ```mysql
        -- 表A right join 表B on 表A.外键 = 表B.主键
        select * from A right join B on A.aID = B.bID
        ```

        <img src="images/04-MySQL数据库.assets/image-20210728111224273.png" alt="image-20210728111224273" style="zoom:50%;" />



- 情况二：**以右表为主**，展示右表**与左表没有关联的数据**

    - ```mysql
        -- 表A right join 表B on 表A.外键 = 表B.主键 where 表A.外键 is null
        select * from A right join B on A.aID = B.bID where A.aid is null
        ```

        <img src="images/04-MySQL数据库.assets/image-20210728111652988.png" alt="image-20210728111652988" style="zoom:50%;" />





### 7.5.4 内连接

- 内连接**只显示左表和右表关联的数据**，即**只显示**符合`左表.外键 = 右表.主键`的数据

    <img src="images/04-MySQL数据库.assets/image-20210728111949736.png" alt="image-20210728111949736" style="zoom:50%;" />

- **inner join**

    - ```mysql
        select * from A inner join B on A.aID = B.bID
        ```

        <img src="images/04-MySQL数据库.assets/image-20210728112428042.png" alt="image-20210728112428042" style="zoom:50%;" />

        - 从上图中我们可以看到 这里只显示出了 **符合A.aID = B.bID的记录**





### 7.5.5 全连接

- 全连接的**使用场景比较少见**，这里只对它做个**简单演练**

- 全连接 = 左连接 + 右连接

    <img src="images/04-MySQL数据库.assets/image-20210728112651276.png" alt="image-20210728112651276" style="zoom:50%;" />



- SQL规范中全连接是使用**FULL JOIN**，但是MySQL中并没有对它支持，需要使用 **UNION** 来实现：

    ![image-20210728113129950](images/04-MySQL数据库.assets/image-20210728113129950.png)

    





## 7.6 多表查询结果的转换

>在**一对多**的关系表中，我们往往希望将**外键**查询到的数据转换为**对象形式**，以`层级嵌套`进行存储
>

- 这里以`products`表和`brand`表举例

<img src="images/01-MySQL数据库.assets/image-20210729190935544.png" alt="image-20210729190935544" style="zoom:50%;" />

- 当多表查询时，我们会发现，查询到的`brand`表数据和`products`表数据**处于同一层级下**

    <img src="images/01-MySQL数据库.assets/image-20210729191526764.png" alt="image-20210729191526764" style="zoom:50%;" />

- 如何将外键查询到的数据**存放到一个对象**中？这时候可以使用`json_object("key", value...)`

<img src="images/01-MySQL数据库.assets/image-20210729191857110.png" alt="image-20210729191857110" style="zoom:50%;" />





>在**多对多**关系中，我们希望查询到的是一个数组

- 比如一个老师选择的多个班级信息，应该是放到一个数组中的
-  数组中存放的是**课程信息**的一个个对象
- 这个时候我们要 `json_arrayagg`和`json_object`和`group by`结合来使用

- 数据表设计：

    ![image-20210729175845948](images/01-MySQL数据库.assets/image-20210729175845948.png)

- 希望转换的数据格式

    <img src="images/01-MySQL数据库.assets/image-20210729193150500.png" alt="image-20210729193150500" style="zoom:50%;" />

-  通过`json_arrayagg`和`json_object`和`group by`实现数据结构转换

    <img src="images/01-MySQL数据库.assets/image-20210729193338436.png" alt="image-20210729193338436" style="zoom:50%;" />





>坑：对结果查询转换时，**json_object(key, vaules)**中的**key**需要使用**双引号或者单引号包裹**
>





















# 八、MySQL - 表和表的关系

- 在设计数据表的时候，**表和表之间的关系**有三种：**一对一**、一**对多**、**多对多**
- **表与表之间的多种关系**，都是**通过外键实现**的



## 8.1 一对一的关系

- **一对一**的关系指**一个表的记录**对应到**另一个表的唯一一个记录**

    - 也就是说在两张表中，左表的一条记录唯一对应右表的一条记录，反之也一样

    - 核心：**外键必须是唯一**的

        

>**一对一**关系的表**设计方法**如下：
>

- 设计2张表：`contacts`和`student`
    - `student`表中通过字段`contacts_id`与`contacts`表产生关系(**通过外键**)
    - `student`表中的`contacts_id`与`contacts`表中的`id`值（主键）应当是一对一的关系
    - **所以在student表中要保证`contacts_id`值是唯一的**

- 两张表的表结构如下

    <img src="images/01-MySQL数据库.assets/image-20210728191257871.png" alt="image-20210728191257871" style="zoom:50%;" />



<img src="images/01-MySQL数据库.assets/image-20210728191656506.png" alt="image-20210728191656506" style="zoom:50%;" />







## 8.2 一对多的关系

- **一对多**：一个表的**一个记录**可以对应另一个表的**多个记录**，这样的关系称为一对多

    - 在一对多的关系里，**外键是不唯一**的

    - 可以理解为**右表的记录为1**，**左表的记录为多**

        

>**一对多**关系的表**设计方法**如下：
>

- 设计2张表：`class`和`student`
    - 业务逻辑：**一个班级可以有多个学生**
    - `student`表中通过字段`class_id`与`class`表产生关系(**通过外键**)
    - `class`表中的`id`值与`student`表中的`class_id`是**一对多**的关系
    - **所以在student表中要保证`class_id`值是不唯一的**



- 两张表的表结构如下

    <img src="images/01-MySQL数据库.assets/image-20210728194436249.png" alt="image-20210728194436249" style="zoom:50%;" />

    

<img src="images/01-MySQL数据库.assets/image-20210728194345655.png" alt="image-20210728194345655" style="zoom:50%;" />





## 8.3 多对多的关系

- 通过一个表的外键关联到另一个表，我们可以定义出一对多关系。有些时候，还需要定义**“多对多”**关系。
  
- 例如，一个老师可以对应多个班级，一个班级也可以对应多个老师，因此，班级表和老师表存在多对多关系。
  
- **多对多**关系实际上是通过**两个一对多关系**实现的，即通过一个**中间表**，关联两个一对多关系的表，就形成了多对多关系

    

>**多对多关系**的表设计方法如下：
>

- `teachers`表和`classes`表：

![image-20210728203157545](images/01-MySQL数据库.assets/image-20210728203157545.png)



- **中间表**`teacher_class`关联**两个一对多**关系：

    <img src="images/01-MySQL数据库.assets/image-20210728205000205.png" alt="image-20210728205000205" style="zoom:50%;" />

    

    <img src="images/01-MySQL数据库.assets/image-20210728203411343.png" alt="image-20210728203411343" style="zoom:50%;" />



- 通过中间表`teacher_class`可知`teachers`到`classes`的关系：
    - `id=1`的张老师对应`id=1,2`的一班和二班；
    - `id=2`的王老师对应`id=1,2`的一班和二班；
    - `id=3`的李老师对应`id=1`的一班；
    - `id=4`的赵老师对应`id=2`的二班。

- 同理可知`classes`到`teachers`的关系：
    - `id=1`的一班对应`id=1,2,3`的张老师、王老师和李老师；
    - `id=2`的二班对应`id=1,2,4`的张老师、王老师和赵老师；

- 因此，**通过中间表**，我们就定义了一个**“多对多”**关系。







## 8.4 多对多关系表的查询

- 创建三张多对多的关系表，并**设置中间表的外键**

    - 理清逻辑：一个老师可以选择多个班级，一个班级可以选择多个老师，通过中间表实现关联
    - 多对多的查询方式：先**第一个外键进行连接查询**，再通过**第二个外键进行连接查询**

    ![image-20210729175845948](images/01-MySQL数据库.assets/image-20210729175845948.png)



1. 查询已选择班级的老师，选择了哪些班级

    <img src="images/01-MySQL数据库.assets/image-20210729180842032.png" alt="image-20210729180842032" style="zoom: 67%;" />



2. 查询所有的老师的选班级情况

    <img src="images/01-MySQL数据库.assets/image-20210729180947471.png" alt="image-20210729180947471" style="zoom:50%;" />

 

3. 查询哪些老师是没有选班级的

<img src="images/01-MySQL数据库.assets/image-20210729181051622.png" alt="image-20210729181051622" style="zoom:50%;" />



4. 查询哪些班级是没有被老师选择的

<img src="images/01-MySQL数据库.assets/image-20210729181419388.png" alt="image-20210729181419388" style="zoom:50%;" />



5. 查询某一个老师选择了哪些课程

<img src="images/01-MySQL数据库.assets/image-20210729181548400.png" alt="image-20210729181548400" style="zoom:50%;" />

























































































