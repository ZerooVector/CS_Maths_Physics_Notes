#MA 

## Cholesky 分解是什么？
Cholesky 分解是对正定矩阵完成的一种操作，它负责将方阵 $A$ 分解成**一个下三角矩阵 $L$ 以及其转置 $L^T$ 的乘积**。也就是：
$$
A =LL^T
$$
![[Pasted image 20230301234123.png|400]]

此外，它还有进阶版本——将任意矩阵分解成下三角阵 $L$ ，其转置 $L^T$ 和对角阵 $D$ 的乘积。，也就是
$$
A = LD^{1/2}(LD^{1/2})^T = LDL^T
$$
也可以有很多写法，例如，令 $B = D^{1/2}, R= L^T$，Cholesky 分解被写成：
$$
A = (BR)^T(BR)
$$
然而，只有正定矩阵才能执行 Cholesky 分解。一个矩阵是正定的，意味着它对应的二次型的值恒为正：
$$
x^TAx >0\ ,\ \forall x
$$
## Cholesky 分解的几何意义
### 特殊情况 1：对角全 1，其余位置是余弦值的矩阵
并不是所有矩阵都能进行 Cholesky 分解，而且，不是所有矩阵的 Cholesky 分解都有很明显的几何意义。因此，我们只讨论一个非常特殊的情况：矩阵的主对角全 1，非主对角的元素为余弦值：
$$
P = \begin{bmatrix}
1 & \cos \theta_{1,2}\\
\cos \theta_{1,2} & 1
\end{bmatrix}
$$
那么，矩阵分解的结果是：
$$
R = LL^T = R^TR = 
\begin{bmatrix}
1 & 0\\
\cos \theta_{1,2} & \sin \theta_{1,2}
\end{bmatrix}
\begin{bmatrix}
1 & \cos \theta_{1,2}\\
0 & \sin \theta_{1,2}
\end{bmatrix}
$$
将 $R$ 按照列向量展开：$R = [r_1,r_2]$，容易发现 $\cos <r_1,r_2> = \cos \theta_{1,2}$ 。

接下来，我们从线性变换的角度下看矩阵 $R$ 的作用。根据我们之前的理论，这个是将原来的基向量经过线性变换后，在某一特定出口基下的坐标（在这里，出口基被指定为和入口基相同），我们可以发现，矩阵 $R$ 将原本垂直的一对正交基变换成了夹角为 $\theta$ 的一组向量。这其实是一种“开合”变换。
![[Pasted image 20230301235138.png|400]]

这个变换的行列式值为 $\sin \theta_{1,2}$，这可以从面积的变化上观察出来:
![[Pasted image 20230301235427.png|400]]

### 特殊情况 2 ： 对余弦值矩阵进行一下缩放
如果一个矩阵是这样子的：
$$
P = \begin{bmatrix}
a^2 & ab\cos \theta_{1,2}\\
ab\cos \theta_{1,2} & b^2
\end{bmatrix}
$$
处理这个矩阵，我们可以先将其打开：
$$
P = 
\begin{bmatrix}
a & \\
& b
\end{bmatrix}
\begin{bmatrix}
1 & \cos \theta_{1,2}\\
\cos \theta_{1,2} & 1
\end{bmatrix}
\begin{bmatrix}
a & \\
& b
\end{bmatrix}
$$
然后再把 Cholesky 分解作用在中间的一部分上：
