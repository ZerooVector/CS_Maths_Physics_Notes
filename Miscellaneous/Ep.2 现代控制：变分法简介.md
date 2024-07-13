#MCM 

泛函：函数的函数。其自变量是某个函数 $x(t)$（称为泛函的**宗量**）。例如：
$$
J = \int_{0}^{1} x(t) dt 
$$
就是一个泛函。
在区间 $[a,b]$ 上，若函数 $x(t),x_{0}(t)$ 均具有连续的 $k$ 阶导数，那么我们这样定义两个函数间的距离：
$$
d((t),x_{0}(t)) = \max(|x(t) - x_{0}(t)|,|x'(t) - x_{0}'(t)|,\cdots ,|x^{(k)}(t) - x_{0}^{(k)}(t)|)
$$
若对于任意给定的正数 $\epsilon$，总能找到另一个正数 $\delta$，在 $d (x_{0}(t)- x (t))<\delta$ 时，总有：
$$
|J(x(t) ) - J(x_{0}(t))| < \epsilon
$$
我们就说 $J(x(t))$ 在 $x_{0}(t)$ 处是 $k$ 阶连续的。
如果 $J(x(t))$ 满足：
$$
J(x_{1}(t) + x_{2}(t)) = J(x_{1}(t)) + J(x_{2}(t)) \quad J(cx(t)) = cJ(x(t))
$$
我们称 $J(x(t))$ 是线性泛函。

泛函宗量的变分是同一函数类中两个函数的差，它仍然是函数：
$$
\delta x(t) = x(t) - x_{0}(t)
$$
对于一个泛函，若其增量可以表示为：
$$
\Delta J = J(x_{0}+ \delta x) - J(x_{0}) = L(x_{0} , \delta x) + R(x_{0}, \delta x )
$$
其中，$L(x_{0},\delta x)$ 是关于 $\delta x$ 的线性连续泛函，叫做泛函增量的线性主部，而 $R[x_{0},\delta x]$ 则是 $\delta x$ 的高阶无穷小。我们将 $L$ 称为泛函 $J$ 在 $x_{0}(t)$ 处的变分，记为 $\delta J(x_{0}(t))$ 。
对于一个函数 $F(x,\dot x ,t)$，我们计算：
$$
\Delta F = F(x +\delta x ,\dot x  + \delta \dot x ,t) - F(x,\dot x ,t) = F_{x}\delta x + F_{\dot x} \delta \dot x +\cdots   
$$
我们将：
$$
\delta F = F_{x}\delta x + F_{\dot x }\delta \dot x 
$$
称为函数 $F$ 的变分。变分符号和求导符号有类似的性质，而且可以与积分号、求导符号交换位置。

若泛函 $J(x(t))$ 可微，则其变分的计算方法为：
$$
\delta J(x(t)) = \frac{\partial }{\partial \epsilon  } J(x(t) + \epsilon \delta x(t))|_{\epsilon = 0}
$$
基本证明方法：将这个偏导数展开得到：
$$
\frac{\partial }{\partial \epsilon}  L(x_{0},\epsilon\delta x) = L(x_{0},\delta x)
$$
与上面泛函变分的定义相同。
例如，考虑力学作用量的变分：
![[Pasted image 20230820094903.png|500]]

若泛函在曲线 $x_{0}(t)$ 的邻域内，增量 $\Delta J \ge 0$ 或是 $\Delta J \le 0$，那么 $J(x(t))$ 在 $x_{0}(t)$ 上达到极大值或者极小值。
容易证明：泛函取极值的条件是：
$$
\delta J(x_{0}(t)) = 0
$$
这是因为 $\Delta J$ 可以看作 $x$ 的泛函，或者是 $\epsilon$ 的函数。这由上面的泛函变分计算方法可以直接导出。

现在我们回到力学作用量上来，我们考虑使得力学作用量取到极小值的真实运动轨迹 $x^{\star} (t),\dot x^{\star}(t)$ 和其附近的一条轨迹 $x = x^{\star}+ \delta x ,\dot x  = \dot x^{\star} + \delta \dot x$ ，我们计算等时变分：
$$
\Delta J = \int_{a}^{b}[ L(x,\dot x,t ) - L(x^{\star},\dot x^{\star},t)] dt 
$$
将其进行 Taylor 展开，并只保留到一阶，有：
$$
\Delta  J  = \int_{a}^{b} [\frac{\partial L}{\partial x}\delta x+ \frac{\partial L}{\partial \dot x }\delta \dot x ]dt
$$
右边一项可以通过分部积分公式变换形式：
$$
\int_{a}^{b} \frac{\partial L}{\partial \dot x}\delta x dt = (\frac{\partial L}{\partial \dot x})|_{x^{\star}} \delta x |_{a}^{b} - \int_{a}^{b} \frac{\mathrm{d}}{\mathrm{d}t}(\frac{\partial L}{\partial \dot x })\delta x dt 
$$
回代，得到：
$$
\Delta J = [(\frac{\partial L}{\partial x})-\frac{\mathrm{d}}{\mathrm{d}t}(\frac{\partial L}{\partial \dot x })]\delta x dt + (\frac{\partial L}{\partial \dot x })\delta x |_{a}^{b} = 0 
$$
这个方程的第一部分得到分析力学中的欧拉-拉格朗日方程，第二部分得到横截条件。在分析力学中，由于系统运动的初始条件和终末条件都是固定的，所以实际上第二项自动得 0.
如果端点不固定，我们必须要求在端点处：
$$
\frac{\partial L}{\partial \dot x } = 0
$$
如果终点处的时间也是自由的，通过相同的推导方式（求解变分，并使得变分得 0），就得到新的横截条件：
$$
(\frac{\partial L}{\partial \dot x })\delta x |_{a}^{b^{\star}} + L(x^{\star},\dot x ^{\star} ,t)|_{b^{\star}}\delta b  = 0 
$$
可以证明，这个横截条件等价于在终点处，轨迹满足：
$$
\frac{\partial L}{\partial \dot x } = 0 \quad  \left(L - \dot x \frac{\partial L}{\partial \dot x }\right)= 0
$$


