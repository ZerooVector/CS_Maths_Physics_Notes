#RL  

在上一次中，我们谈到了 DDP/微分动态规划，这种方法可以用于求解非线性的无约束的轨迹优化。这样的问题通常被写为：
$$
\min_{x,u} J = \sum  l(x_{i},u_{i}) + l_{N}(x_{N})
$$
$$
s.t. \quad x_{i+1} = f(x_{i},u_{i})
$$
我们的通常做的是展开 $V(x)$：
$$
v_{I}(x + \Delta x)  \approx V(x) + p_{i}^{T}\Delta x  + \frac{1}{2} \Delta x^{T} P_{i} \Delta x 
$$
其中:
$$
P_{i} = \nabla^{2} l_{i}(x) \quad  p_{i} = \nabla l_{i}(x)
$$
我们反向求解最小化问题：
$$
V_{i-1} (x + \Delta x)  = \min_{\Delta u} Q(x + \Delta x,u + \Delta u)
$$
通过计算，我们不难得到：
$$
\Delta u_{i-1} = - d_{i-1}  - K_{i-1} \Delta x_{i-1}
$$
$$
P_{i-1} = G_{xx} + K^{T} G_{uu} K - G_{xu} K  + K^{T} G_{ux} \quad p_{i-1}  = g_{x} - K^{T} g_{u} + K^{T} G_{uu}  d  - G_{xu} d 
$$

求解这个问题的方法与之前介绍的“打靶法”类似，实际上是一种二阶打靶法。
我们初始化 $\Delta J = 0$，然后后向推出：
$$
u_{i} \leftarrow u_{i}- \alpha d_{i} - K_{i}(x_{i}'  - x_{i})
$$
更新 $\Delta J$：
$$
\Delta J \leftarrow \Delta J  + \alpha g_{uu}^{T} d_{i}
$$
直到整个一次后向递推。为了保证收敛，需要对 $\alpha$ 进行线搜索。线搜索的停止条件就是：
$$
J(x_{new},u_{new}) < J(x,u) - \Delta J 
$$
因为这里 $\Delta J$ 相当于那个一阶展开项。在前向递推中，我们重新计算 $V$ 以及各个梯度。
在这个过程中，Hessian 矩阵可能并不是正定的，这需要我们正则化。


## 在 DDP 中处理约束
- 对于控制量的极大值限制，我们通常使用一种"squash function"的函数进行处理，例如 sigmoid 或者 tanh 函数。但是，这会增加问题的非线性程度。更好的方法是在反向求解控制量时求解带有约束的二次规划问题：
$$
\Delta u = \arg \min_{\Delta u} S(x + \Delta x  , u + \Delta u)
$$
$$
s.t. \quad u_{min} \le  u + \Delta u \le u_{max}
$$
对于状态的约束（例如，自行车的速度不能过大），这是更加困难的，通常来说我们会使用罚函数方法。一种更好的方法是在 DDP 中使用增广拉格朗日乘子方法。

