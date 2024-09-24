#DifferentialGeometry 

## 嘉当的巧妙想法
在之前研究三维曲线时，我们给出了能沿着曲线移动的坐标系：
$$
\begin{bmatrix}T  \\  N  \\  B\end{bmatrix}' = \begin{bmatrix}0 & \kappa& 0  \\  - \kappa& 0 & \tau  \\ 0 & - \tau & 0 \end{bmatrix} \begin{bmatrix}T  \\ N  \\ B \end{bmatrix}
$$
这里的 $T$ 是切向，$N$ 是法向，而 $B$ 是副法向。这个方法给了我们很多有益的启发：
- 构造了一个与曲线相适应的标架
- 用标架**本身**描写标架的变化率
现在，嘉当提出了他的“活动标架法”，将上面这个标架推广到曲面上的同时又做了许多改进。这里我们首先考察 $\mathbb{R}^{3}$ 中的二维曲面：
- 选择一个向量成为曲面的法向，那么我们自然得到两个切向量，也就得到了与曲面相适应的标架
- 完全解除标架的限制，使得它不仅能沿着曲面滑动，更能在 $\mathbb{R}^{3}$ 中以任意“可微的”方式移动，从而我们可以得到一个标架场
- 将标架用协变矢量而不是逆变矢量表示，使用协变基底本身表示协变基底的变化率。
- 嘉当得到了任意形式的结构方程，然后将它们应用到特定的几何对象上。

## 控制着标架变换的"联络"
我们首先明确哟下符号：
- 向量 $\boldsymbol{v}$
- 1-形式 $\boldsymbol{\theta}$
- 2-形式 $\boldsymbol{\Psi}$
- 矩阵 $[A]$
- 设 $\{e_{i}\}$ 是固定的欧几里得正交基，具有对偶的协变基底 $\{\mathbf{d}x^{i}\}$，$\mathbf{d}x^{i}(e_{j}) = \delta^{i}_{j}$
- 设 $\{m_{i}\}$ 是嘉当正交活动标架场，具有对偶的协变基底 $\{\theta^{i}\}$，$\theta^{i}(m_{j}) = \delta^{i}_{j}$
提请注意：在正交基的情况下，一个逆变基底 $e_{1}$ 的改变仅引起与其下标相同的协变基底 $\mathbf{d}x^{1}$ 的改变，因此我们可以在这种情况下说一个逆变基底只与一个协变基底对偶！

那么我们现在希望用标架本身表示标架的变化率。由于此时的标架是充满了全空间的标架场，因此我们希望看看它是如何沿着 $\mathbb{R}^{3}$ 中的任意向量 $v$ 变化的，那么我们用一个暂时未知的矩阵 $[C]$ 表示这种变化：
$$
\nabla_{v} [m] = [C][m]
$$
由于标架的正交性，我们可以得到矩阵中的系数：
$$
\omega_{ij}(v) = [C]_{ij} = (\nabla_{v} m_{i}) \cdot m_{j}
$$
代表了标架沿着 $v$ 运动时，$m_{i}$ 转向 $m_{j}$ 的初始速率。为什么我们在这里切换符号？根据上面的符号约定，这意味着我们发现**每一个**$\omega_{ij}$ 全都是 1-形式，$\omega_{ij}$ 的下标不代表着它是 $(0,2)$ 阶张量，只代表着它在矩阵中的位置。很容易验证它们都是 1-形式，此外可以得到：
$$
0 = \nabla_{v}(\delta^{i}_{j}) = \nabla_{v}(m_{i} \cdot m_{j}) = \omega_{ij}(v) + \omega_{ji}(v) \Rightarrow \omega_{ij}(v) = - \omega_{ji}(v)
$$
因此，装载有 1-形式的 $[\omega]$ 矩阵事实上是反对称矩阵，其中只有三个独立参数。至此，我们形式化地得到了描述标架场变换的联络方程组：
$$
\nabla_{v} [m] = [\omega(v)] [m] \quad  \nabla_{v} m_{i} = \sum_{j} \omega_{ij}(v) m_{j}
$$
取 $m_{1}=T, m_{2} = N, m_{3} = B , v=T$，可以恢复出曲线上的结果。注意：从几何关系上可以看出，一对向量 $(T,N)$ 绕着轴 $B$ 旋转，这意味着 $T$ 不会向着 $B$ 倾斜，因此有 $\omega_{13}(v) = 0$。

## 描述标架场最终姿态的“姿态矩阵”
显然，如果我们要描述标架场 $\{m_{i}\}$ 的形态，其实只需要知道我们怎么转一转 $\{e_{i}\}$，使之与 $\{m_{i}\}$ 重合，这显然只需要一个正交的旋转矩阵来描述：
$$
[m] = [A][e]
$$
我们定义：一个矩阵的外导数就是其每个元素的外导数重新组成的矩阵：$\mathbf{d}[A] = [\mathbf{d}a_{ij}]$，现在我们证明联络 1-形式的矩阵可以表示为：
$$
[\omega] = (\mathbf{d}[A])[A]^{T} \quad  \omega_{ij}  = \sum_{k}  (\mathbf{d}a_{ik}) a_{jk}
$$
我们计算活动标架本身的转向率：
$$
\nabla_{v} m_{i} = \nabla_{v} \sum_{k}  a_{ik} e_{k}  = \sum_{k} (\mathbf{d}a_{ik}) (v) e_{k}
$$
现在我们来看 $m_{i}$ 向着 $m_{j}$ 的方向偏离了多少，很容易发现：
$$
\omega_{ij}(v) = (\nabla_{v} m_{i}) \cdot m_{j} = \sum_{k} (\mathbf{d}a_{ik}(v)) a_{jk}
$$
从而哦我们证明了结果。

