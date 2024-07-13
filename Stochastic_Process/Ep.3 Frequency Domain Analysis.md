#StochasticProcess 

这一节我们来讲谱分析（频域分析）。直观地来说，谱是我们对复杂对象进行分解的过程，我们希望将复杂的对象分解为简单的成分。


## 确定性信号的谱分析
首先，我们来介绍确定性信号的谱。考虑信号 $X(t)$，我们假定它有周期 $T$，那么我们可以找到信号的傅里叶级数。记 $\omega_{k} = \dfrac{2 k \pi}{T}$（我们将 $k=1$ 的情况称为“基频”），令 $X (t)  = \sum_{k} \alpha_{k} \exp( i \omega_{k} t)$，那么：
$$
\alpha_{k} = \int_{-\frac{T}{2}}^{-\frac{T}{2}}  X(t) \exp(- i \omega_{k}t) \quad \alpha_{k} \in \left[-\dfrac{T}{2},\dfrac{T}{2}\right]
$$

我们使用这样简单的方式就得到了这些系数，这是因为这一组基函数是正交的。

对于非周期函数，我们仍然可以对其进行傅里叶展开，我们希望在 $(\infty,+\infty)$ 上获得信号在这组基上的表达，这意味着 $T \rightarrow \infty$。我们知道：
$$
X(t) = \dfrac{1}{T} \sum_{k} \left(\int_{-\frac{T}{2}}^{-\frac{T}{2}} X(s) \exp(- i \dfrac{2k \pi}{T} s)ds\right)\exp (i \dfrac{2k \pi}{T} t)
$$
在 $T \rightarrow \infty$ 时，$\dfrac{2\pi}{T} \rightarrow 0$，上式可以被改写成：
$$
X(t) = \dfrac{1}{2\pi } \int_{-\infty}^{+\infty}  X(\omega) \exp(i \omega t) d\omega 
$$
这就是傅里叶反变换。对比各式可以发现：
$$
X(\omega ) = \int_{-\infty}^{+\infty} X(t)  \exp(- i \omega t)dt
$$

## 随机信号的谱分析
我们直接沿用确定性信号的做法：
$$
X(t) = \dfrac{1}{2\pi }  \sum_{k} \left(\int_{-\frac{T}{2}}^{- \frac{T}{2}} X(t) \exp\left(- i \dfrac{2k \pi}{T}t\right)dt\right) \exp\left(i \dfrac{2k \pi}{T}t\right)\dfrac{2\pi}{T} 
$$
但是，这里会遇到困难。当 $T \rightarrow \infty$ 时，我们无法判断从 $-\infty$ 到 $+\infty$ 的积分是否收敛。（注意：在确定性信号的谱分析中，我们实际上要求 $\int_{-\infty}^{+\infty}|X (t)|dt < \infty$）在随机信号中，我们通常要求信号是平稳的，这通常会使得积分发散。
直观上来看，我们希望对一个有“衰减”的信号做傅里叶变换，而相关函数通常是衰减的。我们首先考虑下面的积分：
$$
\lim_{T \rightarrow \infty } \dfrac{1}{T}\mathrm{E}\left(\left|\int_{-\frac{T}{2}}^{\frac{T}{2}} X(t) \exp (-i\omega t)dt \right|^{2}\right)
$$
从物理意义上来说，我们是把振幅换成了能量，并且对时间归一化。下面我们来计算这个东西：
$$
\begin{align*}
\dfrac{1}{T}\mathrm{E}\left(\left|\int_{-\frac{T}{2}}^{\frac{T}{2}} X(t) \exp (-i\omega t)dt \right|^{2}\right) \\
&= \dfrac{1}{T}\mathrm{E}\left(\left|\int_{-\frac{T}{2}}^{\frac{T}{2}} X(t) \exp (-i\omega t)dt \right|\ \overline{\left|\int_{-\frac{T}{2}}^{\frac{T}{2}} X(t) \exp (-i\omega s)ds \right|}\right)\\
&= \dfrac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} \int_{-\frac{T}{2}}^{\frac{T}{2}} \mathrm{E}(X(t) \overline{X(s)}) \exp(-i\omega (t-s)) dt ds\\
&= \dfrac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} \int_{-\frac{T}{2}}^{\frac{T}{2}}  R_{X}(t-s) \exp(-i \omega(t-s)) dt ds\\
&= \dfrac{1}{2T} \int \int  R_{X}(u) \exp(-i \omega u)  dudv\\
&= \dfrac{1}{2T} \left(\int_{-T}^{0} \int_{-T-u}^{T+u} + \int_{0}^{T} \int_{u-T}^{-u+T} \right)R_{X}(u)  \exp(- i \omega u )  dv du \\
&= \dfrac{1}{2T} \int_{-T}^{T} \int_{-T-|u|}^{T-|u|} R_{X}(u) \exp(- i \omega u) dv du\\\\
&= \dfrac{1}{2T} \int_{-T}^{+T} (2T -2|u|)  R_{X}(u) \exp(-i  \omega u) du \\
&= \int_{-T}^{T}\left(1- \dfrac{|u|}{T}\right)R_{X}(u) \exp(-i \omega u)du 
\end{align*}
$$
其中，我们利用了换元 $u = t-s, v = t+s$ 。
现在，令 $T \rightarrow \infty$，那么我们可以发现上述积分：
$$
I = \int_{-T}^{T} R_{X}(u) \exp(-i \omega u )du = S_{X}(\omega)
$$
我们可以发现，我们上面的量是相关函数的傅里叶变换，我们将其称为**功率谱密度**。我们可以讨论一些问题：
- 首先，容易注意到它的量纲是 $\dfrac{[I]^{2}[T]^{2}}{[T]}$，这是能量的量纲
- 我们可以容易地得到上式的傅里叶反变换：$$
\dfrac{1}{2\pi} \int_{-\infty}^{+\infty} S_{X}(\omega) \exp(i \omega u) d \omega = R_{X}(u) 
$$ 那么如果令 $u=0$，那么我们立刻得到：$$
\int_{-\infty}^{\infty} S_{X}(\omega) d \omega = R_{X}(0) = \mathrm{E}|X(t)|^{2}
$$ 也就是说，对功率谱密度进行积分，我们将得到一个随机过程的功率。**$S_{X}(\omega)$ 表达了随机过程在每个频率上的功率**
- 从上述推导过程中我们可以直接看到：$S_{X}(\omega) \ge 0$，这与前面“相关函数是正定的”这一结论相符合。
我们将以上结果称为“维纳-辛钦关系”

