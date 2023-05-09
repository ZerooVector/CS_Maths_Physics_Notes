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

找到属于哪个生物群落的城市最多？
```python 
sql='''
SELECT biome
FROM Scene
GROUP BY biome
ORDER BY COUNT(*) DESC
LIMIT 1
'''
```

将表格自身和自身做笛卡尔积，对于生成的所有行，找到两个游客数的和最大的一行
```python 
sql='''
SELECT  Scene1.visitors + Scene2.visitors AS 'sum'
FROM Scene AS Scene1 , Scene AS Scene2 
ORDER BY Scene1.visitors + Scene2.visitors DESC 
LIMIT 1
'''
```

找到超过 95 个游客的景点，要求**不重复地**输出**景点所在的城市**
```python 
sql='''
SELECT city
FROM Scene 
WHERE visitors > 95
GROUP BY city
'''
```
==注意，这里已经对 City 进行了聚合，不能再请求除了 City 字段本身和聚合函数以外的东西==

找到超过 125 个游客的**城市**，要求不重复地输出这些城市的名字
```python 
sql='''
SELECT city 
FROM Scene 
GROUP BY city 
HAVING SUM(visitors) > 125
'''
```

找到游览人数最少的城市
```python 
sql='''
SELECT city 
FROM SCENE 
GROUP BY city
ORDER BY SUM(visitors) 
LIMIT 1;
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
