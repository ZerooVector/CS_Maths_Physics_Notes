#StochasticProcess 

本课程的主讲老师是张颢，来自清华大学。本课程的先修课程包括微积分、线性代数、概率论与数理统计。

 ```python 
#python test
plt.plot([1,2,3],[4,5,6])
plt.show()
```

随机过程研究一组随机变量，我们关心随机变量之间的相互关联、相互影响。我们已知的随机变量之间的关联方式实际上只包含三种： ^08b1c7
- 相关（线性关联）
	- 时域分析->相关函数->高斯过程
	- 频域分析->谱
- 马尔可夫性质->高斯过程
	- 离散时间
	- 连续时间
- 鞅
	- 鞅停止定理
	- 金融应用

## 随机变量的 “相关”关系
假定我们有 $x,y$ 两个随机变量，要考察它们之间的关系，最好的考察方法是 $f(x,y)$
$$
f(x,y) = \dfrac{\partial^{2} }{\partial x \partial y} F(x,y) \quad F(x_{0},y_{0}) = P(x \le x_{0},y \le y_{0})
$$
有些时候，我们发现 $f_{X,Y} (x, y) = f_{X}(x)f_{Y}(y)$，这个时候我们将 $X,Y$ 称为是独立的，在其余情况下，$X,Y$ 之间就发生了关联。
有一种情况，在 $X$ 增大时，$Y$ 的均值也在增大。此时，我们可以认为 $X,Y$ 之间已经产生了线性的关联。 ^06fca1
```python
plt.figure(figsize = (4,3))
x = np.random.normal(0,5,(50,1))
y = x * 2 + np.random.normal(0,3,(50,1))
coefficients = np.polyfit(x.flatten(), y.flatten(), 1) 
y_pred = np.polyval(coefficients, x)
plt.scatter(x,y,marker = "+",color = "royalblue")
plt.plot(x, y_pred, color="tomato", linewidth=2)
plt.title("Linear Correlation")
plt.show()
```

现在，我们就来讨论这种线性关联。我们希望能建立 $Y = \alpha X$ 这样的线性关联，但是这肯定不可能，因为均方误差 $\mathrm{E}(Y - \alpha X)^{2}$ 几乎不可能为 0. 那么什么样子的 $\alpha$ 才是合适的呢？最合适的 $\alpha$ 就是使得 $\min_{\alpha} \mathrm{E}(Y - \alpha X)$ 的，显然有
$$
\alpha_{opt}  = \dfrac{\mathrm{E}(XY)}{\mathrm{E}(X^{2})}
$$
分母上面，反映了随机变量 $X,Y$ 之间的关联。我们将 $\mathrm{E}(XY)$ 称为两个随机变量的“相关”（注：“相关”运算也有其他的定义，例如 $\mathrm{E}((X - \mathrm{E}(X))(Y - \mathrm{E}(Y))) = \mathrm{E}(XY) -\mathrm{E}(X)\mathrm{E}(Y)$，实际上中心化之后只是差了一个常数，没有什么本质的区别），而我们所说的“不相关”就是 $E(XY)=0$，但是，“不相关”与“独立”相比，显然“独立”的条件更强。
>[!EXAMPLE] 不独立且不相关的例子
>假定 $\theta \sim [0,2 \pi], X = \cos (\theta), Y = \sin (\theta)$，$X,Y$ 二者不相关，但是不独立。注意到 $E (X) = \int_{0}^{2\pi} \sin \theta \dfrac{1}{2\pi} d\theta = 0$，与此同时可以相应计算得出 $\mathrm{E}(Y)=0$, $\mathrm{E}(XY) = 0$。

我们接下来希望给出一个几何的看法：相关可以看作两个随机变量的某种内积。内积主要具有以下性质：
- 对称性 $\langle  X, Y \rangle = \langle  Y,X \rangle$
- 非负性 $\langle  X, X \rangle \ge 0$，且等号仅在 $X=0$ 时取到
- 双线性 $\langle  X,\alpha Y + \beta Z \rangle = \alpha \langle  X, Y \rangle + \beta \langle  X,Z \rangle$，或者 $\langle  \alpha X + \beta Y ,Z\rangle= \alpha \langle  X, Z \rangle + \beta \langle  Y,Z \rangle$
显然，我们的相关运算也几乎满足这些特性。唯一一个不太满足的地方是 $\mathrm{E}(X)^{2} = 0 \Rightarrow P(X=0)=1$，但是一般无法推出 $X=0$.我们在线性代数中知道：
$$
\cos (x,y) = \dfrac{\langle  x,y \rangle}{\sqrt{\langle  x,x \rangle,\langle  y,y \rangle}}
$$
这个定义和相关系数可以对应起来。我们可以把随机变量看作某个线性空间里面的矢量。那么，两个随机变量间的夹角：
$$
\cos (X,Y) = \dfrac{\mathrm{E}(XY)}{\sqrt{\mathrm{E}(X)^{2} \mathrm{E}(Y)^{2}}}
$$
余弦位于 $[-1,+1]$ 之内是由柯西不等式保证的，证明很简单。
>[!HINT] 柯西不等式的证明
>构造 $g (\lambda) = \langle  \lambda x + y \rangle = \lambda^{2}\langle  x, x \rangle + 2\lambda \langle  x, y \rangle + \langle  y,y \rangle$，容易发现这对于 $\lambda$ 是一个二次不等式，利用其判别式小于等于 0 即可得证。对于不同的内积定义，柯西不等式可以有不同的形式（例如一个很常见的积分形式）

