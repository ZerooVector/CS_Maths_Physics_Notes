#MA  
## 矩阵函数（续）和微分方程
##### Theorem 
$$
(e^{At})' = Ae^{At}  = e^{At} A
$$
##### Theorem 
考虑常微分方程
$$
\begin{cases}
\dot x(t) = Ax(t) \\
x(0) = x_{0}
\end{cases}
$$
其中，$x(\cdot)$ 是一个向量值函数，那么其解为：
$$
x(t) = e^{At} x_{0}
$$
将解带回验证即可。

##### Theorem 矩阵的 Hurwitz 稳定
记一个 LTI 系统的状态转移矩阵为 $A$，那么我们称系统为：
- Hurwitz 渐近稳定：若 $A$ 的所有特征值的实部均小于 0，则成为 Hurwitz 渐近稳定
- Hurwitz 临界稳定：$\mathrm{Re}\lambda_{A}\le 0$ ，且那些 $\mathrm{Re}\lambda_{A}=0$ 的特征值对应的 Jordan 块都是 $1\times 1$ 的，或者说对应的初等因子都是 1 次的

直观地来说，这个结论来源于
$$
e^{\lambda t} = e^{at}\cdot e^{ibt} 
$$
那么显然可以看出结论。
而在临界稳定时，Jordan 块为 1 阶保证了多项式不出现，从而只有三角函数的部分。

这也是自动控制原理中 Routh 判据的来源。然而，求解巨大矩阵的特征值是困难的，因此，我们发明了其他的方法。

##### Theorem Lyapunov equation
给定矩阵 $A$，如何快速判断 $\mathrm{Re}\lambda (A) <0$？
我们的基本想法是：系统有一种“能量”函数，如果“能量”随着时间单调减少，那么，系统就是稳定的。自然地，我们想到使用一个二次型来表征一个“能量”函数
$$
V(x) = x^{T}Px 
$$
其中，$P$ 是一个正定阵。那么
$$
V(x(t))' = \dot x(t)^{T} Px(t)+x(t)^{T}P\dot x(t) = x^{T}(t)[A^T P+PA]x(t)
$$
那么，如果 $A^{T}P+PA$ 负定，比如说 $A^T P+PA=-I$ ，则沿着任意轨迹，系统能量衰减。

因此，工程上，我们最终得到的定理是：**若关于 $P$ 的矩阵方程 $A^{T} P+PA= -I$ 有对称正定解的充要条件是系统 $A$ Hurwitz 渐近稳定。

##### PF  
正着推：已知 $P$ 对称正定, 且
$$
A^{T} P+PA= -I
$$
根据特征值的定义有：
$$
Ax = x \lambda
$$
$$
x^{H}(A^{T }P+PA)x = -x^{H}x
$$
从而
$$
(x \lambda)^{H}Px  + x^{H}Px \lambda = -x^{H}x
$$
$$
(x^{H} Px)(\bar \lambda+\lambda)= - x^{H}x
$$
由于 $\bar \lambda+\lambda = 2\mathrm{Re}\lambda$ ，容易得到结论！

反着推：
现在我们在已知 $A$ 的特征值都具有负实部的情形下，推导矩阵方程
$$
A^{T} X+XA= -I
$$
的解。我们在方程两边同乘两次 $e^{At}$
$$
LHS = ((e^{At})')^{T} Xe^{At}+(e^{At})^{T}X (e^{At})'= ((e^{At})^{T}Xe^{At})'
$$
两边同时积分：
$$
e^{A^{T} t}Xe^{At}|_{0}^{\infty}= -\int_{0}^{\infty} e^{A^{T}t}e^{At} dt
$$
于是可以直接解出
$$
X = -\int_{0}^{\infty} e^{A^{T}t}e^{At} dt
$$
可以证明，$X$ 是对称正定的



