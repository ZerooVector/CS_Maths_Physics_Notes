#RL  

### 其他的 MPC 例子
- 例子：火箭降落
在建模火箭的运动时，我们通常将平动部分和转动部分解耦合，这里我们只考虑平动。在实际的工程应用中，这个问题的可行域是一个锥。
- 例子：Legged Robot
如何使得机器人的腿不滑动，这个问题的可行域也是一个锥（摩擦锥）。为了简单而迅速地求解这个问题，我们可以将摩擦锥使用其内接正四面体来近似（或其他类似的近似方法）。

## 非线性最优控制问题
在非线性的情况下，我们将遇到诸多挑战：
- 需要更多次牛顿迭代才能收敛，运算速度更慢
- 容易找到局部最优

我们来考虑一个非线性的问题：
$$
\min_{u} J  = \sum_{i=1}^{N-1} l_{i}(x_{i},u_{i}) + l_{N}(x_{N})
$$
$$
s.t. \quad  x_{i+1} = f(x_{i},u_{i})
$$
$$
x_{i} \in \mathcal{X}_{i}  \quad  u_{i}\in \mathcal{U}_{i} 
$$

通常，我们假定损失函数和约束都有二阶连续导数

## Differential Dynamics Programming / 微分动态规划
这是一种近似动态规划方法，其基本思想是：使用状态价值函数 $V(x)$ 的二阶展开近似 $V(x)$
$$
V_{i}(x + \Delta x) = V_{i}(x) + p_{i}^{T} \Delta x  + \frac{1}{2} \Delta x^{T} P_{n}\Delta x
$$
其中，我们使用 $p$ 代表梯度，$P$ 代表 Hessian 矩阵
对于动作价值函数的展开：
$$
Q(x + \Delta x,u + \Delta u) = Q(x,u) + \begin{bmatrix}g_{x} \\  g_{u}\end{bmatrix}^{T}\begin{bmatrix} \Delta x   \\  \Delta u\end{bmatrix} + \frac{1}{2}\begin{bmatrix} \Delta x   \\ \Delta u\end{bmatrix}^{T} \begin{bmatrix} G_{xx} & G_{xu}  \\ G_{ux} & G_{uu}\end{bmatrix} \begin{bmatrix}\Delta x   \\  \Delta u \end{bmatrix}
$$
那么，我们写出 Bellman Equation（思考 $V_{N-1}(x)$ 的含义，是最优决策时的损失函数 ）：
$$
V_{N-1 }(x) = \min_{\Delta u} [Q_{N-1}(x,u) + g_{x}^{T} \Delta x  + g_{u}^{T}\Delta u  + \frac{1}{2}(\Delta x^{T}G_{xx} \Delta  x + \Delta u^{T} G_{uu} \Delta u  + \Delta x ^{T} G_{xu} \Delta u  + \Delta u ^{T} G_{ux} \Delta x )] 
$$
>[!note]
>考虑到
$$Q_{N-1 }(x,u) = l_{N-1}(x,u) + V_{N}(f(x,u))$$
展开 $Q(x,u)$ 的时候，我们已经同时对两部分进行了近似：本步的损失和下一步的价值。因此，我们只需要在 $(x,u)$ 附近找到一个最优策略，就能近似地最小化这两部分的和。我们不需要像 LQR 中的动态规划一样，把这两部分拆开写。

通过要求 $\nabla_{u} V_{i-1}(x)=0$，我们得到：
$$
g_{u}+ G_{uu}\Delta u + G_{ux} \Delta x  = 0 
$$
从而我们可以得到控制量的变化：
$$
\Delta u_{N -1}= - G_{uu}^{-1}  g_{u}- G_{uu}^{-1} G_{ux} \Delta x = - d_{N-1} - K_{N-1} \Delta x
$$
接下来，我们只需要将 $\Delta u_{N-1}$ 代入上面 $V_{N-1}(x)$ 的方程，就可以完成一步递推：
$$
V_{N-1}(x + \Delta x) =  V_{N-1}(x) + g_{x}^{T} \Delta x  + g_{u}^{T} (- d_{N-1}  - K_{N-1} \Delta x ) + \frac{1}{2} \Delta x^{T} G_{xx} \Delta x  + (d_{N-1}+ K_{N-1} \Delta x)^{T} G_{uu}(d_{N-1}+ K_{N-1} \Delta x) - \frac{1}{2} \Delta x^{T} G_{xu} (d_{N-1}+ K_{N-1} \Delta x) - \frac{1}{2}  (d_{N-1}+ K_{N-1} \Delta x) G_{ux} \Delta x 
$$
>[! note]
>注意这里的 
> $$V_{N-1}(x) = V_{N}(f(x,u)) + l_{N-1}(x,u) = Q_{N-1}(x,u)$$
> 所以我们直接把上面的最小化式子里面除了 $Q_{N-1}(x,u)$ 以外的东西加过来就行