现在，我们希望研究功率谱的性质、功率谱和频谱的关系。功率谱密度是一个二阶量，那么显然有：
$$
S_{\alpha X} (\omega) = |\alpha|^{2} S_{X}(\omega)
$$
并且在一般情况下：
$$
S_{X+Y} (\omega)\not = S_{X}(\omega) + S_{Y}(\omega)
$$
如果信号是实数，那么：
$$
S_{X}(\omega) = S_{X}(- \omega)
$$
（对于实的信号来说，负数频率完全没有意义，$\omega$ 的负半轴上完全不应该承载多余的信息，因此直观来看，这个性质就应当成立），我们可以证明这一点。将 $\exp (i \omega\tau)$ 拆开：
$$
S_{X}(\omega) = \int R_{X}(\tau) \exp(-i \omega\tau) d\tau = \int R_{X}\cos(\omega \tau) d \tau + i \int R_{X} \sin(\omega \tau) d \tau 
$$
关注右边积分号下的两个函数：第一个是偶函数，第二个是奇函数，注意到所有积分的上下限都是 $(-\infty,+\infty)$， 那么：
$$
S_{X}(\omega) = \int R_{X}(\tau)  \cos (\omega \tau) d \tau 
$$
显然我们完成了证明。

我们再证明一个有趣的性质，它也许可以刻画相关函数的衰减速率：
$$
R_{X}(0) - R_{X}(\tau) \ge \dfrac{1}{4^{n}} (R_{X}(0) - R_{X}(2^{n} \tau))
$$
显然，上式可以迭代得到。我们只需证明一个最简单的式子：
$$
3R_{X}(0) - 4 R_{X}(\tau) + R_{X}(2 \tau) \ge 0
$$
一种证法是利用矩阵的正定性直接观察，构造：
$$
\begin{bmatrix}R_{X}(0) & R_{X}(\tau) & R_{X}(2 \tau)  \\ R_{X}(\tau) & R_{X}(0) & R_{X}(\tau)  \\ R_{X}(2 \tau) & R_{X}(\tau)  & R_X (0)\end{bmatrix}
$$
这个矩阵是正定的。利用待定系数法构造一个二次型即可。下面换一个证法，考虑：
$$
\begin{align*}
3R_{X}(0) - 4 R_{X}(\tau) + R_{X}(2 \tau) \\
&= \dfrac{1}{2 \pi } \int S_{X}(\omega) (3-4\exp(i  \omega t) + \exp(i \omega 2 \tau))d \omega\\
&= \dfrac{1}{2\pi} \int S_{X}(\omega)(3 - 4 \cos (\omega\tau) + \cos(2 \omega \tau)) d \omega\\
&= \dfrac{1}{2 \pi }\int S_{X}(\omega) (2 \cos (\omega \tau )-1)^{2} d \omega 
\end{align*}
$$
其中，我们利用了功率谱密度 $S_{X}(\omega)$ 也是偶函数的性质。

