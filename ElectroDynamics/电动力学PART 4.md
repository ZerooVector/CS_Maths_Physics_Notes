#ElectroDynamics 

## 库伦规范和洛伦兹规范
在静电场、静磁场的情况下，我们给出 $\rho(r),J(r)$，库仑定律和毕奥-萨伐尔定律就可以给出 $E(r),B(r)$ 的分布.。但是如果给定 $\rho(r,t),J(r,t)$，我们如何计算 $E(r,t)$ 和 $B (r, t)$ 呢？我们仍然考虑能不能找到电场和磁场的某种势。现在，电场有旋度，因此我们不能将其写成某个量的梯度的形式，但是磁场依然无源，因此：
$$
B = \nabla \times A
$$
使用麦克斯韦方程组：
$$
\nabla  \times E = - \dfrac{\partial }{\partial t} (\nabla \times A) \Rightarrow \nabla  \times \left(E + \dfrac{\partial A}{\partial t}\right) = 0
$$
因此，我们可以这样写：
$$
E = - \nabla V - \dfrac{\partial A}{\partial t}
$$
将这个式子代入麦克斯韦方程组 （计算 $E$ 的散度），我们得到：
$$
\nabla^{2}V + \dfrac{\partial }{\partial t}(\nabla  \cdot A) = - \dfrac{1}{\epsilon_{0}} \rho  \quad (\star)
$$
这替换了原来的泊松方程。此时，我们还有一条方程没用，我们计算 $B$ 的旋度：
$$
\nabla \times (\nabla \times A) = \mu_{0}J  - \mu_{0}\epsilon_{0} \nabla \left(\dfrac{\partial V}{\partial t}\right) - \mu_{0}\epsilon_{0} \dfrac{\partial^{2}A }{\partial t^{2}}
$$
使用 $\nabla \times (\nabla \times A) = \nabla (\nabla \cdot A) - \nabla^{2}A$，可以将上式写成：
$$
\left(\nabla^{2}A - \mu_{0} \epsilon_{0} \dfrac{\partial ^{2}A}{\partial t^{2}}\right)-  \nabla \left(\nabla\cdot A + \mu_{0}\epsilon_{0} \dfrac{\partial V}{\partial t}\right)= 0  \quad (\star \star)
$$
在推导 $(\star)$ 和 $(\star \star)$ 式的过程中，我们使用了全部的四条方程，因此这两个式子已经包含了麦克斯韦方程的全部信息。这两条方程中的场已经完全消去，完全是关于 $V$ 和 $A$ 的方程。虽然它的形式很丑陋，但是我们已经稍微化简了问题——将六个分量的求解化简为四个分量的求解。

