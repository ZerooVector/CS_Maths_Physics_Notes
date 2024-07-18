#ElectroDynamics 

## 偶极辐射
辐射是电荷在加速运动的过程中发出能量，这些能量传播到无限远的过程。假设我们有一个巨大的球面，其半径为 $r$，为了求出从这个球面内部流出多少能量，我们必须计算球面上的坡印廷矢量的积分：
$$
P(r,t) = \oint S \cdot da
$$
由于 $t_{0}$ 时刻辐射出的能量将在 $t_{0} + \dfrac{r}{c}$ 时刻到达球面，因此，$t_{0}$ 时刻的辐射功率是：
$$
P_{rad}(t_{0}) = \lim_{r \rightarrow \infty } P\left(r , t_{0} + \dfrac{r}{c}\right)
$$
对于静电场、静磁场的情况来说，$E$ 和 $B$ 都以 $\dfrac{1}{r^{2}}$ 的速度衰减，因此辐射功率显然快速衰减到 0. 只有在电场、磁场变化的情况下才可能出现辐射。现在我们考虑一个最简单的情况：设两金属球相距为 $d$ ，它们之间以一根细导线相连。在 $t$ 时刻，上、下球的电荷量分别为 $q (t), - q(t)$。我们现在使得电荷沿着导线来回移动，从而使得 $q (t) = q_{0}\cos (\omega t)$，我们的电偶极矩：
$$
p(t)  = p_{0} \cos  (\omega t)  \hat z \quad  p_{0}= q_{0}d
$$
从而推迟势：
$$
V(r,t) =  \dfrac{1}{4 \pi \epsilon_{0}} \left[\dfrac{q_{0} \cos\left[\omega\left(t - \dfrac{\mathscr{r}_{+}}{c}\right)\right]}{\mathscr{r}_{+}} - \dfrac{q_{0} \cos\left[\omega\left(t - \dfrac{\mathscr{r}_{-}}{c}\right)\right]}{\mathscr{r}_{- }}\right]
$$
我们现在开始做一些近似。第一个近似是电偶极子的线度十分小，以至于 $d << r$；第二个近似仍然是对偶极子线度的限制，我们要求它远小于电磁波的波长：$d << \dfrac{c}{\omega}$。此时，电势可以写为：
$$
V(r, \theta , t) = \dfrac{p_{0} \cos \theta}{4 \pi  \epsilon_{0}r} \left[ - \dfrac{\omega}{c} \sin \left [\omega \left( t   - \dfrac{r}{c}\right )\right ]+\dfrac{1}{r}\cos  \left [\omega \left( t   - \dfrac{r}{c}\right )\right ]\right]
$$
第三个近似是远场近似，也就是我们研究的位置到原点的距离远远大于电磁波的波长，此时，电势可以近似地写为：
$$
V(r, \theta , t)  =  - \dfrac{p_{0} \omega}{4 \pi \epsilon_{0}c} \left(\dfrac{\cos  \theta}{r}\right)    \sin  \left[\omega\left(t - \dfrac{r}{c} \right)\right ]
$$
现在计算磁矢势：
$$
A(r,t) = \dfrac{\mu_{0}}{4 \pi} \int_{- \frac{d}{2}}^{+ \frac{d}{2}} \dfrac{- q_{0} \omega \sin \left[\omega\left(t  - \dfrac{\mathscr{r}}{c}\right)\right] \hat z}{\mathscr{r}} dzz
$$
作为近似，我们直接使用中心处的值替换这个积分内的函数：
$$
A(r, \theta,t) = - \dfrac{\mu_{0}p_{0} \omega}{4 \pi r} \sin \left(\omega\left(t - \dfrac{r}{c}\right)\right) \hat z
$$
那么我们可以在目前的近似下显式地计算磁场和电场：
$$
E = - \dfrac{\mu_{0}p_{0}\omega^{2}}{4 \pi} \left( \dfrac{ \sin  \theta}{r}\right) \cos \left(\omega\left( 1 - \dfrac{r}{c}\right)\right) \hat \theta
$$
$$
B = - \dfrac{\mu_{0}p_{0} \omega^{2}}{4 \pi c}  \left(\dfrac{\sin \theta}{r} \right)   \cos\left(\omega\left(t  - \dfrac{r}{c}\right)\right) \phi 
 $$
 容易注意到 $E,B$ 是正交的。坡印廷矢量的均值：
 $$