在实际问题中，最优轨迹通常受到各种约束。我们考虑受到约束
$$
G(x,\dot x ,t) = 0
$$
的情况。我们需要使用拉格朗日乘子法将有约束问题转换为无约束问题，构造增广泛函：
$$
J_{a} = \int_{a}^{b} [L+\lambda^{T}G]dt
$$
构造标量函数：
$$
F(x,\dot x ,\lambda ,t) = L + \lambda^{T} G
$$
$$
\Delta J_{a}= [(\frac{\partial F}{\partial x})^{T} \delta x  + (\frac{\partial F}{\partial \dot x})\delta \dot x  + (\frac{\partial F}{\partial \lambda})^{T}\delta \lambda ]dt  = 0 
$$
从而可以得到：
$$
\frac{\partial F}{\partial x} - \frac{\mathrm{d}}{\mathrm{d}t}\frac{\partial F}{\partial \dot x } = 0 
$$
$$
(\frac{\partial F}{\partial x})^{T}\delta x |_{a}^{b} = 0 
$$



接下来，我们考虑固定端点的最优控制问题。设系统的状态方程是：
$$
\dot x  = f(x,u,t)
$$
使用复合型性能指标：
$$
J = \phi [x(t_{f}),t_{f}] + \int_{t_{0}}^{t_{f}}L(x,u,t)dt
$$
终端 $t_{f}$ 给定，但状态自由。系统唯一约束为状态方程约束，构造增广泛函：
$$
J_{a} = \phi [x(t_{f})] + \int_{t_{0}}^{t_{f} } [L(x,u,t) + \lambda^{T}(f(x,u,t) - \dot x)]dt = 0
$$
我们记哈密顿量：
$$
H(x,u,\lambda,t) = L(x,u,t) + \lambda^T f(x,u,t)
$$
那么，上式改写为：
$$
J_{a} = \phi [x(t_{f})] + \int_{a}^{b} H(x,u,\lambda,t) - \lambda^{T}\dot x ]dt  = \phi(x(t_{f})) + \int_{a}^{b}Hdt - \int_{a}^{b} \lambda^{T } \dot x  dt = J_{1}+J_{2}+J_{3} $$

那么：
$$
\Delta J_{1} = \left(\frac{\partial \phi}{\partial x(t_{f})}\right)\delta x |_{t = t_{f}} = 0
$$

$$
\delta J_{2}= \int_{a}^{b} [\left(\frac{\partial H}{\partial x}\right)^{T} \delta x + (\frac{\partial H}{\partial u})^{T} \delta  u  + (\frac{\partial H}{\partial \lambda})^{T} \delta \lambda]dt=0
$$

$$
\delta J_{3}= \delta \int_{a}^{b} \lambda^{T}\dot x dt  = \int_{a}^{b} (\dot x \delta \lambda + \lambda^{T }\delta \dot x )dt
$$
对 $\delta J_{3}$ 的右边一项使用分部积分公式：
$$
\int_{a}^{b} \lambda^{T} \delta \dot x  dt  = \lambda^{T}\delta  x|_{t = t_{f} } - \int \dot \lambda^{T }\delta x = 0  
$$
再将上面三式合并整理，我们可以得到正则方程：
$$
\dot x  = \frac{\partial H}{\partial \lambda} \quad  \dot \lambda = - \frac{\partial H}{\partial x}
$$
以及控制方程（这是真正可以得到最优控制律的方程）：
$$
\frac{\partial H}{\partial u} = 0
$$
横截条件：
$$
\lambda (t_{f}) = \frac{\partial \phi }{\partial x(t_{f})}
$$

推广这种推导方法。若 $t_{f}$ 给定，但状态有约束 $G (x (t_{f}), t_{f}) = 0$，则只要改变横截条件：
$$
\lambda(t_{f}) = \left[\frac{\partial \phi}{\partial x(t_{f})} + (\frac{\partial G}{\partial x(t_{f})})^{T}v\right]
$$
其中，$v$ 也是一个待定的拉格朗日乘子。

如果终端状态自由，终端时间也自由，则横截条件改为：
$$
\lambda(t_{f}) = \frac{\partial \phi}{\partial x(t_{f})} \quad H(t_{f}) = - \frac{\partial \phi}{\partial t_{f}}
$$
如果终端状态有约束，终端时间自由，那么：
$$
\lambda(t_{f}) = \left[\frac{\partial \phi}{\partial x(t_{f})} + (\frac{\partial G}{\partial x(t_{f})})^{T}v\right]\quad H(t_{f}) = -\left[\frac{\partial \phi}{\partial t_{f}}+ (\frac{\partial G}{\partial t_{f}})^{T}v \right]= 0
$$

最后是极小值原理。在实际的控制系统中，控制量会受到约束，因此前面导出的控制方程往往失效。在这里，我们只讨论一般的、简单的情况：即对控制量 $u$ 的约束中不含 $x$。此时，我们只需要将控制方程改写为：
$$
 u^{\star} = \arg \min_{u} H(x,u,\lambda,t)
$$

