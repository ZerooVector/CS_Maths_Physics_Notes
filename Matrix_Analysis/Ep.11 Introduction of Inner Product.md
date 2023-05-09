#MA  

## 内积和欧几里得空间
##### Def 欧几里得空间 （Euclidean Space）
设 $V$ 是 $\mathbb{R}$ 上的线性空间，映射 $\tau : V\times V \rightarrow \mathbb{R}$ 称作 $V$ 的一个内积 (Inner Product)，为了方便起见，记 $\tau (v_{1},v_{2})$ 为 $<v_{1},v_{2}>$，我们将其称为内积，当且仅当
- 对称性：$<v_{1},v_{2}> = <v_{2},v_{1}>$
- 线性性：$<v_{1},v_{2}k+v_{3}l> = <v_{1},v_{2}>k+<v_{1},v_{3}>l$
- 正定性：对任意 $v \not = 0$，$<v,v>\  >0$ 

比如说，如果取 $v_{1},v_{2}$ 都是一维的，那么如果将内积定义为 $\langle  v_{1},v_{2} \rangle=v_{1}v_{2}$，那么在固定 $v_{1}$ 时，内积就是 $v_{2}$ 的线性函数
注意 : $\vec 0$ 与任意向量的内积都为 0，这可以由内积的线性性直接得到。

**如果线性空间上可以定义内积，我们就将这个线性空间称为内积空间，有限维的内积空间称为欧几里得空间**  

##### Def 内积的“双线性”
当我们将内积的任意一个分量固定时，内积对另一个分量就是线性的。
这是显然的，由内积的对称性保证。

##### Example 
$$
\langle  3u_{1}+ \frac{1}{2}u_{2} ,5v_{1}+6v_{2}  \rangle = 15 \langle  u_{1},v_{1} \rangle + () \langle  u_{1},v_{2} \rangle + () \langle  u_{2},v_{1} \rangle + () \langle  u_{2},v_{2} \rangle
$$
也就是说，两个向量组的线性组合的内积，可以由两个向量组中元素两两之间的内积来生成

##### Example $\mathbb{R}^{n}$ 上的标准内积
对于映射 $\tau : \mathbb{R}^{n} \times \mathbb{R}^{n} \rightarrow \mathbb{R}$，有：
$$\langle  x, y \rangle = x^{T}y  = \sum_{i}x_{i}y_{i} $$
这样的内积称为标准内积。

##### PF 
- 交换律：显然成立
- 线性性：这可以通过初等的运算加以证明
- 正定性：显然成立

##### Example $\mathbb{R}^n$ 空间上的非标准内积
我们仅仅以 $n=2$ 的情况来举例，考虑：
$$
\langle  x,y \rangle = x_{1}y_{1}+ \frac{1}{2} x_{1}y_{2}+ \frac{1}{2} x_{2}y_{1}+x_{2}y_{2}
$$
验证：交换律是否得到满足：
换位置：
$$
\langle  y,x \rangle = y_{1}x_{1}+ \frac{1}{2} y_{1}x_{2} + \frac{1}{2}y_{2}x_{1}+y_{2}x_{2}
$$
显然，交换律成立

将 $x$ 固定：注意到：
$$
\langle  x,y \rangle = (x_{1} + \frac{1}{2} x_{2})y_{1}+\left(\frac{1}{2} x_{1}+x_{2}\right)y_{2}  = c_{1} y_{1}+c_{2}y_{2} 
$$
显然是线性的

$x$ 与自身的内积：
$$
\langle  x,x \rangle = x_{1}^{2}+x_{1}x_{2}+x_{2}^{2}
$$
由于系数矩阵正定，所以这个结果肯定是>0 的。
实际上，每一个正定的二次型都对应一个内积。

##### Example 函数空间的内积
考虑定义在 $[a,b]$ 区间，输出在 $\mathbb{R}^n$ 的函数，即函数空间 $\mathcal{F}(I,\mathbb{R}^{n})$ ，函数空间中的每一个元素都是 $F = [f_{1}(x),f_{2}(x),\cdots ,f_{n}(x)]$ ，那么，定义：内积：
$$
\langle  f ,g \rangle = \int_{a}^{b}f^{T}(t)g(t)dt
$$

## 复内积和酉空间（幺正空间, Unitary Space）

在这一部分中，我们将研究复数域上的线性空间，在这样的空间上，内积是 $\tau : V\times V \rightarrow C$ 的映射，复内积和实内积满足几乎相同的要求，唯一的不同是，交换顺序将得到复内积的共轭。定义了复数内积的空间被称为复内积空间，有限维的复内积空间称为幺正空间。

