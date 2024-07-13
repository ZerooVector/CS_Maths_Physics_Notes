#StochasticProcess 

我们首先回顾微积分中的经典概念：
我们定义序列 $x_{n} \rightarrow x$，那么任取 $\forall \epsilon > 0 ,\exists N ,\forall n > N ,|x_{n} -x| \le \epsilon$ 。极限是一种逼近，因此距离的定义是极限定义的核心。这里我们采用的是欧氏距离。我们也可以对 $n$ 维空间中的点列定义极限：若 $x_{n} \in  \mathbb{R}^{n}$，$\forall \epsilon > 0, \exists N > 0 ,\forall n > N, ||x_{n}  - x|| \le \epsilon$。

在随机微积分中，我们研究的对象不是确定的数或者点，而是一组**随机变量**，随机变量是从样本空间映射到实数轴的函数。因此，我们在考察随机变量的极限的时候，我们实际上是在考察函数的极限。我们之前对于函数极限的定义是：$f_{n}(x) \rightarrow f(x)$，这种收敛其实有很多种：
- 逐点（Pointwise）收敛：$\forall x \in A , \forall \epsilon > 0 ,\exists N, \forall n > N ,|f_{n}(x) - f (x)| \le \epsilon$
- 一致（Uniformly）收敛：$\forall x \in A, \forall \epsilon > 0 ,\exists N ,\forall x \in  A, \forall n > N ,|f_{n}(x) - f (x)| \le \epsilon$
- 积分 （Integration）收敛：$||f_{n} - f|| = \int_{A}||f_{n}(x) - f (x)||^{2} dx \rightarrow 0$

## 随机变量的极限
### 均方收敛
我们现在开始讨论随机变量的收敛。记 $\{X_{n}\}$ 是一组随机变量，我们首先使用均方距离：
$$
d(X,Y) = \sqrt{\mathrm{E}|X-Y|^{2}}
$$
我们称 $X_{n}$ 均方收敛到 $X$，如果：
$$
\forall \epsilon> 0,\exists N > 0,\forall  n > N , d(X_{n},X) \le \epsilon
$$
我们研究一下它的性质：均方极限有可加性： $X_{n} \rightarrow X, Y_{n} \rightarrow Y \Rightarrow X_{n} + Y_{n} \rightarrow X+Y$
要验证这一点，只需利用三角不等式得到
$$
d(X_{n} + Y_{n} ,X+Y) \le d(X_{n},X) + d (Y_{n},Y) 
$$
均方极限也有性质：$X_{n}Y_{n} \rightarrow XY$，容易验证：
$$
||X_{n}Y_{n} - XY|| = ||X_{n}Y_{n} - X_{n}Y+X_{n}Y-XY|| \le ||X_{n}Y_{n} -X_{n}Y|| + ||X_{n}Y - XY|| \le ||X_{n}||\ ||Y_{n} - Y|| +||y||\ ||X_{n} -X|| \rightarrow 0 
$$
同样可以验证柯西收敛准则：
$$
||X_{n}-X_{m}|| \rightarrow 0 \ (n,m \rightarrow \infty) \Rightarrow X_{n} \rightarrow X
$$

### 几乎处处 (Almost Surely)收敛
我们将
$$
P(\{\omega \in  \Omega|X_{n}(\omega) \rightarrow X(\omega)\}) = 1
$$
称为 $X_{n}$ 几乎处处收敛到 $X$。举个例子，假如 $\Omega$ 中是 $[0,1]$ 上的实数，每次从 $\Omega$ 中等概率地抽取一点 $x$，那么随机变量 $X_{n} = x^{n}$ 就几乎处处收敛到 $X = 0$（直观上讲， $n \rightarrow \infty$ 时，$X_{n} = 0$ 的概率为 1。）

