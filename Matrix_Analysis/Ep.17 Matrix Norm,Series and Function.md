#MA   

## 向量的范数 (Vector Norm)

##### Def 
若 $V$ 是 $\mathbb{C}$ 上的线性空间，那么映射 $||\cdot ||: V \rightarrow  \mathbb{R}$ 称为向量范数，如果满足以下条件：
- 正性：$||x||>0,\forall x \not = 0$
- 正齐性：$||xk|| = |k|\cdot ||x||$ 
- 三角不等式：$||x+y|| \le ||x||+||y||$ 

##### Example 
$\mathbb{C}^{n}$ 上的范数
- L 1 范数：$||x||_{L1} = \sum x_{i}$ 
- L 2 范数：$||x||_{L2} = \sqrt{\sum x_{i}^{2}}$
- P 范数：$||x||_{p}= [\sum x_{i}^{p}]^{1/p}$ 
- 无穷范数：$||x||_{\infty} = \max x_{i}$ ，这是 $p \rightarrow \infty$ 的必然结果

解释：为什么要引入范数？这是因为从范数可以导出距离。给定 $x, y$ 两个向量，可以定义 $d (x, y) = ||x-y||$ 为 $x, y$ 之间的距离，距离是研究很多其他问题的基础（比如分析学中的极限）。
对于一个距离，以下特征应该得到满足：
- 非负性：$d (x, y)\ge 0$
- 对称性：$d (x, y) = d(y,x)$ 
- 三角不等式：$d (x, y) \le d(x,z)+d(z,y)$ 

我们说，一个序列有极限，即 $\lim s_{n} \rightarrow s$，就是说 $\lim d (s_{n}, s) \rightarrow 0$ 

##### Example 
注意：长度一定是范数，但是范数一定不是长度，例如，L 1 范数能否写成某种自身与自身的内积？这是不行的。因为范数不一定符合长度所满足的平行四边形公式，因此这个范数也不能由内积所导出
这容易验证。例如取 $a = [1,0]^{T}, b = [0,1]^{T}$ 即可验证。
也就是说，由内积决定的长度是一种极其特殊的范数，它有着夹角等更丰富的几何结构。

## 矩阵的范数 (Matrix Norm) 

##### Def 
矩阵范数是一种将矩阵映射到一个实数的函数。$||\cdot || : \mathrm{Matrix } \rightarrow \mathbb{R}$ 被定义为一个范数，如果它满足以下规则：
- 正性：$||A|| >0$，只要 $A$ 不是零矩阵
- 正齐性：$||kA||  = |k| \cdot ||A||$
- 加法相容性（三角不等式）$||A+B|| \le ||A||+||B||$
- 乘法相容性：$||AB|| \le ||A||\cdot ||B||$  

##### Example 由向量范数所导出的矩阵范数
我们将由向量的 $p$ 范数导出的矩阵范数称为矩阵的 $p$ 范数，也就是说
$$
||A||_{p}=\max \frac{||Ax||_{p}}{||x||_{p}}
$$
在 $p=1$ 时，可以证明是矩阵的最大列和（将 $x$ 的分量全部分到 $A$ 的列和最大的一列）
在 $p=2$ 时，问题转化为瑞丽商的极值规划问题，是矩阵的最大奇异值
在 $p \rightarrow \infty$ 时，则是矩阵的最大行和


## 向量与矩阵序列的极限
##### Def
称 $\lim_{k \rightarrow \infty}A_{k} = A$ 如果 $\lim_{k \rightarrow \infty}d(A_{k},A)=0$ ，也就是 $\lim_{k \rightarrow \infty}||A_{k}-A|| = 0$ ，这样，我们就把矩阵序列的极限问题转换为了实数序列的极限问题

##### Theorem 
$\lim A_{k}=A$ 意味着 $\lim (a_{ij})_{k} = a_{ij}$ ，也就是说，矩阵趋近于极限相当于矩阵中的每个元素都趋近于极限

