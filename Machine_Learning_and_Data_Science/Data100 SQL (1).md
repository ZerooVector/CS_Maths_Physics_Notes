E #MLorDS 
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
DROP TABLE IF EXISTS Clothing;

CREATE TABLE Clothing (
id INT PRIMARY KEY auto_increment,
sku CHAR(20) UNIQUE ,
name TEXT NOT NULL
);
'''
```
==这一句实际上是没问题的，但是 Python 给出报错信息== 

```python
sql = '''
CREATE TABLE  Dragon(
name CHAR(20) PRIMARY KEY,
year INT CHECK (year >= 2000),
cute INT NOT NULLe
);
'''
```

## 插入数据和选择数据
```python 
sql ='''
INSERT INTO DRAGON VALUES
('hiccup',2010,10),
('dragon',2011,-100),
('dragon 2',2019,0);
'''
```

```python
sql ='''
SELECT * FROM Dragon
'''
```

- 你可以更改列的名称
``` python
sql = '''
SELECT year AS birth 
FROM Dragon AS Bird;
'''
```

- 笛卡尔积
```python
sql = '''
SELECT *  FROM
Dragon AS Dragon1,
Dragon AS Dragon2
'''
```

- 条件化地选择
```python
sql = '''
SELECT name,year 
FROM Dragon 
WHERE cute > 0
'''
```

- 排序
```python
sql = '''
SELECT * 
FROM Dragon 
ORDER BY cute desc ;
'''
```

- 选择指定数量的行 (LIMIT - 限制，OFFSET - 偏移)
```python
sql = '''
SELECT * FROM Dragon 
LIMIT 2  
OFFSET 1
'''
```

## Groupby : 按照组选择数据
```python
sql = '''
CREATE TABLE Dish (
name CHAR(20) PRIMARY KEY,
type CHAR(20) ,
cost INT 
);
'''
```

```python
sql = '''
INSERT INTO Dish VALUES 
('ravioli','entree',10),
('pork bun','entree',7),
('taco','entree',7),
('edamame','appetizer',4),
('fries','appetizer',4),
('potsticker','appetizer',4),
('ice cream','dessert',5)
'''
```

```python
sql = '''
SELECT * FROM   Dish
'''
```

### Groupby

```python
sql = '''
SELECT type FROM Dish
GROUP BY type
'''
```
这只会获得三个行

### 聚合函数
```python
sql = '''
SELECT COUNT(*)
FROM DISH 
'''
```


```python
sql = '''
SELECT type,COUNT(*)
FROM Dish 
GROUP BY type
'''
```



```python
sql = '''
SELECT type,name 
FROM Dish 
GROUP BY type 
'''
```
==这个有的编译器会报错，有的不会报错，但是不管咋样，这样请求 name 都是没用的== 

### 选取唯一值
```python
sql = '''
SELECT DISTINCT type FROM Dish 
'''
```


- Distinct 作为聚合函数出现
```python
sql = '''
SELECT type ,COUNT(DISTINCT cost ) 
FROM Dish
GROUP BY type
'''
```


### HAVING ： 过滤组
```python
sql = '''
SELECT AVG(cost)
FROM Dish
GROUP By type 
HAVING AVG(cost) > 5;
'''
```
注意比较和下面这个模块中的差距，下面这个模块先请求了均值大于 5 的食物，再将它们按照组聚合；而上面的是先聚合，再请求均值大于 5 的组
```python
sql = '''
SELECT AVG(cost)
FROM Dish 
WHERE cost > 5
GROUP By type 
'''
```




```python

cursor.close()
database.close()

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


