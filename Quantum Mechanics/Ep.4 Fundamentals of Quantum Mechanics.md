#Quantum_Mechanics 

## 经典力学

我们来回顾一下经典力学里面的正则对易关系：
$$
[A,B] = \sum_{\alpha} \dfrac{\partial A}{\partial x_{\alpha}}\dfrac{\partial B}{\partial p_{\alpha}} - \dfrac{\partial A}{\partial p_{\alpha}} \dfrac{\partial B}{\partial x_{\alpha}} 
$$
例如：
$$
[x_{i}, p_{j}] = \sum_{a} \dfrac{\partial x_{i}}{\partial x_{a}}\dfrac{\partial p_{j}}{\partial p_{a}} - \dfrac{\partial x_{i}}{\partial p_{a}} \dfrac{\partial p_{j}}{\partial x_{a}} = \delta_{ia} \delta_{ja}- 0 = \delta_{ij} 
$$
在量子力学中：
$$
[\hat x_{i},\hat p_{j}] = \hat x_{i}\hat  p_{j} - \hat p_{j} \hat x_{i} = i \hbar \delta_{ij}
$$
在后面我们会证明这个结论。

我们继续回顾一下正则运动方程：
$$
\dot q_{\alpha} = \dfrac{\partial H}{\partial p_{\alpha}} \quad \dot p_{\alpha}= - \dfrac{\partial H}{\partial q_{\alpha}}
$$
正则运动方程的推广形式：设有函数 $f(q,p)$
$$
\dfrac{\mathrm{d}f}{\mathrm{d}t} = \dfrac{\partial f}{\partial t} +[f,H]_{PB}
$$
这个方程的推导过程是简单的。只要将全微分展开就行。
从而我们可以把最初的方程写成一个对称的形式：
$$
\cdot q_{a}= [q_{a},H] \quad p_{a} = [p_{a},H]
$$
对比：量子力学中的海森堡方程
$$
\dfrac{\mathrm{d}\hat f}{\mathrm{d}t} = \dfrac{\partial \hat f}{\partial t} + \dfrac{1}{i \hbar} [\hat f,\hat H]
$$
我们将 $\hat f$ 这样的数称为“C-number”（经典的、可对易的），将 $f$ 这样的数称为“Q-number”（与量子相关的）

对比：Ehrenfest 定理
$$
\dfrac{\mathrm{d}}{\mathrm{d}t} \langle \dfrac{\partial \hat f}{\partial t} \rangle = \langle \dfrac{\partial \hat f}{\partial t} \rangle + \frac{1}{i\hbar} \langle [\hat f,\hat h]\rangle 
$$

### 正则变换
正则变换负责构造一个新的哈密顿量。考虑从 $H(q,p)$ 到 $K(Q,P)$ 的正则变换，在这个过程中：
$$
[q,p] = [Q,P] \quad ([q,p])_{Q,P} = ([Q,P])_{q,p}
$$
从而推出：$[A(q,p),B(q,p)]$ 的结果不依赖于 $q,p$ 的具体选择，也不依赖于你在哪套正则坐标下求解。这导致运动方程不变。这样，我们的拉格朗日量和哈密顿量都有无穷多个选择，我们通常要选择一个最简单的，从而使得我们处理问题最方便。我们将：
$$
\det \left(\dfrac{\partial^{2}L }{\partial q_{i}\partial q_{j}}\right) \not = 0 
$$
的 $L$ 称为 Regular Lagrangian。此时，它可以写成：
$$
L = T - V
$$
$T$ 通常只与 $p$ 有关，而 $V$ 通常只与 $q$ 有关。而且此时恰好有：
$$
H = T+V = E
$$
在这种情况下，我们才可以说 $H$ 代表系统的能量。


## 经典电动力学
在经典电动力学中，我们使用高斯单位制。在高斯单位制中：
$$
[E]  = [P] = [D] = [B] =[H] = [M]
$$
也就是说所有主要量的量纲都一样。在国际单位制里面，我们知道：
$$
\epsilon_{0} \mu_{0} = \dfrac{1}{c^{2}}
$$
但是在高斯单位制里面没有。

