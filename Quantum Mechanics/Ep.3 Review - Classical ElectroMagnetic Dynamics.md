#Quantum_Mechanics 

## 矢量分析复习

我们将三维欧氏空间中的一个向量写为：
$$
\vec x = \sum_{i}x_{i}e_{i} = x_{i}e_{i}
$$
在这里，我们已经使用了爱因斯坦求和约定。这里的 $i$ 是 Dummy Index。

矢量之间的运算包括：
- 内积：
$$
e_{i} e_{j} = \delta_{ij} \quad (i,j = 1,2,3)
$$
- 外积
$$
\vec e_{i}\times \vec e_{i}  = \epsilon_{ijk}\vec e_{k}
$$
必须指出，这里的 $\epsilon_{ijk}$ 是 Levi-Civita Tensor。

接下来，我们要说明 $\delta_{ij}$ 和 $\delta_{ijk}$ 的一些性质。
$\delta_{ij}$ 在 $i = j$ 时取 1，否则取 0，因此它经常被用来描述正交性和归一性；
$\epsilon_{ijk}$ 在 $i,j,k$ 是**Even Permutation**时取到+1；在**Odd Permutation**时取到 -1，其余时候取 0
显然，$\delta_{ij}$ 是对称张量，而 $\delta_{ijk}$ 是反对称张量，也就是说 $\delta_{ijk}= -\delta_{jik}$ 

现在取 $F_{ij}= F_{ji}$，那么 $\epsilon_{ijk}F_{ij} = 0$，这是不证自明的。因为
$$
\epsilon_{ijk}  F_{ij} = \frac{1}{2} (\epsilon_{ijk} F_{ij} + \epsilon_{jik} F_{ji}) = 0 
$$
此外，我们有 $F_{i}\delta_{ij} = F_{j}$

现在我们考虑任意两个矢量间的运算：$\vec A = A_{i}\vec e_{i}, \vec B  = B_{j}\vec e_{j}$
首先，内积：
$$
\vec A  \cdot \vec B =  (A_{i} \vec e_{i}) (B_{j} \vec e_{j}) = (A_{i}B_{j})\delta_{ij} = A_{i}B_{i}
$$
外积：
$$
\vec A \times \vec B  = (A_{i}e_{i}) \times  (B_{j}e_{j}) = (A_{i}B_{j}) (e_{i}\times  e_{j} ) = (A_{i}B_{j})(\epsilon_{ijk} e_{k}) = e_{k}(\epsilon_{ijk} A_{i}B_{j})
$$
从而容易发现：$A \times B$ 的第 $k$ 个分量为 $\epsilon_{kij} A_{i}B_{j}$

从而我们进行总结：
$$
A \cdot B  = A_{i}B_{i}  \quad  A \times B  =e_{i} \epsilon_{ijk} A_{j}B_{k}
$$

我们复习一下：矩阵的行列式如何定义？显然，只有方阵才有行列式，我们取 $M$ 为 $n \times  n$ 的矩阵，那么：
$$
\det M = \epsilon_{i_{1},i_{2},\cdots  i_{n}} M_{1i_{1}} M_{2i_{2} }\cdots M_{ni_{n}}
$$
考虑 $\vec A \times \vec B$ 的行列式的定义，显然可以验证这与上面矢量叉乘的定义是一样的。

我们接下来再给出几个重要公式：
$$
\epsilon_{ijk} = e_{i}\cdot (e_{j}\times e_{k}) = \det \left(\begin{bmatrix} \delta_{1i} & \delta_{2i} & \delta_{3i}  \\  \delta_{1j}& \delta_{2j} & \delta_{3j}  \\  \delta_{1k} & \delta_{2k} & \delta_{3k}\end{bmatrix}\right)
$$
$$
\epsilon_{ijk} \epsilon_{lmn} = \det \left (\begin{bmatrix}\delta_{il} & \delta_{im} & \delta_{in}  \\  \delta_{jl} & \delta_{jm} & \delta_{jn}  \\ \delta_{kl} & \delta_{km} & \delta_{kn} \end{bmatrix}\right) 
$$
下面这个公式比较重要：
$$
\epsilon_{ijk} \epsilon_{klm} = \epsilon_{ijk}\epsilon_{lmk} = \delta_{il}\delta_{jm} - \delta_{im}\delta_{jl}
$$

