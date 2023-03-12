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



```python 
sql='''

CREATE TABLE Scene(
id INT PRIMARY KEY,
biome CHAR(20) NOT NULL ,
city CHAR(20) NOT NULL,
visitors INT CHECK(visitors >= 0),
created_at DATETIME 
);
'''
```


```python 
sql='''
INSERT INTO Scene VALUES 
(0,'desert','Las Vegas',100,'2021-01-01'),
(1,'marine','Honolulu',1000,'2021-01-02'),
(2,'freshwater','Paris',50,'2021-01-05'),
(3,'marine','Taipei',100,'2021-01-07'),
(4,'desert','Austin',25,'2021-01-15'),
(5,'freshwater','Austin',240,'2021-01-15'),
(6,'freshwater','Las Vegas',100,'2021-01-15');
'''
```

```python 
sql='''
SELECT COUNT(*) FROM Scene
'''
```


```python 
sql='''
SELECT biome,COUNT(*)
FROM Scene
GROUP BY biome
ORDER BY COUNT(*) desc
LIMIT 1
'''
```


```python 
sql='''

'''
```

```python 
sql='''

'''
```


```python 
sql='''

'''
```

```python 
sql='''

'''
```


```python 
sql='''

'''
```



```python 
sql='''

'''
```

```python 
sql='''

'''
```

```python 
sql='''

'''
```


```python 
sql='''

'''
```

```python 
sql='''

'''
```

```python 
sql='''

'''
```

```python 
sql='''

'''
```

```python 
sql='''

'''
```

```python 
sql='''

'''
```



```python 
sql='''

'''
```

```python 
sql='''

'''
```

```python 
sql='''

'''
```


```python 
sql='''

'''
```