我们举一个例子看看到目前为止我们的成果：
![[Pasted image 20240825130232.png]]

我们构造的柱面标架场是：
$$
\begin{align*}
m_{1}&= \cos  \theta e_{1} + \sin \theta e_{2} \\
m_{2}&= - \sin \theta  e_{1} + \cos  \theta  e_{2}  \\
 m_{3} &= e_{3} 
\end{align*}
$$
姿态矩阵和联络 1-形式矩阵可以被计算为：
$$
\begin{bmatrix}A\end{bmatrix}  =\begin{bmatrix}\cos  \theta & \sin \theta & 0   \\ - \sin  \theta & \cos \theta & 0  \\ 0 &  0 & 1 \end{bmatrix}
\quad  
[\omega] = \begin{bmatrix} 0 &  \mathbf{d} \theta & 0  \\  - \mathbf{d} \theta&  0 &  0  \\ 0 & 0 &  0 \end{bmatrix}
$$
那么我们就得到了：
$$
\nabla_{v} m_{1} = \mathbf{d} \theta(v) m_{2}, \ \nabla_{v} m_{2} = - \mathbf{d} \theta (v) m_{1} ,\  \nabla_{v}  m_{3} = 0 
$$
从下图中，很容易用几何关系证明这一点：
![[Pasted image 20240825130811.png]]

## $(\star )$ 嘉当的两个结构方程
现在，我们将使用协变基底 $\theta^{i}$ 代替逆变基底 $m_{i}$，那么，同一个旋转矩阵将 $\mathbf{d}x$ 旋转到 $\theta$
$$
[\theta] = [A] [\mathbf{d}x] \quad \theta^{i} = \sum_{j} a_{ij} \mathbf{d}x^{j}
$$
这个证明是显然的。因为 $\theta^{i}$ 是 $m^{i}$ 的对偶，因此根据里斯表示定理：
$$
\theta^{i}(e_{j}) = m_{i}\cdot e_{j} = \left[\sum_{k}  a_{ik} e_{k}\right]  \cdot e_{j} =a_{ij}
$$
### 嘉当第一结构方程
现在，我们当然想问：对偶 1-形式 $\theta$ 在空间中是如何变化的？这正是嘉当第一结构方程
$$
\mathbf{d}[\theta] = [\omega] \wedge  [\theta]
$$
这个证明只需要简单计算，首先我们有：
$$
[\theta] = [A] [\mathbf{d}x]
$$
式子两侧求外导数：
$$
\mathbf{d} [\theta] = \mathbf{d}[A] \wedge  [\mathbf{d}x] = \mathbf{d}[A][A]^{T} \wedge  [A][\mathbf{d}x] = [\omega] \wedge  [\theta] \quad  \mathbf{d} \theta^{i} =\sum_{j}\omega_{ij} \wedge  \theta^{j}
$$