\bar S = \left(\dfrac{\mu_{0}p_{0}^{2} \omega^{4}}{32 \pi^{2}c}\right) \dfrac{\sin^{2} \theta}{r^{2}} \hat r 
$$
积分可以得到辐射功率：
$$
\bar P = \dfrac{ \mu_{0} p_{0}^{2} \omega^{4}}{12 \pi c}
$$
它正比于 $\omega^{4}$，可以用于解释一些有趣的现象，例如天空为什么是蓝色的。

与电偶极子辐射类似的是磁偶极子辐射。它可以看作一个半径为 $b$ 的导体环中通有电流 $I (t) = I_{0}\cos (\omega t)$。通过近似条件 $b<<r, b<<\dfrac{c}{\omega}, r >> \dfrac{c}{\omega}$，可以求出其坡印廷矢量平均值：
$$
\bar S = \left(\dfrac{\mu_{0} m_{0}^{2} \omega^{4}}{32 \pi^{2} c^{3}}\right) \dfrac{\sin^{2} \theta}{r^{2}} \hat r
$$
以及：
$$
\bar  P = \dfrac{\mu_{0}m_{0}^{2} \omega^{4}}{12 \pi c^{3}}
$$

现在，我们考虑来自任意源的辐射。此时，电势是：
$$
V(r,t) = \dfrac{1}{4 \pi \epsilon_{0}} \int \dfrac{\rho\left(r', t - \dfrac{r}{c}\right)}{\mathscr{r}} d \tau' \quad  \mathscr{r }= \sqrt{r^{2} + r'^{2} - 2  r \cdot  r'}
$$
我们仍然要采取一些近似。近似 1 ：电荷所在区域的线度远小于场点到原点的距离，也就是 $r \ll r$ ，那么此时可以展开：
$$
\mathscr{r} \approx  r \left(1 - \dfrac{r\cdot r'}{r^{2}}\right)\quad   \dfrac{1}{\mathscr{r}} \approx \dfrac{1}{r} \left(1 + \dfrac{r \cdot r'}{r^{2}}\right)
$$
如果记 $t_{0}= 1 - \dfrac{r}{c}$，则将 $\rho(r,t)$ 在 $t_{0}$ 处展开，得到：
$$
\rho \left(r', t - \dfrac{\mathscr{r}}{c}\right) \approx  \rho(r' ,t_{0}) + \dot \rho(r' , t_{0}) \left(\dfrac{\hat r  \cdot r'}{c}\right) + \cdots 
$$
在这个式子中，我们只想保留第一项（因为后面的项又涉及到 $r$ 的高阶项），这就要求近似条件 2 ：$r' \ll \dfrac{c}{|\ddot \rho / \dot \rho|}, \dfrac{c}{|\dddot \rho/\dot\rho|^{1/2}},\cdots$ 将现在的式子代入电势的表达式，得到：
$$
V(r,t) = \dfrac{1}{4 \pi \epsilon_{0}} \left[\dfrac{Q}{r} + \dfrac{\hat r  \cdot p(t_{0})}{r^{2}} + \dfrac{ \hat r  \cdot \dot p(t_{0})}{rc}\right]
$$
磁矢势：
$$
A(r,t) = \dfrac{\mu_{0}}{4\pi} \int \dfrac{J\left(r', t - \dfrac{\mathscr{r}}{c}\right)}{\mathscr{r }} d \tau' \approx  \dfrac{\mu_{0}}{4 \pi r} \int J(r',t_{0}) d\tau'
$$
一个结论是，$J$ 对空间的积分等于电偶极矩对时间的导数：
$$
A(r,t) = \dfrac{ \mu_{0} }{4 \pi} \dfrac{\dot p(t_{0})}{r}
$$
现在我们来计算场。根据我们之前讨论的，显然电场和磁场中比 $\dfrac{1}{r^{2}}$ 更高阶的项都不会引起辐射，因此我们在计算场时，只保留到 $\dfrac{1}{r}$ 项（近似 3）。那么，电势中的第一项（点电荷的场）和第二项（偶极子的场）都对辐射没有贡献。，于是我们只需计算：
$$
\nabla V  \approx  \dfrac{1}{4 \pi \epsilon_{0}} \nabla  \left[\dfrac{ \hat r \cdot \dot p (t_{0})}{rc}\right] = - \dfrac{1}{4 \pi \epsilon_{0}c^{2}} \dfrac{\hat r \cdot \ddot p(t_{0})}{r} \hat r  
$$
$$
\nabla \times A  \approx  \dfrac{\mu_{0}}{4 \pi r} [(\nabla  \times t_{0}) \times  \ddot p(t_{0})]  = - \dfrac{\mu_{0}}{4 \pi  rc} [\hat r  \times  \ddot p(t_{0})]
$$
因此我们可以显式地给出场：
$$
E(r,t) = \dfrac{\mu_{0} }{4 \pi  r} [\hat r  \times (\hat r  \times  \ddot p) ] \quad  B(r,t) = - \dfrac{ \mu_{0}}{4 \pi r} [\hat r  \times  \ddot  p ]
$$
或者在极坐标中表示这个场，可以写为：
$$
E(r, \theta ,t) = \dfrac{\mu_{0} \ddot p(t_{0})}{4 \pi} \left(\dfrac{\sin \theta}{r}\right) \hat  \theta \quad  B(r, \theta ,t )  = \dfrac{\mu_{0} \ddot p(t_{0})}{4 \pi c} \left(\dfrac{\sin \theta}{r}\right) \hat \phi  
$$
从而：
$$
S(r,t) = \dfrac{\mu_{0}}{16 \pi^{2}c} [\ddot p(t_{0})] \left(\dfrac{\sin^{2} \theta}{r^{2}}\right) \hat r  \quad  P = \dfrac{\mu_{0}}{6 \pi  c} [\ddot p(t_{0})]^{2}
$$


总结一下，实际上，我们可以计算的只是一些特殊情况：远场、电荷分布区域的线度很小（这导致 $r' \ll r$，且 $r$ 远大于电磁波波长，$r'$ 远小于电磁波波长）。在这些情况下，我们可以利用合理的近似，将电荷分布近似成电偶极，然后计算 $S$ 和辐射功率。振荡的电偶极带来 $E,B \sim \dfrac{1}{r}$，因此 $r \rightarrow \infty$ 时，我们得到有限的辐射功率，这就是所谓偶极辐射。

## 运动的点电荷的辐射
之前我们推导了点电荷的电场：
$$
E(r,t) = \dfrac{q}{4 \pi \epsilon_{0}} \dfrac{\mathscr{r}}{(\mathscr{r}\cdot  u)^{3}} [(c^{2} - u^{2}) u + \mathscr{r} \times (u  \times a)]
$$
其中 $u =  c \mathscr{ \hat r} - v$，磁场则是：
$$
B(r,t) = \dfrac{1}{c} \mathscr{ \hat r} \times E(r,t)
$$
我们可以使用和之前偶极辐射一样的套路把这个单粒子的辐射做出来。能流密度：
$$
S = \dfrac{1}{\mu_{0}}(E \times B) = \dfrac{1}{\mu_{0}c^{2}}[E^{2}\mathscr{\hat r} - (\mathscr{\hat r} \cdot E) E]
$$
但是，这个能流密度并不全是粒子辐射出的，有些能量只是跟随着粒子移动。我们现在希望研究那些去往无穷远、一去不返的能量。我们画一个半径为 $\mathscr{r}$ 的球面，球心在粒子 $t_{r}$ 时刻的位置处（因为 $t_{r}$ 时刻粒子辐射出的能量恰好到达这个球面上。由于电荷的运动速度小于光速，所以也只有 $t_{r}$ 时刻辐射出的能量可以到达这个面上。）显然，我们只需要考虑 $E$ 中正比于 $\dfrac{1}{r}$ 的项，我们将这一项称为辐射场：
$$
E_{rad} = \dfrac{q}{4 \pi \epsilon_{0}} \dfrac{\mathscr{r}}{(\mathscr{r \cdot u})^{3}}[\mathscr{r } \times ( u \times a)]
$$
注意这里的 $\mathscr{r} = r - w(t_{r})$ ，之前的 $v$ 也是推迟过的速度。从而 $S_{rad} = \dfrac{1}{\mu_{0}c}E_{rad}^{2} \mathscr{\hat r}$。最简单的情况下，假设粒子在 $t_{r}$ 时刻瞬时静止，那么 $u = c \mathscr{\hat r}$，从而：
$$
E_{rad} = \dfrac{q}{4 \pi \epsilon_{0} c^{2} \mathscr{r }}[\mathscr{\hat r} \times(\mathscr{\hat r}\times a)] = \dfrac{\mu_{0}q}{4 \pi \mathscr{r}}[(\mathscr{\hat r }\cdot a) - a]
$$
计算可以得到：
$$
S_{rad} = \dfrac{\mu_{0}q^{2a^{2}}}{16 \pi^{2}c} \left(\dfrac{\sin^{2} \theta}{\mathscr{r}^{2}}\right)\mathscr{\hat r} \quad P = \dfrac{\mu_{0}q^{2}a^{2}}{6 \pi c}
$$
这个公式被称为 Larmor 公式：粒子的辐射功率与加速度的平方成正比。

现在考虑粒子在 $t_{r}$ 时刻不是瞬时静止的情况。除了电场、磁场和 $S$ 的形式变得复杂之外，还有一个很阴间的问题：能量离开点电荷的速率与穿过球面的速率不再相同。这个问题主要出现在：设 $\dfrac{\mathrm{d}W}{\mathrm{d}t}$ 是能量穿过球面的速率，那么能量离开点电荷的速率是：
$$
\dfrac{\mathrm{d}W}{\mathrm{d}t_{r}} = \dfrac{\dfrac{\mathrm{d}W}{\mathrm{d}t}}{\dfrac{\partial t_{r}}{\partial t}}  = \left(\dfrac{\mathscr{r} \cdot u}{\mathscr{r}c}\right)\dfrac{\mathrm{d}W}{\mathrm{d}t}
$$
（我们来重点解释一下这件事情。这里考虑了非相对论的多普勒效应，使得 $[t,t+dt]$ 内到达球面的能量是由 $[t_{r}, t_{r} + dt_{r}]$ 内被电荷发出的，而 $dt \not  = dt_{r}$。我们现在希望研究在 $t_{r}$ 时刻，单位时间内离开点电荷的能量，而 $\dfrac{\mathrm{d}W}{\mathrm{d}t}$ 给出的是在 $t$ 时刻，单位时间内流出球面的能量，二者之间差一个系数）
那么容易求出从电荷单位时间内辐射到单位立体角内的能量是：
$$
\dfrac{\mathrm{d}P}{\mathrm{d}\Omega} = \dfrac{q^{2}}{16 \pi^{2} \epsilon_{0}} \dfrac{|\mathscr{\hat r}\times (u \times a)|^{2}}{(\mathscr{\hat r}\cdot u)^{5}}
$$
那么对全空间积分，就得到：
$$
P = \dfrac{\mu_{0}q^{2}\gamma^{6}}{6 \pi c} \left(a^{2} - |\dfrac{v \times a}{c}|^{2} \right) \quad \gamma = \dfrac{1}{\sqrt{1 - \dfrac{v^{2}}{c^{2}}}}
$$

显然，运动的粒子辐射能量，这将导致其动能的降低。考虑非相对论的低速粒子，假设辐射带来的等效作用力为 $F_{rad}$，则它满足：
$$
F_{rad} \cdot v   = - \dfrac{\mu_{0} q^{2}a^{2}}{6 \pi c}
$$
注意：这里只考虑了那些辐射到无穷远处的能量，实际上，粒子的场也携带一部分随着粒子运动的能量，粒子与这部分场之间也有能量交换，只不过这里忽略了。我们假定粒子进行某种周期性运动，以至于在 $t_{1},t_{2}$ 时刻系统的状态相同，那么我们取个平均：
$$
\int_{t_{1}}^{t_{2}} F_{rad} \cdot v  dt  =  - \dfrac{ \mu_{0}q^{2}}{6 \pi c} \int_{t_{1}}^{t_{2}} a^{2}dt 
$$
分部积分：
$$
\int_{t_{1}}^{t_{2}} a^{2}dt  = \int_{t_{1}}^{t_{2}} \left(\dfrac{\mathrm{d}v}{\mathrm{d}t}\right)\left(\dfrac{\mathrm{d}v}{\mathrm{d}t}\right) dt = \left(v \cdot \dfrac{\mathrm{d}v}{\mathrm{d}t}\right) - \int \dfrac{\mathrm{d}^{2} v}{\mathrm{d}t^{2}} \cdot v dt 
$$
第一项由于系统在两个边界处状态一致，所以去掉了，那么上式被写为：
$$
\int_{t_{1}}^{t_{2}} \left(F_{rad} - \dfrac{\mu_{0}q^{2}}{6 \pi c} \dot a\right)\cdot v  dt  = 0 
$$
于是：
$$
F_{rad} = \dfrac{\mu_{0}q^{2}}{6 \pi c} \dot a
$$
显然，这会导致各种逆天的、不可接受的结果。

有一个简单的模型来说明这个力产生的机理：两个相距为 $d$ 的电荷，分别带电 $\dfrac{q}{2}$ 。设这个电荷"哑铃"沿着 $y$ 方向放置，而它沿着 $x$ 方向移动。设它在 $t_{r}$ 时瞬时静止，加速度为 $a$，可以计算出它施加在自身上的力是：
$$
F_{self}= \dfrac{q^{2}}{8 \pi  \epsilon_{0}c^{2}} \dfrac{lc^{2} - ad^{2}}{(l^{2} + d^{2})^{3/2}}
$$
其中 $l = x (t) - x(t_{r})$。在 $t_{r}$ 处展开 $x(t)$，令 $T = t - t_{r}$，得到：
$$
l = \dfrac{1}{2}aT^{2} + \dfrac{1}{6}\dot a T^{3} + \cdots  
$$
利用 $(cT)^{2} = l^{2} + d^{2}$，可以展开 $d \approx cT - \dfrac{a^{2}}{8c}T^{3} + \cdots$，从而可以将 $T$ 用 $d$ 表达为：$T \approx \dfrac{1}{c}d + \dfrac{a^{2}}{8c^{5}}d^{3}$ ，代入 $l$ 的表达式得到：$l = \dfrac{a}{2c^{2}}d^{2} + \dfrac{\dot a}{6c^{3}}d^{3} + \cdots$，回代到力的表达式，就得到：
$$
F_{self} = \dfrac{q^{2}}{4 \pi \epsilon_{0}} \left[ - \dfrac{a}{4c^{2}d} + \dfrac{\dot a }{12 c^{3}} + \cdots \right]\hat x 
$$
再利用 $a (t_{r}) \approx a (t) + \dot a (t) \dfrac{d}{c} + \cdots$，上面的结果被写成：
$$
F_{self} = \dfrac{q^{2}}{4 \pi \epsilon_{0}} \left[ - \dfrac{a(t)}{4c^{2}d} + \dfrac{\dot a(t) }{12 c^{3}} + \cdots \right]\hat x 
$$
 第一项只是给这个系统增加了惯性（可以认为是系统的电势能带来的）；第二项则是辐射带来的“反冲”（注意这个"反冲"与前面的公式对比只有一半，这是因为没有计及每个 $\dfrac{q}{2}$ 给自己的力。在一些更复杂的模型里面，例如研究一条线电荷，这个问题会被解决）

