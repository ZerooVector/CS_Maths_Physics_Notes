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

## 等值与非等值连接查询
### 等值连接
连接学生表和选课表，给出同一名学生的基本信息和选课情况
```python 
sql = '''
SELECT Student.* ,SC.* FROM STUDENT,SC
WHERE Student.Sno = SC.Sno
'''
```
这个不会去除两列重复值中的一列

### 自然连接
```python
Sql = '''
SELECT Student.Sno ,SC.Grade FROM STUDENT, SC
WHERE Student. Sno = SC. Sno
'''
```

### 自身连接
找到一门课的先修课的先修课——需要向前倒退两次
```python 
sql = '''
SELECT FIRST.Cno, SECOND.Cpno FROM Course FIRST Course SECOND
WHERE First.Cpno = SECOND.Cno
'''
```
### 内连接
```python
sql = '''
SELECT 
```