### 嘉当第二结构方程
我们自然也想问：控制着标架变化的联络是如何变化的，这需要嘉当第二结构方程：
$$
\mathbf{d}[\omega] = [\omega ] \wedge  [\omega]
$$
我们给一个关于外微分计算的引理，设 $f,g$ 都是函数（$0$ -形式），那么：
$$
\mathbf{d}((\mathbf{d}f)g) =  \mathbf{d} g \wedge  \mathbf{d}f = - \mathbf{d}f \wedge \mathbf{d}g
$$
现在，对联络矩阵两侧外微分：
$$
\begin{align*}
\mathbf{d}[\omega] &= \mathbf{d}[(\mathbf{d}[A])[A]^{T}]\\
&= - (\mathbf{d}[A]) \wedge  \mathbf{d}[A]^{T} \\
&= - (\mathbf{d}[A])[A]^{T} \wedge  [A] \mathbf{d}[A]^{T} \\
&= - (\mathbf{d}[A])[A]^{T} \wedge [(\mathbf{d}[A])[A]^{T}]^{T}\\
&= - [\omega] \wedge [\omega]^{T} \\
&= [\omega] \wedge [\omega]
\end{align*} 
$$
具体计算的时候我们也使用分量式：
$$
\mathbf{d} \omega_{ij} = \sum_{k} \omega_{ik} \wedge  \omega_{kj}
$$
嘉当的两个结构方程可以统一地被写为：
$$
\mathbf{d}[\cdot] = [\omega] \wedge [\cdot ]
$$
### 例子：球面标架场
我们再球面标架场上用一下两个结构方程。很容易用几何关系给出旋转矩阵 $[A]$：
![[Pasted image 20240825151822.png]]
$$
A = \begin{bmatrix}s_{\phi} c_{\theta}& s_{\phi}s_{\theta}& c_{\phi} \\ c_{\phi}c_{\theta}&  c_{\phi} s_{\theta} & - s_{\phi}   \\  - s_{\theta}& c_{\theta} & 0 \end{bmatrix}
$$
我们只需计算联络矩阵中三个有效的分量：
$$
\begin{align*}
\omega_{12} &= \mathbf{d} \phi \\
\omega_{13}  &= \sin \phi  \mathbf{d} \theta \\
\omega_{23} &= \cos \phi  \mathbf{d} \theta
\end{align*}
$$
同样，我们也可以计算与逆变标架对偶的协变基底，但是我们也可以通过几何方式找到。例如考虑图中的小平行六面体，它的对角线是：
$$
v = \delta r m_{1}+ r \delta \phi m_{2} + rs_{\phi} \delta \theta m_{3}
$$
根据对偶基的定义，我们显然有：
$$
\begin{align*}
\theta^{1} &= \mathbf{d}r \\
\theta^{2} &= r \mathbf{d} \phi \\
\theta^{3} &= r s_{\phi}\mathbf{d} \theta
\end{align*}
$$
我们可以通过分量式计算楔积，从而验证：
$$
\mathbf{d} [\theta ] = \begin{bmatrix}0  \\ \mathbf{d}r \wedge \mathbf{d} \theta  \\  s_{\phi} \mathbf{d}r \wedge \mathbf{d} \theta+ r c_{\phi}   \mathbf{d} \phi  \wedge  \mathbf{d} \theta \end{bmatrix}
$$
以及：
$$
\mathbf{d}[\omega] = \begin{bmatrix}0 & 0 &  c_{\phi} \mathbf{d} \phi \wedge  \mathbf{d} \theta  \\ 0 & 0  &  -s_{\phi} \mathbf{d} \phi  \wedge \mathbf{d}\theta \\ -c_{\phi} \mathbf{d} \phi \wedge \mathbf{d}\theta & s_{\phi} \mathbf{d}\phi \wedge \mathbf{d}\theta  & 0 \end{bmatrix}
$$
实际上，之前我们的联络矩阵中的分量也是可以使用一些几何方法算出来的。在 $v$ 很短的时候，$\nabla_{v}  m_{i}$ 就是 $m_{i}$ 沿着 $v$ 从起点到终点的变化。如图，我们这里只讨论 $\omega_{12}(v)$：考虑一下 $m_{1}$ 沿着某个短向量 $v$ 移动时它会发生什么变化：
![[Pasted image 20240825155224.png]]
- 沿着 $\delta r m_{1}$ 移动时，$m_{1}$ 保持不变
- 沿 $rs_{\phi} \delta \theta  m_{3}$ 移动时，$m_{1}$ 将产生沿着 $m_{3}$ 方向的变化：$\delta m_{1} = s_{\phi} \delta \theta m_{3}$
- 沿 $r \delta \phi m_{2}$ 移动时，$m_{1}$ 将产生沿着 $m_{2}$ 方向的变化：$\delta m_{1} = \delta \phi m_{2}$
总计以上，我们就能得到结论：
$$
\omega_{12} = \mathbf{d} \phi
$$
其余的两个元素也可以通过类似的分析得到：
$$
\omega_{13} = s_{\phi} \mathbf{d} \theta,\  \omega_{23} = c_{\phi} \mathbf{d} \phi
$$

## $(\star )$ 曲面的 6 个基本形式方程
我们现在要把嘉当的标架场放到曲面上，看看能得到什么。给定曲面 $\mathcal{S}$，它的法向量为 $n$，那么我们选择 $m_{3} = n$，那么 $m_{1},m_{2}$ 自然成为了曲面内向量 $v$ 的一组基底。那么我们先来看形状导数（法向量 $n$ 沿着向量 $v$ 的变化）：
$$
\begin{align*}
S(v) &= - \nabla_{v} n \\
&= - \nabla_{v} m_{3} \\
&= -[\nabla_{v} m_{3} \cdot m_{1}]m_{1} - [\nabla_{v} ,_{3} \cdot m_{2}] m_{2} \\
&= \omega_{13}(v)m_{1} + \omega_{23}(v) m_{2} 
\end{align*}
$$
因此我们用联络矩阵中的元素表示了形状导数，形状导数的矩阵显然就是：
$$
[S] = \begin{bmatrix}\omega_{13}(m_{1}) & \omega_{13}(m_{2})  \\ \omega_{23} (m_{1}) & \omega_{23}(m_{2})\end{bmatrix}
$$
我们之前所说的外在曲率就是球面映射的面积扩展因子，也就是：
$$
\mathcal{K}_{ext}= \det[S] = \omega_{13}(m_{1}) \omega_{23}(m_{1}) - \omega_{13}(m_{2}) \omega_{23}(m_{2}) = (\omega_{13} \wedge \omega_{23})(m_{1},m_{2})
$$
现在，对偶于标架场的协变基底的作用就是给出切向量 $v$ 在标架场中的坐标：$\theta^{i}(v) =v \cdot m_{i}$，注意任意切向量 $v$ 在 $m_{3}$ 上的坐标都为 0.

