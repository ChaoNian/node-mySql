# node-mySql

Vscode 插件 Database Client

## 命令
操作数据表的命令
```mysql
 create tble `user` (
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) COMMENT ‘名字’, // name属性的值长度是100
    age INT COMMENT 年龄,
    address VARCHAR(200)  COMMENT 地址,
    create_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP  COMMENT ‘创建时间’ // 创建这条数据是自动填充时间
    ）COMMENT ‘用户表’
```
在user 表里 设置id属性
id name age address create_time
字段名称  字段类型  字段属性
NOT NULL 代表   这个字段不能为空
AUTO_INCREMENT 代表这个字段自增
PRIMARY KEY 把这个字段设置为主键
TIMESTAMP 代表时间戳
DEFAULT CURRENT_TIMESTAMP 填充默认值为创建时间
COMMENT 添加注释， 数据库一般都要注释

操作数据库的命令
show database 查看数据库
CREATE DATABASE  `xxx` 创建数据库
DEFAULT CHARACTER SET= 
default charcter set = 'utf8mb4'  创建数据的时候设置的字符集


# 换表的名字
ALTE TABLE ‘user’ RENAME ‘user2’ 
执行
ALTER 改变 RENME 重命名


**增加一列**
新增 hobby 一列
ADD COLUMN ‘hobby’ VARCHAR（200）
ADD COLUMN ‘’

**删除列**
DROP 

**编辑列**
MODIFY


# 查询

查询一列 SELECT 【列名id】 FROM ‘user’ 【表名】
查询多列 逗号分隔 SELECT 【列名id, name】 FROM ‘user’ 【表名】
查询所有列 通配符 *  SELECT * FROM ‘user’ 【表名】
列的别名 as 语法：  SELECT id  as user_id FROM ‘user

排序： ORDER BY [列名id] 【DESC降序 ASC升序】  写法：SELECT * FROM ‘user' ORDER BY id DESC


限制查询结果 LIMIT 开始行0，数量3 从0 开始的查3条， SELECT * FROM ‘user' LIMIT 0,3

条件查询 WHERE  SELECT * FROM ‘user' WHERE 【列名】 = 【值】


联合查询  AND  OR   SELECT * FROM ‘user' WHERE 【列名】 = 【值】AND 【列名】 <= 【值】

模糊查询 SELECT * FROM ‘user’ WHERE name [模糊匹配LIKE] '%xxx'  % 是值以xxx 结尾 的字符，匹配0个或者多个字符，  '%xxx%'只要有xxx 字符的值都要查出来 ；_ 代表模糊一个字符， __ 两个杠 代表查询两个字符


# 增删改
INSERT INTO user('name', 'age', 'hobby') VALUES('scs', 20, 'sds')

新增 INSERT INTO 表名（列名，...）VALUES (值, ...)
新增多个 逗号隔开即可
如果表结构支持null 也是可以插入null的

更新
UPDATE 【表名‘user’】 SET [列 key]=【值 value】

删除 DELETE FROM [表名‘user’] 【删除条件 WHERE id = 17】
删除多条 删除 DELETE FROM [表名‘user’] 【删除条件 WHERE id IN （18，19，20）】


# 表达式 和 函数 
MIN（）
MAX（）
SUM（）
COUNT（）
AVG（）
RIGHT（）


# 两个表关联
子查询 + 连表

子查询
注意 一定要有括号
SELECT * FROM ‘table’ WHERE user_id = (SELECT id FROM 'user' WHERE name = 'sss') 
// SELECT id FROM 'user' WHERE name = 'sss'


连表查询
目的把table表的数据和user表的数据合并在一起

内连接
通过id 来关联
SELECT * FROM ‘user’，‘table’ WHERE 'user'.'id' = 'table'.'user_id'

外连接（左连接 右连接）