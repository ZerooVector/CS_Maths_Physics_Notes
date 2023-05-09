#MA 

## 特殊的向量组——标准正交组

##### Def 标准正交组

设 $V$ 是 $\mathbb{C}$ 上的内积空间，向量组 $\alpha_{1},\alpha_{2},\cdots,\alpha_{s}$ 称为标准正交组，如果满足：
- 标准性：$||\alpha_{i}||=1$ 
- 正交性：$\alpha_{j} \bot \alpha_{i} \ ,\ \forall i\not = j$ 

性质：
- 标准正交基的 Gram 矩阵是单位矩阵。因为我们可以使用 Gram 矩阵计算向量（的线性组合的）内积，因此取成标准正交组的情况大大简化了计算
- 标准正交基一定是线性无关的

##### PF 
线性无关的定义：
$$
v = \sum_{i}\alpha_{i}k_{i} = 0 \quad  or  \quad v=[\alpha_{1},\cdots ,\alpha_{s}]\begin{bmatrix}k_{1} \\ \cdots  \\ k_{s}\end{bmatrix} = 0
$$
只有零解
我们两边用 $\alpha_{i}$ 做内积：$\langle  \alpha_{i},v \rangle=0$，这是因为 $v$ 自身就是零向量。依据内积的线性性展开：
$$
\langle  \alpha_{i},\alpha_{i} \rangle = 0
$$
因此，$k_i =0$ 。取遍所有的 $i$，就可以证得任何一个 $k_{i}=0$
这也是正交基的好处之一：拿其中一个基向量点乘基向量的组合，会发现线性组合被“解耦”了

##### Example ： Fourier 级数
取 $V = \mathcal{L}^{2}([0,2\pi])$ , $F \in V$ 意味着 $f (\cdot):[0,2\pi]\rightarrow \mathbb{R}$，且平方可积。这是一个内积空间，因为我们可以定义函数 $f, g$ 的内积为：
$$
\langle  f,h \rangle = \int_{0}^{2\pi} f(t)g(t)dt
$$
显然，这已经成为一个无限维空间，我们给出一个标准正交组：
$$
\{ \frac{1}{\sqrt{2\pi}},\frac{1}{\sqrt{\pi}}\sin nx,\frac{1}{\sqrt{\pi}}\cos nx ,n=1,2,3,\cdots ,N\}
$$
显然，这个标准正交组满足性质：
- 单位性 $\langle  \frac{1}{\sqrt{2\pi}}, \frac{1}{\sqrt{2\pi}} \rangle = 1$，其余的也满足
- 正交性，容易验证（一一验证即可）
- 
因此，傅里叶级数实际上就是把一个函数向着一组函数空间上的正交基投影。其工程意义是用一组简谐波表示任意的波形：
$$
f(x) = C_{0}\frac{1}{\sqrt{2\pi}} + \sum_{k=1}^{N} a_{k} \frac{1}{\sqrt{2\pi}} \sin nx + \sum_{k=1}^{N} b_{k}\frac{1}{\sqrt{2\pi}}\cos nx
$$
向着一组正交基投影的好处是，求解所有系数的方程组可以被“解耦“——要求哪个基前面的系数，就把哪个基和方程组做内积，例如，我们要求 $C_{0}$
$$
C_{0}\langle \frac{1}{\sqrt{2\pi}} ,\frac{1}{\sqrt{2\pi}}  \rangle = \langle  \frac{1}{\sqrt{2\pi}} ,f \rangle
$$
求解其他系数也可以如此做


## 特殊的正交基——标准正交基

如果标准正交向量组同时又是 $n$ 维内积空间的一组基，那么我们称这个向量组为一组标准正交基。

##### Theorem Gram-Schmidt 正交化方法
如果设 $\alpha_{1},\alpha_{2},\cdots ,\alpha_{s}$ 是线性无关的向量组，我们可以通过某种方式使之正交化。例如，
$$
\beta_{2} = \alpha_{2}- ()\beta_{1}
$$
如何确定这个系数？考虑 $\alpha_{2}$ 在 $\beta_{1}$ 上的投影（消去 $\beta_{2}$），两边用 $\beta_{1}$ 内积 
$$
\langle  \beta_{1},\beta_{2} \rangle = \langle  \beta_{1},\alpha_{2} \rangle - \langle  \beta_{1},\beta_{1} \rangle()
$$
从而推出
$$
() = \langle  \beta_{1},\alpha_{2} \rangle / \langle  \beta_{1},\alpha_{2} \rangle
$$
之后单位化即可。
这保证了任意一个内积空间同构于一个标准内积空间

##### Example 勒让德多项式
$\mathcal{C}[-1,1]=\mathcal{C}([-1,1],\mathbb{R})$ ，考虑 $\mathcal{C}[-1,1]$ 中的向量组（一组函数）：$1, x^{1},\cdots ,x^{N}$，并不是正交组
我们要构造一个标准正交组：
$$g_{0}(x) = 1$$
$$
g_{1}(x) = x - g_{0}(x)[\ ]
$$
两侧对 $g_{0}(x)$ 内积，得到 $[\ ]=0$ ，同理，你可以递归地求解，从而得到所有的系数
这样的多项式被叫做 Legendre 多项式，在工程上被用作高精度的数值积分（更多是使用切比雪夫多项式）

接下来，我们仅仅将目光放在标准幺正空间上

## 标准正交基在标准幺正空间上的具体化

##### Def 幺正矩阵
$A \in \mathbb{C}^{n\times n}$ 被称为幺正矩阵（Unitary Matrix），如果 $A^{H}A=I$ 
其中，幺正矩阵的列向量就是标准幺正空间 $\mathbb{C}^{n}$ 中的标准正交基，$A=[a_{1},a_{2},\cdots a_{n}]$ 是标准正交组
也就是说
$$
(A^{H}A)_{ij} = \delta_{ij}
$$
其中，$\delta_{ij}$ 被称作 Kronecker 符号

##### Theorem Gram-Schmidt 在标准幺正空间上的具体化——QR Decomposition
将正交化的过程写成矩阵形式：
$$
a_{1}= b_{1}
$$
$$
a_{2}= b_{1}()+b_{2}
$$
$$
a_{n}= b_{1}()+\cdots +b_{n}
$$
可以看出，这是一个三角形。记 $A$ 是由原向量作为列向量组成的矩阵，$\tilde B$ 是由标准正交基组成的矩阵
$$
A = \tilde B \begin{bmatrix}||b_{1}|| & () & () & \cdots & ()  \\ 0 &\cdots  \\  \\ 0 & \cdots  \\ 0 & \cdots  &\cdots & \cdots &||b_{n}|| \end{bmatrix}
$$
其中，右侧是一个上三角阵

因此，**任意一个列满秩的矩阵，总可以分解成一个幺正矩阵和一个（唯一一个）上三角矩阵的乘积** ，这就是 QR 分解




































