#StochasticProcess 

今天来了解一下高斯分布、高斯过程和非线性的结合会带来什么。

## 平方系统：利用生成函数
我们找一个高斯过程 $X(t)$ 进行平方，看看会得到什么。也就是：
$$
Y(t) = X^{2}(t)
$$
假定 $X(t)$ 是高斯过程，那么现在问 $Y(t)$ 是什么过程。
显然：
$$
\mathrm{E}(Y(t)) = R_{X}(t,t) 
$$
如果 $X(t)$ 宽平稳，那么 $\mathrm{E}(Y (t)) = R_{X}(0)$
现在求：
$$
\begin{align*}
R_{Y}(t,s) &=  \mathrm{E}(Y(t),Y(s)) \\
&= \mathrm{E}(X^{2}(t) X^{2}(s))\\

\end{align*}
$$
现在我们算不下去了，我们考虑一个简单的问题。我们考虑 $\mathrm{E}(X_{1}X_{2}X_{3}X_{4}) \sim N(0,\Sigma)$，我们希望考虑：
$$
\begin{align*}
\mathrm{E}(X_{1}X_{2}X_{3}X_{4}) &= \int x_{1}x_{2}x_{3}x_{4} f(x_{1},x_{2},x_{3},x_{4}) dx
\end{align*}
$$
直观上，这个东西的结果可能只依赖于 $\Sigma$ 的各个元素。考虑到在概率密度里面 $\Sigma$ 是以逆的形式出现的，而特征函数里面 $\Sigma$ 是以其本体出现的。看起来特征函数可能更简单一点，所以我们试着使用特征函数计算这个矩。考虑到特征函数的定义：
$$
\Phi_{X}(\omega) = \mathrm{E}(\exp(i(\sum \omega_{i}X_{i})))
$$
注意到：
$$
\mathrm{E}(X_{1}) = \dfrac{1}{i}\dfrac{\partial }{\partial \omega_{1}} \Phi_{X}|_{\omega_{i}= 0 }
$$
同理：
$$
\mathrm{E}(X_{k}^{\alpha})= \dfrac{1}{i^{\alpha}}\dfrac{\partial^\alpha }{\partial \omega_{k}^{\alpha}}\Phi_{X}|_{\omega_{i}= 0 }
$$
同理：
$$
\mathrm{E}(\prod_{i}X_{i}^{\alpha_{i}}) = \dfrac{1}{\prod_{i} i^{\alpha_{i}}} \dfrac{\prod_{i} \partial^{\alpha_{i}} }{ \prod_{i} \partial \omega_{i}^{\alpha_{i}}}\Phi_{X}|_{\omega_{i}= 0 }
$$
经过推导，可以得到：
$$
\mathrm{E}(X_{1}X_{2}X_{3}X_{4})= \mathrm{E}(X_{1}X_{2}) \mathrm{E}(X_{3} X_{4}) + \mathrm{E}(X_{1}X_{3}) \mathrm{E}(X_{2} X_{4}) + \mathrm{E}(X_{1}X_{4}) \mathrm{E}(X_{2} X_{3})
$$
可以找规律进行推广，推广到 $2n$ 阶的情况。

回到之前的推导：
$$
\begin{align*}
\mathrm{E}(X^{2}(t) X^{2}(s)) &=  \mathrm{E}(X^{2}(t)) \mathrm{E}(X^{2}(s)) + 2 (\mathrm{E}X(t)X(s))^{2}\\
&=  R_{X}^{2}(0) + 2R_{X}^{2}(t-s)
\end{align*}
$$
注意：这里时域上的平方就是频域上自身和自身卷积。


## 符号函数：计算一个巨大的积分
我们首先计算期望。显然有：
$$
\begin{align*}
\mathrm{E}(Y)  &=  P(X\ge 0) - P(X < 0) \\
&= 
\end{align*}
$$
这个很容易计算。在高斯分布的均值为 $0$ 的时候，显然期望为 0.

