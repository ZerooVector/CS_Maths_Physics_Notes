#MA 

## 子空间的定义、基本性质
设 $V$ 是 $\mathbb F$ 上的线性空间，$W \subseteq V$ 是非空子集。如果
- $W$ 对加法封闭：$\alpha,\beta \in W,\alpha+\beta \in W$
- $W$ 对数乘封闭：$\alpha \in W ,\alpha k \in W$
则称，$W$ 是 $V$ 的子空间！这个定义是说， $W$ 和线性空间满足一样的性质，在 $W$ 内部就可以进行加法和数乘的运算（并且要满足八条规则）
实际上，子空间是对加法、乘法等运算进行了限制，从 $V\times V \rightarrow V$ 限制到了 $W\times W\rightarrow W$ 
##### Example : 反例——不是子空间的集合
![[Ep.4 Subspace 2023-02-27 09.50.35.excalidraw]]

##### Example : 向量组生成的子空间及子空间的生成组
$\alpha_1,\cdots,\alpha_p$ 是向量组，$W = span\{\alpha_i\} =\{\sum_i^p\alpha_ic_i\ ,\ c_i \in \mathbb F\}$ ，那么 $W$ 就是 $V$ 的一个子空间。$W$ 也就是由向量组 $\alpha$ 生成的子空间。（这是不证自明的，因为这样的 $W$ 必然会对加法和数乘封闭。）
现在反过来，已知 $W$，若能找到向量组 $\alpha_1,\cdots,\alpha_p$，使得 $W = span\{\alpha_i\}$，那么我们称 $\alpha$ 为子空间的生成组。
一般来说，我们无法通过列举的方式定义子集，但是，这里，我们可以使用列举生成元的方式表现这个子空间。

##### Example : $A = F^{m\times n}$ 的核 (Kernel) 与像 (Image)
记： $W_1  =\{x|x \in \mathbb F^n\ ,\ Ax=0\}$ 
$W_2 = \{y|y \in \mathbb F^m,\exists x \in F^n , y = Ax\}$ 
$W_1$ 显然是 $\mathbb F^n$ 的子集，下面验证它是子空间：
如果 $Ax_1 = 0, Ax_2 = 0$，那么显然 $A (x_1+x_2) = 0$，因此，这个空间对加法封闭；对于数乘的封闭也是不证自明的（矩阵乘法的结合律）。这个子空间就是方程组 $Ax = 0$ 的解，被称为 A 的核 (Kernel)
下面验证 $W_2$ 是 $\mathbb F^m$ 的子空间：

补充：如果将 $A$ 分成列向量组，$Ax = [a_1, a_2,\cdots, a_n][x_1,x_2,\cdots,x_n]^T$，矩阵的像空间相当于向量组 $a$ 以 $x_i$ 作为系数进行线性组合。就是 $A$ 的列向量组 $a$ 张成的子空间！

## 子空间上的运算
### 子空间的交与和
设 $U, W$ 为 $V$ 的子空间，那么：
- $U\cap W$ 也是子空间，称为 $U,W$ 的交子空间
- $U+W = \mathrm{span}\{U, V\} =\mathrm{span} \{u+w|u=U,w=W\}$，称为 $U,W$ 的和子空间

##### PF : $U\cap W$ 是子空间
$e_1 \in U, e_1 \in W; e_2 \in U, e_2 \in W$，显然，$e_1+e_2 \in U,W$，数乘也是显然的！

##### Example : 两个集合的并未必是子空间
![[Ep.4 Subspace 2023-02-28 19.57.26.excalidraw|300]]

### 








