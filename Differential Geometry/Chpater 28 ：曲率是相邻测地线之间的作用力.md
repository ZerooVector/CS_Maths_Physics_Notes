#DifferentialGeometry 

我们接下来要说明一个神奇的性质：两个质点沿着两条相距很近的测地线移动，如果两条测地线穿过一个正曲率的区域，那么两个质点将会互相吸引，否则反之。我们将会定量地描述这一点。

## 几个直观的例子
### 平面
![[Pasted image 20240731105207.png]]
如左图所示，在测地线 $\mathcal{L},\mathcal{\tilde L}$ 上放置初始速度 $v ,\tilde v$ 相等的质点（模长均为 1），两个质点之间的相对位移是 $\xi = p \tilde p$，因此相对速度是 $\delta v =  \dot \xi$。在这个例子中，$\delta v = 0$。然而，我们要关注的实际上是相对加速度，也就是 $\ddot \xi = \dfrac{\mathrm{d}(\delta v)}{\mathrm{d}t}$，容易发现 $\ddot \xi = 0$。在右图中，尽管 $\dot \xi = \delta \theta$，但是 $\ddot \xi = 0$。

### 球面
![[Pasted image 20240731105844.png]]
在球面上，我们同时从北极发射两个质点，让它们沿着夹角为 $\delta \theta$ 的两条测地线行进。通过简单的几何关系可以注意到：$\xi  = R \delta \theta \sin \left(\dfrac{t}{R}\right)$，那么 $\dfrac{\mathrm{d}^{2}  \xi }{\mathrm{d} t^{2}} = - \left[\dfrac{1}{R^{2}}\right] R \delta \theta  \sin \left(\dfrac{t}{R}\right)$，那么我们立刻得到 $\ddot \xi  = - \mathcal{K} \xi$。两个质点从北极发射，却在南极相交。我们将南极和北极称为一对共轭点。

### 伪球面
![[Pasted image 20240731110950.png]]
考虑两个沿着测地线的母线运动的质点，初始时刻，它们间的间隔是 $|\xi_{0}|$，设 $t$ 时刻它们与对称轴的距离是 $X(t)$，那么：
$$
\xi(t) = X(t) \delta \theta  = \left[\dfrac{|\xi _{0}|}{R} X(t)\right]
$$
两侧求导，并利用曳物线的几何性质：$\dfrac{\mathrm{d}X}{\mathrm{d}t} = -\dfrac{X}{R}$ 得到：
$$
\dot \xi = - \left(\dfrac{1}{R}\right) \xi 
$$
两侧再微分一次，就得到了：
$$
\ddot \xi  = + \left(\dfrac{1}{R^{2}}\right) \xi  = - \mathcal{K} \xi 
$$
从上面的例子中，我们发现了一个共有的结论：似乎有一个经典谐振子的方程：
$$
\ddot  \xi  + \mathcal{K} \xi =  0
$$
成立。这是为什么呢？

