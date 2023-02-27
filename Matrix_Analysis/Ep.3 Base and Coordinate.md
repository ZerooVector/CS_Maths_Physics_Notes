#MA 

![[Ep.3 Base and Coordinate 2023-02-26 08.25.55.excalidraw]]
我们讨论了如何判断向量空间是有限维的——存在极大无关组；以及维数的唯一性：极大无关组中向量的个数是恒定的。

## 向量组的基
##### Theorem 维数的唯一性
设 $\alpha_1,\cdots,\alpha_m$; $\beta_1,\cdots,\beta_n$ 是 $V$ 的两个基，则 $m=n$。
这个定理与极大线性无关组中个数一样的不同是，现在是在全空间的无数个向量中任意挑选向量。要想证明这个定理，我们可以将无限的问题变成有限的问题：将 $\alpha$ 和 $\beta$ 组合起来，成为新的向量组，分别说明 $\alpha$ 和 $\beta$ 是新向量组的极大无关组即可。
- 无关性由基本身的特性保证
- 极大性等价于生成性。由于基可以生成全空间的元素，自然也可以生成母组中的元素。

##### Theorem 基（坐标系）实现了抽象线性空间到标准线性空间的一一对应
有一个映射 $\sigma : S_1 \rightarrow S_2$，我们说它是一一对应的，那么：
- 这个映射既是满射也是单射
	- $\forall s_2 \in S_2,\exists s_1\in S_1,\sigma (s_1) = s_2$，对于像集中的任意元素，都有一个原像（满射）
	- $if \ \sigma (s_1) = \sigma (s_1'), then\  s_1 = s_1'$，像集中的任意一个元素只有一个原像（单射）
- 从方程的观点，若 $t\in S_2, s\in S_1$，$\sigma(s)=t$ 有且仅有一个解
- 这个映射是可逆的，$\exists \tau : S_2\rightarrow S_1 , \tau \sigma$ 是 $S_1$ 上的恒等映射，且 $\sigma\tau$ 是 $S_2$ 上的恒等映射。这里，$\tau$ 是 $\sigma$ 的逆映射。
$\sigma$ 是一一对应的，这意味着 $S_1$ 与 $S_2$ 两个集合同构。
接下来，我们证明基实现了这个一一对应。
##### PF
---
==后面的补充==
这里得先证明是映射：要证明 $\sigma: A\rightarrow b$ 是一个映射，先得证明其满足两个要求：
- $\forall a \in A ,\exists b \in B$ 与之对应（任何一个抽象向量是不是有坐标？这其实是可表示性的要求，任何一个向量都可以在一组基下被表示出来）
- 与 $a$ 对应的 $b$ 唯一，这由基的线性无关性保证。假设 $v = \sum_i\alpha_ik_i= \sum_i \alpha_ik_i'$，那么我们移项得到 $\sum_i \alpha_i(k_i-k_i') =0$，从而 $k_i = k_i'$ 

---
$\alpha_1,\cdots,\alpha_n$ 是 $V$ 中的一个基，构造映射 $\sigma : V \rightarrow \mathbb F^n$，使得 $\forall v \in V, v\mapsto [k_1,\cdots,k_n]^T$ ，也就是将线性空间 $V$ 中的一个向量映射成它的坐标（一个新的向量）。我们来验证映射满足满射和单射：
- $\forall k \in \mathbb F^n$，取 $v = \sum_i \alpha_ik_i$，这使得任意一个像都存在一个原像，从而该映射是满射
- 假设存在 $v'$，若 $v'$ 的坐标也是 $k$，则必定有 $v' = \sum_i \alpha_ik_i$ ，（利用线性无关）从而 $v' = v$，（这就是不证自明的，一组坐标只能有一个原像）从而一组坐标只能找到 $V$ 中一个向量与之对应，该映射是单射

##### Example $\mathbb F^n$ 的标准基和一般基
标准基：$e_1  = [1, 0,\cdots, 0]^T, e_2 = [0, 1,\cdots,0]$，以此类推
- 线性无关性：若 $\sum_i e_ik_i = 0$，则必然有 $k_i = 0$
当然也可以使用线性方程组的方式进行描述：$Ix = 0$，显然只有零解
- 可表示性：$\forall v \in \mathbb F^n$，$v = [c_1, c_2,\cdots,c_n]^T$，只要取 $v = \sum_i e_ic_i$ 即可（这个向量的坐标就是它自己）
从线性方程组的思维看，$Ix = v$ 显然有解
我们将 $\mathbb F^n$ 称为标准线性空间，是因为，任何一个线性空间中的向量总可以映射成 $\mathbb F^n$ 中的一组坐标。