我们现在要说明，1-形式和 2-形式的基底分解也具有唯一性，也就是说，此时曲面上的 1-形式可以唯一地分解为：
$$
\phi = \phi(m_{1}) \theta^{1} + \phi(m_{2}) \theta^{2} 
$$
曲面上的 2-形式则可以被唯一分解为：
$$
\Psi = \Psi (m_{1},m_{2})\mathcal{A}  = \Psi (m_{1},m_{2}) \theta^{1} \wedge \theta^{2} 
$$
那么我们有：
$$
\omega_{13}\wedge \omega_{23} =(\omega_{13}  \wedge \omega_{23}) (m_{1},m_{2}) \theta^{1} \wedge \theta^{2}  = \mathcal{K}_{ext} \theta^{1} \wedge  \theta^{2}
$$

这样，我们将标架场依附在曲面上之后，再次利用嘉当的第一结构方程和第二结构方程，就得到了关于曲面的六个基本方程（这些方程都可以依赖嘉当的两个结构方程计算得到）：
$$
\begin{align*}
\mathbf{d} \theta^{1}&=   \omega_{12} \wedge \theta^{2}  \\
\mathbf{d} \theta^{2} &= \omega_{21} \wedge \theta^{1} \\
\omega_{31} \wedge\theta ^{1}  + \omega_{32} \wedge \theta^{2} &= 0   \\
\mathbf{d} \omega_{12} &= \omega_{13} \wedge \omega_{32} \\
\mathbf{d} \omega_{13} &= \omega_{12} \wedge \omega_{23} \\
\mathbf{d}\omega_{23} &= \omega_{21} \wedge \omega_{13}
\end{align*}
$$


## $(\star )$ 曲面的基本方程能做些什么？
刚才，我们一下子扔下了六个方程（而且，我们在讲解如何将坐标系“依附”在曲面上时是使用逆变基描述的，而这六个方程都在描述协变基和联络），现在我们一定要问：这些方程会如何帮助我们理解曲面？

### 第 3 个方程和第 $(5,6)$ 个方程
首先我们将第 3 个方程应用到曲面切平面的基向量上：
$$
\begin{align*}
0&= [\omega_{31} \wedge \theta^{1} + \omega_{32} \wedge \theta^{2}] (m_{1},m_{2})\\
&= \omega_{31} (m_{1}) \theta^{1} (m_{2}) - \omega_{31} (m_{2}) \theta^{1}(m_{1}) + \omega_{32} (m_{1}) \theta^{2} (m_{2}) - \omega_{32} (m_{2})\theta^{2}(m_{1})\\
&= \omega_{32} (m_{1}) - \omega_{31}(m_{2})
\end{align*}
$$
因此，这实际上意味着形状导数矩阵 $S$ 是一个对称矩阵（这个方程被称为对称性方程）！我们早已知道 $S$ 的本征矢量是正交的，因此这在意料之内。这些本征矢量就是取得最大、最小法曲率 $\kappa_{1},\kappa_{2}$ 的方向！

我们现在可以将标架场的 $m_{1},m_{2}$ 与这些方向对齐，使得：
$$
[S] = \begin{bmatrix}\omega_{13}(m_{1}) &  \omega_{13}(m_{2})  \\ \omega_{23}(m_{1}) & \omega_{23}(m_{2})\end{bmatrix} = \begin{bmatrix}\kappa_{1} &  0  \\ 0  &  \kappa_{2}\end{bmatrix}
$$

将现在的 $\omega_{13},\omega_{23}$ 的形式代入第 5 个基本方程，我们立刻得到：
$$
\mathbf{d} (\kappa_{1} \theta_{1}) = \omega_{12} \wedge \kappa_{2} \theta ^{2}  \Rightarrow \mathbf{d} \kappa_{1} \wedge \theta^{1} + \kappa_{1} \mathbf{d} \theta^{1} = \kappa_{2} \omega_{12} \wedge \theta^{2}
$$
再利用第 1 个基本方程，我们得到：
$$
\mathbf{d} \kappa_{1} \wedge \theta^{1} + \kappa_{1} \omega_{12} \wedge \theta^{2} = \kappa_{2} \omega_{12} \wedge \theta^{2}  \Rightarrow  \mathbf{d}\kappa_{1} \wedge \theta^{1} = (\kappa_{2} - \kappa_{1}) \omega_{12} \wedge \theta^{2}
$$
将方程两端作用在 $(m_{1},m_{2})$ 上，就得到了：
$$
\nabla_{m_{2}} \kappa_{1} = (\kappa_{1}  -\kappa_{2}) \omega_{12}  (m_{1})  \quad \nabla_{m_{1}} \kappa_{1} = (\kappa_{1}  -\kappa_{2}) \omega_{12}  (m_{2}) 
$$
它的几何意义是：当我们与某个主方向成直角运动时，主曲率的变化率正比于两个主曲率之差和主方向旋转速率的乘积。

