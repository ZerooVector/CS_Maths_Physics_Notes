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
$\alpha_1,\cdots,\alpha_n$ 是 $V$ 中的一个基，构造映射 $\sigma : V \rightarrow \mathbb F^n$，使得 $\forall v \in V, v\mapsto [k_1,\cdots,k_n]^T$ ，也就是将线性空间 $V$ 中的一个向量映射成它的坐标（一个新的向量）。我们来验证映射满足满射和单射：
- $\forall k \in \mathbb F^n$，取 $v = \sum_i \alpha_ik_i$，这使得任意一个像都存在一个原像，从而该映射是满射
- 假设存在 $v'$，若 $v'$ 的坐标也是 $k$，则必定有 $v' = \sum_i \alpha_ik_i$ ，（利用线性无关）从而 $v' = v$，从而一组坐标只能找到 $V$ 中一个向量与之对应，该映射是单射

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










