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
print("-----------FINISH------------")
for item in all_update:
	print(item)
```



## 简单的查询

例：查询 CS 系的学生
```python
sql = '''
SELECT Sno Sname 
FROM Student
WHERE Sdept = 'CS';
'''e
```

例：查询选修了课的学生学号，并且去重。DISTINCT 会对所有列同时作用。
```python
sql = '''
SELECT DISTINCT Sno
FROM SC
ORDER BY Sno;
'''
```

例：查询 18-25 岁的学生
```python
sql = '''
SELECT *
FROM Student 
WHERE Sage BETWEEN 18 AND 25
'''
```

下面的语句也能执行：
```python
sql = '''
SELECT *
FROM Student 
WHERE Sage>=18 AND Sage<=25
'''
```

```python
sql = '''SELECT * FROM Student  
WHERE Sage>=18 AND Sage<=25'''
```

```python
sql = "SHOW TABLES"
```

查询全体学生的姓名，出生年份、系，并使用小写字母表示系名
```python
sql = '''
SELECT Sname,'Year of Birth',2023-Sage,LOWER(Sdept)
FROM Student 
'''
```
这样输出的时候，'Year of Birth'会作为常量输出成一列
可以使用列别名的形式使查询更清晰一些

## 逻辑表达式
-  `IN` 要求该列的取值是集合中的某一个
-  `LIKE` 用于字符串匹配，`_` 匹配一个字符，`%` 匹配任意字符串
- `NULL` 匹配空值
- `EXISTS` 存在量词
- `= ,>,<,>=,<=,NOT,!=,!>,!<` 等等

### IN 

查询 20 岁以下的学生姓名和年龄
```python
sql = '''
SELECT Sage,Sname FROM Student
WHERE Sage < 20
'''
```

查询指定系的学生

```python
sql = '''
SELECT Sname FROM Student
WHERE Sdept in('CS','MA','EE')
'''
```

### LIKE 
匹配模板可以是字符串常量或者含有通配符
在常量时，可以使用 `=` 或者 `!=` 来代替 `LIKE`
在使用通配符时，`%` 代表任意长度的任意字符，`_` 代表单个任意字符
如果字符串中本身含有通配符，那么需要使用 `ESCAPE` 进行转义

```python
sql = '''
SELECT Sname,Sno,Ssex FROM Student
WHERE Sname LIKE 'L%'
'''
```

指定转义符：
```python
sql = '''
SELECT Cno FROM Course
WHERE Cname LIKE 'ab\_c'  ESCAPE '\' 
''' 
```