### 第 4 个方程
第四个方程被称为高斯方程，它掌握了内蕴曲率与外在曲率联系的关键，这是因为它可以被重写为：
$$
\mathbf{d} \omega_{12} = - \mathcal{K}_{ext}\theta^{1} \wedge \theta^{2}
$$
例如我们在球面上计算 $\mathbf{d} \omega_{12} = - \dfrac{1}{R^{2}} \theta^{1} \wedge \theta^{2}$，我们立刻得到球面上的外在曲率。

### 度量曲率公式和高斯绝妙定理的证明
我们首先说明：$\omega_{12} = - \omega_{21}$ 是唯一满足第 $(1,2)$ 这两个方程的 1-形式。证明方案很简单，直接将这两个 2-形式作用在基向量 $(m_{1},m_{2})$ 上，立刻得到：
$$
\omega_{12}(m_{1})  = \mathbf{d} \theta^{1}(m_{1},m_{2}) \quad  \omega_{12} (m_{2})  = \mathbf{d} \theta^{2} (m_{1},m_{2})
$$
利用一个 1-形式在一组基底下分解的唯一性立刻得到 $\omega_{12}$ 是唯一的。现在我们开始证明曲率度量公式。从一般情形下的度量公式（此时，我们已经将“网格”选在了两个正交的方向上）：
$$
ds^{2} = (Adu)^{2} + (Bdv)^{2}
$$
可以推导出一组协变基底：
$$
\theta^{1} = A \mathbf{d}u \quad  \theta^{2} =  B \mathbf{d}v
$$
面积 2-形式是：
$$
\mathcal{A} = \theta^{1} \wedge \theta^{2} = AB \mathbf{d} u \wedge \mathbf{d}v
$$
我们计算这一组协变基的外导数：
$$
\mathbf{d} \theta^{1} = \mathbf{d}A  \wedge \mathbf{d}u = \partial_{v} A \mathbf{d} v  \wedge   \mathbf{d}u = - \dfrac{ \partial_{v} A}{B}  \mathbf{d} u \wedge \theta^{2}  
$$
同理我们也有：
$$
\mathbf{d} \theta^{2} = - \dfrac{ \partial_{u} B}{A} \mathbf{d}v \wedge \theta^{1} 
$$
将其与方程 1 比较，我们立刻看到 $\omega_{12}$ 的一个可能的解是：
$$
\omega_{12} = - \dfrac{\partial_{v} A}{B}  \mathbf{d} u + \dfrac{\partial_{u}  B}{A}  \mathbf{d}v
$$
对它再求外导数：
$$
\mathbf{d}\omega_{12}  =\dfrac{1}{AB}\left( \partial_{v} \left(\dfrac{\partial_{v} A}{B}\right)+ \partial_{u}  \left(\dfrac{ \partial_{u} B}{A}\right) \right) \theta^{1} \wedge \theta^{2} 
$$
将其与高斯方程（方程 4）对比，我们也就得到了：
$$
\mathcal{K}_{ext} = - \dfrac{1}{AB}\left( \partial_{v} \left(\dfrac{\partial_{v} A}{B}\right)+ \partial_{u}  \left(\dfrac{ \partial_{u} B}{A}\right) \right)
$$
这里左侧的曲率是外在定义的，而右侧的式子却是完全内蕴的！这正是对高斯绝妙定理的一个证明。

### 一个新的曲率公式
为了简便，现在我们将 $\omega_{12}$ 写成：
$$
\omega_{12} = f_{1} \theta^{1} + f_{2} \theta^{2} \quad  f_{1} = \mathbf{d} \theta^{1}(m_{1},m_{2}) , \ f_{2} = \mathbf{d} \theta^{2} (m_{1},m_{2})
$$
将 2-形式 $\mathbf{d}\omega_{12}$ 直接作用在基向量对 $(m_{1},m_{2})$，那么我们就得到了另一个曲率公式：
$$
\begin{align*}
\mathcal{K} &= - \mathbf{d} \omega_{12}(m_{1},m_{2})\\
&= - [\mathbf{d}f_{1} \wedge \theta^{1}  + f_{1} \mathbf{d} \theta^{1} + \mathbf{d} f_{2} \wedge \theta^{2}  + f_{2} \mathbf{d} \theta^{2}] (m_{1},m_{2})\\
&= \mathbf{d}f_{1}(m_{2}) - \mathbf{d} f_{2}(m_{1}) - f_{1}^{2} -f_{2}^{2} \\
&= \nabla_{m_{2}} f_{1} - \nabla_{m_{1}}   f_{2} - f_{1}^{2} - f_{2}^{2}
\end{align*}
$$

