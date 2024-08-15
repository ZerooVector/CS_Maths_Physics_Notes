#StochasticProcess 

我们在上一节课种聊到了高斯分布的线性性。我们现在假设 $X_{1},\cdots X_{n} \sim N(\mu,\sigma^{2})$ ，让我们求解其样本均值和方差。一个令人惊讶的事实是，在上述条件下，$\bar X,\bar S$ 是独立的。注意到：
$$
\begin{align*}
(n-1) \bar S &=  \sum_{k}(X_{k} - \bar X)^{2} \\
&= \sum_{k}(X_{k}^{2} - 2 X_{k} \bar X  +  (\bar X)^{2})\\
&= \sum_{k} X_{k}^{2} - n(\bar X)^{2}\\

\end{align*}
$$
观察到式子中有一个 $\sum_{k} X_{k}^{2}$ 项，我们希望对 $X_{k}$ 进行一个正交变换，保持 $\sum_{k}X_{k}^{2}$ 不变，我们还希望这个线性变换得到的结果（至少是某个分量）与样本均值有关系。我们会选取这样的矩阵：
$$
A = \begin{bmatrix}\dfrac{1}{\sqrt n} & \dfrac{1}{\sqrt n } & \cdots  & \dfrac{1}{\sqrt n} \\  \cdots & \cdots & \cdots & \cdots  \\ \cdots & \cdots & \cdots & \cdots  \\ \cdots & \cdots & \cdots & \cdots  \\ \cdots & \cdots & \cdots & \cdots  \\ \cdots & \cdots & \cdots & \cdots  \\ \end{bmatrix}
$$
考虑 $Y =  AX$，那么 $Y_{1} = \sqrt n  \bar X,\sum_{k} Y_{k}^{2}  = \sum_{k} X_{k}^{2}$，且 $Y_{1},\cdots ,Y_{n}$ 独立（这是因为 $Y$ 的协方差矩阵是对角阵）。我们回到上面的计算：
$$
\begin{align*}
(n-1) \bar S  &= \sum_{k}X_{k}^{2} - n(\bar X)^{2} \\
&=  \sum_{k}Y_{k}^{2} - Y_{1}^{2}\\
 &= \sum_{k=2}^{n}Y_{k}^{2}
\end{align*}
$$
利用 $Y_{k}$ 之间的互相独立性，立刻得到 $\sum_{k=2}^{n} Y_{k}^{2}$ 与 $Y_{1}$ 独立。我们证明了想要的结论（这个结论被称为 Cochram 定理）。同时，我们验证了样本方差只有 $n-1$ 个自由度的结论（我们没有减去真实的均值，而是只减去了从样本中估计的均值，这导致自由度的减少。）


我们介绍高斯分布的另一个性质。假定 $X_{1},X_{2}$ 服从联合高斯分布，$X_{1} \in \mathbb{R}^{m}, X_{2} \in \mathbb{R}^{n}$，将联合高斯分布的均值和方差分块：
$$
(X_{1},X_{2}) \sim N(\begin{bmatrix}\mu_{1} \\  \mu_{2}\end{bmatrix}, \begin{bmatrix}\Sigma_{11}& \Sigma_{12}  \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix})
$$
我们希望考察 $X_{1}|X_{2}$ 和 $X_{2}|X_{1}$ 是不是高斯分布。（这一段不打算记笔记，因为在 LATEX 中计算所需时间太长）
![[Pasted image 20240211110006.png]]
这里，我们不能使用生成函数这个工具，必须实际计算其中矩阵的逆！
![[Pasted image 20240211110829.png]]
![[Pasted image 20240211112012.png]]

从而我们可以找到均值和协方差阵：
$$
X_{2}|X_{1} \sim N(\mu_{2} + \Sigma_{21} \Sigma_{11}^{-1}(x_{1} - \mu_{1}) ,\Sigma_{22} - \Sigma_{21}\Sigma_{11}^{-1} \Sigma_{12} )
$$
我们接下来找几个特殊情况来研究一下。假定我们的 $X_{1},X_{2}$ 都是一维的，那么：
$$
\mathrm{E}(X_{2}|X_{1}) = \mu_{2} + \dfrac{\sigma_{21}}{\sigma_{11}}(x_{1} - \mu_{1})
$$
其中，$\dfrac{\sigma_{21}}{\sigma_{11}}$ 是一个投影，我们将条件期望写成了两部分：一部分是 $X_{2}$ 自身的期望，另一部分是 $X_{1}$ 对 $X_{2}$ 的影响。这个“影响”就是将 $X_{1}$ 投影到 $X_{2}$ 上，是一个线性的“修正”。
$$
\mathrm{Var}(X_{2}|X_{1}) = \sigma_{22} - \dfrac{\sigma_{12}^{2}}{\sigma_{11}} 
$$
因此，在给了条件以后，$X_{2}$ 的不确定度是降低的。
我们再看一看不相关的情况。此时：
$$
\mathrm{E}(X_{2}|X_{1}) = \mu_{2} \quad \mathrm{Var}(X_{2}|X _{1})= \sigma_{22} 
$$

