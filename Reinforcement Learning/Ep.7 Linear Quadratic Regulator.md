#RL 

## LQR 问题的提出
$$
\min_{x,u} J = \sum_{i=1}^{N-1} \frac{1}{2} x_{i}^{T} Q_{i} x_{i}  + \frac{1}{2} u_{i} R_{i}u_{i} +  \frac{1}{2} x_{N}^{T} Q_{N} x_{N}
$$
$$
s.t. \quad x_{i+1} = A_{i} x_{i} + B_{i} u_{i} 
$$
我们规定 $Q$ 半正定，$R$ 必须严格正定。这个问题可以（在局部）近似许多非线性的问题。

## 使用打靶法求解 LQR 问题
我们只考虑时不变的情况，注意到：
$$
x_{i+1}= \nabla_{\lambda}H (x_{i},u_{i},\lambda_{i-1}) = Ax_{i} + B u_{i}
$$
$$
\lambda_{i} = \nabla_{\lambda}H (x_{i},u_{i},\lambda_{i+1})  = Q x_{i}+ A^{T} \lambda_{i+1}
$$
$$
\lambda_{N} =  Q_{N} x_{N}
$$
$$
u_{i} = \arg \min_{u} H(x_{i},u,\lambda_{i+1}) =  - R^{-1}B^{T}\lambda_{i+1}
$$
求解的步骤是：
- 初始化一个初始解 $u$
- 模拟 $x$ 的轨迹
- 使用模拟的 $x$ 轨迹， 反向推出 $\lambda$ 和 $u$
- 计算 $\Delta u$， 使用线搜索搜索 $\Delta u$，使得性能指标下降
- 回退到第 2 步，直至收敛
它的本质就是从一个控制量 $u$ 开始猜，不断按照 $u \rightarrow x \rightarrow \lambda \rightarrow u$ 的顺序猜，直到性能指标足够小，实际上和梯度下降差不多，对于很多问题，这种方法无法保证得到全局最优解。

例如，考虑一个无摩擦的质点，建模结果是：
$$
A = \begin{bmatrix}1 & h  \\ 0 & 1 \end{bmatrix} \quad B = \begin{bmatrix} \frac{1}{2}h^{2} \\ h\end{bmatrix}
$$
控制量 $u$ 是合外力。
**注意：我们可以把对终端条件的约束放到 $Q_{N}$ 里面** 
一个小技巧是把各个变量缩放到同一个数量级上，否则容易导致梯度爆炸等问题


## 将 LQR 问题视作二次规划
假定 $x_{1}$ 给定，将决策变量向量记为：
$$
z = [u_{1},x_{2},u_{2},\cdots ,x_{N}]^{T}
$$
为了便于书写，定义：
$$
H = \mathrm{diag} (R_{1},Q_{2},R_{2},\cdots ,Q_{N})
$$
那么，我们的目标函数为：
$$
J = \frac{1}{2} z^{T}H z
$$
接下来我们定义约束条件：
$$
C = \begin{bmatrix} B & -I & 0 & 0 & \cdots  \\ A  & B & -I & 0  & \cdots  \\ \cdots  & \cdots & A_{N-1}& B_{N-1} & -I  \end{bmatrix}
$$
$$
d = \begin{bmatrix}-A x_{1} & 0 & 0 & \cdots & 0\end{bmatrix}
$$
那么，我们有约束条件：
$$
Cz = d
$$
写出拉格朗日量：
$$
L(z, \lambda) = \frac{1}{2} z^{T}H z + \lambda^{T}(Cz - d)
$$
写出 KKT 条件：
$$
\nabla_{z} = Hz + C^{T }\lambda= 0 
$$
$$
\nabla_{\lambda}L = Cz - d = 0
$$
那么容易写出我们求解的方程组是：
$$
\begin{bmatrix} H & C^{T}   \\  C & 0\end{bmatrix} \begin{bmatrix} z  \\  \lambda\end{bmatrix} = \begin{bmatrix} 0 \\ d \end{bmatrix}
$$
显然，这个方程有一个解析解。


## Riccati Recursion 

我们考虑把上面矩阵方程中的某些行写出来。首先，终止条件：
$$
Q_{N}x_{N} - \lambda_{N} = 0
$$
第一种递推 （使用 $x_{i}$ 表示 $u_{i}$）：
$$
R u_{i} + B^{T} \lambda_{i+1}  = 0 \Rightarrow  Ru_{i} + B^{T}Q_{i+1}x_{i+1} = 0 \Rightarrow Ru_{i}+ B^{T}Q_{i+1}(Ax_{i}+ Bu_{i}) = 0
$$
第二种递推（使用 $x_{i}$ 表示 $\lambda_{i}$）：
$$
Qx_{i}- \lambda_{i}+ A^{T} \lambda_{i+1}= 0 \Rightarrow Qx_{i} - \lambda_{i} + A^{T}Q_{i+1}x_{i+1} = 0 \Rightarrow Qx_{i} - \lambda_{i} + A^{T}Q_{i+1} (Ax_{i}+ B u_{i}) = 0 
$$

我们记：
$$
u_{i}= - K_{i}x_{i} \quad \lambda_{i} = P_{i}x_{i}
$$
那么我们容易得到递推式：
$$
P_{N}  = Q_{N}
$$
$$
K_{i} = (R + B^{T} P_{i+1} B)^{-1} B^{T} P_{i+1}A 
$$ $$
P_{i} = Q + A^{T} P_{i+1}(A-BK_{i})
$$
那么我们可以通过反向的 Riccati 递推求解这个二次规划问题，通过前向计算来求解 $x,u$ 序列。这个做法可以减小算法的时间复杂度。原始的二次规划方法的时间复杂度是 $O(N^{3}(n+m)^{3})$，但是 Riccati 递推的时间复杂度是 $O(N(n+m)^{3})$ 。
这个算法首先计算 $K,P$ 矩阵序列，这些矩阵序列的计算不依赖于初始条件。当我们给出新的初始条件 $x_{1}$，我们就可以相应地计算控制量 $u_i$ 和状态序列 $x_{i}$，此外，这里的控制量 $u_{i}$ 是根据 $x_{i}$ 实时计算的，而不是在一开始就生成的，因此这是一个**闭环控制策略**。