下面计算相关函数：
$$
\begin{align*}
R_{Y}(t,s) &= P(Y(t)Y(s)=1) - P(Y(t)Y(s)= - 1)\\
&= 2 P(Y(t)Y(s)=1)  - 1 \\
&= 2P(X(t)X(s)>0)-1 \\
&= 
\end{align*}
$$
这个概率算起来可不简单！下面我们来计算它（在 1、3 象限积分）：
$$
\begin{align*}
\left(\int_{-\infty }^{0} \int_{-\infty }^{0} + \int_{0}^{\infty}\int_{0}^{\infty}\right)   \dfrac{1}{2 \pi \sigma_{1} \sigma_{2} \sqrt{1 - \rho^{2}}} \left(- \dfrac{1}{2(1- \rho)^{2}} \left(\left(\dfrac{x}{\sigma_{1}}\right)^{2} + \left(\dfrac{x_{2}}{\sigma}\right)^{2}  -2 \rho (\dfrac{x_{1}}{\sigma_{1}})(\dfrac{x_{2}}{\sigma_{2}})\right)\right)
\end{align*}
$$
我们需要完成这个积分：
换元，令：
$$
x_{1}' = \dfrac{x_{1}}{\sigma_{1}} \quad x_{2}' = \dfrac{x_{2}}{\sigma_{2}}
$$
之后可以令：
$$
x_{1}'' = u+v \quad x_{2}'' = u-v
$$
来消除交叉项。之后令：
$$
u' = \dfrac{u}{\sqrt{1 + \rho}} \quad v' = \dfrac{v}{\sqrt{1 + \rho}}
$$
之后使用极坐标进行积分：
$$
u' = r  \cos  \theta  \quad v' = r \sin \theta
$$
![[Pasted image 20240216154542.png]]
这个积分的最终结果是：
$$
I =\dfrac{2}{\pi} \arctan (\dfrac{1+ \rho}{1 - \rho})
$$
（上面计算过程的系数有一点错误）注意到：
$$
\rho = \dfrac{R_{X}(t-s)}{R_{X}(0)}
$$
那么可以直接看出宽平稳的特征。利用万能公式可以对上面的积分结果进一步化简。
![[Pasted image 20240216160024.png]]
整理上述结果，得到：
$$
P(X(t)X(s) \ge 0) = \dfrac{1}{2} + \dfrac{1}{\pi}  \arcsin \rho  
$$
这一结果被称为“反正弦律”。在直观上，这一结果也可以很好地和图形进行对应。

## 高斯过程通过非线性系统的一般处理方式
现在我们考虑一般的情况。考虑非线性系统 $g(x_{1},x_{2})$，其中 $(X_{1}, X_{2}) \sim N(0,0,\sigma_{1}^{2} , \sigma_{2}^{2},\rho)$，我们希望计算 $\mathrm{E}(g)$。注意到：
$$
\begin{align*}
\dfrac{\partial \mathrm{E}(g)}{\partial \rho} &=  \sigma_{1} \sigma_{2} \mathrm{E}\left(\dfrac{\partial^{2} g}{\partial x_{1}\partial x_{2}}\right)
\end{align*}
$$
我们先使用一下它。首先，根据我们现在处理的问题：
$$
g(x_{1},x_{2}) = \mathrm{sign}(x_{1}) \mathrm{sign}(x_{2})
$$
求导得到：
$$
\dfrac{\partial^{2}g }{\partial x_{1} \partial x_{2}} = 4 \delta(x_{1}) \delta(x_{2})
$$
求期望：
$$
\mathrm{E}\left(\dfrac{\partial^{2}g }{\partial x_{1} \partial x_{2}}\right)=  \int \int \dfrac{4 \pi \delta(x_{1})\delta(x_{2})}{2 \pi \sigma_{1} \sigma_{2} \sqrt{1 - \rho^{2}}} \left(- \dfrac{1}{2(1- \rho)^{2}} \left(\left(\dfrac{x}{\sigma_{1}}\right)^{2} + \left(\dfrac{x_{2}}{\sigma}\right)^{2}  -2 \rho \left(\dfrac{x_{1}}{\sigma_{1}}\right)(\dfrac{x_{2}}{\sigma_{2}})\right)\right)= \dfrac{2}{\pi} \dfrac{1}{\sigma_{1} \sigma_{2}} \dfrac{1}{\sqrt {1 - \rho^{2}}}
$$
从而我们得到结果：
$$
\dfrac{\partial E}{\partial \rho} = \dfrac{2}{\pi} \dfrac{1}{\sqrt{1 - \rho^{2}}}
$$
那么显然有：
$$
E(g) = \dfrac{2}{\pi}\arcsin \rho
$$
这显然就说我们之前所得到的反正弦律。

