#StochasticProcess 

在之前，我们已经提到过相关的计算方法。假定我们有随机变量 $X,Y$，那么它们的相关被定义为 $\mathrm{E}(XY)$，这是一种内积运算。现在，我们将会研究一个随机矢量 $X = (X_{1},\cdots, X_{n})^{T}$ 的分布（在 $n$ 维空间中的联合分布）或者直观的认识。一般情况下，这些随机变量的联合分布有点难以研究，所以我们想要获得一点直观的认识。我们试图研究这些随机变量之间的相关情况。显然我们可以从中找到 $\dfrac{1}{2}n(n-1)$ 个相关量，我们会把这些相关量排列成矩阵，令 $r_{ij} = \mathrm{E}(X_{i}X_{j})$ ，该矩阵 $R_{X}$ 有特点：
- 是对称矩阵
- 是正定的
今天，我们将会研究一些其他的内容。

## 去相关/白化
$R_{X}$ 一般不是对角阵。我们现在希望找到 $A$，令 $Y = AX$，希望 $\mathrm{E}(YY^{T})$ 是对角矩阵。这个问题是欠定的，但是我们知道相关矩阵有对称、正定等等性质，从而使得我们可以求解这个问题。考虑：
$$
R_{Y} = \mathrm{E}(YY^{T})  = \mathrm{E}(AXX^{T}A) = A \mathrm{E}(XX^{T}) A^{T} = AR_{X}A^{T}
$$
由于 $R_{X}$ 是对称矩阵，那么：
$$
R_{X}=  \sum \lambda_{k} U_{k} U_{k}^{T}
$$
其中，$U_{k}$ 是 $R_{X}$ 的本征矢量。我们记 $U = (U_{1}, U_{2},\cdots U_{n})$，那么显然 $R_{X} = U\Lambda U^{T}$ ，显然只要取 $A =U^{T}$ 即可。

## 主成分分析
主成分分析是在空间中找一些特征方向。我们最关心的一个特征方向是投影后新的随机变量具有最大方差的方向。给定矢量 $\alpha$，那么 $X$ 在 $\alpha$ 上的投影是：
$$
\mathrm{Proj}_{\alpha}(X) = \dfrac{\langle  \alpha,X \rangle}{\langle  \alpha,\alpha \rangle} \alpha
$$
我们现在要最大化方差，也就是：
$$
\mathrm{E}|\text{Proj}_\alpha(X)|^{2}=  \mathrm{E}\left(\dfrac{|\alpha^{T} X|^{2}}{||\alpha||^{4}}||\alpha||^{2} \right)= \dfrac{1}{||\alpha||^{2}} \mathrm{E}(\alpha^{T}X)^{2}= \mathrm{E}|\left(\dfrac{\alpha}{||\alpha||}\right)^{T}X|^{2}
$$
现在，求解优化问题：
$$
\max_{||\alpha||=1} \mathrm{E}(\alpha^{T}X X^{T}\alpha) = \max_{||\alpha||=1} \alpha^{T} R_{X} \alpha
$$
这是个经典优化问题，可以一眼看出结果，我们试着使用乘子方法解：
$$
L(\alpha,\lambda) = \alpha^{T} R_{X} \alpha - \lambda(\alpha^{T} \alpha-1 ) 
$$
从而：
$$
\nabla_{L} = 2 R_{X}\alpha - 2 \lambda  \alpha = 0  \Rightarrow R_{X} \alpha = \lambda \alpha
$$
那么，这些特征方向恰好就是 $R_{X}$ 的本征矢量方向。将这个结果代入上式，得到：
$$
\alpha^{T} R_{X} \alpha = \lambda \alpha^{T} \alpha = \lambda
$$
所以如果希望最大化上式，我们应当选择最大的本征值对应的本征矢量。这些本征矢量都是正交的，所以显然这些本征矢量能够起到“去相关”的作用。对于高维的情况，每次做优化时在之前的正交补空间上做。
主成分分析是一种重要的机器学习算法，例如，它在图像压缩上有巨大的作用，被称作“变换编码”。除此之外，其他的压缩方法还包括对视频进行“运动编码”和对文件进行的“熵编码”。

>[!EXAMPLE]
>假定有两个随机变量 $X_{1},X_{2}$，假定它们的均值为 0，方差为 1，$\mathrm{E}(X_{1}X_{2}) = \rho$，现在问第一个主成分与 $X_{1}$ 轴的夹角和 $\rho$ 是否有关。
>容易注意到 $R$ 的两个本征值是 $1 + \rho, 1 - \rho$，两个本征矢量是 $(1,1)$ 和 $(1,-1)$，那么就是没有关系。（主成分的方向与两个方差有关）

## 展开
根据之前的结果：
$$
Y = AX = U^{T} X \Rightarrow X = UY = \sum U_{k} Y_{k}
$$
在这里，我们分离了时间上的变化和随机性。$U_{k}$ 是相关矩阵的特征矢量，完全没有随机性，而 $Y_{k}$ 是有随机性的。同时，这里的 $U_{k}$ 是标准正交基，而 $Y_{k}$ 也是正交的。因此，这是一个“双正交”的展开，被称为 Karhunan-Loeve 展开。
我们可以将其推广到连续时间的随机过程上，令：
$$
X(t) = \sum_{k} \alpha_{k}  \phi_{k}(t) \quad (t \in I)
$$
这里的基底（$\phi$）和系数（$\alpha$）都是正交的。类比离散形式可以得到：
$$
\sum_{j}R_{X}(i,j) \phi_{k}(j) = \lambda_{k} \phi_{k}(j) \Rightarrow  \int_{I} R_{X}(t,s) \phi_{k}(s) ds = \lambda_{k} \phi_{k}(t)
$$

