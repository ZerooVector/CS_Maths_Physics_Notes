#Classcal_Mechanics  #DynamicalSystem

首先，我们得找平衡点（连续系统：任意时间演化；离散系统：任意次数映射->不动点）。我们分别看：
$$
\dot x = 0 \qquad x_{0} = f(x_{0})
$$

对于非自治系统，我们进行如下操作。考虑：
$$
\ddot x  = f(x,\dot x ,t)
$$
我们令：
$$
\dot x  = f(x,y,z) \quad y = \dot x  \quad \dot z = 1
$$

我们现在对于稳定性给出定义。
- 李雅普诺夫稳定：$\forall \epsilon >0,\exists \delta >0$，使得 $||x (0) - x_{0}|| \le  \delta$ 时，$||x (t)-x_{0}||<\epsilon$ 总成立，那么我们称系统是李雅普诺夫稳定的。
-  渐近稳定：在李雅普诺夫稳定的基础上要求 $\lim_{t \rightarrow \infty } ||x (t)-x_{0}|| \rightarrow 0$

在分析任意系统的稳定性时，我通常要对其进行线性化。因此，我们先来研究线性系统的稳定性。将非线性系统线性化的方法是：
$$
\dot x_{0}(t) + \dot \xi(t) = f(x_{0}) + \left[\dfrac{\partial f}{\partial x}\right] \xi  \Rightarrow \dot \xi = \left[\dfrac{\partial f}{\partial x}\right] \xi 
$$
一个结论是：
- 线性系统的渐近稳定->非线性系统的渐近稳定
- 线性系统的不稳定 ->非线性系统的不稳定
- 非线性系统的李雅普诺夫稳定无法判别
我们现在给出线性方程 $\dot \xi  = A \xi$ 的解析解：
$$
\xi(t) = C \exp(At)
$$
将这个解代入 $\dot \xi  = A \xi$ 可以得到结论：
$$
CA = AC
$$
（其中 $C$ 是常向量）。我们给出：
$$
CA = \lambda C  \Rightarrow C(A  - \lambda I) = 0 
$$
在非平凡解的情况下：$A - \lambda I =0$。

本征值与系统的稳定性有关，例如我们在二维的情况下判断：
![[Pasted image 20240307193114.png]] ![[Pasted image 20240307194209.png]]

我们将其推广到多维，从而得到重要判据**李雅普诺夫第一法**：
- 若 $A$ 的所有本征值实部均为负数->渐近稳定
- $A$ 有一个本征值的实部为正数->不稳定
- $A$ 至少一个本征值实部为 0，其余本征值实部为负数->无法判断

另外有一个判据叫做**劳斯判据**，它不需要求本征值。具体请滚去看自动控制。

我们能否直接判断非线性系统的稳定性？可以，这种方法称为**李雅普诺夫第二法**：
设 $V (x)$ 是相空间原点的邻域 $D$ 中的连续函数，且 $V(x)$ 正定，那么我们称 $V(x)$ 为李雅普诺夫函数。我们沿着非线性方程的解的方向求解其方向导数：
$$
\dot V(x) = \sum_{i} \dfrac{\partial V(x)}{\partial x} f(x)
$$
- 如果 $\dot V(x)$ 负半定，那么系统稳定
- 如果 $\dot V(x)$ 负定，那么系统渐近稳定
- 如果 $\dot V(x)$ 正定，那么系统不稳定

