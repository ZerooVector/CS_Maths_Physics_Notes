#Quantum_Mechanics 

我们要说明，经典力学为量子力学打下了坚实的基础。并且，经典力学为量子力学提供了丰富的（数学）工具。
现在常说的“Classcial Mechanics”通常被分为三个模块：
- Newtonian Mechanics 
- Analytical Mechanics 
	- Lagrangian Mechanics 
	- Hamilton Mechanics 

## Newtonian Mechanics 
人类对于璀璨星空的向往催生了牛顿力学。在这一部分中，我们主要有如下成果：
- 提供了物理中研究的空间和基本的研究手段：欧几里得空间、直角坐标系（笛卡尔坐标系）
- 提供了基本定律：惯性 (Inertia)、牛顿第二定律（$\dfrac{\mathrm{d}P}{\mathrm{d}t} = F,\dfrac{\mathrm{d}L}{\mathrm{d}t} = N$）
- 提供了基本模型：质点、刚体->轴角表示和欧拉角->进动、章动、自旋，质心系解两体

## Analytical Mechanics 
在分析力学中，我们不再考虑天体这样的自由质点，转而考虑有约束的系统。这是因为，在具有大量约束的系统中，我们对约束反力并不感兴趣，我们只想要导出系统的运动方程。
一般来说，我们将只与位置坐标有关的约束称为完整约束 (Holomonic Constraint)，我们可以使用拉格朗日方法求解。利用 $\delta S= 0$，我们就可以推出广为人知的运动方程：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t} \left(\dfrac{\partial L}{\partial \dot q_{\alpha}}\right)  = \dfrac{\partial L}{\partial q_{\alpha} }
$$
其中，$L(q,\dot q ,t)$ 是拉格朗日量。容易注意到，拉格朗日量是函数的函数，因此我们称之为“泛函”(Functional)。我们称：
$$
S = \int_{t_{1}}^{t_{2}}  L(q,\dot q ,t) dt = S[q]   
$$
为“作用量”(Action)。注意到 $\dot q$ 在积分一次后变成了 $q$，因此作用量是 $q(t)$ 的泛函。作用量与角动量的量纲相同，都是动量乘以位置（或者能量乘以时间），可以注意到它与普朗克常数的量纲也一致

对于有约束的问题，假若我们处理有 $3n$ 个自由度，使用牛顿定律时需要求解 $3n$ 个微分方程。但是若系统内有 $m$ 个约束，实际上我们只需要选择 $3n-m$ 个互相独立的广义坐标描述系统即可。这些广义坐标所在的空间被称为“位形空间”(Configuration Space)。位形空间的维度等于广义坐标的数量

Hamilton Mechanics 和 Lagrangian Mechanics 是等价的。在 Hamilton Mechanics 中，我们定义了“相空间”(Phase Space)，其中包括 $q(t),p(t)$。我们将 $q(t)$ 称作“正则位置”(Canonical Position)，将 $p(t)$ 称作“正则动量”(Canonical Momentum)，我们将这一组量称为“正则坐标”。我们现在说明如何通过 Legendre 变换得到哈密顿量。我们有 $L(q,\dot q ,t)$，通过定义 $p  = \dfrac{\partial L}{\partial \dot q}$，就得到了 $H(q,p,t)$。显然，我们可以发现性质 $\dfrac{\partial L}{\partial p},\dfrac{\partial H}{\partial q}$ 都恒等于 0.
在相空间中，一个系统的运动方程写为：
$$
\dot q_{\alpha} = \dfrac{\partial H}{\partial p_{\alpha}}\quad  \dot p_{\alpha}  = -\dfrac{\partial H}{\partial q_{\alpha}}
$$
注意到 Hamilton 方程比 Lagrangian 方程数量多了一倍，但是阶数降了一阶。
Hamilton 方程可以进行推广，假定我们有物理量 $f(p,q,t)$，我们有：
$$
\dfrac{\mathrm{d}f}{\mathrm{d}t} = \dfrac{\partial f}{\partial t} + [f,h]_{PB}
$$
其中，Poissonian 对易关系被定义为：
$$
[f,H]_{PB} = \sum_{\alpha} (\dfrac{\partial f}{\partial q_{\alpha}} \dfrac{\partial H}{\partial p_{\alpha}} - \dfrac{\partial f}{\partial p_{\alpha}}\dfrac{\partial H}{\partial q_{\alpha}})
$$


我们知道，如果将相点密度记作 $\rho(p,q,t)$，那么我们显然有：
$$
\int \rho(p,q,t) dV = 1
$$
我们可以推出：
$$
\dfrac{\mathrm{d}\rho}{\mathrm{d}t} = 0 
$$
这是 Liouville 方程。在量子力学中，这个方程被写为：
$$
\dfrac{\partial \hat \rho}{\partial t} = \dfrac{1}{i \hbar} [\hat H ,\hat \rho]
$$

最后，我们必须说明正则变换。在正则变换中，我们将 $H(q,p,t)$ 变成 $K(Q,P,t)$。虽然正则动量和正则坐标都发生变化，但是运动方程不变。并且，任意 $[f(q,p),g(q,p)]$ 是在正则变换下不变的。































