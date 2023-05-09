#MA  

## 幺正矩阵作为线性变换

##### Theorem 以下等价
- $U$ 是酉矩阵
- $U$ 作为线性变换保内积，也就是说 $\langle  Ux, Uy \rangle = \langle  x,y \rangle$
- $U$ 作为线性变换保长度 $||Ux|| = ||x||$

##### PF 
（2）推（3）是显然的

（3）推（2）：
我们考虑
$$
\langle  x,y \rangle = \mathrm{Re}(\langle  x,y \rangle) + i\mathrm{Im}(\langle  x,y \rangle) 
$$
那么，
$$
\mathrm{Re}\langle  x,y \rangle = ||x+y||^{2} -||x||^{2} - ||y||^{2}
$$
$$
\mathrm{Im}\langle  x,y \rangle = -Re \langle  x,iy \rangle = - \frac{1}{2}(||x+iy||^{2}-||x||^{2}-||y||^{2})
$$
因此，我们其实可以仅仅通过向量的长度来计算内积
那么，保长度相当于保内积！

（1）推（2）：
$$
\langle  Ux,Uy \rangle = (Ux)^{H}Uy = x^{H}(U^{H}U)y = \langle  x,y \rangle
$$

（2）推（1）：
留做习题答案略，读者自证不难

##### Example 平面旋转
考虑平面上原来的基底是 $i,j$，而变换后的基底是 $i',j'$，那么
$$
\mathcal{A}[i,j] = [i,j]\begin{bmatrix}\cos \theta  & -\sin \theta \\ \sin \theta & \cos \theta\end{bmatrix}
$$

实际上就是将变换后的 $i',j'$ 沿着 $i,j$ 展开
类似的还有平面反射

性质：幺正矩阵的特征值的模为 1.

## Schur 定理
之前，我们知道，通过 $AP = PJ$，我们选择一组基同时作为入口和出口，就能将矩阵 $A$ 化作 Jordan 块，那么现在我们考虑，仅仅使用标准正交基，$A$ 会被化简到什么程度。

##### Theorem Schur 定理
对于 $A\in \mathbb{C}^{n \times n}$，必然存在幺正矩阵 $U$ 使得 $U^{H}AU$ 成为上三角阵

##### PF 
考虑将 $A$ 化成 Jordan 标准型：
$$
AP = PJ
$$
现在将 $P$ 改造成一组标准正交基：
$$
P=UR
$$
$U$ 中储存了正交基
$$
AUR = URJ
$$
那么：
$$
U^{-1}RU = RJR^{-1}
$$
注意到 （==需要自行验证==）$R,J,R^{-1}$ 均是上三角矩阵，它们的乘积也应该是上三角矩阵，那么我们就证得了 Schur 定理

## 谱分解

接下来，我们研究：如何用用一个幺正矩阵将某一矩阵化成对角阵？

##### Theorem
给定 $A\in \mathbb{C}^{n\times n}$ ，存在幺正矩阵使得 $U^{-1}AU$ 为对角阵，那么
$$
A^{H}A=AA^{H}
$$
也就是说，$A$ 和 $A$ 的共轭转置是可交换的，这样的矩阵 $A$ 称为正规矩阵

##### PF 
首先，我们证明如果 $A$ 可以正交对角化，那么 $A, A^H$ 是可交换的
$$
A = U \Lambda U^{H}
$$
直接计算就可以验证这个定理
反过来，首先，必然存在幺正矩阵将 $A$ 化成上三角, 容易验证，变换后的 $\Lambda$ 和 $\Lambda^{H}$ 也应该是可交换的。我们要利用这一点证明其为上三角阵
计算 $\lambda \lambda^{H}$ 和 $\lambda^{H}\lambda$ 的第一行和第一列的元素，容易得证

## Hermite 矩阵
Hermite 矩阵类似于对称矩阵，其意义是：
$$
A^{H}=A
$$
容易发现，Hermite 矩阵一定是正规矩阵，于是，必然存在幺正矩阵 $U$ 使得 $U^{-1}AU$ 成为对角阵，对角线上是特征值，此外，可以证明，Hermite 矩阵的特征值必然为实数

##### PF 
考虑特征值的定义：
$$
Ax = x \lambda
$$
两边取共轭转置，
$$
x^{H}A^{H}= x^{H}A = \bar \lambda x^{H}
$$
又考虑到
$$
x^{H}Ax = x^{H}x \lambda
$$
而且
$$
x^{H}A^{H }x= \bar \lambda  x^{H} x
$$
以上两式对比，得到 $\lambda$ 是实数

### 非负定和正定 Hermite 矩阵
##### Def 非负定 Hermite 阵
一个非负定的 Hermite 矩阵要求 $x^{H}Ax \ge 0$ ，而进一步地，正定要求 $x^{H}Ax  > 0,\forall x \not = 0$ ，一个 Hermite 矩阵非负定等价于特征值大于等于 0，而正定要求特征值严格大于 0

##### Def Rayleigh 商
对于非负定的 Hermite 阵，一下关系成立：
$$
\lambda_{\max} (A) = \max_{x\not=0}  \frac{x^{H}Ax}{x^{H}x}= \max_{||x||=1} x^{H}Ax
$$
这个等式中的变换通过 $||X||^{2}= x^{H}x$ 容易证明

##### PF 
显然，$A$ 是正规矩阵，可以相似对角化，那么
$$
x^{H}Ax = (U^{H}x)^{H}\Lambda (Ux)
$$
取 $y=Ux$，显然 $||y||=1$
$$
y^{H }\Lambda y  = \sum_{i}\lambda_{i} y_{i}^{2}
$$
容易看出结果。但是要说明，对于任意一组 $y_{i}$，上式的值都小于等于 $\lambda_{1}$，其次要说明 $\lambda_{1}$ 被某一组 $y_i$ 取到。
这给我们提供了一种使用凸规划算法求出矩阵特征值的方法。








