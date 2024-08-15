#MathematicalPhysics 

现在我们考虑 $n \times n$ 的矩阵，我们将基底取为 $(e_{ij})$，代表只在 $(i,j)$ 位置为 1，其余位置全为 0 的矩阵。这意味着 $(e_{ij})_{lk} = \delta_{il} \delta_{jk}$，并且：
$$
(e_{ij}e_{kl})_{mn} = \sum_{r} (e_{ij})_{mr} (e_{kl})_{rn} = \sum_{r} \delta_{im} \delta_{jr}\delta_{kr}\delta_{ln}= \delta_{jk}(e_{il})_{mn}
$$
或者说 $e_{ij}e_{kl} = \delta_{jk}e_{il}$。结构常数是 $c_{ij, kl}^{mn} = \delta_{im}\delta_{jk}\delta_{ln}$ 。如果一个抽象代数的乘积和结构常数由上面的式子给出，我们就称这样的抽象代数是一个全矩阵代数。在 $\mathcal{F}$ 上的矩阵代数记作 $\mathcal{M}_{n}(\mathcal{F})$，它与实数（复数）矩阵代数同构，但是元素不一定要是 $n \times n$ 的矩阵。我们现在来构建这个代数的左理想。考虑：
$$
\left(\sum_{i,j}\alpha_{ij} e_{ij}\right)e_{pq} = \sum_{i} \alpha_{ip} e_{iq}
$$
这个矩阵只在第 $q$ 列有东西。于是我们显然要猜测这样的矩阵是不是全矩阵代数的一个左理想。考虑：
$$
\left(\sum_{l,m}\beta_{lm}e_{lm}\right)\left(\sum_{i}\gamma_{i} e_{iq}\right)  = \sum_{l}\left(\sum_{m} \beta_{lm} \gamma_{m}\right)e_{lq}  = \sum_{l} \eta_{l} e_{lq}
$$
这样我们就找到了左理想，同理我们能找到右理想。
>[!note]
> $M_{n}(\mathbb{F})$ 的极小左（右）理想是除了一列（行）外均为零的矩阵。

显然，$\mathcal{M}_{n}(\mathbb{F})$ 是不存在双侧理想的。容易找到 $\mathcal{M}_{n}(\mathbb{F})$ 的中心是单位矩阵（通过直接计算证明，首先证明其中心必然是对角阵，其次可以证明必须是单位阵），因此 $\mathcal{M}_{n}(\mathbb{F})$ 是一种简单的中心代数。



