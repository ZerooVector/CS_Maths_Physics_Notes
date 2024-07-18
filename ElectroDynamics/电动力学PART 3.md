#ElectroDynamics 

## 一维波的描述
我们考虑一维上，波以恒定速度传播的情形。不妨设波是向 $z+$ 方向传播的，那么我们是使用 $f(z,t)$ 表示 $z$ 位置在 $t$ 时刻的位移，显然有 $f (z, t) = f (z-vt, 0) = g(z-vt)$（为方便起见，我们记 $f (z-vt, 0) = g(z-vt)$）。各种各样的波都可以在介质中传播，我们可以写出介质的动力学方程。例如，我们关注弦线上 $[z,z+ \Delta z]$ 一段，两端处弦线与 $z$ 轴的夹角分别为 $\theta$ 和 $\theta'$，弦线上的张力为 $T$，那么这一段弦线的受力：
$$
\Delta F = T \sin \theta '  - T \sin \theta  \approx T(\tan \theta ' - \tan \theta)= T\left(\dfrac{\partial f}{\partial z}|_{z + \Delta z} - \dfrac{\partial f}{\partial z}|_{z}\right) \approx T \dfrac{\partial^{2} f}{\partial z^{2}} \Delta z
$$
根据牛顿第二定律，我们就可以写出波动方程：
$$
\dfrac{\partial^{2}f }{\partial z^{2}} = \dfrac{\mu}{T} \dfrac{\partial ^{2}f}{\partial t^{2}}
$$
波速与比例系数有关，$v = \sqrt{\frac{T}{\mu}}$ 。

利用 $f (z, t) = g(z-vt)$ ，两侧对 $z, t$ 求两阶导数可以很快验证这一点。因为波动方程中只含有 $v^2$ ，所以我们改变一下 $v$ 的符号就可以得到另一个解：$f (z, t) = h(z + vt)$。因此，波动方程的解是：
$$
f(z,t) = g(z-vt) + h(z+vt)
$$

最简单的一维波就是正弦波。它可以写为：
$$
f(z,t) = A \cos[k(z - vt) + \delta]
$$
其中 $k$ 被称为波数，$\lambda = \dfrac{2\pi}{k}$ 称为波长，$T = \dfrac{2\pi}{kv}$ 称为周期，$\nu =\dfrac{v}{\lambda}$ 称为频率，$\omega = k v$ 称为角频率。

为了在数学上操作更为方便，我们会将波写成复数的形式：
$$
\tilde f(z,t) = \tilde A \exp(i  (kz - \omega t)) \quad f(z,t) = \text{Re}[\tilde f(z,t)]
$$
根据傅里叶定律，每个波都可以被写成无限多个正弦波叠加的形式：
$$
\tilde f(z,t) = \int_{-\infty}^{+\infty} \tilde A(k) \exp(i (kz -\omega t)) dk 
$$


现在我们来考虑一下边界条件。考虑一个简单的情形：一束波沿着弦线向 $z+$ 方向射来，但是在原点处，两条弦线被系在一起，它们的张力相同，但线密度却不一样。此时，入射波是：$\tilde f_{I}(z, t) = \tilde A_{I}\exp(i (k_{1}  z  - \omega t))$ ，反射波是 $\tilde f_{R}(z, t) = \tilde A_{R}\exp(i (-k_{1}  z  - \omega t))$，透射波是 $\tilde f_{T}(z, t) = \tilde A_{T}\exp(i (k_{2}  z  - \omega t))$。原点处的位移一定是连续的：$f (0^{-}, t) = f(0^{+},t)$，并且，如果忽略绳结的质量，那么还有 $\dfrac{\partial f}{\partial z}|_{0^{-}} = \dfrac{\partial f}{\partial z}|_{0^{+}}$。通过这些边界条件，我们就可以得到：
$$
\tilde A_{R} = \left(\dfrac{v_{2} - v_{1}}{v_{2} + v_{1}}\right) \tilde A_{I} \quad \tilde A_{T} = \left(\dfrac{2v_{2}}{v_{2} + v_{1}}\right) \tilde A_{I}
$$

我们刚才研究的弦线上的波是横波。对于横波，我们定义一个处在其振动的面内的矢量 $\hat n$
为其偏振方向。偏振方向显然与波的传播方向垂直。