## 随机信号通过线性时不变系统
我们知道，对于确定性信号，它通过线性时不变系统后：
$$
Y(t) = \int h(t - \tau) X(\tau) d \tau   \quad  Y(\omega) = H(\omega)X(\omega)
$$
那么，现在假设信号 $X(t)$ 是随机的，我们希望从输入信号的相关函数算出输出信号的相关函数：
$$
\begin{align*}
R_{Y}(t,s) \\
&=  \mathrm{E}(Y(t)Y(s)) \\
&= \mathrm{E}\left(\int h(t - \tau)X(\tau) d \tau\right)\overline{\left(\int h(s - r)X(r) d r\right)}\\
&= \int \int \mathrm{E}(X(\tau) \overline{X(r)}) h(t - \tau) \overline{h(s - r)} d \tau dr\\
&=  \int  \int R_{X}(\tau - r ) h (t -\tau) \overline{h(s - r)} d\tau dr
\end{align*}
$$
注意上式并不是一个卷了两次的卷积，其中有些东西的正负号不对。（一种简单的判断卷积的小技巧是把所有被积函数的自变量加在一起，看积分变量是否被消掉。如果消掉，那么就是正确的卷积。==其实这里我也不太清楚这种卷积的具体物理意义，我只能从写法上判断它的正确与否。实际上，如果正负号有点问题我们也可以通过积分消去 $r,\tau$，但是这个时候可能不是我们正常约定的“卷积“的写法。这个地方暂时存疑，后面再说==）于是我们构造：$\tilde h (t) = \overline{h (- t)}$，使得上式中出现正确的卷积，再继续完成上式：
$$
\begin{align*}
R_{Y}(t,s)\\
&= \int \int  R_{X}( \tau - r) h(t - \tau) \tilde h (r-s) d \tau d r\\
&= (R_{X} * h * \tilde h ) (t-s)
\end{align*}
$$
因此，输出信号也是宽平稳的。同时我们显然可以得到：
$$
S_{Y}(\omega) = S_{X}(\omega) H(\omega)\tilde H(\omega)
$$
容易计算得到 $\tilde H (\omega) = \overline{H(\omega)}$，从而：
$$
S_{Y}(\omega) = S_{X}(\omega)|H(\omega)|^{2}
$$
这里有个平方项，这也说明功率谱密度是个二阶量。

>[!EXAMPLE]
我们举一个小例子。之前，我们已经知道柯西不等式：
$$|\mathrm{E}(X(t)Y(t))| \le (\mathrm{E}^{2}X(t) \mathrm{E}Y^{2}(t))^{\frac{1}{2}}$$
也就是说：
$$|R_{XY}(0)| \le  (R_{X}(0) R_{Y}(0))^\frac{1}{2}$$
其中 $R(X,Y)$ 是信号 $X(t),Y(t)$ 的互相关函数。 上式意味着：
$$\left|\int S_{XY}(\omega) d \omega\right| \le \left(\int S_{X}(\omega)d \omega \int S_{Y}(\omega)d \omega \right)^\frac{1}{2}$$
接下来我们将积分放到某一区间 $(a,b)$ 上，这相当于原来的信号过了一个线性系统，因此上式也是成立的：
$$\left|\int_{a}^{b} S_{XY}(\omega) d \omega\right| \le \left(\int_{a}^{b} S_{X}(\omega)d \omega \int_{a}^{b} S_{Y}(\omega)d \omega\right)^\frac{1}{2}$$