## 雅可比方程的证明
我们将上面这个方程称为雅可比方程，现在我们给出证明。我们首先引入测地极坐标：从曲面 $\mathcal{S}$ 上任意一点 $o$ 向四面八方以单位速率发射质点，并选定其中一个方向为 $\theta = 0$。设 $o$ 周围的区域不包含共轭点，那么每个点都会在唯一时刻被唯一质点击中。我们将这个点被击中的时刻和质点的发射方向称为这个点的测地极坐标 $(t , \theta)$ 。
我们现在证明直观上正确的高斯引理：如果从一般曲面上的一点沿着所有的方向发射质点，让它们沿着测地线走过距离 $\sigma$，它们将形成内蕴半径为 $\sigma$ 的测地圆周 $K(\sigma)$，这个测地圆周 $K(\sigma)$ 与其测地线半径正交。
![[Pasted image 20240731152117.png]]
我们研究无限近的两条测地线段：$op,oq$。设 $p,q$ 都在 $K(\sigma)$ 上，但是假设 $pq$ 不是正交于 $op,oq$ 的，此时，$\angle opq = \dfrac{\pi}{2}  - \alpha$，画一条过 $q$ 的测地线正交于 $pq$，使得它与 $op$ 交于 $r$，那么 $\angle prq = \alpha$，此时，$o \rightarrow r \rightarrow q$ 的长度是 $R - rp (1 - \cos \alpha)< R$，这与 $oq$ 是测地线矛盾。此时，$\theta$ 方向是沿着 $K(\sigma)$ 圆周的方向，而 $t$ 方向则是沿着测地线向外的方向。因此：
$$
d \hat s^{2} = dt^{2} + \rho^{2}(t, \theta) d \theta^{2}
$$
由于从同一点发射出的质点，在同一时间必然到达相同的圆周上，那么：
$$
\xi  = \rho \delta \theta  \quad  \ddot  \xi   = \ddot \rho \delta \theta
$$
而利用度量曲率公式，可以得到：
$$
\mathcal{K} =  \dfrac{\ddot  \rho }{\rho }
$$
从而立刻推出：
$$
\ddot \xi = - \mathcal{K} \xi 
$$


接下来再给出一个依赖于几何的证明。
![[Pasted image 20240731161145.png|400]]
如图，我们找到两条测地线 $\mathcal{L}$ 和 $\mathcal{\tilde L}$，找到无限小的线段 $a \tilde a$ 使得它与两条测地线垂直。经过 $\delta t$ 时间后，两者的相对速度是 $\delta v  = \ddot \xi dt$。我们应该比较 $v(b)$ 和 $\tilde v(\tilde b)$，但是它们两个的差显然不是内蕴的。为了得到相对加速度的内蕴量度，我们需要沿着 $b \tilde b$ 平行移动 $v(b)$，从而得到相对加速度的内蕴量度：
$$
\ddot \xi di = \delta v  = \tilde v (\tilde b) - v_{\parallel}(b)
$$
设两个向量在 $\tilde b$ 点的夹角为 $\delta \psi$，那么显然有 $\delta v = \delta \psi$。很容易注意到的一点是：如果沿着 $\tilde b b a  \tilde a \tilde b$ 的方向平行移动 $v_{\parallel} (b)$，那么它转过的角度恰好是 $\delta \psi$，从而我们可以得到一连串的等式：
$$
|\ddot \xi| dt  = |\delta v|  = \delta \psi  = \mathcal{R}(\mathcal{L}) = \mathcal{K} \delta \mathcal{A} = \mathcal{K} |\xi | \delta t
$$
注意到对于图中的情况，$\delta v$ 的方向和 $\xi$ 相反，因此我们得到：
$$
\ddot \xi = - \mathcal{K} \xi 
$$

最后，我们之前说过，生活在曲面上的居民可以通过小测地圆的周长和面积来得知这个曲面的曲率。现在我们定义 $g (r) = \rho(\theta_{0},r)$，设 $\xi(r)$ 是沿着 $\theta_{0}$ 与 $\theta_{0}+ \delta \theta$
发射出来的两条测地线的间隔，那么 $\xi (r) = g (r) \delta \theta$。将 $g(r)$ 展开：
$$
g(r) = r + \dfrac{1}{2} g''(0) r^{2} + \dfrac{1}{6} g^{(3)} (0) r^{3} + \cdots 
$$
由前面的讨论，我们已经知道 $g'' (r) =  - \mathcal{K} g(r)$，而：
$$
g^{(3)} (0) = - [\mathcal{K}g] '(0) = - \mathcal{K}'(0)g(0) - \mathcal{K}(0) g'(0) = - \mathcal{K}(0)
$$
因此：
$$
C(r) = 2 \pi r - \dfrac{\pi}{3} \mathcal{K}(0) r^{3} \Rightarrow \mathcal{K} = \dfrac{3}{\pi} \left[\dfrac{2\pi r - C(r)}{r^{3}}\right]
$$
面积也可做类似的推理。