## 真空中的电磁波
麦克斯韦方程组预言了电磁波的产生，我们现在试图将 $E$ 和 $B$ 解耦：
$$
\nabla \times(\nabla \times E) = \nabla(\nabla\cdot  E) - \nabla^{2}E = \nabla \times \left(- \dfrac{\partial B}{\partial t}\right) = - \dfrac{\partial }{\partial t}(\nabla \times B)  = - \mu_{0} \epsilon_{0} \dfrac{\partial ^{2}E}{\partial t}
$$
对 $B$ 可做类似的处理。我们最终得到：
$$
\nabla^{2}E = \mu_{0}\epsilon_{0} \dfrac{\partial ^{2}E}{\partial t^{2}}  \quad \nabla^{2}B = \mu_{0}\epsilon_{0} \dfrac{\partial ^{2}B}{\partial t^{2}}  
$$
因此，$E$ 和 $B$ 都符合三维波动方程，且波速 $c = \dfrac{1}{\sqrt{\epsilon_{0} \mu_{0}}}$ 。

接下来我们研究最简单的情形：沿着 $+z$ 方向传播的单色平面波。此时，$E$ 和 $B$ 被写为：
$$
\tilde  E(z,t) = \tilde E_{0} \exp(i (kz - \omega t))  \quad  \tilde  B(z,t) = \tilde B_{0} \exp(i (kz - \omega t))
$$
每一个麦克斯韦方程组的解都满足波动方程，但并不是每一个波动方程的解都满足麦克斯韦方程组。很容易看出麦克斯韦方程组其实施加了额外的条件，由于真空中 $\nabla \cdot E = 0, \nabla \cdot B = 0$，所以 $(\tilde E_{0})_{z} = (\tilde B_{0})_{z} = 0$。此外，法拉第电磁感应定律施加了另一个限制：
$$
\tilde B_{0} = \dfrac{k}{\omega}(\hat z \times \tilde E_{0})
$$
因此，$B$ 和 $E$ 是互相正交的，但是有相同的相位。
我们容易写出沿着任意方向传播的电磁波的方程：
$$
\tilde E(r,t) = \tilde E_{0}\exp(i (k\cdot r - \omega t)) \hat n  \quad B  = \dfrac{1}{c} \hat k \times E
$$

我们可以求出电磁波携带的能量密度（这里电场和磁场贡献相同的的能量密度）：
$$
u= \epsilon_{0}E^{2} = \epsilon_{0} E_{0}^{2} \cos^{2}(kz  - \omega t + \delta )
$$
同理可以计算能流密度矢量和动量密度，计算得到的平均值是：
$$
\bar u  = \dfrac{1}{2} \epsilon_{0} E_{0}^{2} \quad  \bar  S = \dfrac{1}{2}c \epsilon_{0}E_{0}^{2} \hat z \quad \bar g = \dfrac{1}{2c} \epsilon_{0}E_{0}^{2} \hat z  
$$
我们将单位时间内单位面积上传播的能量称为电磁波的强度，也就是 $I = \dfrac{1}{2}c \epsilon_{0}E_{0}^{2}$。当电磁波射入到一个可以吸收电磁波的物体的时候，电磁波将其携带的动量转移到物体上。转移的动量是 $\Delta  p  = \bar g  Ac \Delta t$，据此我们可以计算出辐射压强 $P = \dfrac{I}{c}$。


## 介质中的电磁波
仿照真空中电磁波的推导过程，容易写出介质中电磁波的波速 $v = \dfrac{c}{n}$ ，其中 $n = \sqrt{\dfrac{\epsilon \mu}{\epsilon_{0} \mu_{0}}}$ 被称为折射率。容易推导出介质中波的强度是 $I = \dfrac{1}{2}\epsilon v E_{0}^{2}$。