>[!EXAMPLE]
> $X_{1}, X_{2} \sim N(0,1)$ 独立，计算 $\mathrm{E}(X_{1} + X_{2} | X_{1} - X_{2})$
> 首先很容易注意到：$(X_{1}+X_{2}, X_{1}-X_{2}) \sim N(0,2I)$
> 那么直接套用上面的公式直接可以得到结果为 0. 这是显然的，因为 $X_{1}+X_{2},X_{1}-X_{2}$ 互相独立。


>[!EXAMPLE]
> $X_{1}, X_{2} \sim N(0,1)$ 独立，计算 $\mathrm{E}((X_{1} + X_{2})^{2} | X_{1} - X_{2})$
> 一种简单的做法是利用上面的结论，发现 $(X_{1}+X_{2})^{2}$ 和 $X_{1}-X_{2}$ 是独立的，从而
> $$\mathrm{E}((X_{1} + X_{2})^{2} | X_{1} - X_{2}) = \mathrm{E}(X_{1}+X_{2})^{2} = \mathrm{Var}(X_{1}+X_{2}) = 2$$
> 一种有趣的看法是将 $X_{1}+X_{2}|X_{1}-X_{2}$ 的分布作为一个新的随机变量 $Y$ 的分布，那么上面实际上是要计算 $\mathrm{E}(Y^{2})$（注意，条件肯定是不需要被平方的！被平方的是前面随机变量的部分。我们仍然在 $X_{1}-X_{2}$ 的条件下计算 $(X_{1}+X_{2})^{2}$），所以：
> $$\mathrm{E}(Y^{2}) = \mathrm{Var}(Y) + \mathrm{E}(Y)^{2}$$

>[!EXAMPLE]
>计算 $\mathrm{E}((X_{1}+X_{2})^{4}|X_{1}-X_{2})$
>考虑一个升级版的问题。如果 $Y \sim N(0,\sigma)$，计算 $\mathrm{E}(Y^{n})$。显然我们只需要计算 $\mathrm{E}(Y^{2k})$：
> $$\begin{align*}\mathrm{E}(Y^{2k}) &= \dfrac{1}{2 \pi \sqrt \sigma}  \int y^{2k} \exp\left(- \dfrac{y^{2}}{2 \sigma^{2}}\right)d y\\
&= - \sigma^{2} \dfrac{1}{2 \pi \sqrt \sigma} \int  y^{2k-1} d\left(\exp\left(- \dfrac{y^{2}}{2 \sigma^{2}}\right)\right)\\ &= (2k-1) \sigma^{2}\dfrac{1}{2 \pi \sqrt \sigma} \mathrm{E}(Y^{2k-2}) \end{align*}$$
经过递推容易得到：
$$\mathrm{E}(Y^{2k}) = (2k-1)!! (\sigma^{2})^{k}$$

类似的问题还有很多，都可以通过相似的套路解决。我们直接给出一个困难的。
>[!EXAMPLE]
>计算 $\mathrm{E}(\cos(3X_{1}+2X_{2})|2X_{1}+3X_{2})$
>我们仍然可以构造一个变量 $Y$，但是我们需要先给出其分布。在前面我们已经知道：
> $$3X_{1}+2X_{2} \sim N(\dfrac{12}{13}(2X_{1}+3X_{2}),13 - \dfrac{12^{2}}{13})$$
> 然后我们要考虑 $Y \sim N(\mu,\sigma^{2})$，问 $\mathrm{E}(\cos(Y))$。这个无法通过积分得到，只能使用特征函数。注意到：
> $$\mathrm{E}(\cos Y) = \dfrac{1}{2}\mathrm{E}(\exp(jY) + \exp(-jY)) = \dfrac{1}{2}(\Phi_{Y}(1) + \Phi_{Y}(-1)) = \exp(- \dfrac{1}{2}\sigma^{2})\cos(\mu)$$
>这告诉我们特征函数可以用来做一些奇妙的操作，比如在这里求一些奇怪的期望。
>

最后我们再给出一个例子。
>[!EXAMPLE]
> $X \sim N (\mu,\Sigma_{X}), Y = BX+Z, Z \sim N(0,\sigma^{2}I)$，且 $Z$ 与 $X$ 独立。（1）判断 $X,Z$ 和 $X,Y$ 是否服从联合高斯分布？（2）给出 $X|Y$ 的分布。（这实际是贝叶斯，通过观测求出系统的状态）
> 显然：
> $$f_{X,Z}(x,z) = \exp(- \dfrac{1}{2}((x-\mu)^{T},z^{T})\text{diag}(\Sigma_{X}^{-1},\sigma^{2} I)(x-\mu,z)^{T})$$
> 显然，$X,Z$ 服从一个联合高斯分布。容易注意到 $X,Y$ 由 $X,Z$ 线性变换得到，所以它们也服从联合高斯分布。
> 完成（1）中的判断后，直接代入公式。其中：
> $$\Sigma_{XY }= \mathrm{E}[(X - \mu_{X})(BZ-B\mu_{X}+Z)^{T }]= \Sigma_{Z}B^{T}$$ 
> $$\Sigma_{YY }= \mathrm{E}[(BX- B\mu_{X})(BX - B\mu_{X}+Z)^{T}] = B\Sigma_{X}B^{T} + \Sigma_{Z}$$ 
> 将以上两者代入公式即可。















