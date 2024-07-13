#RL  

## 问题的定义
对于确定性最优控制，我们有如下定义：
$$
\min_{u(t)} J(x(t),u(t)) = \int_{t_{0}}^{t_{f}} L(x(t),u(t))dt + l_{f}(x(t_{f}))
$$
$$
s.t. \quad  \dot x(t) = f(x(t),u(t))
$$
- 这是一个无穷维的问题，为什么？显然，这是一个序贯决策问题。我们可以从 $u(t)$ 上选取无限个点。
- 这个问题的解实际上是一个开环控制，整个过程中没有任何的反馈环节

它的离散时间版本是：
$$
\min_{u} J(x_{i},u_{i}) = \sum_{i=1}^{N-1} l(x_{i},u_{i}) + l_{f} (x_{n}) 
$$
$$
s.t. \ x_{n+1} = f(x_{n},u_{n})\quad u_{\min} \le u \le u_{\max}  \quad c(x_{n}) \le 0 
$$
- 显然，这是一个有限维的问题
- $x_{i},u_{i}$ 这些点被称为“节点”(Knot Point)

## 极值原理
### 一阶必要条件
在这里，我们只考虑动力学约束。我们将使用微积分的方法完成对极值原理的推导，而不是变分法。
构造拉格朗日量：
$$
L = \sum_{i} l(x_{i},u_{i}) + \lambda_{i+1}^{T} (f(x_{i},u_{i}) - x_{i+1} ) + l_{F}(x_{N})
$$
我们定义系统的哈密顿量是：
$$
H(x,u,\lambda) = l(x,u) + \lambda^{T} f(x,u)
$$
将其代入拉格朗日量：
$$
L = H(x,u,\lambda_{2}) + \left[\sum_{i=2}^{N-1} H(x_{i},u_{i},\lambda_{i+1}) - \lambda_{i}^{T}x_{i}\right] + l_{F}(x_{N}) - \lambda_{N}^{T}X_{N}
$$
求导：
$$
\frac{\partial L}{\partial \lambda_{i}} = \frac{\partial H}{\partial \lambda_{i}} - x_{i+1} = 0 
$$
$$
\frac{\partial L}{\partial x_{i}} = \frac{\partial H}{\partial x_{i}} - \lambda_{i}^{T} = 0 
$$
注意 $x_{N}$ 要单独处理：
$$
\frac{\partial L}{\partial x_{N}} = \frac{\partial l_{F}}{\partial x_{N}} - \lambda_{N}^{T} = 0 
$$
$$
u_{i} = \arg \min_{u} H(x_{i},u,\lambda_{i+1})
$$
我们显然可以看到经典力学中的正则方程，但是，这个正则方程是逆向的！方程右侧的 $H$ 中包含 $\lambda_{i+1}$，但是左侧是 $\lambda_{i}$ 

对于连续时间的版本：
$$
\dot x  = \nabla_{\lambda} H \quad \dot \lambda = -\nabla_{x}H \quad u = \arg \min_{u}H \quad \lambda(t_{f}) = \frac{\partial l_{f}}{\partial \lambda}
$$
那么，我们如何求解这个方程组？特别是方程组中有一个“逆时而行”的方程？实际上，很多方法尝试前向/后向对方程组进行积分从而梯度下降地求解 $u(t)$，这种方法被称为“打靶法 (Shooting Method)”