现在我们研究波的反射和透射问题。假设我们有两种介质，它们的交界面是 $x-y$ 平面。现在，一束电磁波沿着 $+z$ 方向射来：
$$
\tilde E_{I} (z,t) = \tilde E_{0I} \exp(i(k_{1}z - \omega t)) \hat x \quad \tilde B_{I} (z,t) = \dfrac{1}{v_{1}} \tilde E_{0I} \exp(i(k_{1}z - \omega t)) \hat y
$$
我们给出反射波：
$$
\tilde E_{R} (z,t) = \tilde E_{0R} \exp(i(- k_{1}z - \omega t)) \hat x \quad \tilde B_{R} (z,t) = - \dfrac{1}{v_{1}} \tilde E_{0R} \exp(i(- k_{1}z - \omega t)) \hat y
$$
和透射波：
$$
\tilde E_{T} (z,t) = \tilde E_{0T} \exp(i(k_{2}z - \omega t)) \hat x \quad \tilde B_{T} (z,t) = \dfrac{1}{v_{2}} \tilde E_{0T} \exp(i(k_{2}z - \omega t)) \hat y
$$
利用边界条件：
$$
\tilde E_{0I} + \tilde  E_{0R} = \tilde E_{0T} \quad \dfrac{1}{\mu_{1}}\left(\dfrac{1}{v_{1}}\tilde E_{0I}  -  \dfrac{1}{v_{1}} \tilde E_{0R}\right) = \dfrac{1}{\mu_{2}} \left(\dfrac{1}{v_{2}} \tilde E_{0T} \right)
$$
可以立刻得解：
$$
\tilde E_{0R} = \left(\dfrac{v_{2} - v_{1}}{v_{2} + v_{1}}\right) \tilde E_{0I} \quad  \tilde E_{0T} = \left(\dfrac{2v_{2}}{v_{2} + v_{1}}\right) \tilde E_{0I} 
$$
我们会将反射率和透射率定义为强度比：
$$
R = \dfrac{I_{R}}{I_{T}} = \left(\dfrac{n_{1} - n_{2}}{n_{1}+n_{2}}\right)^{2}  \quad T = \dfrac{I_{T}}{I_{I}} = \dfrac{4n_{1}n_{2}}{(n_{1}+n_{2})^{2}}
$$
由于能量守恒，我们自然得到 $R+T =1$。

但是，以上情况太过简单：因为电磁波是垂直于界面入射的。现在我们要研究一般的情况。我们现在给出如下的入射、反射、透射波：
$$
\tilde E_{I}(r,t) = \tilde E_{0I} \exp(i(k_{I}\cdot r - \omega  t)) \quad  \tilde B_{I}(r,t) = \dfrac{1}{v_{1}} (\hat  k_{I}  \times \tilde E_{I})
$$
$$
\tilde E_{R}(r,t) = \tilde E_{0R} \exp(i(k_{R}\cdot r - \omega  t)) \quad  \tilde B_{R}(r,t) = \dfrac{1}{v_{1}} (\hat  k_{R}  \times \tilde E_{R})
$$
$$
\tilde E_{T}(r,t) = \tilde E_{0T} \exp(i(k_{T}\cdot r - \omega  t)) \quad  \tilde B_{T}(r,t) = \dfrac{1}{v_{2}} (\hat  k_{T}  \times \tilde E_{R})
$$
所有的波都有相同的角频率：$k_{I}v_{1} = K_{R}v_{1} = k_{T} v_{2} = \omega$。现在我们开始考虑边界条件。显然，边界上的电磁场应该连续（注意，这应该对边界上的任意一点成立！）那么：
$$
k_{I}\cdot r = k_{R} \cdot r = k_{T}\cdot r
$$
那么这就需要 $k_{I},k_{R},k_{T}$ 的分量分别相等。我们现在将三者与法线的夹角记为 $\theta_{I},\theta_{R},\theta_{T}$，那么，我们有：
- **三线共面**：$k_{I},k_{R},k_{T}$ 在同一平面内
由于 $k_{I} \sin \theta_{I} = K_{R} \sin \theta_{R} = K_{T} \sin \theta_{T}$，我们立刻又得到：
- **两角相等**：入射角等于反射角
- **折射定律**：$n_{1} \sin \theta_{I} = n_{2} \sin \theta_{T}$
这就是几何光学中重要的三定律。

