#DifferentialGeometry 

我们现在要证明之前提出的曲率公式：
$$
\mathcal{K} =  - \dfrac{1}{AB}\left(\partial_{v} \left[\dfrac{\partial_{v} A}{B}\right]+\partial_{u}\left[\dfrac{\partial_{u} B}{A}\right]\right)
$$
这里，$u,v$ 是曲面上的正交坐标系，而 $A,B$ 是 $u,v$ 坐标的变化和 $X,Y$ 坐标变化的比例：
$$
\delta X = A \delta u  \quad  \delta Y  = B \delta v 
$$
利用度量公式表示曲面上两点之间的距离：
$$
d \hat s^{2}  = dX^{2} + dY^{2} =A^{2} du^{2} + B^{2} dv^{2}
$$

我们现在引入一下向量场的旋度。我们定义向量场 $V$ 围绕 $L$ 的环流量 $C_{L}(V)$ 是 $V$ 的分量沿着 $L$ 方向的曲线积分：
$$
C_{L}(V) = \oint_{L} V  \cdot dr = \oint_{L}[Pdu  + Qdv]
$$
当环路 $L$ 的面积越缩越小的时候，我们可以定义：$V$ 的旋度是单位面积上的局部环流量
$$
\text{curl}  V = \partial_{u} Q - \partial_{v} P
$$

我们先从最简单的例子开始：研究平面上的一个小环路的和乐性。我们取极坐标，选择基准向量场是径向向外的射线：
![[Pasted image 20240730110052.png]]
从右图中，容易看出，绕着所选回路的和乐性为 0. 现在我们考虑另一个推导：边 $\hat g \hat f$ 略长于边 $\hat h \hat e$，如果没有长出这一段的话，$w$ 在移动到 $\hat g \hat h$ 上的时候是与 $\hat g \hat h$ 没有夹角的！两条边长度的差距是 $\delta r  \delta \theta$。更一般地，如果我们将边长表为 $\delta Y  = B  \delta v$，那么由 $u$ 增加 $\delta u$ 引起的边长增加：
$$
\delta ^{2}Y  = [\partial_{u} B \delta u] \delta v 
$$
另外显然容易从左图中看出，每条边上的环流量恰好等于这条边上的和乐性，换言之：
$$
\mathcal{R}(\hat L) = C_{L}(V)
$$

现在我们论证上述结论。我们设 $R$ 是地图上以 $p$ 为中心的一个平行四边形，而它被映射到曲面上以 $\hat p$ 为中心的 $\hat R$。虽然此时的 $\hat R$ 很像一个真正的矩形，但是显然，它对边的长度是不同的。
![[Pasted image 20240730112801.png]]
这里，我们将小矩形投影到 $\hat p$ 的切平面上。如图，两条对边的长度差距是 $\delta^{2} X = [\partial_{v} A \delta  v]\delta u$。根据上面在极坐标系中的推理，我们知道这会导致向量 $w$ 在平行移动的过程中相对于某个基准向量场（这里选为 $u$ 曲线）旋转角度：
$$
\delta \mathcal{\hat  R}_{1} = \dfrac{\partial_{v} A \delta v \delta u }{B \delta v} = \dfrac{\partial_{v} A}{B}\delta u 
$$
同理，沿着 $\hat f \hat g$ 的平行移动会产生和乐性（这里是相对于 $v$ 曲线的旋转角度）：
$$
\delta \mathcal{\hat R}_{2} = - \dfrac{\partial_{u}B}{A} \delta v
$$
现在我们只计算出沿着两条边走，带来的和乐性。如果我们要计算整个曲线的和乐性，做法显然应该是在地图平面上定义向量场 $V = \begin{bmatrix}\dfrac{\partial_{v} A}{B }  \\ = \dfrac{\partial_{u} B}{A}\end{bmatrix}$，并计算该向量场的环量。

这样我们就证明了曲率公式，此外，我们还可以得到在共形地图下它的特殊形式：
$$
\mathcal{K} = \dfrac{\nabla^{2} \ln \Lambda}{\Lambda^{2}} \quad A = B  = \Lambda
$$
