#MLorDS 
##### 前置代码，请引入到任何学习使用 mySQL 的笔记本中，并首先执行一次
```python 
import pymysql
database = pymysql.connect(host = 'localhost',user = 'root',password = '030329',database = "test_db")
cursor = database.cursor() # 创建用于管理数据库的游标

```

##### 后置代码注射，请引入到任何学习使用 mySQL 的笔记本中
```python{post}
cursor.execute(sql)
all_update = cursor.fetchall()
database.commit()
print("-----------FINISH------------")
for item in all_update:
	print(item)
```


## 视图是什么？
==CHAT-GPT== 在 SQL（结构化查询语言）中，视图（View）是一个虚拟表，它是一个基于 SQL 查询的结果集。视图并不存储实际的数据，而是根据定义它的查询语句从一个或多个基础表（Base Table）中实时计算和显示数据。视图可以像普通表一样进行查询、插入、更新和删除操作（但这些操作受到一定限制）

## 视图的创建

视图创建时不执行子查询语句，只有在调用视图时，DBMS 才会执行子查询
视图的列名必须全部指定，或者全部省略（沿用原表格）

在 SQL 中，`WITH CHECK OPTION` 是一个可用于创建视图时的子句，它用于约束对视图进行的数据修改操作。当在视图上使用 `WITH CHECK OPTION` 时，它确保任何对视图执行的插入、更新或删除操作不会导致视图所定义的查询结果集之外的数据被插入、修改或删除。换句话说，`WITH CHECK OPTION` 确保在修改视图数据时遵循视图定义中的条件。

`WITH CHECK OPTION` 的主要用途是保持数据的完整性和一致性。它可以防止用户通过视图修改那些不应被修改的数据。例如，如果您有一个视图，仅显示销售额大于 1000 的订单，那么使用 `WITH CHECK OPTION` 可确保用户无法插入或更新销售额低于 1000 的订单。


```python
sql = '''

CREATE VIEW Sage_20
AS SELECT *
FROM Student 
WHERE Sage<20
WITH CHECK OPTION

'''
```

定义一个反应学生出生年份的视图

```python
sql = '''
CREATE VIEW BT_S(Sno,Sname,Sbirth)
AS SELECT Sno,Sname,2023-Sage
FROM Student
'''
```

按照系建立学生的平均年龄

```python
sql = '''

'''
```

### 通过连接查询建立视图

**在建立多张表上的视图时，必须指定列名**

```python
sql = '''
CREATE VIEW CS_SC (Sno,Sname,Grade)
AS SELECT Student.Sno,Sname,Grade
FROM Student , SC
WHERE Sdept = 'CS' AND Student.Sno = SC.Sno AND SC.Cno = '100001'
'''
```

### 视图的嵌套定义

```python
sql = '''
CREATE VIEW  CS_70 
AS SELECT *
FROM CS_SC 
WHERE Grade > 70
'''
```

建议不用 `SELECT * ` 选择属性建立视图，而是列出属性，不然原表改变后，视图无法正常工作

```python
sql = '''

'''
```

## 删除视图
`DROP VIEW <viewname> [CASCADE]` 来删除视图，如果启用 `CASCADE`，将会级联地删除视图

```python
sql = '''
DROP VIEW CS_70 CASCADE
'''
```

## 视图上的操作

### 视图上的查询
视图实体化两步走：先将视图查出来，成为一张表，在这张临时表上查询，查完了再删掉
视图消解也是两步走：结合视图查询和用户查询操作，再直接在基表上查询
视图消解可能存在问题，尤其是含有聚集函数的等复杂查询

```python
sql = '''
SELECT * FROM Sage_20 
WHERE Sdept = 'CS'
'''
```

### 视图上的修改

```SQL
INSERT INTO Sage_23
VALUES ('20041'，'LM',25,'F','MATH')
```

==问题：不使用 `WITH CHECK OPTION`，是不是就绕过了检测？== 

下面的删除不可能删除视图中看不到的学生
```sql
DELETE FROM Sage_23
WHERE Sname = 'TDW'
```


```sql
UPDATE Sage_23 
SET Sdept = 'MATH'
WHERE Sname = 'TDW'
```

**有一些视图不可被更新，因为对于视图的更新无法通过任何方法转换成对于基本表的操作**   
**比如，使用聚集函数定义的视图、涉及到两张表的视图不可更新** 
**仅在一个表上进行的取行、列操作的视图必然是可以更新的，因为视图中的一个元组对应于基本表中的一个元组**

```python
sql = '''

'''
```

## 视图有什么优势？
- 提供了一定程度的逻辑独立性，使得数据库逻辑结构变化时，用户的外模式几乎不变。
- 简化用户的操作，很多需要连接多张表的、复杂嵌套的查询被显示在一张视图上，可以避免重复造轮子。
- 从多种角度看待同一张基表上的数据（类似于“数据透视表”），具有灵活性
- 对于不同用户可以定义不同的视图，从而使每个用户仅仅操作一部分数据，提供了安全保护功能

```python
sql = '''

'''
```

## 简介：SQL 的授权

### GRANT 语句
`GRANT () ON () TO () (WITH GRANT OPTION)`
```sql
GRANT SELECT , DELETE (Gr)
ON TABLE Student 
TO user 2 
WITH GRANT OPTION
```

### REVOKE 语句

`REVOKE() ON () FROM () (RESTRICT|CASCADE)`
```sql
REVOKE SELECT 
ON TABLE Student
FROM User2
CASCADE 
```


```python
sql = '''

'''
```





```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```



```python
sql = '''

'''
```


```python
sql = '''

'''
```


```python
sql = '''

'''
```