### 希尔伯特引理
希尔伯特证明了如果在曲面上的一点 $p$ 具有以下三个性质，那么曲面在 $p$ 点处的曲率不可能是正的：
- $\kappa_{1}$ 在 $p$ 处取到局部极大值
- $\kappa_{2}$ 在 $p$ 处取到局部最小值
- $\kappa_{1}(p) > \kappa_{2}(p)$
我们来证明一下：由 $\kappa_{1},\kappa_{2}$ 取极值的一阶条件得到：
$$
\nabla_{m_{2}} \kappa_{1} = \nabla_{m_{1}} \kappa_{2} = 0 
$$
再利用二阶条件：
$$
\nabla_{m_{2}} \nabla_{m_{2}} \kappa_{1} \le 0 , \  \nabla_{m_{1}} \nabla_{m_{1}} \kappa_{2} \ge 0 
$$
利用我们在上面得到的结论，有：
$$
\omega_{12}(m_{1}) = \omega_{12}(m_{2}) = 0 
$$
这样，我们刚才推出的新曲率公式就被简化为：
$$
\mathcal{K} = \nabla_{m_{2}}[\omega_{12}(m_{1})]  - \nabla_{m_{1}}[\omega_{12}(m_{2})]
$$
对着我们之前得出的 $\nabla_{m_{2}}\kappa_{1}$ 的结果再求导，得到：
$$
\nabla_{m_{2}} \nabla_{m_{1}} \kappa_{1}= [\nabla_{m_{2}} (\kappa_{1}  - \kappa_{2})] \omega_{12}(m_{1}) + (\kappa_{1} - \kappa_{2}) \nabla_{m_{2}} [\omega_{12} (m_{1})] = (\kappa_{1} - \kappa_{2}) \nabla_{m_{2}} [\omega_{12} (m_{1})]
$$
由于 $\kappa_{1}- \kappa_{2} > 0$，立刻得到：
$$
\nabla_{m_{2}}[\omega_{12}(m_{1})] \le  0 
$$
以同样的逻辑得到：
$$
\nabla_{m_{1}}[\omega_{12}(m_{2})] \ge   0
$$
代入上面简化过的新曲率公式，就完成了证明。

### 利布曼的刚性球面定理
显然，如果曲面具有常正曲率 $\mathcal{K}$ 的曲面的内蕴几何度量一定与半径为 $\dfrac{1}{\sqrt{\mathcal{K}}}$ 的球面一致。但是，这个面不一定是球面！图示的两种面都显示了这一点，或者我们也可以尝试将一个乒乓球切一半，然后压一压，也能发现这一点。但是，一个结论是：嵌入 $\mathbb{R}^{3}$ 的常曲率封闭曲面只能是一个球面，换言之，一个完整的球面是刚性的，它不能被变形成任意的形状。
![[Pasted image 20240825202626.png]]
假设我们考虑的封闭曲面是 $\mathcal{S}$，曲率在 $\mathcal{S}$ 上是处处为正的常数，假设 $\kappa_{1}$ 不是常数，那么它必然在封闭曲面上达到一个最大值，而 $\kappa_{2}$ 就在这一点处达到最小值，这意味着在这一点上不能有 $\kappa_{1} > \kappa_{2}$，因此我们有 $\kappa_{1}^{\max} \le \kappa_{2}^{\min}$ ，而根据我们的定义，我们默认 $\kappa_{1}\ ge  \kappa_{2}$。 因此很容易知道我们应当有 $\kappa_{1}^{\max} = \kappa_{1}^{\min} = \kappa_{2}^{\max} = \kappa_{2}^{\min}$，这意味着在每一点上都有 $\kappa_{1} = \kappa_{2}$，于是这只能是个球面！


## $(\star )$$n$ 维流形上的曲率 2-形式
刚才，我们所有的研究都发生在平坦的 $\mathbb{R}^{3}$ 中，我们现在要说明嘉当的第二结构方程就像是“三角形的内角和是 $\pi$”一样，只在平坦空间中成立。而在弯曲的 $n$ 维流形中，空间的弯曲由方程两侧的差值来刻画：
$$
[\Omega] = \mathbf{d} [\omega] - [\omega] \wedge [\omega]
$$
其中 $[\Omega]$ 称为曲率矩阵，其每个元素都是一个 2-形式：
$$
\Omega_{ij} = \mathbf{d} \omega_{ij} - \sum_{k}  \omega_{ik} \wedge \omega_{kj}
$$
我们要说明这些曲率 2-形式含有和黎曼曲率张量相同的信息。我们在这里重复黎曼曲率张量的定义：
$$
\mathbf{R}(u,v;w) = \mathcal{R}(u,v) w = \{[\nabla_{u} ,\nabla_{v}] - \nabla_{[u,v]}\} w
$$
我们之前实际上从未推导任何直接计算黎曼曲率张量的公式，而现在，我们将给出：
$$
\Omega_{ij}
 = R_{ijkl} \theta^{k}\wedge \theta^{l}
$$

