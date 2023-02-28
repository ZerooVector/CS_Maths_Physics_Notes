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
给定线性映射：$\mathcal A : V\rightarrow W$, $\dim V =n,\dim W = m$，则线性映射的构造方法是：选取 $V$ 的基：$\epsilon_1,\cdots,\epsilon_n$（input base），选取 $W$ 的基 $\eta_1,\cdots,\eta_n$ (output gate)，记第 $j$ 个入口基向量 $\epsilon_j$ 的像 $\mathcal A (\epsilon_j)$ 在出口基下的坐标为 $[a_{1j},\cdots,a_{mj}]^T$  

