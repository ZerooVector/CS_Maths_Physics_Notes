#MA
## 线性映射
##### Def : 线性映射和线性变换
设 $V_1, V_2$ 是 $\mathbb F$ 上的线性空间，$\sigma: V_1\rightarrow V_2$ 是映射，如果：
- 保加法（向量间的加法关系依然被保持）：$\sigma (e_1+e_2) = \sigma (e_1)+\sigma(e_2)$
- 保数乘法：$\sigma (ke_1) = k\sigma(e_1)$
如果这两条要求得到满足，我们称 $\sigma$ 是 $V_1\rightarrow V_2$ 的线性映射。进一步，如果 $V_1=V_2=V$，则成为 $V$ 上的线性变换。

##### Example: 线性与非线性映射
我们取 $V_1 = \mathbb R^2 , V_2 = \mathbb R^2$，
- $\mathcal A:[x_1, x_2]^T\mapsto [x_1+x_2,x_1x_2]$，这显然不是线性的！
- $\mathcal B : [x_1, x_2, x_3]^T \mapsto [x_1+x_2-x_3, 0.5x_1-3x_2]^T$，这是线性的

**注**：若线性映射 $\sigma : V_1 \rightarrow V_2$ 是一一对应（可逆的映射），那么称 $\sigma$ 是一个线性同构

##### Example：矩阵与线性空间之间的线性映射，两事物的等同性
给定 $A \in \mathbb F^{m\times n}$，通过右乘向量可以完成 $\mathbb F^n \rightarrow \mathbb F^m$ 的映射。这是显然的。反之呢？一个映射一定对应一个矩阵吗？
记 $\mathbb F^n$ 的标准基 $\epsilon_1,\cdots ,\epsilon_n$，则 $\mathcal A (\epsilon_i)\in \mathbb F^m$，我们将各个像拼成一个矩阵 $A = [\mathcal A(\epsilon_1),\cdots,\mathcal A(\epsilon_n)]$，那么它是 $n$ 列，$m$ 行的矩阵。现在验证，$A$ 是否可以通过右乘列向量的方式进行映射。
取 $x \in \mathbb F^n$，那么将 $x$ 沿着标准基展开，$x = [\epsilon_1,\cdots,\epsilon_n][x_1, \cdots,x_n]^T$ (坐标向量正是 $x$ 自身)。
利用抽象映射 $\mathcal A$ 的定义（保持加法和数乘法不变的特性）：
$$
\mathcal A (x) = \sum_{i=1}^n \mathcal A(\epsilon_i)x_i = [\mathcal A(\epsilon_1),\cdots,\mathcal A(\epsilon_n)][x_1,\cdots,x_n]^T = Ax
$$
所以，由矩阵 $A$ 带来的线性映射和抽象的线性映射导致相同的效果。**因此，一个抽象的线性映射总可以使用一个矩阵来实现**！矩阵 $A$ 的构造方法就是对各个基向量进行线性映射，再按照列排列起来！

##### Def: 线性映射的矩阵表示
给定线性映射：$\mathcal A : V\rightarrow W$, $\dim V =n,\dim W = m$，则线性映射的构造方法是：选取 $V$ 的基：$\epsilon_1,\cdots,\epsilon_n$（input base），选取 $W$ 的基 $\eta_1,\cdots,\eta_n$ (output base)，记第 $j$ 个入口基向量 $\epsilon_j$ 的像 $\mathcal A (\epsilon_j)$ 在出口基下的坐标为 $a_j = [a_{1j},\cdots,a_{mj}]^T$  ，也就是 $\mathcal A (\epsilon_j) = [\eta_1,\cdots,\eta_m][a_{1j},\cdots,a_{mj}]^T$，将这些坐标拼成矩阵
$A = [a_1, a_2,\cdots,a_n]$，那么 $A$ 就被称作映射 $\mathcal A$ 在入口基 $\{\epsilon_1\}$ 和出口基 $\{\eta_i\}$ 下的矩阵表示。
直观来讲，线性映射的矩阵表示就是在说：**入口基向量经过变换后，在出口基下应该如何表示**？
**补充**：在很多直观讲述高等代数的书上，他们会说，$A$ 的各个列就是变换后线性空间的基向量，最终得到的向量就是它们的线性组合。这种说法是因为，**线性变换是在同一个线性空间中实行的，如果不是特殊指定，变换前和变换后的基是一样的**，矩阵 $A$ 的各列就是原基向量经过变换后，在原来的的基上的坐标。例如，一个拉伸变换
$$
\begin{bmatrix}
1 & 0\\
0 & 2
\end{bmatrix}
$$
那么，变换前、后的基向量都是 $[1,0],[0,1]$，只不过变换使得向量 $[0,1]$ 伸长了两倍而已。
![[Ep.5 Linear Mapping 2023-03-01 08.51.36.excalidraw|550]]

