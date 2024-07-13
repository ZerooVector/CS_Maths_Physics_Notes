#ElectroDynamics 

## 一维的 Delta 函数
我们考虑一个在当前定义下的悖论。假定我们有矢量场 $v = \dfrac{1}{r^{2}}\hat r$，那么经过计算我们可以知道它的散度是处处为 0 的，但是，对于任意包围原点的面，该矢量场的通量不为 0，这二者显然是相互矛盾的。注意到 $\int (\nabla \cdot v) d \tau$ 的结果实际上与 $r$ 无关，那么根据散度定理，我们可以发现这个矢量场就像只在原点处有散度一样。（这就像是一个质点一样，在某一点处的密度是无穷大，其余位置密度都为 0，总质量为一个有限值。）在这种情况下，我们会引入一个广义函数——狄拉克 Delta 函数来解决这个问题。在一维上，Delta 函数被定义为：
$$
\delta(x) = \begin{cases}
0  &\quad x \not= 0 \\
+\infty &\quad  x =0  
\end{cases}
\quad 
\int_{-\infty}^{+\infty} \delta(x)dx = 1
$$
你可以把 Delta 函数想成面积为 1 的，不断变窄的矩形或者等腰三角形。容易注意到 Delta 函数满足性质 $f (x) \delta (x) = f (0) \delta(x)$，那么可以很容易发现选择性质：
$$
\int_{- \infty}^{+ \infty} f(x) \delta (x-a)dx = f(a)
$$
还容易注意到 Delta 函数的一个性质是
$$
\delta(kx) = \dfrac{1}{|k|} \delta(x)
$$
对于这个结果的直观理解，我们可以视为 $\delta(kx)$ 是在 $x$ 方向上“压缩”了 Delta 函数。

虽然 Delta 函数并不是一个符合数学上对“函数”的定义的函数，但是 Delta 函数在积分号下面可以正常地运行，甚至你可以理解为 Delta 函数是只能在积分号下面运行的。一般来说，$D_{1}(x),D_{2}(x)$ 是含有 Delta 函数的表达式，如果它们两个相等，我们的意思是它们对于任意函数有着相同的“选择”作用，也就是：
$$
\int_{-\infty}^{+\infty} f(x) D_{1}(x) dx = \int_{-\infty}^{+\infty} f(x) D_{2}(x) dx
$$

## 三维的 Delta 函数
一个三维的 Delta 函数被定义为：
$$
\delta^{3}(r) = \delta(x)\delta(y) \delta(z)
$$
它在全空间的积分：
$$
\int_{\text{all space}} \delta^{3}(r) d\tau = \int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty} \delta(x) \delta(y)\delta(z) dxdydz = 1
$$
从而它也有选择性质：
$$
\int_{\text{all space}}  f(r) \delta^{3}(r-a)d\tau = f(a)
$$

那么我们可以解决在本节一开始时提出的问题，我们需要使用 Delta 函数来定义散度：
$$
\nabla \left(\dfrac{\hat r }{r^{2}}\right) = 4 \pi \delta^{3}(r) 
$$
这个时候就不会出现不自洽的问题。显然我们也可以得到：
$$
\nabla^{2} \dfrac{1}{r} = -4 \pi \delta^{3}(r)
$$
