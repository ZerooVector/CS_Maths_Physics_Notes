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



## 嵌套查询

下面的语句查询选修了 2 号课的学生名字，可以用连接运算代替
```python
sql = '''
SELECT Sname 
FROM Student 
WHERE Sno IN 
(
SELECT Sno FROM SC 
WHERE Cno  = '100002'
)
'''
```
- 注意：子查询中不能也没有必要使用 `ORDER BY` 语句

- 不相关子查询：子查询的查询条件不依赖于父查询，那么直接从里向外处理即可
- 相关子查询：首先取出通过了外层 WHERE 的一个元组，根据它与外层查询相关的属性值来处理内层查询，如果内层的 WHERE 也通过，放入结果中

例如，查询学生所选课程超过该门课程平均成绩的学生编号和课程号

```python
sql = '''
SELECT Sno,Cno 
FROM SC as x
WHERE GRADE > 
(SELECT AVG(Grade)
FROM SC y 
WHERE y.Cno = X.Cno )
'''
```

从 X (SC)表中找到了所有的学生号 Cno，传入二级查询中，二级查询负责筛选出这门课的所有成绩，并且计算这门课的平均成绩，平均成绩被传回外层，再与这个学生的成绩作比较

### 带有 IN 的子查询

查询与"TDW"这名学生在同一个系的学生，其中的 `IN` 可以换成 `=` ，这是一个不相关子查询，别名的定义是可选的，这个例子里可以不加
```python
sql = '''
SELECT Sno,Sname
FROM Student AS s1
WHERE Sdept IN
(
SELECT Sdept 
FROM Student AS s2
WHERE s2.Sname = "TDW"
)
'''
```
==使用自身连接进行查询的情况，请你自行完成== 


查询选修了某一门课的学生
```python
sql = '''
SELECT Sno,Sname
FROM STUDENT 
WHERE Sno IN 
(
SELECT Sno 
FROM SC 
WHERE Cno IN
(
SELECT Cno 
FROM Course 
WHERE Cname = 'Algo'
)
)
'''
```


### 带有比较运算符的查询
在内层返回一个单值的时候，可以使用 `=` 代替 ` IN `

### 带有 ANY 或者 ALL 
- `ANY` 指代查询结果中的任意一个值
- `ALL` 指代查询结果中的所有值
![[Pasted image 20230313134549.png|450]]


查询其他系中比 CS 系中任意一个学生小的学生的姓名和年龄，这也可以用聚集函数实现
```python
sql = '''
SELECT sname,sage FROM Student
WHERE SAge < ANY 
(
SELECT Sage FROM Student 
WHERE Sdept = 'CS'
)
AND Sdept <> 'CS'
'''
```

### 带有 EXISTS 
`EXISTS` 只返回 `True` 或 `False` 中的一个，其本质就是返回“能不能找到满足条件的元组”
例如，查询选择了 1 号课的学生的姓名
```python
sql = '''
SELECT Sname 
FROM Student AS x
WHERE EXISTS 
(
SELECT *
FROM SC AS y 
WHERE y.Sno = x.Sno AND y.Cno = '100001'
)
'''
```

### 实现全称量词 FORALL 

查询选修了全部课程的学生姓名，也就是对于目标的学生，**不存在**一门课**没有被选中**
```sQL
SELECT Sname --选择一个学生
FROM Student --应该从学生表里面选
WHERE NOT EXISTS --对于这个学生，以下条件不能被满足 （由于下一层是找课程，因此限制条件就是下面描述的这种课不能被选出来）（三层合起来，意思就是“这个学生不可以有没选的课”）
	(
	SELECT * 
	FROM Course --找到课程
	WHERE NOT EXISTS --这门课不能满足下面的条件（这里合起来，表达的就是“第二层中查找的课程是这个学生没有选择的课程”）
		(
		SELECT *
		FROM SC 
		WHERE Sno = Student.Sno AND Cno = Course.Cno  --条件是“这个学生选了这门课“”
		)
	)
```






## 集合查询
SQL 的集合查询支持 `UNION`，对于 `INTERSECT` 和 `MINUS` 必须手动实现

### UNION
```python
sql = '''
SELECT * 
FROM student 
WHERE Sdept = 'CS'
UNION 
SELECT * 
FROM student
WHERE Sage < 19
'''
```

### INTERSECT 
交操作可以使用 `AND` 或者子查询实现。
例如，查询同时选修课程 1，又选修了课程 2 的学生
```python
sql = '''
SELECT * 
FROM SC AS x
WHERE x.Cno = '100001' AND x.Sno IN
(SELECT Sno 
FROM SC AS y
WHERE y.Cno = '100002')
'''
```
如果交操作同时落在两个属性上，那么你可以用 `AND`，否则，你只能用子查询


### EXCEPT
差操作一般使用子查询实现。
```python
sql = '''
SELECT  Sno 
FROM SC
WHERE Cno = '100001'
AND Sno NOT IN 
(
SELECT Sno 
FROM SC 
WHERE Cno = '100002'
)
'''
```

### 集合操作的排序
对于集合操作进行排序时，只能将 `ORDER BY` 语句放在最末尾，不能在中间排序

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