我们希望研究一下它和均方收敛之间的关系。实际上，二者之间没有关系。我们来给出反例。假定 $\Omega = [0,1]$，样本点出现的概率 $P ([c, d]) = d-c$。我们构造随机变量序列 $X_{n}$，使得 $X_{n}$ 几乎处处收敛到 0，但是没有均方收敛到 0.
我们令 $X_{1} = a$，$X_{2}$ 在 $[0,\dfrac{1}{2}]$ 取值为 $2a$，在后半部分取值为 0，$X_{3}$ 在 $[0,\dfrac{1}{4}]$ 取值为 $4a$，其余部分取值为 0……以此类推。容易注意到：
$$
\mathrm{E}||X_{n}(\omega) - 0||^{2} = \int_{\Omega}  |X(\omega)|^{2} P(d \omega) = a
$$
但是，在直观上，我们似乎觉得几乎处处收敛比均方收敛要强一点。只要规定 $X_{n}$ 有界，那么几乎处处收敛就包含了均方收敛。

我们给出另一个构造。我们令 $X_{1}$ 在 $[0,\dfrac{1}{2}]$ 取值为 $1$，在后半部分取值为 0； $X_{2}$ 在 $[\dfrac{1}{2},1]$ 取值为 1，前半部分取值为 0；$X_{3}$ 在 $[0,\dfrac{1}{4}]$ 取值为 1，后半部分取值为 0；$X_{4}$ 在 $[\dfrac{1}{4},1]$ 上取值为 1，前半部分取值为 0……以此类推。根据定义可以显然判断，$X_{n}$ 不是几乎处处收敛的，而它却均方收敛。

### 依概率收敛 (Convergence in Probability)
我们称 $\forall \epsilon$，
$$
P(\{\omega \in \Omega|\ |X_{n}(\omega) - X(\omega)| \ge  \epsilon \}) \rightarrow 0
$$
为 $X_{n}$ 依概率收敛到 $X$。依概率收敛比几乎处处收敛要弱。我们给出证明：
首先，说明几乎处处收敛一定可以推出依概率收敛。我们改写几乎处处收敛的写法，它等价于：
$$
P(\{\omega  : X_{n}(\omega) \not \rightarrow X(\omega)\}) = 0
$$
我们知道，$x_{n} \not \rightarrow x$ 的逻辑表述是：$\exists \epsilon > 0 , \forall N , \exists n > N,|x_{n} - x| \ge \epsilon$ ，根据此，我们把上式等价地改写成：
$$
P(\bigcup_{\epsilon > 0} \bigcap_{N} \bigcup_{n > N} \{\omega:|X_{n}(\omega) -X(\omega)| \ge \epsilon\} )  = 0
$$
在这里，我们将“存在”重新表述成集合的并，“任取”重新表述成集合的交。上式中将 $\epsilon$ 固定， 可以推出：
$$
P(\bigcap_{N} \bigcup_{n>N} \{\omega:|X_{n}(\omega) - X(\omega)|  \ge \epsilon \}) = 0
$$
假定 $B_{N}=\bigcup_{n>N} \{\omega:|X_{n}(\omega) - X(\omega)|\}$，注意到 $B_{N+1}\subseteq B_{N}$ ，上式等价于：
$$
\lim_{N \rightarrow \infty} P(\bigcup_{n>N}\{\omega:|X_{n}(\omega) - X(\omega)|  \ge \epsilon \}) = 0
$$
这显然已经涵盖了依概率收敛的定义，也就是 ：
$$
\lim_{N \rightarrow \infty} P(\{\omega:|X_{N+1}(\omega) - X(\omega)|  \ge \epsilon \}) = 0
$$
 
接下来说明为什么不能反着推。如上文中所述：
>我们给出另一个构造。我们令 $X_{1}$ 在 $[0,\dfrac{1}{2}]$ 取值为 $1$，在后半部分取值为 0； $X_{2}$ 在 $[\dfrac{1}{2},1]$ 取值为 1，前半部分取值为 0；$X_{3}$ 在 $[0,\dfrac{1}{4}]$ 取值为 1，后半部分取值为 0；$X_{4}$ 在 $[\dfrac{1}{4},1]$ 上取值为 1，前半部分取值为 0……以此类推。

