#DifferentialGeometry 

我们现在为 GGB 提供一个完全内蕴的证明（使用另一种方法将曲率和奇点指数联系起来）。首先我们将和乐性推广到非闭合曲线 $K$。正如定义奇点指数一样，此时我们可以将和乐性定义为：
$$
\mathcal{R}_{U} (K)= \delta_{K}(\angle Uw_{\parallel})
$$
显然，$\mathcal{R}_{U}$ 与 $U$ 的选择一定是相关的，但是与 $w$ 的选择无关。此时，三角形的和乐性就可以写成三边上的和乐性之和。

我们现在要证明：
$$
\mathcal{K}(S_{g}) = \iint_{S_{g}} \mathcal{K} d \mathcal{A} = 2 \pi \sum_{i} \mathcal{J}_{F}(s_{i})
$$
之前我们已经证明过，$\sum_{i} \mathcal{J}_{F} = 2 - 2g$，现在的问题让是如何将它与总曲率联系起来。
![[Pasted image 20240730084443.png|400]]
如图，我们找一个测地三角形，在其中放置一个奇点 $s$（我们这里放置了一个源），我们考察：
$$
\begin{align*}
\mathcal{K}(\Delta) - 2 \pi \mathcal{J}_{F}(s) &=  \mathcal{R}(\Delta ) - \delta_{\Delta}(\angle UF) \\
&= \sum_{i}[\mathcal{R}_{U}(K_{i}) - \delta_{K_{i}} (\angle UF)]\\
&= \sum_{i}[\delta_{K_{i}}(\angle U w_{\parallel}) - \delta_{K_{i}}(\angle UF)]\\
 &= \sum_{i}\delta_{K_{i}}(\angle F w_{\parallel})
\end{align*}
$$
因此这个差值其实只与我们放置的向量场 $F$ 有关系，独立于作为基准的 $U$。显然，走过边 $K_{i}$ 的方向反向的时候，上面这个差值也会反向。
![[Pasted image 20240730085544.png]]
现在在曲面上设置向量场，并对曲面做多边形剖分，使得每个多边形中至多包含一个奇点。对所有多边形求和，立刻得到：
$$
\mathcal{K}(S_{g}) = 2 \pi \sum_{i} \mathcal{J}_{F}(s_{i}) =2\pi (2 - 2g)
$$
从而定理得证。