现在，我们再倒回来使用几何视角求解上面的 $\min \mathrm{E} (Y - \alpha X)^{2}$ 的问题。
![[Ep.1 Intro to Stochastic Process 2024-01-12 15.15.05.excalidraw]]
把夹角用相关系数表示：
$$
\alpha X = ||Y|| \cos \theta \dfrac{X}{||X||} =\left( \dfrac{||Y||}{||X||} \cos \theta \right) X = (\dfrac{||Y||}{||X||} \dfrac{\mathrm{E}(XY)}{||X||\ ||Y||})X
$$
从而：
$$
\alpha_{opt}=  \dfrac{\mathrm{E}(XY)}{\mathrm{E}(X)^{2}}
$$

## 相关函数
在引入相关函数之前，我们就要引入随机过程。简单地来说，随机过程就是一组随机变量 $X(t)$。在一个随机过程上，我们可以定义相关函数（是一个二元函数）：
$$
R_{X}(t,s) = \mathrm{E}(X(t)X(s))
$$
它显然有一些特点：
- 对称性：$R_{X}(t, x) = R_{X}(s,t)$
- 柯西不等式 $|R_{X}(t, s)| \le (R_{X}(t,t) R_{X}(s,s))^{\frac{1}{2}}$
我们现在希望做一些假设，将其变成一元函数。在这里，我们要引入“平稳性”的概念，它代表随机过程的某一种统计性质随着时间的发展而保持不变。显然，我们可以定义许多种“平稳性”。接下来，我们首先定义“宽平稳”：
- 随机过程的均值 $\mathrm{E}(X (t)) = m$
- 相关函数 $R_{X}(t, s) = R_{X}(t+D, s+D) , \forall D$
显然，第二条会更加重要。有了第二条性质，我们可以对相关函数做出如下的简化：
$$
R_{X}(t,s) = R_{X}(t-s) = R_{X}(\tau)
$$


>[! EXAMPLE] 振幅调制
>如果 $X (t) = A (t) \cos (2\pi f_{0}t + \theta)$，其中 $A(t)$ 是随机变量，$\theta \sim U(0,2\pi)$，且 $A$ 与 $\theta$ 相互独立。
>首先计算均值：
> $$\mathrm{E} (X (t)) = \mathrm{E}(A(t))\mathrm{E}(\cos(2\pi  f_{0} t + \theta))= \mathrm{E}(A(t)) \int_{0}^{2\pi}\dfrac{1}{2\pi}\cos(\cdot)d\theta = 0$$
> 然后计算相关函数（利用积化和差拆开三角函数的乘积，很容易得到）：
> $$R_{X}(t,s) = \mathrm{E}(A(t) A(s))= \mathrm{E}(A(t)A(s)) \dfrac{1}{2} \cos(2\pi f_{0} (t-s))$$
> 显然，如果 $A(t)$ 是宽平稳的，那么整体的调制信号就是宽平稳的。

>[!EXAMPLE] 随机电报
>随机电报信号是在任意时刻只能取 1 或者-1 的信号。在长度为 $t-s$ 的时段中，变化 $k$ 次的概率服从泊松分布：
> $$P(k) = \dfrac{(\lambda(t-s))^{k}}{k!}\exp(- \lambda (t-s))$$
> 我们来给出其相关函数：
> $$E(X(t)X(s)) = 1 \cdot P_{+} + (-1) \cdot P_{-}$$
> 如果 $t,s$ 时刻信号的值同号，则代表信号翻转了偶数次，否则反之：
> $$P_{+} = \sum_{\text{k is even}} P (k) \quad P_{-} = \sum_{\text{k is odd}} P(k)$$
> 利用基本的事实：$\sum_{k=0}^{\infty} \dfrac{(\lambda (t-s))^{k}}{k!} = \exp(\lambda(t-s))$，现在如果我们只把其中的偶数次项拿出来，只需使用简单的技巧（加一个负号），容易得到：
> $$P_{+} = \dfrac{1}{2}[1 + \exp(-2 \lambda(t-s))] \quad P_{-} = \dfrac{1}{2}[1- \exp(-2 \lambda(t-s))]$$
> 从而：$$R_{x}(t, s) = \exp(-2\lambda(t-s))$$
> 于是，这是一个宽平稳的随机过程。

我们发现，宽平稳广泛地存在于现实中。==必考==


