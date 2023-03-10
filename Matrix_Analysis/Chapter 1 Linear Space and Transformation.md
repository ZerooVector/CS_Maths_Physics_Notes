---
banner: "![[banner21.png]]"
---
#MA

# 课堂教授内容
## Vector 
- 数域：和差积商运算封闭的集合, e.g. $\mathcal R,\mathcal C$
- 显然，向量的始端可以任意平移，因此，向量和空间中的点是一一对应的
![[Pasted image 20230222141735.png|400]]

向量可以有多种运算：
-  和：$a+b = (a_1+b_1, a_2+b_2,\cdots , a_n+b_n)$
- 数乘： $\lambda a  = (\lambda a_1,\cdots ,\lambda a_n)$
- 数量积 
- 外积
- 线性组合

## Vector Space
既然我们将数域定义为某种集合，那么，向量空间也是满足特定要求的向量集合！这些要求通常包括：
- 对于加法和数乘封闭

一般来说，几个向量进行线性组合，就可以“张成 (span)”一个向量空间。我们将几个向量的所有线性组合称为它们的 span, 也就是：
$$
span(a_1,\cdots ,a_n) = \lambda_1a_1+\cdots+\lambda_n a_n
$$
齐次方程组的解构成解空间，这很容易验证：解相加仍然是解，解数乘仍然是解


## Linear Space 

### Def:
线性空间是在向量空间的基础上发展而来的，它还要求：
- 空间中的加法和数乘得到唯一的结果
- 向量加法交换律成立
- 向量加法结合律成立
- 存在一个零向量：$a+\theta =a,\forall a \in V$
- 存在加法逆元：$\exists -a, (-a)+a = 0,\forall a \in V$
- 向量数乘的乘法分配律成立，这包括：$\lambda (a+b) = \lambda a+\lambda b \quad (\lambda+\mu) a = \lambda a+\mu a$
- 结合律成立
- 存在乘法单位元

一些线性空间的例子：
- 数域上不超过 $n$ 次的一元多项式是多项式空间 $P[t]_n$ （当然，把多项式的所有系数提出来就是多项式空间中的向量）
- 数域 $F$ 本身、$F$ 上的加法和乘法是一个向量空间（例如，有理数，可以看作是一维的向量空间）
- $[a,b]$ 上全体实函数（？）

### 性质
- 零元唯一，这可以假设存在两个零元，使用然后得到它们相等
- 逆元唯一
- $0a = \theta \quad (-1) a = -a \quad k \theta  = 0$
- 如果 $ka = \theta$ 则 $k=0 \ \ or \ \  a = 0$

### 线性相关
我们可以进一步定义线性相关：
$$
\exists \lambda_i,\sum_i \lambda_ia_i = \theta
$$
则称 $a_i$ 线性相关
![[Pasted image 20230222144049.png|400]]
线性相关的向量组中，至少有一个向量可以被其他向量的线性组合表出
向量组中最大可以取出的线性无关的向量的数目，称为向量组的秩 (rank)，显然，$m$ 个向量线性相关的充要条件是向量组的秩小于 $m$ 。（最多地）被取出来的这些线性无关的向量，则称为向量组的极大线性无关组

## Sub Space
$V$ 是 $F$ 上线性空间， $W$ 是 $V$ 的非空子集。若 $W$ 中关于 $V$ 的加法和数乘仍然是 $F$ 上的子空间，则 $W$ 是 $V$ 的子空间。

### 性质
-  $V$ 是线性空间，则 $V$ 中任意 $m$ 个向量的线性组合都构成 $V$ 的子空间
- $a_i$ 和 $b_j$ 是线性空间中的两组向量，若 $\forall a_i$ 可以由 $b_j$ 线性地表出，那么 $a_i$ 张成的空间是 $b_i$ 张成空间的子空间

### 子空间的运算
我们希望在子空间内引入一些运算，以此研究子空间的数学性质。要考虑在线性空间内引入何种运算，我们首先可以类比常见的几何空间。显然，对于现实中的两个平面，我们可以引入它们的交集、并集，等等。我们可以把这些概念推广到一般的线性空间中。现在，设 $V$ 是一个线性空间，$V$ 有两个子空间 $V_1, V_2$：

#### 子空间的交
$V_1 \cap V_2$ 定义为子空间的交。子空间的交是子空间吗？
首先，我们说明它不是空集。由于零元素位于任何的线性空间中，因此，它们的交集中至少有零元素。
其次，我们再来说明对加法封闭。任取 $a, b \in V_1 \cap V_2$，则 $a+b \in V_1, a+b \in V_2$，从而，$a+b \in V_1 \cap V_2$
最后，我们说明对乘法封闭。这也是容易说明的。

显然，子空间的交满足交换律和结合律。

#### 子空间的并
$V_1 \cup V_2$ 定义为子空间的并。显然可以看出，一般不是。