现在，我们已经考虑完了指数项，是时候考虑介质中电磁场所满足的边界条件了。四个边界条件是：
$$
\epsilon_{1} (\tilde E_{0I}+ E_{0R})_{z} = \epsilon_{2}(\tilde E_{0T})_{z} \quad (\tilde B_{0I} + \tilde B_{0R})_{z}= (\tilde B_{0T})_{z} 
$$
$$
(\tilde E_{0I} + \tilde E_{0R})_{x,y} = (\tilde E_{0T})_{x,y} \quad \dfrac{1}{\mu_{1}} (\tilde B_{0I} + \tilde B_{0R})_{x,y}  = \dfrac{1}{\mu_{2}}(\tilde B_{0T})_{x,y}
$$
边界条件 1 给出：
$$
\epsilon_{1}( - \tilde E_{0I} \sin \theta_{I} + \tilde E_{0R}  \sin  \theta_{R})  = \epsilon_{2} ( - \tilde E_{0T} \sin \theta_{T})
$$
边界条件 2 给出 $0=0$，没啥用
边界条件 3 给出：
$$
\tilde E_{0I} \cos \theta_{I} + \tilde E_{0R} \cos  \theta_{R} = \tilde E_{0T}  \cos  \theta_{T}
$$
边界条件 4 给出：
$$
\dfrac{1}{\mu_{1} v_{1}} (\tilde E_{ot} - \tilde E_{0R}) = \dfrac{1}{\mu_{2} v_{2}} \tilde E_{0T}
$$

利用这些边界条件可以给出：
$$
\beta = \dfrac{\mu_{1} n_{1}}{\mu_{2} v_{2}} \quad  \alpha= \dfrac{ \cos \theta_{T}}{\cos \theta_{I}}
$$
$$
\tilde E_{0R} = \left(\dfrac{\alpha - \beta}{\alpha  + \beta}\right) \tilde E_{0I} \quad  \quad  \tilde E_{0T} = \left(\dfrac{2}{\alpha+ \beta}\right) \tilde E_{0I}
$$
这一组公式称为菲涅尔公式。在 $\theta_{I} = 90^{\circ}$ 时，$\alpha \rightarrow +\infty$，因此所有能量都被反射。在 $\alpha= \beta$ 时，也就是 $\theta_{I} = \theta_{B} = \arctan \left(\dfrac{n_{2}}{n_{1}}\right)$ 时，没有能量被反射。这个角度称为布儒斯特角。我们仍然可以按照强度之比定义反射率和透射率：
$$
R= \dfrac{I_{R}}{I_{I}} = \left(\dfrac{\alpha- \beta}{\alpha + \beta}\right)^{2} \quad  T = \dfrac{I_{T}}{I_{I}} = \alpha \beta\left(\dfrac{2}{\alpha + \beta}\right)^{2} 
$$


## 导体中的电磁波、电磁波的吸收和色散
我们现在要讨论导体中的电磁波。此时，$\rho_{F}$ 和 $J_{F}$ 都不为 0。根据欧姆定律，我们有 $J_{F} = \sigma E$；根据电流的连续性方程，我们有：$\nabla \cdot J_{F} = - \dfrac{\partial \rho_{F}}{\partial t}$。那么：
$$
\dfrac{\partial \rho_{F}}{\partial t} = - \dfrac{\sigma}{\epsilon} \rho_{F}
$$
从而推出，对于某一位置的电荷密度：
$$
\rho_{F}(t) = \exp\left(- \dfrac{\sigma}{\epsilon}t\right)\rho_{F}(0)
$$
因此，在导电性能良好的导体中，自由电荷将会很快消散。在之后的讨论中，我们认为 $\rho_{F} = 0$。像之前一样，我们可以写出 $E$ 和 $B$ 满足的方程：
$$
\nabla^{2}E  = \mu \epsilon \dfrac{\partial ^{2}E}{\partial t^ {2}} + \mu  \sigma \dfrac{\partial E}{\partial t} \quad \nabla^{2}B  = \mu \epsilon \dfrac{\partial ^{2}B}{\partial t^ {2}} + \mu  \sigma \dfrac{\partial B}{\partial t}
$$
我们仍然能将电磁波写成如下形式：
$$
\tilde E(z,t) = \tilde E_{0} \exp( i ( \tilde kz  - \omega t)) \quad \tilde B(z,t) = \tilde B_{0} \exp( i ( \tilde kz  - \omega t))
$$
其中，$\tilde k = k + i \kappa$。因此，电磁波会在传播的过程中不断衰减。我们将电场或磁场的振幅衰减到原来的 $\dfrac{1}{e}$ 时电磁波传播的距离称为趋肤深度 $d$，那么 $d = \dfrac{1}{\kappa}$。$\tilde k$ 的实部决定了波长、波速和折射率等等。此外，由于麦克斯韦方程组，$\tilde E_{0},\tilde B_{0}$ 之间有约束：
$$
\tilde B_{0} = \dfrac{\tilde k}{\omega} \tilde E_{0}
$$
此时，$B$ 和 $E$ 的相位通常是不同的。

