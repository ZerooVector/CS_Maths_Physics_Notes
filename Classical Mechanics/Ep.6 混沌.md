#Classcal_Mechanics  #DynamicalSystem 

混沌理论是一种“内禀”的随机性。

“混沌是振奋人心的，因为它开启了简化复杂现象的可能性；混沌是令人忧虑的，因为它导致对科学的传统建模程序的新怀疑；混沌是迷人的，因为它体现了数学、科学及技术的相互作用；但混沌首先是美的。这并非偶然，而是数学美可以看得见的证据；这种美曾被局限于数学家的视野之内，由于混沌，它正在渗透到人类感觉到的日常世界之中。”

一个混沌的典型例子是洛伦兹方程：
$$
\begin{align*}
\dfrac{\mathrm{d}x}{\mathrm{d}t} &= - \sigma(x - y) \\
\dfrac{\mathrm{d}y}{\mathrm{d}t} &= rx - y - xz \\
\dfrac{\mathrm{d}z}{\mathrm{d}t} &= - bz + xy
\end{align*}
$$
它有耗散性质：
$$
\begin{align*}
\dfrac{\mathrm{d}V}{\mathrm{d}t} &= \int_{V} \nabla (f) dV \\
&= - V(\sigma+ b + 1)
\end{align*}
$$
从而：
$$
V(t) = V_{0}\exp(- (\sigma+ 1 + b )t)
$$
（注意：这不意味着它有稳定的平衡点）
![[Pasted image 20240411193724.png]]

![[Pasted image 20240411193749.png]]

![[Pasted image 20240411193806.png]]

对系统混沌程度的一种定量描述是李雅普诺夫指数。对于连续动力系统 $\dot x  = f(x,t)$，我们希望研究 $w (t) = x (t) - \bar x(t)$ 随着时间变化的规律。如果系统进入了混沌，那么李雅普诺夫 $w(t)$ 将 $e$ 指数增长。根据这种直觉，我们将李雅普诺夫指数定义为：
$$
\sigma(\bar u , w_{0}) = \lim_{t \rightarrow \infty } \dfrac{1}{t} \ln \dfrac{||w(t)||}{||w_{0}||}
$$
同理，对于离散时间动力系统，李雅普诺夫指数被定义为：
$$
\sigma(\bar u , w_{0}) = \lim_{j \rightarrow \infty } \dfrac{ 1}{j} \ln \dfrac{||w_{j}||}{||w_{0}||}
$$
![[Pasted image 20240411201925.png]]

通向混沌的道路：
- 不断产生的倍周期分叉
- 奇怪吸引子
- 非线性耦合

