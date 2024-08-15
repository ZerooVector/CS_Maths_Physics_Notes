#StochasticProcess 

## 对布朗运动的建模
我们先考虑一个随机扩散问题。我们假定一个粒子历经时间 $\tau$ 的扩散后，它的位置服从概率密度分布 $\rho(y)$。我们进一步假定 $\rho (y) = \rho(-y)$，那么我们立刻可以得到 $\mathrm{E}(\rho) = 0$，二阶矩是一个常数 $D$。
令 $f(x,t)$ 是 $t$ 时刻在 $x$ 位置上粒子的浓度，显然 $f (0,0) = C$，我们希望求出 $f(x,t)$ 满足的偏微分方程。我们现在考察 $f(x,t)$ 和 $f(x,t+\tau)$ 之间的关系，那么显然有：
$$
f(x,t+\tau) = \int f(x-y) \rho(y) dy 
$$
我们现在对 $f (x, t)$ 进行展开，即可得到：
$$
f(x,t) + \dfrac{\partial f}{\partial t}  \tau  = \int \left(f\left(x,t\right) - \dfrac{\partial f}{\partial x}y + \frac{1}{2} \dfrac{\partial f}{\partial x^{2}} y^{2}\right)\rho (y) dy 
$$
利用我们前面对于 $\rho(y)$ 的假设，我们就可以得到：
$$
f(x,t) + \dfrac{\partial f}{\partial t} \tau = f(x,t) + \dfrac{D}{2} \dfrac{\partial^{2} f}{\partial x^{2}} \Rightarrow \dfrac{\partial f}{\partial t} = \dfrac{D}{2 \tau}  \dfrac{\partial^{2} f}{\partial x^{2}}
$$
这就是一维扩散方程。此方程的解为：
$$
f(x,t) = \dfrac{1}{\sqrt{2 \pi c t}} \exp(- \dfrac{x^{2}}{2ct})
$$
这里的 $c = \lim_{\tau \rightarrow 0} \dfrac{D}{2 \tau}$。

在离散的情况下，我们也可以建立这个模型。假定 $P(m,n)$ 代表 $m$ 处，$n$ 时刻粒子的数目。假定每个粒子在每一时刻向两侧游走的概率均为 $\dfrac{1}{2}$，容易写出递推方程：
$$
P(m,n+1) = \dfrac{1}{2} P(m+1,n) + \dfrac{1}{2} P(m-1,n) 
$$
从而：
$$
P(m,n+1) - P(m,n) = \dfrac{1}{2} P(m+1,n) + \dfrac{1}{2} P(m-1,n) - \dfrac{1}{2} P(m,n)= \dfrac{1}{2}(P(m+1,n) - 2P(m,n) +P(m-1,n))
$$
左侧是对时间的一阶差分，而右侧是对空间的二阶差分。通过取极限，我们可以得到与之前完全一致的方程：
$$
\dfrac{\partial P}{\partial t} = C \dfrac{\partial^{2} P }{\partial x^{2}}
$$

## 最大熵问题
设 $f(x)$ 是一个概率分布，我们定义其微分熵为：
$$
H(f) = - \int f(x) \log f(x) dx 
$$
这显然是一个有约束泛函的极值问题，需要使用变分法求解。假定 $f_{0}$ 是最优解，那么我们构造一个辅助函数 $g (t) = H(f_{0} + t \cdot h)$，$h$ 是任意函数。显然，$g (0) \ge g(t)$，从而我们可以通过对 $g(t)$ 进行求导的方式解决这个问题。
$$
g(t) = H(f_{0} + t \cdot h ) = - \int (f_{0} + t \cdot h )  \log(f_{0}+ t \cdot h ) dx 
$$
在解决问题之前，我们首先要考虑到这里的随机性是依赖于随机变量的方差的，而且乘以一个因子之后，随机变量的随机性也会改变。因此，我们要施加约束条件：$\mathrm{E} (X) = m,\mathrm{E}(X^{2}) = \sigma^{2}$，所以我们得到：
$$
\begin{align*}
L(t,\lambda_{1},\lambda_{2},\lambda_{3}) \\
&= \int (f_{0} + th ) \log (f_{0}+ th ) dx + \lambda_{1}\left(\int x(f_{0}+th)dx-m\right)+ \lambda_{2}\left(\int x^{2}(f_{0}+th )dx - \sigma^{2}\right) + \lambda_{3}\left(\int (f_{0}+ th)dx-1\right)
\end{align*}
$$
求导：
$$
\begin{align*}
\dfrac{\partial }{\partial t} L(t,\lambda_{1},\lambda_{2},\lambda_{3}) \\
&= \int h ((\log f_{0}+ th)  +1) + \lambda_{1} \int  h x + \lambda_{2} \int h x^{2} + \lambda_{3} \int h \\
&= \int h(x) (logf_{0}+ th + \lambda_{1}x +  \lambda_{2} x^{2} + \lambda_{3} +1 )dx \\

\end{align*}
$$
在 $t=0$ 时，我们可以给出：
$$
\int h(x) ( \log (f_{0}) + \lambda_{1}x  + \lambda_{2}x^{2} + \lambda_{3})dx = 0 
$$
由 $h (x)$ 选择的任意性，显然得到：
$$
\log f_{0}(x) = - \lambda_{1}x^{2} - \lambda_{2}x - \lambda_{3}
$$
从而得到：
$$
f_{0}(x) = c \exp(- c_{2}x^{2} - c_{1}x )
$$
这也是一个高斯分布。因此，高斯分布是最大熵的分布。


## 利用中心极限定理分析随机游走
考虑离散随机游走，令 $X_{k}$ 是服从伯努利分布的随机变量，有均等概率取 $0,\Delta x$。记 $S_{n} = \sum_{k} X_{k}$。假定粒子在 $[0,t]$ 内运动，它所走的步数 $n = \dfrac{t}{\Delta t}$。首先我们将随机变量标准化：
$$
\tilde X_{k} = \dfrac{\left(X_{k} -\dfrac{\Delta x}{2}\right)}{\sqrt {\dfrac{\Delta x^{2}}{4}}}
$$
容易计算得到：
$$
S_{k}= \dfrac{\Delta x}{2}  \sum_{k=1}^{n}\tilde X_{k} + \dfrac{n}{2} \Delta x \Rightarrow \dfrac{S_{n} - \frac{n \Delta x}{2}}{\frac{\Delta x}{2}} = \sum_{k} \tilde X_{k}
$$
那么在 $n  \rightarrow \infty$ 时：
$$
\dfrac{S_{n} - \frac{n \Delta x}{2}}{\frac{\Delta x}{2} \sqrt n } \rightarrow N(0,1)
$$
这里的 $n = \dfrac{t}{\Delta t}$，分母上是 $\dfrac{\sqrt t}{2} \dfrac{\Delta x}{\sqrt {\Delta t}}$，我们要求 $\dfrac{\Delta x}{\sqrt{\Delta t}}$ 是一个常数。那么就可以看出 $S_{n} \sim N(?,Dt)$ 的结论。这验证了前面模型的结论。






