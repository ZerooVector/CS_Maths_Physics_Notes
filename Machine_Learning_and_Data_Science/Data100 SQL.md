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

## 在真正使用 SQL 之前
SQL 可以使用的约束：
- NOT NULL
- DEFAULT
- UNIQUE
- PRIMARY KEY
- CHECK 

可以使用的类型：
- INT
- REAL
- TEXT
- BLOB
- NULL

一般来说，我们会使得主键是一个整数，这会使得数据库有很高的效率

## 建立表格
```python
sql = "show databases"
```

```python
sql = '''
CREATE TABLE Animal(
type CHAR(20) PRIMARY KEY ,
legs INTEGER CHECK (legs >= 0),
weight INTEGER CHECK (weight >= 0)
);
'''
```

```python
sql = '''
CREATE TABLE Member(
athlete CHAR(20),
esport CHAR(20),
skill INTEGER,
PRIMARY KEY (athlete,esport)

);
'''
```

```python
sql = '''
DROP TABLE IF EXISTS Clothing；
CREATE TABLE Clothing (
sku TEXT UNIQUE
name TEXT NO
)；
'''
```