$$
A\cdot (B \times C ) = B \cdot (C \times  A) = C \cdot (A \times B )
$$
我们对这个公式给一下证明：
$$
A \cdot ( B \times C) = A_{i}(B \times C )_{i} = A_{i}\epsilon_{ijk} B_{j}C_{k} = B_{j} \epsilon_{jki} C_{k}A_{i}
$$
通过交换 $\epsilon_{ijk}$ 的三个下标的位置，上面的式子就得证。其几何意义是以 $A,B,C$ 为三个从同一顶点出发的棱的平行六面体的体积。

接下来给出一些电动力学中可能使用的公式：
$$
\nabla (uv) = u (\nabla v) + (\nabla  u) v  
$$
$$
\nabla \times (\nabla \times A) = \nabla (\nabla A) - \nabla ^{2}A 
$$
$$
\nabla \times (\nabla \phi) = 0
$$
其几何意义是标量场的梯度一定无旋。
$$
\nabla (\nabla \times A) = 0
$$
其几何意义是矢量场的旋度一定无散。这些公式的证明利用了对称张量和反对称张量指标缩并后得到 0。
$$
\nabla \left(\frac{1}{r}\right)= \dfrac{\vec x}{r^{3}} \quad \nabla^{2} \left(\frac{1}{r} \right)= 4 \pi \delta (\vec x )
$$
其几何意义是一个 $r^{-1}$ 的势对应的场，以及这个场对应的荷

广义 Stokes 定理（我们先不管这个）：
$$
\int_{\partial \Omega} \omega  = \int_{\Omega} d \omega 
$$
它可以写成各种具体的形式：
- 牛顿-莱布尼兹公式
- 格林公式
$$
\oint  fdx + gdy = \iint_{D} (\dfrac{\partial g}{\partial x} - \dfrac{\partial f}{\partial y})dxdy 
$$
- 高斯定理：面积分会变成体积分
$$
\iint \vec F \cdot  d \vec \Sigma  = \iiint (\vec \nabla\cdot \vec F )dV 
$$
它有两个常见推论：
$$
\iint \phi d \vec \Sigma = \iiint  (\vec \nabla  \phi) dV  \quad \iint d \vec \Sigma \times \vec A  = \iiint (\vec \nabla \times  \vec A) dV 
$$


- Stokes 定理：线积分会变成面积分
$$
\oint \vec F \cdot \vec dl  = \iint (\vec \nabla \times \vec F ) d \vec \Sigma 
$$
它有一个常见推论：
$$
\oint \phi dl = \iint d \vec \Sigma   \times \vec \nabla \phi 
$$

亥姆霍兹定理：对于任意矢量 $\vec F$ 场，只要 $\vec F$ 连续、可微，那么 $\vec F$ 可以写成纵向场和横向场之和，也就是说：
$$
\vec F = \vec F_{1} + \vec  F_{2}
$$
其中，$F_{1}$ 无旋，而 $F_{2}$ 无源。那么：
$$
\vec F  = - \vec \nabla \phi - \vec \nabla \times \vec A
$$
因此，只要我们可以研究清楚一个矢量场的散度和旋度，我们就可以研究清楚一个矢量场。