一般基：$n$ 个向量要想成为一组基，需要它们的秩为 $n$，也就是它们线性无关。接下来，我们需要证明这组基的可表示性：
也就是说，对于任意向量 $v$，由基排成的矩阵 $A$ 总可以使得：$Ax=v$ 有非零解。显然，该方程组的系数矩阵的秩等于增广矩阵的秩，所以有非零解。
**注**：线性方程组的求解问题就是求右端向量的坐标的问题。

##### 补充 ：有限维和无限维的问题
例子：函数空间
$$
\mathbb F[x] = \left\{f|f\in \mathcal F(\mathbb F,\mathbb F),f\ is \ a\ polynomial \right\}
$$
这意味着定义域是 $\mathbb F$，值域也是 $\mathbb F$ 的多项式的全体组成的空间
$$
\mathbb F_n[x] = \left\{polynomials\ which\ <n\ orders,coeffs\   are\ from\ \mathbb F\right\}
$$
简而言之，$\mathbb F[x]$ 就是多项式的全体；$\mathbb F_n[x]$ 就是不高于 $n$ 阶的多项式全体
下面我们说明，将数域 $\mathbb F$ 取成实数域 $\mathbb R$，那么 $\mathbb R_n[x]$ 是 $n$ 维的，但 $\mathbb R[x]$ 不是有限维的。
首先，我们可以找到一个向量组（实际上是一组多项式），构成 $\mathbb R[x]$ 的基。显然，选法可以是 $x\cdot x^0; 1\cdot x,\cdots 1\cdot x^{n-1}$
- 首先来验证可表示性 $\forall f \in \mathbb R_n[x]$，则 $f = a_0+a_1x+a_2x^2+\cdots +a_{n-1}x^{n-1}$，显然可以写成各个基的线性组合。$f = [1, x,\cdots, x^{n-1}] \times [a_0,a_1,\cdots,a_{n-1}]^T$
- 如果 $a_0\times1+a_1x+a_2x^2+\cdots+a_{n-1}x^{n-1}=0$，注意这里的 $0$ 是 $0$ 函数（函数空间中的 $0$），意味着将任意的 $x$ 代入多项式，都必须有左右相等。特别地，现在代入 $n$ 个 $x$ 的特定值，$x = 1, 2,\cdots,n$，我们将其写成矩阵的形式：$f = [1, x,\cdots, x^{n-1}] \times [a_0, a_1,\cdots, a_{n-1}]^T = 0$ ，现在代入 $n$ 个值，将其排成矩阵的形式：
$$
\begin{bmatrix}
1^0 &1^1&\cdots &1^{n-1}\\
\cdots & \cdots&\cdots&\cdots\\
n^0& n^1 &\cdots &n^{n-1}
\end{bmatrix}
\begin{bmatrix}
a_0 \\
\cdots\\
a_{n-1}
\end{bmatrix}
= 
\begin{bmatrix}
0\\
\cdots\\
0
\end{bmatrix}
$$
左侧这个矩阵的行列式不为 0（Vandermonde determinant）, 那么意味着这个线性齐次方程组只能有 0 解，因此，若希望 $f=0$，只能取 $a_i=0$，因此，各个基是线性无关的。

接下来，我们取任意向量组 $f_1, f_2,\cdots,f_N$，说明它们都不能成为 $\mathbb R[x]$ 的基，这只需要找到一个多项式不能写成它们的线性组合。
记 $d_i$ 为多项式 $i$ 的次数，取 $d = \max\{d_1,\cdots,d_N\}$，现在证明 $x^{d+1}$ 不能被这一个向量组表示。否则，$x^{d+1} = \sum_i a_if_i (x) = b_0x_0+\cdots+b_dx^d$
于是，$b_0x_0+b_1x+\cdots+b_dx^d-x^{b+1}=0$，根据与上面相同的步骤，可以证明这个式子的系数必须都是 0 才能成立，这与 $-1\not =0$ 矛盾，因此多项式的全体不是有限维的！










