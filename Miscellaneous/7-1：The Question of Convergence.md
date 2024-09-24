#MathematicalPhysics 

之前我们看过了有限维向量空间，现在我们要考虑无限维向量空间上的事情。有一件事情使得有限维向量空间和无限维向量空间上的研究出现本质不同：在有限维向量空间上，我们只考虑有限个数的和（比如在计算范数的时候）。但是，在无穷维向量空间上，我们就要考虑无穷个数的和了！

我们来看几个关键的问题：首先是收敛性的定义。谈到收敛，就要谈到距离。在有限维内积空间上，例如 $\mathbb{C}^{n},\mathbb{R}^{n}$，我们可以引入所谓 $p-$ 范数：
$$
||a||_{p} = \left(\sum_{i=1}^{n} |\alpha_{i}|^{p}\right)^\frac{1}{p}
$$
让我们先从柯西列的定义开始：一个向量序列 $\{| a_{i} \rangle\}_{i=1}^{\infty}$ 被称为是柯西列，如果：
$$
\lim_{i \rightarrow  \infty  , j \rightarrow \infty } ||a_{i} - a_{j}|| = 0
$$
我们定义一个完备的向量空间是一个装备了范数的线性空间，该线性空间 $\mathcal{V}$ 中的每一个柯西列的极限都在 $\mathcal{V}$ 中，也就是说，存在向量 $| a \rangle \in  \mathcal{V}$，使得：
$$
\lim_{i \rightarrow  \infty } ||a_{i}  -a|| =  0
$$
显然，$\mathbb{R}$ 和 $\mathbb{C}$ 都是完备的，但是 $\mathbb{Q}$ 不是完备的，因为：
$$
\lim_{k \rightarrow\infty } \left(1 + \dfrac{1}{k}\right)^{k}  \rightarrow e
$$
我们现在考虑在一个有限维向量空间 $\mathcal{V}_{N}$ 中选择一组基底 $| e_{k} \rangle$，并且将 $| a_{i} \rangle, | a_{j} \rangle$ 在基底上的投影系数记为 $\alpha_{k}^{(i)},\alpha_{k}^{(j)}$，那么很容易知道：
$$
||a_{i} - a_{j}||^{2} = \sum_{k=1}^{N} |\alpha_{k}^{(i)} - \alpha_{k}^{(j)} |^{2}
$$
如果 $| a_{i} \rangle$ 是柯西列，那么上式必须趋于 0. 从而对于每个 $k$，$\alpha_{k}$ 都是柯西列。由于 $\mathbb{C}$ 的完备性，存在 $\alpha_{k} \in \mathbb{C}$，使得 $\lim_{n \rightarrow \infty } \alpha_{k}^{(n)} = \alpha_{k}$，我们很容易证明 $| a \rangle = \sum_{k} \alpha_{k} | e_{k} \rangle$ 是序列 $| a_{i} \rangle$ 的极限。这样我们就证明了重要结论：
>[!note]
每一个有限维的复（实）向量空间对于其上内积诱导的范数是完备的。

我们现在展示一下为什么“有限”这个词很重要。考虑函数序列 $\{f_{k} \} \in \mathscr{C}^{0}(-1,1)$  ：
$$
f_{k}(x) = \begin{cases}
 1 \quad  &\dfrac{1}{k} \le x  \le 1 \\
\dfrac{kx+1}{2} \quad & -\dfrac{1}{k} \le x \le \dfrac{1}{k} \\ 
0 \quad &  -1 \le x \le  - \dfrac{1}{k}
\end{cases}
$$
我们定义内积：
$$
\langle  f |g  \rangle =  \int_{-1}^{+1} f^{\star} (x) g(x) dx
$$
很容易证明 $f_{k}(x)$ 确实是柯西列，但是它的极限却是阶跃函数！（下图中是可视化）
![[Pasted image 20240901005043.png]]

