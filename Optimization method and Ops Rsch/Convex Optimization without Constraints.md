#OPTandOR 

在这一节中，我们来求解非常简单的一类问题：
$$
\begin{aligned}
min \quad f(x) &\\
var. \quad x \in R^n&
\end{aligned}
$$
其中，$f (x)$ 是一个二阶连续可微的函数。

## Def of Convex Function
### 凸函数的定义
![[Pasted image 20230223170150.png|400]]
凸集：集合中任取两个点，两点间线段上的点仍然属于此集合。
数学上的定义：取 $x, y \in C$，以及 $\lambda \in [0,1]$，那么只要 $\lambda x + (1-\lambda) y \in C ,\forall \lambda$，则称 $C$ 是凸集

凸函数：要求函数及以上的区域是凸集！
![[Pasted image 20230223171232.png|450]]

严谨定义：
- 函数的定义域是凸集
- 对任意 $x, y \in C$ 且 $\lambda  \in[0, 1]$，都有 $f (\lambda x+(1-\lambda) y ) \leq \lambda f (x)+(1-\lambda )f(y)$
直观上，这意味着“y 轴上的平均值大于 x 轴上的平均值”
![[Pasted image 20230223171855.png|500]]

### 凸函数的快速检验方法
- Theorem ： **凸函数的一阶条件**
若 $f (x)$ 是一阶可微的，那么对于 $\forall x,y$

$$
f(y) \geq f(x)+\nabla f(x)^T(y-x)
$$
在一维条件下，这个不等式比较了切线斜率和割线的斜率
![[Pasted image 20230223172541.png|500]]

- Theorem : **凸函数的二阶条件**
（对于凸集上的二阶可微函数）要求 Hessian 矩阵是半正定矩阵，即 $\nabla^2 f(x)$ 是半正定阵。这意味着这个矩阵代表的二次型的值恒为正，也就是说，对于任意向量 $u$，$u^TAu \geq 0$ ，则 $A$ 为半正定矩阵。
判定方法：$A$ 的顺序主子式都为非负，则矩阵是半正定的。
特例：变量的维数为 1 时，条件退化成二阶导大于 0。

**对于凸函数，局部最优解就是全局最优解**（不要求 $f (x)$ 二阶连续可微）


