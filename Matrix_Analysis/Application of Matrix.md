#MA 

## 图的矩阵表示

我们可以定义图的邻接矩阵
$$
a(i,j) = \begin{cases}
1   , \ \ \langle  v_{i},v_{j}  \rangle \in G \\
0, \ \ \langle  v_{i},v_{j}  \rangle \not \in G \\
\end{cases}
$$
无向图的邻接矩阵应当是对称矩阵

如果一个图的任意两个节点之间都有一条有向路径，那么这张图是强连通的。

图的完全关联矩阵则反映了一条边连接的点的情况。对于 $n$ 个顶点, $k$ 个连通分支的情况，其秩为 $n-k$

## 统计学
随机变量 $X = (X_{1},X_{2},\cdots ,X_{n})$ 的协方差矩阵为  $A = [a_{ij}]$：
$$
a_{ij} = E[(X_{i}- \bar X)(X_{j}-\bar X)]
$$

## PCA 
PCA 实际上就是低秩估计问题：若我们找到秩为 $r$ 的矩阵 $A$ 和秩不满 $r$ 的矩阵 $B$，求解低秩估计问题
$$
\min_B ||A-B||_{2}^{2} 
$$
可以证明：
$$
||A-B||_{2}^{2} \ge \sum_{i}(\sigma_{i}(A)^{2})
$$
那么我们可以通过将 $B$ 进行奇异值分解，对其保留最大的 $k$ 个奇异值来对 $A$ 进行最佳逼近



