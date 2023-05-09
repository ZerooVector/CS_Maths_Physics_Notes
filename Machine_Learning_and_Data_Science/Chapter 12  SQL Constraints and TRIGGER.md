#MLorDS 
- 完整性：防止数据库中出现不正确的数据
- 安全性：防止恶意破坏和非法存取

## 数据库的完整性概述
- 完整性的约束条件
- 列级约束：约束数据类型、格式、域和空值
- 元组约束
- 关系约束：实体完整性、参照完整性、函数依赖、统计约束

- 静态
- 动态

## 实体完整性
- 主键的值不能为空
- 主键的值唯一
这通过手动指定其中一列为 `PRIMARY KEY` 来完成
- 对于单属性主键，允许声明为列级约束或者表级约束
- 对于多属性主键，必须是表级约束

```SQL
CREATE TABLE STUDENT 
(
Sno CHAR(9) PRIMARY KEY
)
```
或者
```SQL
CREATE TABLE STUDENT 
(
Sno CHAR(9) 
PRIMARY KEY (Sno)
)
```

在多属性主键：
```SQL 
CREATE TABLE SC 
(
SNO CHAR(9) NOT NULL
Cno CHAR(4) NOT NULL 
PRIMARY KEY (Sno,Cno)
)
```
当插入或者对主键进行更新操作时，DBMS 将检查实体完整性

## 参照完整性
- 外键的值要么为空，要么只能取参照对象的值
通过使用 `FOREIGN KEY` 和 `REFERENCES` 进行指定
```Sql
FOREIGN KEY (Sno) REFERENCES Student(Sno)
```
在插入数据时，参照完整性不受影响
在主键被修改时：三种策略：（1）改变外键（2）禁止修改（3）外键置空
在被参照表被删除时：三种策略：（1）不许删除（2）级联删除（3）外键置空
对参照表中的外键插入和修改时，都会影响参照完整性，此时如果有违约，则拒绝执行

一般来说，系统会自动将处理策略设置为“拒绝执行”(`NO ACTION`)，否则需要指明：
```SQL
FOREIGN KEY (Cno) REFERENCES Course (Cno)
ON DELETE CASCADE
ON UPDATE NO ACTION
```

## 用户定义完整性
属性上，你可以使用 `UNIQUE`，`NOTNULL`，`CHECK`, `DEFAULT`
元组上，使用 `CHECK` 指明你想要检查的条件
```Sql
c2 CHAR(4) CHECK (C2 IN ('0001','0002'))
```

## 完整性约束命名子句
使用 `CONSTRAINT<条件名><条件>` 来给完整性约束条件命名
```Sql
CONSTRAINT C4 CHECK (Ssex IN ('M','F'))
CONSTRAINT C3 CHECK (Sage < 30)
```
那么，可以使用 `DROP` 来删除约束，使用 `ADD` 添加新约束
```sql
ALTER TABLE Student
DROP CONSTRAINT C1
ADD CONSTRAINT C2
```

## 触发器
触发器是一种由事件驱动的特殊过程，用于实现复杂的业务规则，比约束更加灵活
触发器在 `UPDATE`，`INSERT`，或者 `DELETE` 事件发生时自动启动

使用下面的语句定义一个触发器：
```Sql
CREATE TRIGGER <触发器名>
[BEFORE|AFTER] <触发事件> ON <表格>
FOR EACH [ROW|STATEMENT]
[WHEN <触发条件>]
<触发动作体>
```

- `<表格>` 指定触发器作用的目标
- 事件可选： `INSERT,UPDATE,DELETE`，可以使用 `UPDATE ON Col`
- `BEFORE` 和 `AFTER` 选择触发事件，是决定在触发条件之前还是之后执行触发动作体中的操作
- `FOR EACH ROW` 对每一个修改的元组进行触发器的检查或执行（如果你修改了整张表，那么你修改的每一行将导致触发器启动一次）
- `FOR EACH STATEMENT` 对一个 SQL 语句仅启动一次触发器
- 触发条件：为真时触发动作体才执行
- 如果触发动作体执行失败，**激活触发器的事件将停止执行** 

例子：
```sql
CREATE TRIGGER In_or_Up_Sal
BEFORE INSERT OR UPDATE ON Teacher 
(
FOR EACH ROW 
BEGIN 
	IF (:new.Job = '0001') AND (:new.Sal<4000) THEN
	:new.Sal := 4000
	END IF;
END
)
```

例子：
```sql
CREATE TRIGGER INSERT_Sal
AFTER INSERT ON Teacher 
FOR  EACH ROW 
BEGIN 
	if(:new.sal <> : old.sal)
	THEN INSERT INTO Sal_log VALUES (
	:new.Eno,:new.Sal,CURRENT_USER,CURRENT_TIMESTAMP)
END
```

删除触发器使用如下语句：
```sql
DROP TRIGGER <触发器名> ON <表名>
```
只能由表格的拥有者来删除这个触发器。触发器比较耗时，谨慎使用。