首先我们说说亥姆霍兹定理。我们可以将一个矢量场分成两个部分：
$$
F = F_{1} + F_{3}
$$
其中，$F_{1}$ 是无旋的，被称为“纵向场”，从而 $F_{1} = \nabla  \Phi$；$F_{2}$ 是无源的，被称为“横向场”，从而 $F_2 = \nabla  \times A$。那么，我们只要研究一个场的旋度和散度的性质，就可以完全刻画这个场。我们给出麦克斯韦方程组：
$$
\nabla \cdot E = 4 \pi \rho \quad  \nabla \cdot B = 0 
$$
$$
\nabla  \times E = - \dfrac{1}{c}  \dfrac{\partial B}{\partial t}  \quad  \nabla \times B = \dfrac{4\pi}{c} j + \dfrac{1}{c} \dfrac{\partial E}{\partial t} 
$$
那么我们知道：
$$
E = - \nabla  \phi - \dfrac{1}{c}\dfrac{\partial }{\partial t}A \quad B = \nabla \times A
$$
我们说一句规范不变性。假如我们令：
$$
\phi' = \phi + \nabla X \quad A' = A - \dfrac{1}{c} \dfrac{\partial }{\partial t}X
$$
那么我们会得到 $E' = E, B' = B$

再说说多级展开。电偶极、磁偶极和外场的相互作用：
$$
W_{e}= \ d \cdot E \quad W_{m}= - \mu \cdot B
$$
电偶极 $d = q\cdot x$ 是一个奇函数。这很重要，会影响到量子力学中的选择定则。磁偶极 $\mu = \dfrac{qL}{\alpha m c}$，这里的 $L$ 包含轨道角动量和自旋角动量。


## 再谈矢量分析
我们重新写一下矢量分析的东西。
$$
A \cdot B  = A_{i}B_{i}
$$
$$
(A \times B )_{i} = \epsilon_{ijk} A_{j}B_{k}
$$

关于对称和反对称张量。$\delta_{ij}$ 显然是一个对称张量，而 $\epsilon_{ijk}$ 是一个反对称张量。假定我们有对称张量 $F_{ij}$，那么：
$$
\epsilon_{ijk} F_{ik} = 0
$$
然后是两个 Levi-Civita 张量相乘的结论：
$$
\epsilon_{ijk}  \epsilon_{klm} =  \delta_{il} \delta_{jm} - \delta_{im} \delta_{jl}
$$
一个例子是计算经典力学中的 $[L_{i},L_{j}]$ 是什么：
$$
\begin{align*}
[L_{i},L_{j}] &= 
\end{align*}
$$
首先注意到：
$$
L_{i}= \epsilon_{iab} x_{a} p_{b}  \quad L_{j} = \epsilon_{jcd} x_{c}p_{d} 
$$
注意到对易运算的性质：
$$
[A,BC] = [A,B]C + B[A,C] \quad [AB,C] = [A,C]B + A[B,C] \quad [A,B] = -[B,A]
$$
我们继续我们的运算：
$$
\begin{align*}
[L_{i},L_{j}] &= \epsilon_{iab} \epsilon_{jcd} [x_{a}p_{b},x_{b}p_{a}]\\
&= \epsilon_{iab} \epsilon_{jcd} (x_{c}[x_{a} ,p_{a}]p_{b} + x_{a}[p_{b},x_{c}]p_{a})\\
&= \epsilon_{iab} \epsilon_{jcd} (x_{c}p_{b} \delta_{ad} - x_{a} p_{d} \delta_{bc})\\
&= \epsilon_{iab} \epsilon_{jca} x_{c} p_{b} - \epsilon_{iab} \epsilon_{jbd}  x_{a} p_{d}\\
&= \epsilon_{bia} \epsilon_{jca} x_{c} p_{b} + \epsilon_{iab}  \epsilon_{jdb}x_{a}p_{b}\\
&= (\delta_{bj}\delta_{ic}  - \delta_{bc} \delta_{ij}) x_{c}p_{b} +(\delta_{ij} \delta_{ad} - \delta_{id} \delta_{aj}) x_{a}p_{b}\\
&= x_{i}p_{j} - (x \cdot p) \delta_{ij} + (x \cdot p) \delta_{ij} + x_{j} p_{i}\\
&= x_{i}p_{j} - x_{j} p_{i}
\end{align*}
$$
注意到：
$$
\begin{align*}
\epsilon_{ijk} L_{k} \\
&= \epsilon_{ijk}(x \times p)_{k}\\
&= \epsilon_{ijk} \epsilon_{klm} x_{l} p_{m}\\
&= (\delta_{il} \delta_{jm} - \delta_{im} \delta_{jl}) x_{l}p_{m}\\
&= [L_{i},L_{j}]
\end{align*}
$$
这里面的运算过程只是基本对易关系的体现：
$$
[x_{i},p_{j}] = \delta_{ij}
$$
