要想得到这个式子，我们需要将外微分 $\mathbf{d}$ 的作用范围推广到形式之外，不过在此之前我们先来改写一下之前用过的符号：
$$
\nabla_{v} m_{j} = \sum_{i}  \omega_{ji}  (v) m_{i}= \sum_{i} \omega^{i}_{j}(v) m_{i} = \omega^{i}_{j}(v)   m_{i}
$$
这样的写法使得我们恢复了爱因斯坦求和记号。我们也能再次从中看到 $\omega_{ji}$ 的几何意义（我们将向量 $j$ 向其他三个方向上的变化求和起来）
现在我们推广外导数 $\mathbf{d}$，定义它对标架场 $m_{j}$ 的作用：
$$
\mathbf{d} m_{j}(v) = \nabla_{v}m_{j} = \omega^{i}_{j} (v) m_{i}
$$
也就是沿着向量 $j$ 移动时，标架场的一个向量 $m_{j}$ 变化了多少，它接受一个向量，输出一个向量，可以看作三个 1-形式排列成一个向量。
我们将推广后的记号 $\mathbf{d}$ 应用到一般的向量场 $w = w^{j}m_{j}$ 上：
$$
\mathbf{d}w = \mathbf{d}[w^{j}m_{j}] = [\mathbf{d}w^{j}]m_{j} + w^{j}\mathbf{d}m_{j} = m_{i}(\mathbf{d}w^{i}+ \omega^{i}_{j} w_{j})
$$
现在，我们再将 $\mathbf{d}$ 作用一次，我们可以发现，最初的性质 $\mathbf{d}^{2}= 0$ 此时不再存在：
$$
\begin{align*}
\mathbf{d}^{2}w &= \mathbf{d}m_{k} \wedge (\mathbf{d}w^{k} +  \omega^{k}_{j}w^{j}) + m_{i}(\mathbf{d}^{2} w^{i} + w^{j} \mathbf{d}\omega^{i}_{j} - \omega^{i}_{j} \wedge \mathbf{d}w^{j})\\
&= \omega^{i}_{k} m_{i} \wedge (\mathbf{d}w^{k} + \omega^{k}_{i}w^{i}) + m_{i}(w^{j} \mathbf{d}\omega^{i}_{j} - \omega^{i}_{k} \wedge \mathbf{d}w^{k})\\
&= m_{i} (\mathbf{d}\omega^{i}_{j} + \omega^{i}_{k} \wedge \omega^{k}_{j}) w^{j}\\
&= m_{i} \Omega^{i}_{j} w^{j}
\end{align*}
$$
中间的 $\Omega^{i}_{j}$ 就是曲率 2-形式。注意我们现在算出的 $\Omega^{i}_{j}$ 和之前定义的 $\Omega_{ij}$ 之间差了一个负号，这使得两个结构方程中都有符号变化：
$$
[\Omega^{i}_{j}] = \mathbf{d}[\omega] + [\omega]\wedge [\omega] 
$$
以及：
$$
\mathbf{d} \theta^{i} = - \omega^{i}_{j} \wedge \theta^{j} 
$$
再考虑我们最初对 1-形式的外导数的定义：
$$
\mathbf{d} \phi (u,v) = \nabla_u \phi(v) - \nabla_v \phi(u) - \phi([u,v])
$$
在上式中，使用 $\mathbf{d}w (v) = \nabla_{v} w$ 来代替 $\phi$，有：
$$
\mathbf{d}^2 w(u,v) = \nabla_u \mathbf{d}w(v) - \nabla_v  \mathbf{d} w(u) - \mathbf{d} w([u,v]) = \mathcal{R} (u,v) w
$$
通过对比这个式子输出的向量与上面推出的另一个 $\mathbf{d}^{2}w$ 输出的向量的各个分量，我们就得到了：
$$
- R^i_{jkl} \theta^k  \wedge  \theta^l  = \Omega^i_j   = \mathbf{d}\omega^i_j  + \omega^i_m \wedge \omega^m_j 
$$

现在，我们可以推导（广义的）比安基恒等式。考虑对 $\theta^{i}$ 求二阶外导数，有：
$$
\begin{align*}
0 &=  - \mathbf{d} \mathbf{d} \theta^{i} \\
&= \mathbf{d}(\omega^{i}_{j} \wedge \theta^{j}) \\
&= \mathbf{d}\omega^{i}_{j} \wedge \theta^{j}  - \omega^{i}_{k} \wedge \mathbf{d} \theta^{k}  \\
&= (\mathbf{d}\omega^{i}_{j} + \omega^{i}_{k}  \wedge \omega^{k}_{j}) \wedge \theta^{j} \\
&= \Omega^{i}_{j} \wedge \theta^{j}
\end{align*}
$$
写成更紧凑的形式，我们就得到了：
$$
[\Omega] \wedge [\theta] = 0 
$$
对于另一个恒等式，只需要将 $\mathbf{d}^{2}$ 作用在联络 1-形式上即可：
$$
\begin{align*}
0 &= - \mathbf{dd} \omega^{i}_{j} \\
&= \mathbf{d}(\Omega^{i}_{j} - \omega^{i}_{k} \wedge \omega^{k}_{j}) \\
&= \mathbf{d} \Omega^{i}_{j} - \mathbf{d}\omega^{i}_{k} \wedge \omega^{k}_{j} + \omega^{i}_{k} \wedge \mathbf{d}\omega^{k}_{j} \\
&= \mathbf{d}\Omega^{i}_{j} - \mathbf{d}(\Omega^{i}_{k} - \omega^{i}_{m} \wedge \omega^{m}_{k}) \wedge \omega^{k}_{j} + \omega^{i}_{k}\wedge(\Omega^{k}_{j} - \omega^{k}_{m} \wedge \omega^{m}_{j})\\
&= \mathbf{d} \Omega^{i}_{j} - \Omega^{i}_{k} \wedge \omega^{k}_{j} + \omega^{i}_{k} \wedge \Omega^{k}_{j}
\end{align*}
$$
于是我们又得到一个恒等式：
$$
\mathbf{d}[\Omega] = [\Omega] \wedge [\omega] - [\omega] \wedge[\Omega]
$$

