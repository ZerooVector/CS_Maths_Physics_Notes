#RL 

最优控制最早出现在航空航天领域，用于设计航天器的最优轨迹。本课程的内容包括：
- 经典最优控制技术
- 最优控制在机器人学中的应用
- 从最优控制的视角看强化学习

## Continuos Time Dynamics 
最基本的动力系统有如下的形式：
$$
\dot x  = f(x,u)
$$
对于一个力学系统来说，$x = [q, v]^T$ ，其中 $q$ 是广义坐标，而 $v$ 则是广义速度
例如，我们考虑一个数学摆，其摆球的质量为 $m$，摆线的长度为 $l$，那么其动力学方程显然是：
$$
m l^{2}\ddot \theta + mgl \sin \theta = u 
$$
$u$ 是我们施加的外力矩。我们选择：
$$
x = \begin{bmatrix}\theta \\ \dot \theta \end{bmatrix}
$$
那么我们有：
$$
\dot x  = \begin{bmatrix}\dot \theta  \\ - \frac{g}{l} \sin \theta  + \frac{1}{ml^{2}} u\end{bmatrix}
$$


有一种系统被称为“控制仿射系统 (Control Affline System)”，其动力学方程可以写为：
$$
\dot x  = f_{0}(x) + B(x) u
$$
大多数系统都可以被归入这一类。例如，上面的单摆就可以写出这个形式。

### Manipulator Dynamics 
我们将一类动力系统写为：
$$
M(q) \dot v + C(q,v) = B(q) u
$$
其中，$M(q)$ 被称为广义惯量张量，$C(q,v)$ 被称为动力学偏差 (Dynamics Bias)。通常来说，$\dot q$ 可以被写作是 $v$ 的某种线性函数：
$$
\dot q = G(q) v
$$
这种方程可以被转换成最初的形式：
$$
\dot x = f(x,u) = \begin{bmatrix}G(q) v \\ - M(q)^{-1} (B(q) u - C)\end{bmatrix}
$$
可以验证，所有的力学系统都可以写成这样的形式，这种形式其实等价于欧拉-拉格朗日方程。对于单摆来说，显然有：
$$
M(q) = ml^{2} \quad C(q,v) = gl \sin \theta  \quad B = I \quad G = I 
$$
将拉格朗日量写成
$$
L = \frac{1}{2}  v^{T} M(q) v - U(q)
$$
的形式，你就可以导出上面的方程了

### Linear Systems
最为简单的一种系统被称为线性系统。其动力学方程为：
$$
\dot x  = A(t)x + B(t) u
$$
如果 $A (t) = A, B (t) = B$，则系统被称为是“线性时不变系统（LTI）”，否则称为“线性时变系统”
对于非线性的系统，我们通常通过泰勒展开将其线性化：
$$
A = \frac{\partial f}{\partial x }\quad B = \frac{\partial f}{\partial u}
$$

## Equilibria 
我们将 $\dot x= 0$ 的点称为系统的平衡点，也就是 $f (x, u) =0$ 的根。
控制中的一类问题就是移动系统的平衡点。例如，如果我们想将单摆在平衡时与竖直方向的夹角移动到 $\pi/2$ ，那么有：
$$
u = mgl 
$$
得到平衡点之后，我们还需讨论平衡点的稳定性。对于一个一维系统，其稳定的条件显然是：
$$
\frac{\partial f}{\partial x }<0
$$
对于高维系统来说，$\frac{\partial f}{\partial x}$ 是一个雅可比矩阵，我们可以通过对其进行本征值分解：
$$
\frac{\partial f}{\partial x } = P^{-1} \Lambda P
$$
从而将其解耦到多个一维系统。显然，我们要求所有一维系统都是稳定的，也就是要求每一个本征值的实部都小于 0. 这种方法几乎只对线性的系统有用，因为在非线性系统中，你无法度量高阶展开项的影响。