对比一下上文中 $V(x)$ 的展开式，注意到：
$$
P_{N-1} = G_{xx}+ K_{N-1}^{T }G_{uu} K_{N-1}  - G_{xu}K_{N-1} - K_{N-1}^{T} G_{ux}
$$
$$
p_{N-1}= g_{x} - K_{N-1}^{T} g_{u} + K_{N-1}^{T}G_{uu} d_{N-1}  - G_{xu}d_{N-1}
$$

## 补充内容：一些矩阵微积分
我们考虑一个函数 $f (x): \mathbb{R}^{n} \rightarrow \mathbb{R}^{m}$，我们希望看看它被展开到二阶的样子：
$$
f(x + \Delta x ) = f(x)  +  \frac{\partial f}{\partial x} \Delta x  + \frac{1}{2} (\frac{\partial }{\partial x}(\frac{\partial f}{\partial x} \Delta x ))
$$
其中，$\frac{\partial f}{\partial x}$ 是一个 $\mathbb{R}^{m\times n}$ 矩阵，被称为 Jacobian 矩阵。我们并不想在这里写出 $\frac{\partial^{2} f}{\partial x^{2}}$，因为这是一个（计算机科学中的）张量

我们介绍一个 Kronecker 积：
$$
A \otimes B = \begin{bmatrix}a_{11}B & a_{12} B & \cdots  \\ a_{21} B & a_{22}B  & \cdots  \\ \cdots & \cdots & \cdots \end{bmatrix}
$$
再介绍一些矢量化算符。我们知道，一个矩阵 $A$ 可以被写成：
$$
A= \begin{bmatrix} A_{1} & A_{2}& A_{3}& \cdots \end{bmatrix}
$$
我们定义：
$$
\mathrm{vec}(A) = \begin{bmatrix}A_{1} \\  A_{2}  \\ A_{3} \\ \cdots \end{bmatrix}
$$
也就是把 $A$ 的所有列向量拼接在一起。那么我们有：
$$
\mathrm{vec}(ABC) = (C^{T}\otimes A) \mathrm{vec}(B)
$$
$$
\mathrm{vec}(AB) = (B^{T}\otimes I) \mathrm{vec}(A) = (I \otimes A) \mathrm{vec}(B)
$$
那么，我们可以方便地写出矩阵对一个向量求微分的结果
$$
\frac{\partial A(x)}{\partial x} = \frac{\partial \mathrm{vec}(A)}{\partial x}
$$



那么：
$$
f(x + \Delta x) = f(x)  + \frac{\partial f}{\partial x}\Delta x  + \frac{1}{2} (\Delta x^{T} \otimes I ) \frac{\partial^{2}f }{\partial x^{2}} \Delta x 
$$
有的时候，我们需要利用转置来求出这个微分：
$$
\frac{\partial }{\partial x} (A(x)^{T}B) = (B^{T} \otimes I) T \frac{\partial A}{\partial x}
$$
其中
$$
T \mathrm{vec(A)} = \mathrm{vec}(A^{T})
$$
接下来，我们开始对动作价值函数求导：
$$
S_{i}(x,u) = l_{i}(x,u) + V_{i+1}(f(x,u))
$$
$$
\frac{\partial S}{\partial x} = \frac{\partial l}{\partial x}+ \frac{\partial V}{\partial x}\frac{\partial f}{\partial x} \quad \frac{\partial S}{\partial u} = \frac{\partial l}{\partial u}  + \frac{\partial V}{\partial f} \frac{\partial f}{\partial u}
$$

我们记 $\frac{\partial f}{\partial x} = A,\frac{\partial f}{\partial u} = B$，我们得到：
$$
g_{x}= \nabla_{x}l + A_{i}^{T} p_{i+1} \quad g_{u} = \nabla_{u}l + B_{i}^{T }p_{i+1}
$$
$$
G_{xx}= \nabla_{xx}^{2}l(x,u) + A_{i}^{T}\nabla^{2}V_{i+1} A_{i} + (p_{i+1} \otimes I) T \frac{\partial A}{\partial x}
$$
其余的 $G_{xu},G_{ux},G_{uu}$ 可做类似推导，在这里不再继续推导。
在后面一节课中，我们将继续讨论微分动态规划的实施细节。