## 从电磁学中的实验定律到麦克斯韦方程组
- 库仑定律：
$$
\vec E(x) = \int  \dfrac{\rho(x')}{|x - x'|^{3}} (x - x') d^{3}x'
$$
从中立刻可以推出电势的表示：
$$
\phi(x) = \int \dfrac{\rho(x')}{|x - x'|}
 d^{3} x'$$
以及电场高斯定律：
$$
\vec \nabla \cdot \vec E = 4 \pi \rho(x)
$$

- 毕奥-萨伐尔定律
$$
\vec B  = \int \dfrac{\vec j(x') \times (x - x') }{|x - x'|^{3}} dx'  = \vec \nabla \times \vec A(x)
$$
从中推出磁矢势的表示：
$$
\vec A(x) = \dfrac{1}{c} \int \dfrac{\vec j(x')}{|x - x'|}d^{3}x' 
$$
以及从中推出高斯磁定理：
$$
\vec \nabla \cdot \vec B = 0 
$$

- 安培环路定律
$$
\oint \vec B \cdot d\vec l  =\dfrac{4\pi}{c} \iint \vec j \cdot d\vec \Sigma 
$$

- 法拉第电磁感应定律
$$
\oint \vec E \cdot d \vec l = - \dfrac{1}{c} \dfrac{\mathrm{d}}{\mathrm{d}t} \iint \vec B  \cdot d \vec \Sigma 
$$
利用斯托克斯定理，立刻推出：
$$
\vec \nabla \times \vec E = - \dfrac{1}{c} \dfrac{\partial \vec B}{\partial t}
$$

最后是一条公理：电荷守恒定律
$$
\dfrac{\mathrm{d}Q}{\mathrm{d}t} = 0 \quad Q = \iiint \rho d^{3}x
$$
可以立刻推出其微分形式：连续性方程：
$$
\dfrac{\partial \rho}{\partial t} + \vec \nabla \cdot \vec j  = 0 
$$
那么，如果四条实验定律中不增加一项，那么实验定律与守恒方程相悖。我们改写第三条实验定律为：
$$
\vec \nabla  \times \vec B  =\dfrac{4 \pi}{c} \vec j  + \dfrac{1}{c} \dfrac{\partial \vec E}{\partial t}
$$
至此，四条麦克斯韦方程集齐。
最后，我们要考察粒子与场的相互作用。那么，粒子受力：
$$
\vec F  = q (\vec E  + \dfrac{\vec v}{c} \times \vec B)
$$
其中：
$$
\vec E = - \vec \nabla \phi  - \dfrac{1}{c} \dfrac{\partial }{\partial t} \vec A  \quad \vec B = \vec \nabla \times \vec A
$$


### 带电粒子在电磁场中的运动
我们直接说明，带电粒子在电磁场中时：
$$
L = \frac{1}{2} m \dot x^{2}  - q \phi  + \dfrac{q}{c} (\vec v \cdot \vec A) \quad H = \dfrac{1}{2m} \left(\vec p - \dfrac{q}{c}\vec A\right)^{2}+ q\phi 
$$
这里 $p = m \dot{\vec x} + \dfrac{q}{c}\vec A$，是粒子的正则动量。

### 多极展开
注意到：
$$
\dfrac{1}{|x - x'|} = \dfrac{1}{|x|} - \vec x' \vec \nabla \left(\dfrac{1}{|x|}\right) + \cdots
$$
尤其是在 $|x| >> |x'|$ 时，上式可以用作近似。因此，我们可以将 $\phi$ 和 $\vec A$ 写成：
$$
\phi = \phi^{(0)}  + \phi^{(1)}  +\cdots  \quad \vec A = \vec A^{(0)} + \vec A^{(1)}+\cdots 
$$
那么，我们可以将一堆电荷在远处的场展开成点电荷、电偶极子、电四极子……叠加的形式；我们可以将一堆电流在远处的场展开成磁单极子（不存在，故 $\vec A^{(0)}=0$）、磁偶极子……叠加的形式。那么，电场和磁场都可以做类似的展开。在考虑电荷与场的作用时，各个项可以与电磁场分别作用。