这是一个经典反例。说明结束。

均方收敛为什么可以推出依概率收敛？这是因为切比雪夫不等式。很显然。

### 依分布收敛 (Convergence in Distribution)
$X_{n}$ 的分布函数为 $F_{X_{n}}(x)$，$X$ 的分布函数为 $F_{X}$，那么我们称 $X_{n} \rightarrow X$ 如果在 $F_{X}$ 的连续点 $F_{n}(x) \rightarrow F_{X}(x)$。这是一种很弱的收敛。
举个例子。假设 $X \sim N (0,1), X_{n} = (-1)^{n} X$。显然 $X_{n}$ 依分布收敛到 $X$。我们现在说明：如果 $X_{n}$ 依概率收敛到 $X$，那么它一定依分布收敛到 $X$。

我们知道：
$$
\begin{align*}
F_{n}(x)\\
&= P(X_{n} \le x)\\
&= P(X_{n} \le x,X>y ) +P(X_{n}\le x ,X \le y) \quad \text{假设}y>x \\
&\le P(|X_{n}-X| >y-x) + P(X < y)\\ 
\end{align*}
$$
此时在两边同时取极限。
$$
\lim_{n} \sup F_{n}(x) \le F_{X}(y)
$$
我们现在希望构成：
$$
F_{X}(z) \le  \lim_{n} \inf F_{n}(x) \le  \lim_{n} \sup F_{n}(x) \le F_{X}(y) 
$$
右边已经有了。要得到左边，只要将上面的流程再进行一遍，但是将 $F_{X}$ 替换成 $F_{n}$。然后我们就自然证成。

总结来看，几乎处处收敛最强，强于依概率收敛，又强于依分布收敛。三者的应用是强大数定律、弱大数定律、中心极限定理。此外补充一点：均方收敛可以推出依概率收敛。


## 大数定律
接下来我们介绍这些“收敛”定义的实际应用。一个最重要的应用就是大数定律。假定有随机变量序列 $X_{1}, X_{2},\cdots,X_{n}$ 独立同分布。大数定律希望研究 $\dfrac{1}{n} \sum X_{k}$ 的性质。人们发现，在 $n \rightarrow \infty$ 的时候，$\dfrac{1}{n} \sum X_{k}$ 的随机性会“逐渐消失”，这个和趋近于 $\mathrm{E}(X_{k})$。
根据收敛的方式不同，大数定律分为两种：
- 强大数定律：几乎处处收敛
- 弱大数定律：依概率收敛

我们先看看均方收敛：
$$
\begin{align*}
\mathrm{E}|\dfrac{1}{n}\sum X_{k} - \mathrm{E}X_{k}|^{2}\\
&= \dfrac{1}{n^{2}} \mathrm{E}|\sum_{k}(X_{k} - \mathrm{E}X_{k})|^{2}\\
&= \dfrac{1}{n^{2}} \sum_{k} \mathrm{E} |X_{k} - \mathrm{E}X_{k}| ^{2} + \dfrac{2}{n^{2}} \sum_{i \not =  j} \mathrm{E}((X_{i} - \mathrm{E}X_{i})(X_{j} - \mathrm{E} X_{j}))\\\
&= \dfrac{1}{n} \mathrm{Var}(X_{k})
\end{align*}
$$
因此，若 $X_{k}$ 方差有限，那么 $\dfrac{1}{n} \sum X_{k}$ 一定均方收敛到 $\mathrm{E}X_{k}$。

