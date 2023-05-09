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

***The goal of this lesson is to create multiple table in SQL***

在数据库的建立过程中，我们通常要使用一种叫做规范化 (Normalization)的技术，这将大的表格拆解成小的表格，从而使得在每个表格上的插入、删除等操作更加容易，也使得我们的数据库占据了更少的空间。

数据库中可能的关系主要分为三种：
- 一对一的
- 一对多的
- 多对多的

## 连接两张表格

### 创建表格

```python
sql = '''
CREATE TABLE breed 
(
id INT PRIMARY KEY auto_increment,
name CHAR(20) 
);

INSERT INTO Breed (name) VALUES 
('Corgi'),
('Bernese'),
('Bulldog');

CREATE TABLE Pet 
(
id INT  PRIMARY KEY auto_increment,
breed_id INT NOT NULL,
name CHAR(20) NOT NULL
);

INSERT INTO Pet (breed_id,name) VALUES 
(1,'Apricot'),
(2,'Boots');
'''
```

### Cross Join 
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


