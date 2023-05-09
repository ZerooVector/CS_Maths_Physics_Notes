---
banner: "![[banner7.png]]"
---
#Python

## Some Python features
### Division
```python
from operator import truediv,floordiv
truediv(1043,10)
# or you can say
1043/10

floordiv(1043,10)
# or you can say 
1043 // 10

1043 % 10 
mod(1043,10)

```

## Conditional statements 
以下是一个选择分支的例子
```python
def abs(x):
	if x<0:
		return -x
	elif x==0:
		return 0;
	else : 
		return x;
```

在代码中，必须包含一个 ```if```，零个或多个 ```elif``` ，以及至多一个 ```else``` 。

## Iteration
以下是一个循环的例子：
```python
i,total = 0,0
while i < 3:
	i = i + 1
	total = total + i
	
```

## Return
