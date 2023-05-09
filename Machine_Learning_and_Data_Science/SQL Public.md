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


# 下面开始正文
---



```python
sql = "show databases"
```

```python
sql = "create database if not exists test_db"
```

