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
给定线性映射：$\mathcal A : V\rightarrow W$, $\dim V =n,\dim W = m$，则线性映射的构造方法是：选取 $V$ 的基：$\epsilon_1,\cdots,\epsilon_n$（input base），选取 $W$ 的基 $\eta_1,\cdots,\eta_n$ (output gate)，记第 $j$ 个入口基向量 $\epsilon_j$ 的像 $\mathcal A (\epsilon_j)$ 在出口基下的坐标为 $a_j = [a_{1j},\cdots,a_{mj}]^T$  ，也就是 $\mathcal A (\epsilon_j) = [\eta_1,\cdots,\eta_m][a_{1j},\cdots,a_{mj}]^T$，将这些坐标拼成矩阵
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
![[Ep.5 Linear Mapping 2023-03-01 08.51.36.excalidraw|600]]

### 线性映射的坐标求法
##### Theorem 
设 $\mathcal A$ 是从 $V$ 到 $W$ 的线性映射，$V$ 的基是 $\epsilon_i$，$W$ 的基是 $\eta_i$。给定 $v \in V$，其坐标为 $x$，那么其像的坐标是 $Ax$。直观地理解：$A$ 中记载的是各个原基向量的
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