同样地，我们可以讨论导体界面上的透射和反射。假设介质 1 是不导电的线性电介质，介质 2 是导体，分界面是 $xy$ 面，一束平面单色波从无穷远处沿 $+z$ 方向射来，使用边界条件 
$$\epsilon_{1}E_{1}^{n} - \epsilon_{2}E_{2}^{n} = 0 \quad  E_{1}^{t} = E_{2}^{t} \quad B_{1}^{n} = B_{2}^{n} \quad \dfrac{1}{\mu_{1}}B_{1}^{t} - \dfrac{1}{\mu_{2}}B_{2}^{t} = K_{f} \times n $$
以及电磁场的连续性，可以得到：
$$
\beta = \dfrac{ \mu_{1} v_{1}}{\mu_{2} \omega } \tilde  k_{2} \quad \tilde E_{0R} = \left(\dfrac{1 - \tilde \beta}{1 + \tilde \beta}\right) \tilde E_{0I} \quad  \tilde E_{0T} = \left(\dfrac{2}{1 + \tilde \beta}\right) \tilde E_{0I}
$$


接下来我们研究另一件事情：我们知道，玻璃对于不同颜色的光的折射率一般不同，这种现象被称为色散。一般来说，介质的磁导率相差不大，都在 $\mu_{0}$ 附近，因此折射率主要受到电导率的影响（$n \approx \sqrt{\epsilon_{r}}$）。我们现在希望研究材料的电导率和入射波的频率有何关系。
我们知道，在色散介质中，波的不同频率分量传播的速度不同。波包中每个正弦分量的传播速度是：
$$
v = \dfrac{ \omega}{k}
$$
这被称为“相速度”，而整个波包的传播速度则是：
$$
v_{g}=  \dfrac{\mathrm{d}\omega}{\mathrm{d}k}
$$

这被称为“群速度”。
我们现在建立一个简单的模型来描述电介质中被束缚的电子在外场下的运动。设这些电子的运动方程是：
$$
m \dfrac{\mathrm{d}^{2}x}{\mathrm{d}t^{2}} + m \gamma \dfrac{\mathrm{d}x}{\mathrm{d}t} + m \omega_{0}^{2}x  = q E_{0}\cos  (\omega t)
$$
可以求出电子的位移是 $\tilde x (t) = \tilde x_{0}\exp(- i \omega t)$，其中：
$$
\tilde x_{0} = \dfrac{q / m }{\omega_{0}^ {2} - \omega^{2} - i \gamma \omega} E_{0}
$$
这带来的电偶极矩是 $\tilde p (t) = q \tilde x(t)$。设某种介质单位体积内有 $N$ 个分子，固有频率为 $\omega_{i}$，阻尼系数为 $\gamma_{i}$ 的电子有 $f_{i}$ 个，则介质的电极化强度矢量：
$$
\tilde P = \dfrac{Nq^{2}}{m} \left(\sum_{i} \dfrac{f_{i}}{\omega_{i}^{2} - \omega^{2} - i \gamma_{i} \omega}\right)  =\epsilon_{0} \tilde \chi \tilde E
$$
从而：
$$
\tilde \epsilon_{r} = 1 + \dfrac{Nq^{2}}{m \epsilon_{0}} \sum_{i} \dfrac{f_{i}}{\omega_{i}^{2} - \omega^{2} - i \gamma_{i} \omega}
$$
此时电磁波被写为 $\tilde E (z, t) = \tilde E_{0} \exp( i (\tilde k z - \omega t))$ 。此时 $\tilde k = k + i \kappa$，电磁波也是在衰减的（这是因为我们在电子的运动方程中引入了阻尼项，这显然会消耗能量）

