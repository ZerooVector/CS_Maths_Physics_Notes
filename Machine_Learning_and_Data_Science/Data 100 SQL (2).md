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





```python
sql = '''

'''
```