现在考虑我们的随机过程满足宽平稳的情况：
$$
\int_{I} R_{X}(t-s) \phi_{k}(s) ds = \lambda_{k} \phi_{k}(t)
$$
此时，可以说明上式中的 $\phi_{k}(t) = \exp(i \omega_{k}t)$，这很容易验证。直接代入并进行积分换元：
$$
\begin{align*}
\int_{I} R_{X}(t-s) \exp(i \omega_{k} s)ds \\
&= \left(\int_{I'} R_{X}(s') \exp(-i \omega_{k} s') ds'\right) \exp(i \omega_{k}t ) 
\end{align*}
$$
为了解决 $I'$ 依赖于 $t$ 的问题，我们先假设这个随机过程以 $T$ 为周期且宽平稳，那么 $\mathrm{E}|X (t+T) -  X (t)|^{2}= 0 \Rightarrow R_{X}(t+T) = R_{X}(t)$ 
$$
\begin{align*}
\int_{-\frac{T}{2}}^{\frac{T}{2}} R_{X}(t-s) \exp(i \omega_{k} s)ds \\
&= \left(\int_{-\frac{T}{2}}^{\frac{T}{2}} R_{X}(s') \exp(-i \omega_{k} s') ds'\right) \exp(i \omega_{k}t ) 
\end{align*}
$$
如果此时再令 $\omega_{k}= \dfrac{2k\pi }{T}$，那么括号里面的部分是常数，从而：
$$
\begin{align*}
\int_{-\frac{T}{2}}^{\frac{T}{2}} R_{X}(t-s) \exp(i \omega_{k} s)ds \\
&= \lambda_{k} \exp(i \dfrac{2 k \pi}{T}t)
\end{align*}
$$
根据刚才的 K-L 展开，我们就有：
$$
X(t) = \alpha_{k} \exp(i \dfrac{2k \pi}{T}t)
$$
这说明对于任意周期性宽平稳随机过程的 K-L 展开和傅里叶展开是一致的。我们之前在计算如下积分在 $T \rightarrow \infty$ 时 遇到困难：
$$
\alpha_{k} = \dfrac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}}  X(t) \exp\left(- i \dfrac{2 k \pi}{T}t\right)dt
$$
我们希望得到积分：
$$
X(t) = \int \hat X(\omega) \exp(i \omega t) d \omega 
$$
但是我们就写不出来。我们换一个写法：
$$
X(t) = \int \exp(i \omega t) d F_{X}(\omega)
$$
直观上，这个记号表示：$\int f (x) dg (x) = \sum_{k} f (x_{k}) (g(x_{k})  - g(x_{k-1} ))$ 。通过这样的记号，我们可以规避 $\hat X(\omega)$ 奇点的问题。根据前面提到的 $\alpha$ 的正交性，我们显然可以知道：
$$
\mathrm{E}(dF_{X}(\omega_{1}))\overline{(dF_{X}(\omega_{2}))} = 0 
$$
如果我们将 $F_{X}(\omega)$ 看作 $\omega$ 上的随机过程，那么 $dF_{X}$ 就是这个随机过程的小增量，那么这就是一个正交增量过程。我们还要说明另一个性质，也就是考虑 $\omega_{1} = \omega_{2}$ 的时候：
$$
\begin{align*}
R_{X }(t,s)\\
&= \mathrm{E}\left(\int \int \exp(i(\omega_{1} t- \omega_{2}s)) dF_{X}(\omega_{1}) \overline{dF_{X}(\omega_{2})}\right) \\
&= \int \int  \exp(i \omega_{1}s) \exp (i \omega_{2}t) \mathrm{E}(dF_{X}(\omega_{1}) \overline{dF_{X}(\omega_{2})})\\
&= \int \exp(i \omega(t-s)) \mathrm{E}|dF_{X}(\omega)|^{2}\\
&= \dfrac{1}{2\pi} \int \exp(i \omega(t-s)) S_{X}(\omega) d \omega 
\end{align*} 
$$
容易注意到：
$$
\mathrm{E}|dF_X (\omega)|^{2} = \dfrac{1}{2\pi } S_{X}(\omega) d \omega
$$
我们用这一套方法再来看看随机信号通过线性系统：
$$
Y(t) = \int_{-\infty}^{+\infty} h(t-s) X(s)ds 
$$
那么：
$$
\begin{align*}
Y(t) &= \int h(t-s) \left(\int \exp(i \omega s )dF_{X}(\omega)\right)ds\\
&= \int \left(\int h(t-s) \exp(i \omega s )ds \right)dF_{X}(\omega)\\
&= \int \exp(i \omega t ) \left(\int_{-\infty}^{+\infty} h(s') \exp(- i \omega s ) ds\right)dF_{X}(\omega)\\
&= \int \exp(i \omega t) H(\omega) dF_{X }(\omega)\\
&= \int dF_{Y}(\omega) \exp(i \omega t)
\end{align*}
$$
从而，我们找到了 $X$ 和 $Y$ 的**谱过程**的关系：
$$
dF_{Y}(\omega) = H(\omega) dF_{X}(\omega)
$$

通过 KL 展开，我们可以在宽平稳过程和 $\exp(i \omega t)$ 这样的函数之间找到一种对应。对于随机过程，我们有均方距离 $\mathrm{E}|X(t) - X(s)|^{2}$，而在函数空间中我们也可以建立一种距离：
$$
\int |\exp(i \omega t) - \exp(i \omega s) |^{2} S_{X}(\omega) d \omega
$$
这两种距离是相等的。这说明我们在随机过程和确定性函数之间找到了一种等距同构，一个随机过程和一个复指数函数相互对应。