### 线性映射的坐标求法
##### Theorem 
设 $\mathcal A$ 是从 $V$ 到 $W$ 的线性映射，$V$ 的基是 $\epsilon_i$，$W$ 的基是 $\eta_i$。给定 $v \in V$，其坐标为 $x$，那么其像的坐标是 $Ax$。
##### PF :
$$
v = [\epsilon_1,\cdots,\epsilon_n]x
$$
$$
\begin{aligned}
\mathcal A (v) &= \mathcal A(\sum_i \epsilon_i x_i)\\
&=[\mathcal A(\epsilon_i)]x = ([\eta_1,\cdots,\eta_n]A)x = [\eta_1,\cdots,\eta_n](Ax)
\end{aligned}
$$
直观理解 ：$v$ 本来可以写成基向量的线性组合，在线性映射之后仍然可以写成原基向量的线性组合。只不过原基向量的坐标变了而已。
![[6bf61bac76b7079da06512da2eb16f1.jpg]]

比如图里这个，变换前可以写出 $\epsilon_1+\epsilon_2$，变换后仍然可以这样写，但是 $\epsilon_1 = \frac{1}{2}\eta_1-\frac{1}{2}\eta_2$，这样一代入，我们就得到在新的基下面的坐标了。（矩阵 $A$ 只是给出了原基向量的一个新的表示方法）

##### Example: 微分算子的矩阵表示
我们只给一个实例：$\mathcal D:\mathbb R_4 [x] \rightarrow \mathbb R_3[x]$
在入口空间中，选择 $1,x,x^2,x^3$；在出口空间中，选择 $1,x,x^2$, 那么，映射矩阵是
$$
A=
\begin{bmatrix}
0 &1&0&0\\
0 &0 & 2&0\\
0 &0&0&3

\end{bmatrix}
$$

##### Example : 旋转变换的几何表示
我们仅仅考虑几何空间绕着固定轴的旋转，旋转了角度 $\theta$。那么，入口空间和出口空间都是三维几何空间，我们将出口基和入口基选择成相同的（注意，这个选择不是必然的）
![[Ep.5 Linear Mapping 2023-03-01 12.32.55.excalidraw|300]]
矩阵每一列都是变换后的原基底在新基底下的投影，那么：
$$
B = 
\begin{bmatrix}
\cos \theta & -\sin \theta & 0\\
\sin \theta & \cos \theta & 0\\
0 & 0 & 1
\end{bmatrix}
$$
##### Example : 镜像反射
![[Ep.5 Linear Mapping 2023-03-01 12.44.09.excalidraw|300]]
严格的镜像反射是依赖于投影进行的，投影使用张量积进行计算，此外还依赖于一组正交基的巧妙性质（正交基分别求张量积，加起来等于单位矩阵）进行，具体可以看 [[Orthogonal Projection]] 一节中的介绍。
根据图，显然是
$$
A = \begin{bmatrix}
1&0&0\\
0&1&0\\
0&0&-1
\end{bmatrix}
$$
或者，选择法向量 $v = [0,0,1]$，由 $H = I-2v\otimes v$ 也可以得到上述矩阵。


