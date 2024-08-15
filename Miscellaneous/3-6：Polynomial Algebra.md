#MathematicalPhysics 

我们令 $\mathcal{A}$ 是一种有单位元 $1$ 的满足结合律的代数，对于 $\mathcal{A}$ 中一个固定的元素 $a \in \mathcal{A}$，考虑能够写成下面这样的元素集合 $\mathcal{P}[a]$：
$$
p(a) = \sum_{k=0}^{\infty}  \alpha_{k} a^{k} \quad  \alpha_{k} \in \mathbb{C}
$$
并令其中只有有限项是非零的。这显然是关于 $a$ 的多项式。集合 $\mathcal{P}[a]$ 是带有单位元的可交换的代数，这被称为由 $a$ 生成的多项式代数。最高项前面系数为 1 的多项式被称为首一的，多项式中 $a$ 的最高次幂 $p$ 被称为其次数，使用 $\deg p$ 表示。$\alpha_{n}a^{n}$ 称为次数为 $n$ 的单项式。显然，$\{a_{k}\}$ 是 $\mathcal{P}[a]$ 的一组基底，如果 $p (a) = \sum_{k=0}^{]infty} \alpha_{k}a^{k}, q (a) = \sum_{j=0}^{\infty} \beta_{j} a^{j}$，那么：
$$
(p+q)(a) = \sum_{k} (\alpha_{k}+ \beta_{k})a^{k}\quad (pq)(a) = \sum_{i=0}^{\infty} \gamma_{i}a^{i}  , \gamma_{i} = \sum_{j+k= i} \alpha_{k} \beta_{j}
$$
此外，显然可以验证的关系是：
$$
\deg(p+q) \le \max(\deg p,\deg q) \quad \deg (pq) = \deg  p + \deg q
$$
我们将映射：$d : \mathcal{P}[a] \rightarrow  \mathcal{P}[a]$ 称为微分映射:
$$
da^{k}  = k  a^{k-1} \quad  da^{0}  = d1  = 0 
$$
>[!note]
>微分映射是 $\mathcal{P}[a]$ 上的导数。

由于 $d (pq) = d (p) q  +  p d(q)$，那么很容易得到 $d (q^{2}) = 2qd(q)$，进一步地，$d (q^{k}) = k q^{k-1} d(q)$。另外容易得到求导的链式法则：$d (p (q)) = p' (q) \cdot q'$。多项式的 $n$ 阶导数是：
$$
d^ {r}(a^{n}) = \dfrac{n!}{(n-r)!} a^{n-r} 
$$
利用这个，我们可以重写二项式定理：
$$
(a+b)^{n}  = \sum_{r=0}^{n} C_{n}^{r} a^{n-r}  b^{r}  = \sum_{r=0}^{n} \dfrac{1}{r!} d^{r}(a^{n}) b^{r}
$$
这里左侧是 $p(a+b)$ 中的某一项，因此取上式的线性组合可以给出 $p$ 的泰勒公式：
$$
p(a+b) = \sum_{r=0}^{n}  \dfrac{p^{(r)} (a)}{r!} b^{r}
$$
多项式 $p$ 的根满足 $p (a)=  \sum_{k=0}^{n} \eta_{k}\lambda^{k} =0$。代数基本定理指出，每一个系数在 $\mathbb{C}$ 中的多项式都可以满足以下分解：
$$
p(a) = \eta_{n} (a - \lambda_{1} 1)^{k_{1}} \cdots  (a - \lambda_{s} 1)^{k_{s}}
$$
注意每个括号里面都是一个一次多项式。那么这里 $\lambda_{i}$ 就是多项式的根，$\lambda_{i}$ 是根的重数。由于系数在 $\mathbb{C}$ 上的多项式具有这样的性质，我们称 $\mathbb{C}$ 是代数封闭的。但是，$\mathbb{R}$ 没有这个代数封闭的性质，但是仍然可以被分解为系数均在 $\mathbb{R}$ 中的一次和二次多项式的乘积。为了证明这一点，我们设 $\lambda$ 是多项式的复数根，容易注意到其复共轭 $\bar  \lambda$ 也是一个根，此外 $\lambda$ 和 $\bar \lambda$ 应当有相同的重数（将多项式取共轭即可看出这一点），从而把上面的式子中的括号中的项两两相乘得到：
$$
(a - \lambda_{m} 1)^{k_{m}} (a - \bar  \lambda_{m}1)^{k_{m}} = (a - 2 \gamma_{m} a + \gamma^{2}_{m} 1+ \xi ^{2}_{m}1)^{k_{m}} \quad \alpha_{m}^{2} < 4 \beta_{m}
$$
>[!note]
>一个实多项式 $p (a) = \sum_{k=0}^{n}  \eta_{k}a^{k}$ 有以下分解：$p (a) = \eta_{n} \prod_{i=1}^{r}(a - \lambda_{i} 1)^{k_{i}} \prod_{i=1}^{R} (a^{2} + \alpha_{j} a + \beta_{j} 1)^{K_{j}} ,\  \alpha_{j} ^{2} < 4 \beta_{j}$。其中 $\lambda_{i}$ 是不同的，$(\alpha_{j},\beta_{j})$ 也是不同的。另外，一个次数为偶数的实多项式至少有一个实根。