## 施瓦西解的曲率

我们来看看之前的施瓦西度规：
$$
ds^{2} = - \left(1 - \dfrac{2GM}{r}\right) dt^{2} + \dfrac{1}{1 - \dfrac{2GM}{r}} dr^{2} + r^{2}(d\phi^{2} + \sin^{2} \phi d \theta^{2})
$$
它是爱因斯坦真空场方程：
$$
\mathbf{Ricci}_{ik} = 0
$$
的一个解。为了简化数学，我们定义：
$$
f(r) = 1 - \dfrac{2GM}{r}
$$
施瓦西度规可以写成：
$$
g = - \theta^{t} \otimes  \theta^{t} + \theta^{r} \otimes  \theta^{r} + \theta^{\phi}\otimes \theta^{\phi} + \theta^{\theta}\otimes  \theta^\theta
$$
其中：
$$
\theta^{t} = \sqrt{f} \mathbf{d}t \quad \theta^{r}  = \dfrac{1}{\sqrt f} \mathbf{d}r  \quad  \theta^{\phi} = r \mathbf{d} \phi \quad \theta^{\theta}= r \sin \phi \mathbf{d} \theta
$$
计算嘉当第一结构方程中的各个项，这里其实就是计算各个 1-形式的外导数，我们略去具体计算过程，直接给出结果：
$$
\begin{align*}
\omega^{t}_{m} \wedge \theta^{m} &= \dfrac{f'}{2\sqrt f} \theta^{t} \wedge \theta^{r} \\
\omega^{r}_{m} \wedge \theta^{m} &= 0 \\
\omega^{\phi}_{m}\wedge \theta^{m} &= \dfrac{\sqrt f}{r} \theta^{\phi} \wedge \theta^{r} \\
\omega^{\theta}_{m}\wedge \theta^{m} &= \dfrac{\sqrt f}{r} \theta^{\theta} \wedge \theta^{r}  + \dfrac{\cot \phi }{r} \theta^{\theta} \wedge  \theta^{\phi}
\end{align*}
$$
我们可以进一步简化地给出 $[\omega]$ 的各个元素，这里，我们直接采用一种不严谨的取法：
$$
\omega^{t}_{r} = \dfrac{f'}{2\sqrt f} \theta^{t} \quad  \omega^{\phi}_{r} = \dfrac{\sqrt f }{f} \theta^{\phi} \quad \omega^{\theta}_{r} = \dfrac{\sqrt f}{r} \theta^{\theta} \quad \omega^{\theta_{\phi}}= \dfrac{\cot \theta}{r} \theta^\theta
$$
接下来计算曲率 2-形式，这个计算也是繁琐而简单的，因此我们直接将结果写在这里。现在我们只有 6 个曲率 2-形式：
$$
\Omega^{t}_{r} = - \dfrac{f''}{2} \theta^{t}\wedge \theta^{r} \quad\Omega^{t}_{\phi} = - \dfrac{f'}{2r} \theta^{t} \wedge \theta^{\phi} \quad  \Omega^{t}_{\theta} = - \dfrac{f'}{2r} \theta^{t} \wedge \theta^\theta
$$
$$
\Omega^{\phi}_{r}=  - \dfrac{f'}{2r} \theta^{\phi} \wedge \theta^{r} \quad  \Omega^{\theta}_{r} = - \dfrac{f'}{2r} \theta^{\theta}\wedge \theta^{r} \quad \Omega^{\theta}_{\phi} = \left[\dfrac{1-f }{r^{2}}\right] \theta^{\theta}\wedge \theta^{\phi}
$$
根据 $\Omega^{i}_{j} = R^{i}_{jlk} \theta^{k} \wedge \theta^{l}$，我们可以解出黎曼张量的部分分量：
$$
R^{t}_{rrt} = +\dfrac{2GM}{r^{3}} \quad  R^{t}_{\phi\phi t} = R^{t}_{\theta \theta  t}= R^{\phi}_{rr\phi}=R^{\theta}_{rr \theta}= -\dfrac{GM}{r^{3}} \quad  R^{\theta}_{\phi\phi \theta }= \dfrac{2GM}{r^{3}}
$$
显然，就算里奇张量为 0，黎曼曲率张量也不为 0. 通过计算 $\mathbf{Ricci}_{tt}$ 等四个分量，我们可以验证这个度规确实满足爱因斯坦场方程。
实际上，我们还可以从爱因斯坦场方程直接推出 $f(r)$ 的形式：
$$
\mathbf{Ricci}_{\phi\phi} = \mathbf{Ricci}_{\theta\theta}=0 \Rightarrow \dfrac{\mathrm{d}f}{\mathrm{d}r} = \dfrac{1-f }{r}  \Rightarrow  f(r) = 1- \dfrac{C}{r}
$$
此时：
$$
\mathbf{Ricci}_{tt} = \mathbf{Ricci}_{rr} = \dfrac{f''}{2} + \dfrac{f'}{r} = 0
$$
是自动满足的。

---
**至此，我们的五幕数学正剧就完全结束了**！