我们发现，上面的方程并不唯一确定 $V$ 和 $A$，假设我们有两组势 $(V,A)$ 和 $(V',A')$，它们之间有关系：$A' = A + \alpha, V' = V + \beta$。由于我们需要 $\nabla \times \alpha = 0$，那么 $\alpha$ 需要是某个标量的梯度：$\alpha = \nabla \lambda$。在静电场中，$V$ 可以差一个常数（这时两个 $V$ 给出相同的场），但是现在 $E = - \nabla V - \dfrac{\partial A}{\partial t}$，我们不能这么干。为了让新的势也给出相同的场，我们有：
$$
\nabla \beta  + \dfrac{\partial \alpha }{\partial t} = 0  \Rightarrow \nabla \left(\beta + \dfrac{\partial \lambda}{\partial t}\right)= 0 
$$
因此，括号内的东西应该与位置无关。我们可以将 $\beta$ 表达为：
$$
\beta  = - \dfrac{\partial \lambda}{\partial t} + k(t)
$$
这样括号内只剩下一个 $k(t)$，只与时间有关。为了方便写，我们一般将 $\lambda$ 加上 $\int_{0}^{t} k (t') dt'$ 变成新的 $\lambda$，从而将 $k(t)$ 吸收掉。而这一项显然不影响 $\lambda$ 的梯度（因为这一项只与时间有关）。因此，我们有：
$$
A' = A + \nabla \lambda\quad  V' = V - \dfrac{\partial \lambda}{\partial t}
$$
我们将这样的变换称为"规范变换"。

前面学习静磁学的时候我们知道，只要设置 $\nabla  \cdot A = 0$，很多问题都能迎刃而解（比如，磁矢势会很容易求出）。但是现在，我们可能需要根据问题选择 $V$ 和 $A$ 的最佳形式。接下来我们介绍两种最常见的情况。

**库伦规范**：正如我们之前做的一样，设置 $\nabla \cdot A = 0$，那么 $(\star)$ 方程变成：
$$
\nabla^{2}V = - \dfrac{1}{\epsilon_{0}} \rho 
$$
这就是泊松方程，而之前我们已经获得了它的解：
$$
V(r,t) = \dfrac{1}{4 \pi \epsilon_{0}} \int \dfrac{\rho(r',t)}{\mathscr{r}} d \tau '
$$
在库伦规范中，$t$ 时刻的电势是由 $t$ 时刻的电荷分布立刻确定的！注意：电势是一个不可测量的量，我们能测量的只有电场 $E$，而电场还与 $A$ 有关。因此，并不会出现信息超过光速传播之类的问题。库伦规范的优势是 $V$ 非常好计算，作为代价，$A$ 非常难以计算：
$$
\nabla^{2}A - \mu_{0}\epsilon_{0} \dfrac{\partial ^{2}A}{\partial t^{2}} = - \mu_{0}J  + \mu_{0} \epsilon_{0} \nabla \left( \dfrac{\partial V}{\partial t}  \right)
$$
**洛伦兹规范**：将磁矢势的散度设置为：$\nabla \cdot A = - \mu_{0}\epsilon_{0} \dfrac{\partial V}{\partial t}$ 。这样的话，上面的两条方程改写为：
$$
\nabla^{2}A - \mu_{0}\epsilon_{0} \dfrac{\partial ^{2} A}{\partial t^{2}} = - \mu_{0}J  \quad  \nabla^{2}V - \mu_{0} \epsilon_{0} \dfrac{\partial ^{2} V}{\partial t^{2}} = - \dfrac{1}{\epsilon_{0} }\rho 
$$
我们闲杂记达朗贝尔算子：$\nabla^{2} - \mu_{0}\epsilon_{0} \dfrac{\partial^{2 }}{\partial t^{2}}= \square^{2}$，那么麦克斯韦方程组被改写为：
$$
\square^{2} V = -\dfrac{1}{\epsilon_{0}} \rho \quad  \square ^{2}A = - \mu_{0}J 
$$
这个方程组可以被视为泊松方程的四维推广。在洛伦兹规范下，$V$ 和 $A$ 均满足非齐次的波动方程，因此电动力学的所有问题转化为求解这个方程的问题。

下面我们会把洛伦兹力也一并改写一下。考虑到：
$$
F=  \dfrac{\mathrm{d}p}{\mathrm{d}t} = q(E + v \times B) = q\left[ - \nabla V  - \dfrac{\partial A}{\partial t} + v  \times (\nabla  \times A)\right]
$$
利用矢量分析公式可以改写为：
$$
\dfrac{\mathrm{d}p}{\mathrm{d}t} = - q \left[\dfrac{\partial A}{\partial t} + (v \cdot \nabla)A  + \nabla (V  - v  \cdot A) \right]
$$
我们引用流体力学中的一个概念，$\dfrac{\partial A}{\partial t} + (v \cdot \nabla)A$ 称为 $A$ 的物质导数，写作 $\dfrac{\mathrm{d}A}{\mathrm{d}t}$，代表了随着电荷运动，电荷所在处 $A$ 随着时间的变化：
$$
dA = A(r + v dt , t + dt) - A(r, t)= \sum_{i = x,y,z} \dfrac{\partial A}{\partial i}v_{i} dt + \dfrac{\partial A}{\partial t} dt
$$
此时，洛伦兹力公式可以被改写成：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t}(p + qA) = - \nabla [q(V - v \cdot A)]
$$
类比一个一般的运动方程 $\dfrac{\mathrm{d}p}{\mathrm{d}t} = - \nabla U$，现在新的动量 $p_{can}= p+qA$，被称为正则动量，新的势能则是 $q(V - v \cdot A)$。


## 推迟势
现在，我们考虑洛伦兹规范下的电势和磁矢势怎么写。一个直观感受是：当源发生变化后，信息以光速传播，推迟一段时间 $\dfrac{\mathscr{r}}{c}$ 到达场点。（注意：现在我们关于 $V,A$ 的方程是对称的，要想使得 $E,B$ 是因果的，我们的 $V,A$ 都得推迟相同的时间）于是我们猜测，$V$ 和 $A$ 应当满足以下的形式：
$$
V(r,t) = \dfrac{1}{4 \pi  \epsilon_{0}} \int \dfrac{\rho(r',t_{r})}{\mathscr{r}} d \tau' \quad  A(r,t) = \dfrac{1}{4 \pi  \epsilon_{0}} \int \dfrac{J(r',t_{r})}{\mathscr{r}} d \tau' \quad t_{r} = t - \dfrac{\mathscr{r}}{c}
$$
现在我们要证明这个形式是正确的。我们要证明这个表达式满足非齐次波动方程和洛伦兹规范的条件。于是我们开始验证上面的 $V$，也就需要求出其二阶导数：
$$
\nabla V = \dfrac{1}{4\pi \epsilon_{0}}\int \left[(\nabla \rho) \dfrac{1}{\mathscr{r}} + \rho  \nabla \left(\dfrac{1}{\mathscr{r}}\right)\right] d\tau'
$$
其中，$\nabla \rho = \dot \rho \nabla t_{r}  = - \dfrac{1}{c} \dot \rho \nabla \mathscr{r}$ ，于是我们得到：
$$
\nabla V = \dfrac{1}{4\pi \epsilon_{0}}\int \left[- \dfrac{\dot \rho }{c} \dfrac{\mathscr{\hat r}}{\mathscr{r }} - \rho \dfrac{\mathscr{\hat r }}{\mathscr{ r}^{2}}\right]d \tau'
$$
继续向下求导：
$$
\nabla^{2} V = \dfrac{1}{4\pi \epsilon_{0}} \int \left\{- \dfrac{1}{c}\left[\dfrac{\mathscr{\hat r}}{\mathscr{r}} \cdot (\nabla \dot \rho) + \dot \rho  \nabla  \cdot \left(\dfrac{\mathscr{\hat r}}{r}\right)\right]   -\left[ \dfrac{\mathscr{\hat r}}{\mathscr{r}^{2}}\cdot (\nabla \rho ) + \rho  \nabla  \left( \dfrac{\mathscr{\hat r}}{\mathscr{r}^{2}} \right) \right]          \right\} d \tau'
$$
得到：
$$
\nabla^{2}V = \dfrac{1}{4 \pi \epsilon_{0}} \int\left[\dfrac{1}{c^{2}} \dfrac{\ddot \rho}{\mathscr{r}} - 4\pi \rho \delta ^{3}(\mathscr{r})\right]d \tau' = \dfrac{1}{c^{2}} \dfrac{\partial ^{2}V}{\partial t} - \dfrac{1}{\epsilon_{0}} \rho(r,t)
$$
（注意这里需要将前面的 $V$ 直接代入。这没有逻辑问题，因为我们就是将猜测的 $V$ 的表达式作为已知条件，验证麦克斯韦方程是否成立。）我们就完成了 $V$ 的证明。关于 $A$ 的证明此处不再写。提请注意：如果取 $t_{r}= t + \dfrac{\mathscr{r}}{c}$，也可以完成证明。但是这显然违反因果律。


Jefimenko 方程给出了电场和磁场的显式表达式。在前面，我们已经计算过 $\nabla V$ ，现在我们又知道：
$$
\dfrac{\partial A}{\partial t} = \dfrac{\mu_{0}}{4 \pi} \int \dfrac{\dot J}{\mathscr{r}}
 d\tau'$$
 那么直接得到：
 $$
E(r,t) = \dfrac{1}{4 \pi \epsilon_{0}} \int \left[\dfrac{\rho(r',t_{r})}{\mathscr{r}^{2}} \mathscr{\hat r} + \dfrac{\dot \rho (r',t_{r})}{c \mathscr{r}}  \mathscr{\hat r} - \dfrac{\dot J(r',t_{r})}{c^{2} \mathscr{ r}}\right]d \tau'
$$
计算 $A$ 的旋度：
$$
\nabla \times A  = \dfrac{\mu_{0}}{4 \pi }\int \left[\dfrac{1}{\mathscr{ r}}(\nabla \times J)  -J  \times \nabla \left(\dfrac{1}{\mathscr{r}}\right)\right] d \tau'
$$
将 $\nabla \times J$ 拆开成三个方向计算：
$$
(\nabla \times J)_{x} = \dfrac{\partial J_{z}}{\partial y} - \dfrac{\partial J_{y}}{\partial z}
$$
注意到其中：
$$
\dfrac{\partial J_{z}}{\partial y} = \dot J_{z} \dfrac{\partial  t_{r}}{\partial y} = - \dfrac{1}{c} \dot J_{z} \dfrac{\partial \mathscr{r}}{\partial y} \Rightarrow  (\nabla \times J)_{x}= - \dfrac{1}{c} \left(\dot J_{z} \dfrac{\partial \mathscr{r}}{\partial y} -\dot J_{y} \dfrac{\partial \mathscr{r }}{\partial z}\right) = \dfrac{1}{c}[\dot J \times (\nabla \mathscr{r})]_{x}
$$
从而 $\nabla \times J = \dfrac{1}{c} \dot J \times \mathscr{r}$。磁场的显式表达式为：
$$
B(r,t) = \dfrac{\mu_{0}}{4\pi} \int \left[\dfrac{J(r',t_{r})}{\mathscr{r}^{2}} + \dfrac{\dot J(r',t_{r})}{c \mathscr{r}}\right] \times \mathscr{\hat r} d\tau'
$$
我们可以看出，电场与 $\rho,\dot \rho,\dot J$ 有关，而磁场与 $J,\dot J$ 有关。这个方程实际上不常用，因为求出推迟势再进行微分经常是一个更简单的做法。

## 运动粒子的电磁场
我们现在计算一个运动的粒子的电磁场。比如我们计算电场：
$$
V(r,t) = \dfrac{1}{4\pi \epsilon_{0}} \int \dfrac{\rho(r',t_{r})}{\mathscr{r}} d\tau'
$$
看起来，对于一个点电荷，我们可以直接将其写为 $\dfrac{q}{4 \pi \epsilon_{0} \mathscr{r}}$ ，其中 $\mathscr{r}$ 是推迟过的位置。但很不幸这是错误的。原因是：
$$
\int \rho(r,t_{r}) d\tau'  = \dfrac{q}{1 - \mathscr{\hat r}\cdot v/c}
$$
这是因为推迟项的存在，因此在场点上看起来，带有电荷的区域会在运动方向上被“拉长”一个系数倍（更远的地方产生的影响，会在更晚的时候到达场点）

现在，我们用 $w(t_{r})$ 记点电荷推迟过的位置，令 $\mathscr{r} = r - w(t_{r})$（显然，在这个问题里面，只有推迟过的位置是有意义的），那么我们可以得到:
$$
V(r,t) = \dfrac{1}{4 \pi \epsilon_{0}} \dfrac{qc}{(\mathscr{r}c  -\mathscr{r}\cdot v)} \quad A(r,t) = \dfrac{v}{c^{2}}V(r,t)
$$
注意这里的 $v$ 也是推迟过的速度。从这个势中，我们可以显式计算出电场、磁场（这里计算量逆天，我们直接给出结果）：
$$
E(r,t) = \dfrac{q}{4 \pi \epsilon_{0}}\dfrac{\mathscr{r}}{(\mathscr{r}\cdot u)^{3}}[(c^{2} - v^{2}) u + \mathscr{r} \times (u \times a)]  \quad B(r,t) = \dfrac{1}{c}\mathscr{\hat r}\times E(r,t)$$
特别地，对于匀速运动的带电粒子，令 $R = r - vt$，其中 $r$ 是粒子现在的位置，则 $R$ 是推迟过的位置，那么：
$$
E(r,t) = \dfrac{q}{4 \pi \epsilon_{0}} \dfrac{1 - \dfrac{v^{2}}{c^{2}}}{(1 - \dfrac{v^{2}}{c^{2}}\sin^{2}\theta)^{\frac{3}{2}} } \dfrac{\hat R}{R^{2}}
 \quad B = \dfrac{1}{c^{2}}(v \times E)$$