### 弱大数定律
我们先介绍切比雪夫不等式：
$$
P(|X| \ge a ) \le \dfrac{\mathrm{E}|X|^{2}}{a^{2}}
$$
这是概率论中一大堆“收缩”不等式的一个。这很容易证明：
$$
\mathrm{E}|X|^{2} = \int_{\mathbb{R}} x^{2}f_{X}(x) dx = \left(\int_{|x| \ge a} + \int_{x < a} \right)x^{2}f_{X}(x)dx \ge \int_{|x| \ge a} x^{2}f_{X}(x)dx \ge \int_{|x| \ge a} a^{2} f_{X}(x) dx 
$$
这就完成了证明。从切比雪夫不等式，我们很容易得到：
$$
P(|X-\mathrm{E}X| \ge a) \le \dfrac{\mathrm{Var}(X)}{a^{2}}
$$
所以很显然：
$$
P\left(\left|\dfrac{1}{n}\sum_{k} X_{k} - EX_{k}\right| \ge \epsilon\right) \le \dfrac{1}{\epsilon^{2}} \dfrac{1}{n} \mathrm{Var}(X_{k})
$$
因此弱大数定律成立。

### 强大数定律
我们直接说明处处收敛也是正确的，暂时不给出证明（甚至不需要方差有限的条件）。


## 中心极限定理
如果 $X_{1},\cdots X_{n}$ 是均值为 0、方差为 1 的独立同分布随机变量，那么：
$$
\dfrac{1}{\sqrt n} \sum_{k} X_{k}  \rightarrow N(0,1)
$$
这里，随机变量的和除以 $\sqrt{N}$ 时，得到了高斯分布；如果除以 $N$，就只能得到均值了。那么，在中间一定有一个因子使得随机性完全消失，这个因子是 $\sqrt{n \ln \ln n}$

我们给出一个证明，这个证明来自李雅普诺夫。我们定义随机变量 $X$ 的特征函数 
$$\Phi_{X}(\omega) = \mathrm{E}(\exp(i \omega X))= \int f_{X}(\omega) \exp(i \omega x)dx$$
也就是概率密度的傅里叶逆变换。我们现在考察 $\mathrm{E}(X_{k}) = 0 ,\mathrm{Var}(X_{k}) = 1$ 的一组独立同分布的随机变量，我们计算一个特征函数：
$$
\Phi \dfrac{\sum_{k} X_{k}}{\sqrt n } = \prod_{k} \mathrm{E}\left(\exp\left(i \dfrac{\omega}{\sqrt n }X_{k}\right)\right) = \left(\Phi_{X_{1}}\left(\dfrac{\omega}{\sqrt n }\right)\right)^{n}
$$
我们展开上面的特征函数：
$$
\Phi_{X}\left(\dfrac{\omega}{\sqrt n}\right) = \mathrm{E}\left(1 + i \dfrac{\omega}{\sqrt n}X + \dfrac{1}{2} \left(i \dfrac{\omega}{\sqrt n}  X \right)^{2}\right)
$$
注意：必须展开到二阶项！我们最终打算向基本极限靠拢，因此我们必须使得 $\dfrac{1}{n}$ 这一项暴露出来（考虑基本极限的形式），使得高阶项变成 $o\left(\dfrac{1}{n}\right)$（这样高阶项对极限的结果没有影响），同时，$\mathrm{E}(X^{2})$ 是有东西的，而 $\mathrm{E}(X) = 0$，这也必须要求我们展开到二阶项。那么显然有：
$$
\Phi_{X}\left(\dfrac{\omega}{\sqrt n }\right)= 1 - \dfrac{\omega^{2}}{2n}
$$
那么我们就可以得到：
$$
\Phi \dfrac{\sum_{k} X_{k}}{\sqrt n } = \left(1 - \dfrac{ \omega^{2}}{2n}\right)^{n} = \exp\left(- \dfrac{\omega^{2}}{2}\right)
$$
显然得到了高斯函数的傅里叶变换。我们可以使用相同的方法导出弱大数定律。
