对于一个有限维向量空间，它包含所有的 $| a_{i} \rangle$，它就必然包含所有的 $\sum_{i=1}^{n} \alpha_{i} | a_{i} \rangle$，但是对于无穷维的不是这样的，因为我们会遇到无限求和。我们首先要指定一个范数，再使用这个范数定义收敛，我们还要要求这个空间对于这种范数是完备的。总之，我们将装备了范数的完备向量空间称为巴拿赫空间。因为范数往往是由内积自然诱导出的，因此我们将装备了内积的完备向量空间称为希尔伯特空间，通常用 $\mathcal{H}$ 表示。
我们显然可以在 Hilbert 空间内选择一组完备的正交向量组 $| e_{i} \rangle$，那么对于任意向量 $| f \rangle$ 我们都可以展开成：
$$
| f_{n} \rangle = \sum_{i} \langle  e_{i} | f \rangle | e_{i} \rangle
$$
根据柯西-施瓦茨不等式，对任意两个向量 $| f \rangle,| f_{n} \rangle$ 有：
$$
|\langle  f | f_{n} \rangle|^{2} \le  \langle  f | f \rangle \langle  f_{n} | f_{n} \rangle = \langle  f | f \rangle \left(\sum_{i=1}^{n} |f_{i}|^{2}\right)
$$
而直接计算 $f$ 和 $f_{n}$ 的内积会得到：
$$
\langle  f |f_{n}  \rangle = \sum_{i=1}^{n} f_{i} \langle  f |e_{i}  \rangle = \sum_{i=1}^{n} f_{i} f_{i}^{\star} = \sum_{i=1}^{n} |f_{i}|^{2}
$$
联立以上两式，我们就得到了所谓帕塞瓦尔不等式：
$$
\sum_{i=1}^{n} |f_{i}|^{2} \le  \langle  f |f  \rangle
$$
或者将以上有限和的情况推广至无限和的情况：
>[!note]
设 $| e_{i} \rangle$ 为希尔伯特空间中的无穷正交向量组，$| f \rangle \in \mathcal{H}$，在各个向量上的展开系数是 $f_{i} = \langle  e_{i} | f \rangle$，那么我们有贝塞尔不等式 $\sum_{i=1}^{\infty} |f_{i}|^{2} \le  \langle  f | f \rangle$

贝塞尔不等式显然是要求无限求和的收敛性，然而它自身显然不保证这一点。我们需要声明一下希尔伯特空间中基底的完备性。我们称希尔伯特空间中的一组正交向量 $\{| e_{i} \rangle\}$ 是完备的，如果 $\mathcal{H}$ 中与所有 $\{| e_{i} \rangle\}$ 正交的向量只有零向量。此时，$\{\vec e_{i}\}$ 才被称为 $\mathcal{ H}$ 的一组基底。
在此之后，我们提到的希尔伯特空间都有可数个基底。那么我们有：
>[!note] 希尔伯特空间中的几个等价结论
>设 $\{| e_{i} \rangle\}$ 是希尔伯特空间 $\mathcal{H}$ 中的正交向量序列，那么以下几个结论是等价的：
>- $\{|e_{i}  \rangle\}$ 完备
>-  $| f \rangle = \sum_{i=1}^{\infty} | e_{i} \rangle \langle  e_{i} |  f\rangle$，对于 $\forall | f  \rangle \in \mathcal{H}$
>-  $\sum_{i=1}^{\infty} | e_{i} \rangle \langle e_{i} | = \mathbf{1}$
>- $\langle  f |g  \rangle = \sum_{i=1}^{\infty} \langle f | e_{i} \rangle \langle  e_{i} | g \rangle$
>- $||f||^{2} = \sum_{i=1}^{\infty} |\langle  e_{i} | f \rangle|^{2}$

现在，我们就有：
$$
||f||^{2} = \langle  f | f \rangle = \sum_{i=1}^{\infty} |\langle  e_{i} |  f\rangle|^{2}  = \sum_{i=1}^{\infty} |f_{i}|^{2}
$$
也就是说，帕塞瓦尔不等式和帕塞瓦尔等式都是讨论了一个函数与自己的内积和它在一个正交向量组上展开系数的平方之间的关系，它们的区别在于这个正交向量组是否完备。我们再把完备性关系放在这里：
$$
1 = \sum_{i}| e_{i }\rangle \langle e_{i} |
$$



