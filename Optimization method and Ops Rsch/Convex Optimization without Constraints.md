#OPTandOR 

在这一节中，我们来求解非常简单的一类问题：
$$
\begin{aligned}
min \quad f(x) &\\
var. \quad x \in R^n&
\end{aligned}
$$
其中，$f (x)$ 是一个二阶连续可微的函数。


## 凸函数的定义
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

## 凸函数的快速检验方法
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
##### PF 
反证法：若存在 $x_l$ 和 $x_g$，那么必有
$$
f(x_l)>f(x_g)
$$
取 $\theta \in [0,1]$，取
$$
x_\theta = \theta x_{loc}+(1-\theta)x_{global}
$$
那么取 $\theta$ 很接近 1 ，则 $x_\theta$ 很接近 $x_l$，由局部极小值的定义：
$$
f(x_l)<f(x_\theta) = f(\theta x_l+(1-\theta )x_g)<\theta f(x_l)+(1-\theta)f(x_g)<f(x_{l})
$$
这显然推出了矛盾。

##### Theorem 
若 $f (x)$ 是一阶可微凸，那么 $x^\star$ 是 $f (x)$ 的全局最小值的充要条件是：
$$
\nabla f(x^\star) = 0
$$
充分性可以由凸函数的一阶条件直接证得。

## 求解凸优化的算法
例如，我们希望求解岭回归和 LASSO 回归问题：
$$
\min \frac{1}{N} ||Aw-b||_2^2+\lambda||w||_{1 \ or \ 2}^2
$$
这里面，容易得到 $\nabla ||Aw-b|| = 2A^T (Aw-b)$，$\nabla^2||Aw-b||=2A^TA$ 。然后需要证明 $u^TA^TAu \geq 0$，那么令 $v=Au$，显然 $v^Tv \geq 0$，所以 $A^TA$ 是半正定的。也容易证明 $$ 








