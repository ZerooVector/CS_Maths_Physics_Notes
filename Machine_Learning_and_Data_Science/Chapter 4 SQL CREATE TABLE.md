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


## 模式的定义


## 表的定义

要想建立一张表，需要给出表名、每一列的列名，以及完整性约束条件
```sql
CREATE TABLE SST.Student -- 声明想要建立一张表
(
	Sno CHAR(6) NOT NULL UNIQUE, -- 在定义属性的同时定义列级约束
	Sname CHAR(8),
	Sage INT,
	Ssex CHAR(2),
	Sdept CHAR(12),
	CONSTRAINT C1 CHECK (Ssex IN ('男','女')), --定义列级约束（可以和属性一起定义，也可以单独定义）
	CONSTRAINT S_PK PRIMARY KEY (Sno) -- 定义表级约束
);
```

```python
sql = "CREATE TABLE student(Sno CHAR(6) NOT NULL UNIQUE, Sname CHAR(8),Sage INT,Ssex CHAR(2),Sdept CHAR(12),CONSTRAINT C1 CHECK (Ssex IN ('F','M')),CONSTRAINT S_PK PRIMARY KEY(Sno))"
```


我们可以指定参照约束，使得一张表参照另一张
```SQL
CREATE TABLE SST.SC -- 指定表依赖的模式
(
Sno CHAR(6) NOT NULL,
Cno CHAR(6) NOT NULL,
GRADE INT CHECK (GRADE BETWEEN 0 AND 100),
PRIMARY KEY (Sno,Cno),
CONSTRAINT SC_FK1 FOREIGN KEY (Sno) REFERENCES Student(Sno), -- 指定本表参考外表
);
```

## 表的修改
要想修改一张表，需要先使用 `ALTER TABLE`，此后可以使用子句 `ADD`, `DROP`, `ALTER` 进行修改或删除
```sql
ALTER TABLE Student 
	ADD CLASS CHAR(8) -- 增加一列
```
注意，新增加的列会被强制置为空值

```sql
ALTER TABLE Student
	AlTER Sname CHAR(20) -- 修改数据的类型，可能导致数据截断
```

```sql

```

除了修改表之外，我们可以建立**索引**来提高查询的速度，使用 `CREATE [UNIQUE] [CLUSTER] INDEX <索引名> ON <表名> (<列名>[<次序>],...]` 来建立索引

```python
sql = '''
INSERT INTO student VALUES 
('000001','TDW',20,'M','CS'),
('000002','MTY',21,'M','PHY'),
('000003','CYX',21,'M','PHY'),
('000004','CXY',20,'M','PHY'),
('000005','SYH',19,'M','CS'),
('000006','TZ',18,'F','EE'),
('000007','ZXL',19,'F','MATH'),
('000008','XZJ',20,'M','MECH'),
('000009','GMZ',20,'M','CS');
'''
```

```python
sql = '''
INSERT INTO course VALUES
('100001','Algo',6),
('100002','DataSci',3),
('100003','ML',3),
('100004','DL',6),
('100005','Stat',3),
('100006','EleDy',6),
('100007','MatMec',5),
('100008','MaAna',6),
('100009','DigCir',2),
('100010','Pol',3);
'''
```

```python
sql = '''
INSERT INTO SC VALUES 
('000001','100001',90),
('000001','100003',91),
('000002','100002',88),
('000002','100006',92),
('000003','100002',85),
('000003','100004',87),
('000004','100005',98),
('000004','100008',92),
('000005','100002',92),
('000005','100005',95),
('000006','100009',94),
('000006','100002',91),
('000007','100008',92),
('000007','100003',95),
('000008','100002',61),
('000008','100005',45),
('000009','100006',47),
('000009','100009',99);

'''
```

```python
sql = '''
SELECT * FROM SC
'''
```