##### PF 
如果是 1 范数，这是显然的，因为 1 范数会大于 $A_k -A$ 中的每一个元素
下面我们将说明对于任何一个范数都成立。我们将矩阵中的一个元素表示为：
$$
(a_{ij}(k)-a_{ij}) = \alpha_{i}^{T}(A(k)-A)\beta_{j}
$$
其中，$[\alpha_{1},\cdots ,\alpha_{m}] = I_{m},[\beta_{1},\cdots ,\beta_{n}] = I_{n}$ ，你总能通过合理地选择 $\alpha_{i},\beta_{j}$，来提取你想要的元素。 那么：
$$
(a_{ij}(k)-a_{ij}) \le ||a_{i}^{T} ||\ ||A(k)-A||\ ||\beta_j||
$$
由于右边极限为 0，显然左边极限也为 0！

接下来我们倒推：
$$
(A(k)-A) = \sum_{i,j}((a_{ij}(k))-a_{ij})\mathbb{E}(i,j)
$$
其中，$\mathbb{E}(i,j)$ 是一个第 $i$ 行第 $j$ 列为 1，其余为 0 的阵
因此：
$$
||A(k)-A|| \le \sum_{ij} |a_{ij}(k)-a_{ij}|\ ||\mathbb{E}_{ij}||
$$
显然，右边的极限为 0，左边也为 0！

这样，我们就看到了引入范数在研究极限上的好处！

## 矩阵级数
接下来，我们研究 $e^{A}$ 和 $e^{At}$ 的问题

##### Theorem 
$A \in \mathbb{C}^{n \times n}$ ，矩阵级数
$$
\sum_{k=0}^{\infty} \frac{A^{k}}{k!} 
$$
收敛，即部分和序列收敛
$$
S_{n}= \sum_{k=0}^{n} \frac{A^{k}}{k!} 
$$
收敛。

对于一个数列，我们要研究它的敛散性，那么我们有 Cauchy 收敛准则：
$$
|a_{n}-a_{m}| < \epsilon 
$$
那么，对于矩阵，我们只要说明数列
$$
||\sum_{k=p+1}^{q} \frac{A^{k}}{k!} || \le \sum_{k=p}^{q} \frac{||A||^{k}}{k!} = \exp(||A||)
$$
收敛，那么根据 Cauchy 收敛准则，显然收敛。

##### Example 矩阵级数的计算
基于 Jordan 型计算矩阵级数
$$
P^{-1}AP = \mathrm{diag}(J_{1},\cdots ,J_{q})
$$
那么，我们要求的级数可以表示为：
$$
e^{At} = Pe^{Jt}P^{-1}
$$
而 $e^{Jt} = \mathrm{diag}(e^{J_{1}t},\cdots ,e^{J_{q}t})$，我们考虑如何计算一个特定的 Jordan 块上求出的结果

##### Lemma 
$$
e^{A+B} =e^{A}e^{B}
$$
当且仅当 $A, B$ 可交换

那么，一个 Jordan 块可以分解成 $J_{1} = \lambda I + N$ ，$N^{i}$ 就是第 $i$ 条对角线上的全 1 ，其他地方全 0 的阵

$$
e^{J_{1}t}= e^{\lambda It+Nt} = e^{\lambda It}e^{Nt} 
$$
那么显然
$$
e^{\lambda It} = \mathrm{diag}(e^{\lambda_{i}t})
$$
另外一部分：
![[Pasted image 20230319112441.png|450]]


## 向量（矩阵）值函数
$A (\cdot):[a, b] \rightarrow \mathbb{C}^{m\times n}$ 被称为一个矩阵值函数

##### Def 极限
$$
\lim_{t \rightarrow t_{0}} A(t) = A 
$$
意味着
$$
\lim_{t \rightarrow t_{0}} ||A(t)-A|| = 0
$$

##### Def 导数
$$
A'(t_{0}) = \frac{A(t_{0}+\Delta t )-A(t_{0})}{\Delta t } = A'(t_{0})
$$
##### Def 定积分
$$
\int_{a}^{b}  A(t)dt = \lim_{\max |t_{i}-t_{i-1}| \rightarrow0} \sum A(t_{i})\Delta t_{i} 
$$

##### Theorem 
- 矩阵函数的极限是每个元素取极限
- 矩阵函数的导数相当于每个元素求导
- 矩阵函数的积分相当于每个元素积分

其他性质：
$$
(AB)' = A'B+AB'
$$
$$
(A^{-1}(t))' = -A^{-1}(t)(A(t))'A^{-1}(t)
$$
