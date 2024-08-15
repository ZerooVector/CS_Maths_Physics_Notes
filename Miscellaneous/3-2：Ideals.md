#MathematicalPhysics 

设 $\mathcal{A}$ 是一个代数，$\mathcal{A}$ 的子空间 $\mathcal{B}$ 称为是 $\mathcal{A}$ 的一个左理想，如果它包含 $ab,\forall a \in \mathcal{A}, b \in \mathcal{B}$，也可写成 $\mathcal{AB} \subset \mathcal{B}$ 。同理，右理想可以定义为 $\mathcal{BA} \subset \mathcal{A}$。若 $\mathcal{B}$ 既是 $\mathcal{A}$ 的左理想，又是 $\mathcal{A}$ 的右理想，我们称 $\mathcal{B}$ 是 $\mathcal{A}$ 的双侧理想，简称理想。显然，理想自动成为 $\mathcal{A}$ 的子代数

>[!note]
>设 $\phi: \mathcal{A} \rightarrow \mathcal{B}$ 是代数同态，那么 $\ker \phi$ 是 $\mathcal{A}$ 的理想。这很容易证明。

交换代数的左理想很容易构造：取元素 $x \in \mathcal{A}$ ，考虑 $\mathcal{A}x = \{ ax | a \in  \mathcal{A}\}$，容易检查它是 $\mathcal{A}$ 的左理想，而 $x \mathcal{A}$ 则是右理想，$\mathcal{A}x \mathcal{A}$ 是双侧理想。这些称为由 $x$ 生成的理想。

一个代数 $\mathcal{A}$ 的理想 $\mathcal{M}$ 被称为极小理想，如果每个包含在 $\mathcal{M}$ 中的理想都与之重合。最小理想有性质：
>[!notes]
>设 $\mathcal{L}$ 是 $\mathcal{A}$ 的左理想，那么以下命题等价：
>- $\mathcal{L}$ 是 $\mathcal{A}$ 的极小左理想
>- $\mathcal{A}x = \mathcal{L},\forall x \in \mathcal{L}$
>- $\mathcal{L}x = \mathcal{L},\forall x \in \mathcal{L}$

给出一些证明：
1）推 2）：
根据理想的定义，我们知道 $\mathcal{A}x \subseteq L$，不妨设 $\mathcal{A}x = \mathcal{L}' \subset \mathcal{L},\forall x \in \mathcal{L}$，则对于 $x' \in \mathcal{L}'$，必有 $\mathcal{A}x' \subseteq \mathcal{L}',\forall x \in  \mathcal{L}'$，因此 $\mathcal{L}'$ 也是 $\mathcal{A}$ 的左理想，则 $\mathcal{L}$ 不是 $\mathcal{A}$ 的极小左理想，与 1）矛盾。因此必有 $\mathcal{A}x = \mathcal{L}$ 成立。
2）推 3）：
首先 $\mathcal{L}x \subseteq \mathcal{L}, \forall x \in \mathcal{L}$，由 2），*需要一个高人来证明*

>[!note]
>设 $\mathcal{A}$ 和 $\mathcal{B}$ 是代数，$\phi: \mathcal{A} \rightarrow \mathcal{B}$ 是满射，$\mathcal{L}$ 是 $\mathcal{A}$ 的（极小）左理想，那么 $\phi(\mathcal{L})$ 是 $\mathcal{B}$ 的（极小）左理想。特别地，一个代数的自同态是极小理想间的同构。

证明：取 $b \in \mathcal{B}, y \in \phi(\mathcal{L})$，那么可以找到 $a \in \mathcal{A}, x \in \mathcal{L}$，使得 $b = \phi (a), y = \phi(x)$，从而：
$$
by = \phi(a) \phi(x) = \phi(ax )  \in \phi(\mathcal{L})
$$
因此 $\phi(\mathcal{L})$ 是 $\mathcal{B}$ 的左理想。现在假设 $\mathcal{L}$ 是极小的，我们要证明 $\phi(\mathcal{L})$ 是 $\mathcal{B}$ 的极小理想，那么我们只需利用上面的等价关系，证明 $\mathcal{B}u = \phi (\mathcal{L}) , u \in  \phi(\mathcal{L})$。注意到存在 $t \in \mathcal{L}$：
$$
\mathcal{B} u = \phi(\mathcal{A}) \phi(t) = \phi(\mathcal{A} t ) = \phi(\mathcal{L})
$$
得证。

下面我们继续研究代数的直和。若 $\mathcal{A} = \mathcal{B} \oplus \mathcal{C}$，且 $\mathcal{BC} = \mathcal{CB} = 0$，那么 $\mathcal{A}$ 是其子代数 $\mathcal{B},\mathcal{C}$ 的直和。如果一个代数可以写成其子代数的直和，那么这个代数是可约的。

>[!note]
>一个中心代数是不可约的。

如果 $\mathcal{A} = \mathcal{B} \oplus \mathcal{C}$，两侧乘以 $\mathcal{B}$ 得到：$\mathcal{AB} = \mathcal{BB} \oplus  0 = \mathcal{BB} \subset \mathcal{B}$，这意味着 $\mathcal{B}$ 是 $\mathcal{A}$ 的左理想，同理可得 $\mathcal{B}$ 是 $\mathcal{A}$ 的右理想。对于 $\mathcal{C}$ 来说也一样。又由于 $\mathcal{B,C}$ 中不能有共同的非零元素（注意，这里的 $\mathcal{B}$ 是 $\mathcal{B} \oplus \{0\}$，$\mathcal{C}$ 同理），否则 $\mathcal{BC} = 0$ 将不成立，那么 $\mathcal{A}$ 的其他非平凡理想均包含在 $\mathcal{B}$ 或 $\mathcal{C}$ 中。


我们可以根据一个代数的理想情况对其分类。如果一个代数除了 $\mathcal{A}$ 和 $\{0\}$ 之外没有其他的（双侧）理想，则称这个代数是简单的。
>[!note]
>一个简单代数 $\mathcal{A}$ 和任意代数 $\mathcal{B}$ 间的非平凡同态是单射。

对于 $\phi : \mathcal{A} \rightarrow \mathcal{B}$，$\ker \phi$ 是 $\mathcal{A}$ 的理想。若 $\phi$ 非平凡，那么 $\ker \phi = 0$，从而 $\phi$ 是单射。

接下来我们将商空间的概念推广到代数中。设 $\mathcal{A}$ 是一个代数，$\mathcal{B}$ 是 $\mathcal{A}$ 的一个子空间，那么设 $[a],[a'] \in \mathcal{A/B}$ ，自然地可以定义元素间的乘积：$[a][a'] = [aa']$。由于 $[a] = [a + b], [a'] = [a' + b']$，为了使得这个乘积有意义，我们必须有 $bb'  = b '' \in  \mathcal{B}$（取 $a = a' = 0$），这意味着 $\mathcal{B}$ 必须是 $\mathcal{A}$ 的子代数。若设 $a' = 0$，那么我们得到：
$$
ab' + bb' = b '' 
$$
这意味着 $\mathcal{B}$ 必须是 $\mathcal{A}$ 的左理想。若设 $a = 0$，则得到 $\mathcal{B}$ 是 $\mathcal{A}$ 的右理想。因此，$\mathcal{B}$ 是 $\mathcal{A}$ 的理想。