我们考虑通过平方系统的情况，再来使用一遍上面的方法。首先，我们显然知道：
$$
g = x_{1}^{2}x_{2}^{2}
$$
求导：
$$
g_{x_{1}x_{2}} = 4x_{1}x_{2}
$$
计算期望：
$$
\mathrm{E}= 4\mathrm{E}(X(t) X(s)) = 4 R_{X}(t-s)
$$
注意到：
$$
\sigma_{1} \sigma_{2} =R_{X}(0) \quad  \rho = \dfrac{R_{X}(t-s)}{R_{X}(0)}
$$
那么：
$$
\dfrac{\partial E}{\partial\rho} = 4 \rho R_{X}^{2}(0)
$$
那么我们直接得到：
$$
\mathrm{E}(g) = R_{X}^{2}(0) + 2 R_{X}^{2}(t-s)
$$

再举一个例子：$\mathrm{ReLU}(x)$。留做习题答案略，读者自证不难。

我们接下来开始证明这一定理。直接对 $\mathrm{E}(g)$ 进行求导肯定不成（这一切一切的原因都是 $\Sigma$ 矩阵求了逆）！我们仍然需要使用特征函数！
我们需要完成积分：
$$
\int  \int g(x_{1},x_{2}) f(x_{1},x_{2}) dx_{1}dx_{2}
$$
注意到特征函数：
$$
\phi(\omega_{1} ,\omega_{2}) = \exp\left(- \dfrac{1}{2} (\sigma_{1}^{2} \omega_{1}^{2} + \sigma_{2}^{2}\omega{2}^{2}+ 2 \rho  \sigma_{1} \sigma_{2} \omega_{1}\omega_{2}) \right)  
$$
显然，我们希望将原问题尽可能地和特征函数扯上关系！上述积分可以被写为（把 $f$ 用特征函数表示）：
$$
\begin{align*}
\int  \int g(x_{1},x_{2}) f(x_{1},x_{2}) dx_{1}dx_{2}\\
&= \int \int g  \int \int  \phi \exp(- i (\omega^{T}x)) d \omega   dx
\end{align*}
$$
此时对 $\omega$ 求导：
$$
\begin{align*}
\dfrac{\mathrm{d}I}{\mathrm{d}\rho}\\
&= \int \int g \int \int (- \sigma_{1} \sigma_{2} \omega_{1}\omega_{2}) \phi \exp(-i (\omega^{T}x)) d \omega dx \\
&= \sigma_{1} \sigma_{2} \int \int g \dfrac{\partial ^{2}}{\partial x_{1} \partial x_{2}}  \int \int \phi \exp(- i (\omega_{1}x_{1} + \omega_{2}x_{2})) dx_{1}dx_{2}d \omega_{1} d \omega_{2}\\
&= \sigma_{1} \sigma_{2} \int \int g \dfrac{\partial^{2}  }{\partial x_{1} \partial x_{2}} f(x_{1},x_{2})dx_{1}dx_{2}\\
&= \sigma_{1} \sigma_{2} \int \int \dfrac{\partial^{2} g }{\partial x_{1} \partial x_{2}}  f(x_{1},x_{2}) dx_{1}dx_{2}
\end{align*}
$$
![[Pasted image 20240216205442.png]]
其中第四个等号使用了（两次）分部积分，我们将其边界值忽略了（这是因为 $f$ 下降得十分快）。我们完成了证明。这一定理称为 Price 定理。

再给一个特殊的例子。
>[!EXAMPLE] 高斯过程通过 $g = \exp(\cdot)$，求相关函数。
>不要作死使用 Price 定理，因为 $\exp(\cdot)$ 求导之后不变样子。
>注意到 $$\mathrm{E}(\exp(X_{1} + X_{2})) = \phi(-i,-i)$$
>本题可以直接求解。






