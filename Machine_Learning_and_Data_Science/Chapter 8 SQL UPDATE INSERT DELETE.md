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

***注意：本节中的很多操作都需要检查调整后的数据表是否满足约束条件***  


## 插入数据
### 直接插入数据
使用 `INSERT INTO <Table Name>(<Columns>) VALUES((),();) ` 进行插入

### 插入子查询的结果

求每个系学生的平均年龄
先创建表格
```python
sql = '''
CREATE TABLE Dept_age
(
Sdept CHAR(15),
Avg_Age INT
);
'''
```

再插入新的数据
```python
sql = '''
INSERT INTO Dept_age(Sdept,Avg_Age)
SELECT Sdept , AVG(Sage)
FROM Student 
GROUP BY Sdept ;
'''
```

检查结果
```python
sql = '''
SELECT * FROM dept_age
'''
```
在插入新的值时，会检查是否满足约束


```python
sql = '''

'''
```

## 修改数据


```python
sql = '''
UPDATE Student 
SET SAGE = 22
WHERE Sno = '000001'
'''
```

### 在修改中运算

```python
sql = '''
UPDATE Student 
SET SAGE = SAGE+1
WHERE Sdept = 'Mech'
'''
```

### 带有子查询的修改语句

```python
sql = '''
UPDATE SC 
Set Grade  = Grade - 10
WHERE Sno IN 
(
SELECT SNO 
FROM Student
WHERE Sdept  = 'CS'
)
'''
```

## 删除数据

```python
sql = '''
DELETE FROM Student
WHERE Sage > 100
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