#RL 

在上一次中，我们聊到了使用正则化改进后的牛顿法，但这种方法容易导致一些问题：比如，梯度下降的“学习率”过大，导致我们直接越过最优解。我们将讨论这一问题的解决方案。

## Line Search 
Line search 的基本思想是：我们将检查，沿着我们找到的方向走到底是否能找到更优的解，如果步长过大，我们会“回溯”一点点，从而避免越过最优解。一种简单的方法是，我们设置一个步长（学习率）$\alpha  = 1$，我们要求：
$$
f(x + \alpha \Delta x )   < f(x) + \beta  \alpha ( \nabla f(x) )^{T} \Delta x 
$$
这里的 $\beta$ 是一个常数。如果不满足这个条件，我们将缩小步长,，这可以通过使得 $\alpha \leftarrow c\alpha$ 来实现。
直觉：我们使用一条直线来控制下一步的位置，如果下一步位置的目标函数越过了这条直线，我们就缩小步长。
在实际应用中，我们通常设置 $c = 0.5,\beta \in [10^{-4},0.1]$

## 含有等式约束的最优化
我们考虑如下的最优化问题：
目标函数：
$$
\min f(x) \quad f(x) : \mathbb{R}^{n} \rightarrow \mathbb{R} 
$$
约束条件：
$$
s.t. c(x) = 0  \quad c(x) : \mathbb{R}^{n}  \rightarrow \mathbb{R}^{m}
$$
一阶条件应该是：
- 在无约束的方向上梯度得 0
- 约束条件得到满足
![[Ep.4 Optimization(2) 2023-09-20 13.28.05.excalidraw]]
换一个说法，从上面的图中我们容易看出，在局部极值附近，沿着 $c (x) = 0$ 移动时，$f(x)$ 的值不能改变。因此，我们要求 $\nabla f(x)$ 和 $c (x) = 0$ 所定义的超曲面垂直。显然，$\nabla c(x)$ 是与 $c (x) = 0$ 定义的超曲面处处垂直的，因此，一阶条件会是：
$$
\nabla f(x) + \lambda  \nabla c(x) = 0 
$$
这里的 $\lambda$ 称为“拉格朗日乘子“或者“对偶变量”。我们一般把上式写成：
$$
\nabla_{x} L = \frac{\partial f}{\partial x} + \lambda^{T} \frac{\partial c}{\partial x} = 0  \quad \lambda\in \mathbb{R}^{m}
$$
再加上
$$
\nabla_{\lambda} L = c(x) = 0 
$$
这就是等式约束优化问题的 KKT 条件

这仍然是一个方程组的求解问题，因此你可以使用牛顿法来求解它。只需要：
$$
\nabla_{x} L(x + \Delta x ,\lambda + \Delta  \lambda) \approx  0 
$$
$$
\nabla_{\lambda}L(x + \Delta x ,\lambda + \Delta \lambda) \approx 0
$$
你需要联立上面两个方程，得到：
$$
\begin{bmatrix}\frac{\partial^{2} L }{\partial x^{2} } & (\frac{\partial c}{\partial x})^{T} \\ \frac{\partial c}{\partial x } & 0 \end{bmatrix} \begin{bmatrix}\Delta x \\ \Delta \lambda\end{bmatrix} = \begin{bmatrix}-\nabla_{x}L(x,\lambda ) \\ - c(x)\end{bmatrix}
$$
然后我们就可以得到步长 $\Delta x$ 和 $\Delta \lambda$。我们把这样的方程组叫做"KKT System"

我们还有一种方法，称为 Gauss-Newton 方法。我们计算：
$$
\frac{\partial ^{2} L}{\partial x^{2}} = \nabla^{2} f + \frac{\partial }{\partial x}[(\frac{\partial c}{\partial x})^{T}\lambda]
$$
我们会扔掉第二项（这一项有时被称作"constraint curvature"）。这会导致收敛过慢，但是这会避免约束条件对 $H$ 矩阵的正定性质的影响，而且可以加速每一步的计算。这使得 Gauss-Newton 方法常常在实践中被使用。

## 含有不等式约束的最优化
我们接下来解决这样的最优化问题：
目标函数：
$$
\min f(x)
$$
约束条件：
$$
s.t. c(x) \le 0
$$
类比上文，我们先来介绍一阶的必要条件：
- 在无约束方向上梯度得 0
- 约束条件得到满足
那么：
$$
\nabla f + (\frac{\partial c}{\partial x})^{T}  \lambda=  0
$$
$$
c(x) \le  0 
$$
$$
\lambda \ge  0 
$$
$$
\lambda^{T} c(x) = 0 
$$
直观上，我们可以看到：当一个约束处于活动状态时，它所对应的乘子为正（这些约束相当于等式约束）；否则它对应的乘子为 0（这些约束相当于不存在）