#### 子空间的和——由两个子空间中的向量组合生成
之前的定义都是基于子空间本身，而子空间的和将空间延展：
$$
V_1+V_2:=\{a_1+a_2|a_1\in V_1,a_2 \in V_2\}
$$
由于零元素的存在，所以 $V_1+V_2$ 非空。
任取 $V_1+V_2$ 中的两个向量 $a_1+a_2,b_1+b_2$，其中 $a_1, b_1 \in V_1; a_2, b_2 \in V_2$
$$
(a_1+a_2)+(b_1+b_2) = (a_1+b_1)+(a_2+b_2)
$$
因此，$a_1+b_1 \in V_1$, $a_2+b_2 \in V_2$ ，因此，它属于 $V_1+V_2$
$k (a_1+a_2) = ka_1+ka_2$，其中 $ka_1 \in V_1, ka_2 \in V_2$，因此，对数乘也封闭
以上得证，子空间的和也是子空间

显然，子空间的加法有交换律和结合律。


##### Pf：
1->2


2->3

3->1


**补充：可以认为，线性空间和向量空间仅仅是两个不同的表述形式，不必纠结于它们到底怎样不同**


## Base and Dimension

对于线性空间上的一组线性无关的向量 $a_1, a_2,..., a_n$，它们自己线性无关，但是其他任意一个向量 $b$ 均可由它们的线性组合表出，那么，这些向量就被称为一组基。
那么，我们可以将 $b$ 写成：
$$
b = \sum_i x_ia_i
$$
这里的 $x_i$ 称为 $b$ 在基 $a$ 下面的坐标。

显然，$V$ 是 $m$ 维的线性空间，则 $V$ 中任意 $m$ 个线性无关的向量均是一组基

##### Theorm
$$
dim(S_1+S_2)+dim(S_1 \cap S_2) = dim(S_1)+dim(S_2)
$$
##### Pf:
==这里需要补上证明==

## Linear Transformation
### Def
如果，一个变换满足
$$
f(a+b) = f(a)+f(b) \quad f(\lambda a ) = \lambda f(a)
$$
那么我们就称 $f$ 是一个线性变换。
### 性质
- 零元的线性变换也是零元
- $f$ 将线性相关的向量组变成线性相关的向量组
- 可逆线性变换的逆变换也是线性变换
- 线性变换的乘积：$(fg)(a) = f(g(a))$，因此，线性变换一般是满足结合律，但不满足交换律的
- $(f+g) a = f(a)+g(a)$
- $\lambda f (a) = f (\lambda a)$

### 值域与核
- V 中元素在 $f$ 下像的集合称为 $f$ 的值域
- V 中元素在线性变换中被变为 0 的部分，称为 $f$ 的核（或零空间）
- V 的值域与核都是 V 的子空间。
- $f$ 的值域的秩与核的秩的和为 $n$

## Matrix
矩阵是线性变换的一种描述，我们通常使用 $Mx$ 表示队 $x$ 的变换，这里，矩阵 $M$ 中的每一列是一个基向量










# 选择性阅读内容

## Vector Space

- 一个向量空间的基底，指的是这个向量空间中一组线性无关的向量，它们能够张成这个向量空间。
- 维数就是基底中向量的个数
- 仿射空间：向量空间平移后得到的空间就是仿射空间
- 基底的选择不是唯一的，但是，一个向量在不同的基底下可以有不同的坐标
- 基，正交基，标准正交基

**恶心人的东西：基底的转换**
我们先以二维平面上的向量作为例子说明这一点：
假设在第一套基底中，任何一个向量 $x$ 可以写成：
$$
x = [u_1\ u_2][y_1,y_2]^T = UY
$$
这个方程其实表示，$x$ 是 $u_1, u_2$ 的线性组合，也就是:
$$
x = y_1u_1+y_2u_2
$$
现在，平面上，存在另一套基底：
$$
x = [v_1\ v_2][z_1,z_2]^T=VZ
$$
此外，在标准正交基下，$x$ 的坐标可以被写为
$$
x = X
$$
也就是说，
$$
X = UY = VZ
$$
那么，我们可以转换坐标：
$$
Z  = V^{-1}UY
$$

个人把 $U, V$ 这样，用将基向量作为列向量，拼接而成的矩阵称为 base mat，那么，将在一组基下面的坐标 $Y$ 转成另一组基下面坐标 $Z$ 的方法是，左乘自己这组基的 base mat，再左乘新的基的 base mat 的逆

**向量空间的一个超级直观的可视化：用 RGB 颜色给空间涂色**
将三个基底设为 $[1, 0, 0],[0, 1, 0],[0, 0, 1]$，使得它们互相正交，张成的空间如下图所示：
![[Pasted image 20230222154536.png|400]]

另外，基底转换这件事，还有一个矩阵是过渡矩阵，其定义是，把一个 base mat 转换成另一个的矩阵：
$$
[v_1\ v_2\ v_3] = A[e_1\ e_2\ e_3]
$$
比如，RGB 色系和印刷四色（这里只展示三色）可以互相转
![[Pasted image 20230222155330.png|400]]