如果认为 $\epsilon_{r}$ 和 1 的偏离很小（例如，对于稀薄的气体），我们可以适当使用小量近似后推出折射率：
$$
n =  1 +  \dfrac{Nq^{2}}{2 m \epsilon_{0}} \sum_{i} \dfrac{f_{i}}{\omega_{i}^{2} - \omega^{2}}
$$
对于大部分透明材料来说，$\omega_{i}$ 通常分布在紫外线区间，因此 $\omega < \omega_{i}$。若认为 $\omega<<\omega_{i}$，则再次使用小量近似，就得到所谓"柯西公式"：
$$
n = 1 + A (1  + \dfrac{B}{\lambda^{2}})
$$
这一公式对绝大多数气体成立。

## 波导
我们现在考虑电磁波在一个中空管道（波导）内的传播，波导的管壁由理想导体制成，因此其中 $B=0,E=0$。利用边界条件，在内壁上必然有：$E^{t} = 0, B^{n} = 0$。现在考虑电磁波的一般形式：
$$
\tilde E(x,y,z,t) = \tilde E_{0}(x,y) \exp(i (kz - \omega t))  \quad \tilde B(x,y,z,t) = \tilde B_{0}(x,y) \exp(i (kz - \omega t))
$$
现在我们要寻找 $\tilde E_{0} ,\tilde B_{0}$，使得麦克斯韦方程组和边界条件得到满足。通过将 $E$ 和 $B$ 写成分量式，代入麦克斯韦方程，我们可以得到：
$$
\left[\dfrac{\partial ^{2}}{\partial x^{2}} + \dfrac{\partial ^{2}}{\partial y^{2}} + \left(\dfrac{ \omega }{c}\right)^{2} - k^{2}\right ]E_{z} = 0  \quad \left[\dfrac{\partial ^{2}}{\partial x^{2}} + \dfrac{\partial ^{2}}{\partial y^{2}} + \left(\dfrac{ \omega }{c}\right)^{2} - k^{2}\right ]B_{z} = 0 
$$
我们将 $E_{z} = 0$ 的波称为 TE 波，将 $B_{z}=0$ 的波称为 TM 波，若二者均为 0，则我们称之为 TEM 波。可以证明 TEM 波不会在一个中空的波导中出现。

我们可以考虑一些特殊的例子，例如，在矩形波导内传播的 TE 波。使用分离变量法，令 $B_{z}(x, y) = X(x)Y(y)$，得到关于 $X(x),Y(y)$ 的全微分方程：
$$
\dfrac{1}{X} \dfrac{\mathrm{d}^{2}X}{\mathrm{d}x^{2}} = - k_{x}^{2} \quad \dfrac{1}{Y} \dfrac{\mathrm{d}^{2}Y}{\mathrm{d} y^{2}} = - k_{y}^{2}
$$
得到通解：
$$
X(x) = A \sin (k_{x}x) + B \cos (k_{x}x)
$$
利用边界条件可以确定 $k_{x}  =\dfrac{m \pi }{a}, A = 0$，其中 $a$ 是波导的长，对于 $Y(y)$ 也类似。因此我们最终得到结论：
$$
B_{z} = B_{0}\cos\left( \dfrac{ m \pi x }{a}\right) \cos\left(\dfrac{n \pi y}{b}\right)
$$
波数是：
$$
k = \sqrt{\left(\dfrac{\omega}{c}\right)^{2} - \pi^{2}\left[\left(\dfrac{m}{a}\right)^{2} + \left(\dfrac{n}{b}\right)^{2}\right] }
$$
在 $k$ 为复数时，对应频率的电磁波将衰减，无法传播。最低的截断频率是 $\omega_{10} = \dfrac{c \pi}{a}$。

一种可以传输 TEM 波的波导是共轴传输线。它由一根半径为 $a$ 的圆柱形导线和半径为 $b$ 的导体圆柱壳组成。在其中传播的电磁波有如下形式：
$$
E = \dfrac{A\cos(kz -  \omega t)}{s} \hat s  \quad  B = \dfrac{A \cos(kz - \omega t)}{cs} \hat \phi 
$$

