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
给定 $A \in \mathbb F^{m\times n}$，通过右乘向量可以完成 $\mathbb F^n \rightarrow \mathbb F^m$ 的映射。