##### Theorem 复内积对第一个变元是共轭线性的
$$
\langle  v_{1}k+v_{2}l , u \rangle = \bar  k \langle  v_{1},u \rangle + \bar l \langle  v_{2},u \rangle
$$
这个定理可以通过计算 $(\langle  u,v_{1}k+v_{2}l\rangle)'$ 来得到。注意：**复内积只是对第一个变量是共轭线性的，对第二个变量是完全线性的！** 

##### Example 标准幺正空间上的内积
$$
\langle  x,y \rangle = \bar x^{T}y
$$

##### Theorem 线性组合内积的矩阵表示
$$
\langle  \sum_{i=1}^{s} \alpha_{i}k_{i} ,\sum_{j=1}^{t} \beta_{j}l_{j} \rangle = [\bar k_{1},\bar k_{2},\cdots ,\bar k_{s}] [\langle  \alpha_{i},\beta_{i} \rangle] [l_{1},l_{2},\cdots ,l_{t}]^{T} 
$$
注意，中间的矩阵在数据科学上叫做 Gram Matrix，在物理上则被称作 Metric Tensor 
以后看到 $x^{T}Ay$ 这种形式，就要怀疑是不是内积的一个矩阵表示。

##### Def  向量组的 Gram 矩阵/基的度规张量
记 $\beta_{1},\beta_{2},\cdots ,\beta_{s}$ 是内积空间的一个向量组，那么矩阵
$$
G(\beta_{1},\cdots ,\beta_{s}) = [\langle  \beta_{i},\beta_{j} \rangle]
$$
称为向量组 $\beta_{i}$ 的 Gram 矩阵。基向量组的 Gram 矩阵则被称为这组基的度规张量
根据前面的例子，只要知道了一个向量组的 Gram 矩阵，由该向量组张成的子空间中任意两个向量的内积都可以确定。知道了基向量的度规张量，实际上我们可以求出空间中线元的表示。
因此，空间中的内积由度规唯一决定。

##### Theorem Gram 矩阵的性质
- Hermite 性：$\bar G^{T} = G$ 
- 非负定性：$\forall z \in \mathbb{C}^{s},\bar z^{T}Gz \ge 0$ 
- $G$ 正定，等价于 $\beta_{i}$ 线性无关
- $G$ 的秩与向量组 $\beta$ 的秩相等

##### PF 
(1) $G$ 的 $i$ 行 $j$ 列元素为 $\langle  \beta_{i},\beta_{j} \rangle$ ，$G^{H}$ 的 $i$ 行 $j$ 列元素则是 $(\langle  \beta_{j},\beta_{i} \rangle)'$，由内积的性质，显然得证。
(2) $G$ 的非负定性质由 $G$ 的对称性保证：
$$z^{H}Gz = [\bar z_{1},\cdots ,\bar z_{s}]G[z_{1},\cdots ,z_{s}]^{T}$$
根据上面的推导，这可以看作两个向量的内积：
$$
z^{H}Gz = \langle  \beta_{1}z_{1}+\beta_{2}z_{2},\cdots ,+\beta_{s}z_{s},\cdot  \rangle
$$
这显然是大于 0 的。
(3) 如果 $G$ 正定，那么对于任意的 $z$ 都有 $\sum_{i}\beta_{i}z_{i} \not = 0$，这就是 $\beta_{i}$ 线性无关的定义
注意：性质 3 提供了判断抽象向量组线性无关的具体做法，尤其是对于函数空间中的向量

##### Example 几何空间化为内积空间
在几何空间中定义内积：
$$
\langle  \alpha ,\beta  \rangle =||\alpha|| \cdot ||\beta || \cdot \cos \theta
$$
那么，这里 Gram 矩阵的含义：
$$
G = \begin{bmatrix} \langle  \alpha,\alpha \rangle & \langle  \alpha,\beta \rangle \\  \langle  \beta,\alpha \rangle  & \langle  \beta,\beta \rangle\end{bmatrix}
$$
其行列式：
$$
\det (G) = ||\alpha ||^{2}||\beta||^{2}(1-\cos ^{2} \theta) = ||\alpha||^{2}||\beta||^{2}\sin ^{2}\theta 
$$
对应于 $\alpha,\beta$ 张成的平行四边形面积的平方。这可以被推广到三维上。


















