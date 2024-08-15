 #MathematicalPhysics 

我们现在要将代数分成更小的代数，现在我们来研究可分解的条件。在本小节中，我们认为所有的代数都是可交换的。

我们定义一个元素 $a \in \mathcal{A}$ 是幂零的，如果对于某些整数 $k$ 有 $a^{k} = 0$，其中最小的整数称为 $a$ 的指数。$\mathcal{A}$ 的子代数 $\mathcal{B}$ 被称为是幂零的，如果 $\mathcal{B}$ 的所有元素都是幂零的。如果 $\mathcal{B}^{v} = \{0\}$，但是 $\mathcal{B}^{v-1} \not = 0$，那么我们称 $\mathcal{B}$ 的指数是 $v$。$P \in \mathcal{A}$ 被称为幂等的，如果 $P^{2} = P$。
一个例子是：$n \times n$ 的严格上三角矩阵是 $n$ 阶的幂零代数。

>[!note]
>一个幂零代数的理想也是幂零的。

一个代数的左、右、双侧幂零理想包含在某一个幂零理想中。接下来我们解释这一点。
>[!note]
>设 $\mathcal{L}$ 和 $\mathcal{M}$ 是 $\mathcal{A}$ 的两个左（右）幂零理想，指数分别为 $\lambda,\mu$，则 $\mathcal{L+M}$ 也是 $\mathcal{A}$ 的左（右）幂零理想，其指数至多为 $\lambda+ \mu  -1$。

显然 $\mathcal{A}(\mathcal{L}+ \mathcal{M}) \subseteq \mathcal{L} + \mathcal{M}$，因此 $\mathcal{L} + \mathcal{M}$ 是 $\mathcal{A}$ 的左理想。$(\mathcal{L} + \mathcal{M})^{k}$ 中的元素都可以被写成 $a_{1}a_{2}\cdots a_{k}$ 的形式，$a_{i}$ 是 $\mathcal{L}$ 或 $\mathcal{M}$ 中的元素。不妨设其中有 $l$ 项在 $\mathcal{L}$ 中，有 $m$ 项在 $\mathcal{M}$ 中，设 $j$ 是最大的整数，使得 $a_{j} \in \mathcal{L}$，从 $a_{j}$ 开始往左看，直到碰到另一个 $\mathcal{L}$ 中的元素 $a_{r}$ ，由于 $\mathcal{L}$ 是 $\mathcal{A}$ 的左理想，那么我们立刻知道：
$$
a_{r+1} \cdots a_{j} = a_{j}' \in \mathcal{L}
$$
从而：
$$
a_{1}a_{2}\cdots a_{k} = b_{1}b_{2} \cdots b_{l} c = c_{1}c_{2} \cdots c_{m}  b 
$$
由于 $k = l + m$，如果 $k = \mu + \lambda -1$，那么 $(\mu - m) + (\lambda - l) = 1$。这说明如果 $m <  \mu$，那么 $l \ge \lambda$；如果 $l < \lambda$，那么 $m \ge \mu$，那么立刻得到 $a_{1} \cdots a_{k} = 0$。

>[!note]
>设 $\mathcal{L}$ 是 $\mathcal{A}$ 的一个幂零左理想，那么 $\mathcal{J} = \mathcal{L} + \mathcal{LA}$ 是 $\mathcal{A}$ 的双侧幂零理想。

注意到：
$$
\mathcal{AJ} = \mathcal{AL} + \mathcal{ALA}  \subseteq \mathcal{L} + \mathcal{LA}  = \mathcal{J}
$$
$$
\mathcal{JA} = \mathcal{LA} + \mathcal{LAA} \subseteq  \mathcal{LA} + \mathcal{LA} \subset \mathcal{J} 
$$
因此 $\mathcal{J}$ 是 $\mathcal{A}$ 的双侧理想。
现在考虑 $\mathcal{LA}$ 中 $k$ 个元素的乘积：$l_{1}a_{1}l_{2}a_{2} \cdots l_{k}a_{k} = l_{1}' l_{2}' l_{k}' a_{k}$，因此如果 $k$ 高于 $\mathcal{L}$ 的次数，则上面的乘积是零，因此 $\mathcal{LA}$ 是幂零的。由于 $\mathcal{L}$ 也是幂零的，利用上面的引理得证。

>[!note]
>代数 $\mathcal{A}$ 存在一个唯一幂零理想，包含了 $\mathcal{A}$ 的每个左、右、双侧幂零理想。

设 $\mathcal{N}$ 是维度最高的幂零理想，$\mathcal{M}$ 是任意的幂零理想，根据引理，$\mathcal{N} + \mathcal{M}$ 是一个幂零理想。由于 $\mathcal{N}+ \mathcal{M} \subset \mathcal{N}$，那么 $\mathcal{M} \subset \mathcal{N}$，显然 $\mathcal{N}$ 包含了所有幂零理想。如果我们有另一个极大幂零理想 $\mathcal{N}'$，那么 $\mathcal{N}' \subseteq \mathcal{N},\mathcal{N} \subseteq \mathcal{N}'$，这意味着 $\mathcal{N'} = \mathcal{N}$，那么 $\mathcal{N}$ 是唯一的极大幂零理想。如果 $\mathcal{L}$ 只是左侧幂零理想，那么 $\mathcal{L} \subset \mathcal{J} = \mathcal{L} + \mathcal{LA} \subset \mathcal{N}$。对于右侧幂零理想是同理的。因此 $\mathcal{N}$ 包含了所有左侧、右侧、双侧幂零理想。

我们现在定义：代数 $\mathcal{A}$ 的极大幂零理想被称为 $\mathcal{A}$ 的根，使用 $\text{Rad} (\mathcal{A})$ 表示。

>[!note]
>设 $\mathcal{A}$ 中有一个元素满足 $\mathcal{A}a^{k} = \mathcal{A}a^{k-1}$ 对于某个正整数 $k$ 成立，那么 $\mathcal{A}$ 包含一个幂等元素。

令 $\mathcal{B} = \mathcal{A}a^{k-1}$，那么 $\mathcal{B}$ 是 $\mathcal{A}$ 的右理想（$\mathcal{B}a = \mathcal{B}$）。两侧同乘以 $a$，得到：$\mathcal{B}a^{2} = \mathcal{B} a^{3} = \mathcal{B}$，从而 $\mathcal{B}a^{k} = \mathcal{B}$。而 $a^{k} \in \mathcal{B}$，现在，令 $b = a^{k}$，我们得到 $\mathcal{B} b = \mathcal{B}$，也就是说我们能找到 $b$ 中一个元素 $P$，使得 $Pb = b$，也就是 $P^{2} = P$，从而 $\mathcal{A}$ 中包含幂等元素 $P$。

>[!note]
>一个代数是幂零的，当且仅当它不含幂等元素。

依照定义，幂零代数一定不能含有幂等元素。接下来证明另一侧。首先我们有 $\mathcal{A} a \subseteq \mathcal{A}$，那么就有 $\mathcal{A} a^{k} \subseteq \mathcal{A} a^{k-1}$。由上面的引理知道，如果 $\mathcal{A}$ 中无幂等元素：
$$
\mathcal{A} \supset  \mathcal{A}a \cdots  \supset \mathcal{A}a^{k} \supset \cdots 
$$
由于 $\mathcal{A}$ 是有限维的，那么必然有 $\mathcal{A} a^{r} = \{0\}$，也就是 $a^{r+1} = 0$。得证。

现在令 $P$ 是 $\mathcal{A}$ 中的一个幂等元素，而 $\mathcal{L}(P)$ 是 $P$ 的左零化子，也就是说 $\mathcal{L}(P) P = 0$。对于任意 $a \in \mathcal{A}$，都有 $(a- aP) \in \mathcal{L}(P)$ 成立（这是显然的）。此外，如果 $a \in P \mathcal{L}(P)$，也就是说对于某个 $x \in \mathcal{L}(P)$，有 $a = Px$。此时，我们有 $Pa=a$（因为 $P$ 是幂等的）和 $aP=0$。同理，如果 $a \in \mathcal{R}(P)P$，那么我们也有 $aP = a, Pa = 0$。
现在取 $\mathcal{J}(P) = \mathcal{L}(P) \cap \mathcal{R}(P)$，显然 $\mathcal{J}(P)$ 是 $\mathcal{A}$ 的双侧理想，而且 $\mathcal{J}(P)$ 中所有元素 $a$ 都满足 $aP = Pa = 0$。另外，我们还可以找到一个子代数 $P \mathcal{A} P$，其中的元素 $a$ 满足 $Pa = aP = a$ 。
因此，我们找到了四个子代数：
![[Pasted image 20240731183812.png|400]]

>[!note]
>设 $\mathcal{A}$ 是有一个幂等元素的 $P$，那么我们可以将代数 $\mathcal{A}$ 做直和分解：$\mathcal{A} = P \mathcal{A} P \oplus_{V} P \mathcal{L}(P) \oplus_{V}\mathcal{R}(P) P \oplus_{V} \mathcal{J}(P)$，这里的 $\oplus_{V}$ 是向量空间的直和。

证明是显然的：
$$
a = PaP + P(a - aP) +(a-Pa)P +(a-Pa-aP+PaP)
$$

对于 $a \in  \mathcal{A}$，如果 $aP = Pa = 0$，那么我们说它与 $P$ 正交。如果 $\mathcal{J}(P)$ 中不再包含任何幂等元素，我们说 $P$ 是主要的。若 $P_{0}$ 不是主要的，那么 $\mathcal{J}(P_{0})$ 包含一个幂等元素 $q$，令 $P_{1} = P_{0} + q$，那么 $P_{1}P_{0} = P_{0}P_{1} = 0$，$P_{1}q = qP_{1} = q$，现在取 $x \in \mathcal{J}(P_{1})$，那么 $xP_{1} = P_{1}x = 0$，同时显然又有 $xP_{0} = P_{0}x  = 0$，因此 $\mathcal{J}(P_{1}) \subseteq \mathcal{J}(P_{0})$。又由于 $q \in \mathcal{J}(P_{0})$，但是 $q \in \mathcal{J}(P_{1})$，所以我们知道 $\mathcal{J}(P_{0}) \supset \mathcal{J}(P_{1})$。继续推理下去，假如 $P_{1}$ 也不是主要的，那么我们可以继续找到其子集 $\mathcal{J}(P_{2})$。因此，我们最终能找到 $P_{n}$ 是主要的。因此：
>[!note]
>每一个非幂零的代数都能找到一个主要的幂等元素。

我们称一个幂等元素是本原的，如果它不能写成两个正交幂等元素的和。
>[!note]
> $P$ 是本原的，当且仅当它是 $P \mathcal{A} P$ 中的唯一幂等元素。

设 $P$ 不是本原的，那么 $P = P_{1} + P_{2}$，显然对于 $i = 1,2$，有 $PP_{i} = P_{i}P = P_{i}$，因此 $P_{i} \in P \mathcal{A} P$，矛盾。再设 $P$ 不是 $P \mathcal{A} P$ 中唯一的幂等元素（另外一个是 $P'$），那么我们有 $PP' = P'P = P'$，这意味着：
$$
(P - P')P' = P'(P - P') = 0 \quad  (P - P') P = P(P - P') = P - P'
$$
那么：$(P - P') \in  P \mathcal{A} P$，且它与 $P'$ 正交，还是个幂等元素。因此 $P = (P - P') + P'$，从而 $P$ 不是本原的。

>[!note]
>任意一个幂等元素都可以被表示成有限个互相正交的本原幂等元素之和。


我们现在来研究半简单代数。如果一个代数的根中只含有零，那么我们称其是半简单的。
>[!note]
>一个简单代数是半简单的。

简单的代数 $\mathcal{A}$ 的理想只有 $\mathcal{A}$ 和 $\{0\}$，我们现在要说明 $\mathcal{A}$ 是不幂零的。使用反证法，$\mathcal{A}^{2}$ 必须是 $\mathcal{A}$ 的真子集。由于 $\mathcal{A}^{2}$ 是 $\mathcal{A}$ 的理想，因此它只能为 $\{0\}$，这意味着 $\mathcal{A}$ 的任意子集都是它的理想，导出了矛盾。

>[!note]
>如果 $\mathcal{A}$ 是半简单的，$P$ 是 $\mathcal{A}$ 中任意的主要幂等元素，那么 $\mathcal{A} = P \mathcal{A} P$。

由于 $\mathcal{A}$ 不是幂零的，那么其中必然含有一个主要的幂等元素 $P$，那么 $\mathcal{J}(P)$ 必然不包含幂等元素，是幂零的。而由于 $\mathcal{A}$ 是半简单的，那么 $\mathcal{A}$ 是没有除了 $\{0\}$ 之外的极大幂零理想的，那么 $\mathcal{J}(P) = \{0\}$，注意到 $\mathcal{R}(p) \mathcal{L}(p)$ 是 $\mathcal{J}(P)$ 的子集，那么 $\mathcal{R}(P) \mathcal{L}(P) = \{0\}$，也就是说 $(lr)^{2} = 0$，这意味着 $\mathcal{L}(P)\mathcal{R}(P)$ 是简单的，从而 $\mathcal{L}(P) \mathcal{R}(P) = \{0\}$。在前面我们讲过矩阵的直和分解，将直和分解左乘 $\mathcal{L}(P)$，并利用结果 $\mathcal{L}(P) P = \{0\}$，我们直接得到 $\mathcal{L}(P) \mathcal{A} = \mathcal{L} (P) \mathcal{R}(P) P = \{0\}$ ，特别地，$\mathcal{L}(P)$ 是零，同理可以推知 $\mathcal{R}(P)$ 也是零。因此根据前面的直和分解，我们可以发现 $\mathcal{A}$ 的直和分解就只剩下第一项了。因此，$\mathcal{A} = P \mathcal{A} P$

>[!note]
>一个半简单代数 $\mathcal{A}$ 必须包含单位元。进一步地，单位元是 $\mathcal{A}$ 中唯一的主要幂等元素。

设 $P$ 是 $\mathcal{A}$ 中的主要幂等元素，取一个元素 $b \in \mathcal{A}$，那么 $b = PaP$，从而容易验证 $Pb = bP = b$，因此 $P$ 是单位元。
>[!note]
>如果 $\mathcal{A}$ 是半简单的，那么对于任意幂等元素 $P \in  \mathcal{A}$ ，$P \mathcal{A} P$ 也是半简单的。

令 $\mathcal{N} = \text{Rad}(P \mathcal{A} P)$，取 $x \in \mathcal{N} \subset P \mathcal{A} P$。根据前面的论述：$Px = xP = x$，从而：
$$
(\mathcal{A}x)^{v+1} = \mathcal{A}x ( P \mathcal{A} Px)^{v}
$$
我们有 $P \mathcal{A}Px \subset \mathcal{N}$，如果 $v$ 是 $\mathcal{N}$ 的指数，那么 $(P \mathcal{A} Px)^{v} = \{0\}$，从而 $(Ax)^{v+1} = \{0\}$，也就是说 $\mathcal{A}x$ 是幂零的。由于 $\mathcal{A}$ 是半简单的，而 $\mathcal{A}x$ 是 $\mathcal{A}$ 的理想，那么必有 $\mathcal{A}x = \{0\}$，因此对于任意 $a$，都有 $ax = 0$，也就是说 $Px = x = 0$。，从而 $P \mathcal{A} P$ 也是半简单的。

>[!note]
>设 $\mathcal{A}$ 是半简单代数，$P$ 是 $\mathcal{A}$ 中的幂等元素，那么 $P \mathcal{A} P$ 是除法代数，当且仅当 $P$ 是本原的。

设 $P \mathcal{A} P$ 是除法代数，那么单位元是其中唯一的幂等元素。由于 $P$ 是 $P \mathcal{A} P$ 的单位元，那么 $P$ 就是 $P \mathcal{A} P$ 中的唯一幂等元素。利用前面的结论可知 $P$ 是本原的。
设 $P$ 是本原的，取 $x \in  P \mathcal{A} P$ 是非零元素，那么 $\mathcal{L} = P \mathcal{A} Px$ 不能是幂零的（因为 $P \mathcal{A} P$ 是半简单的）, 那么 $\mathcal{L}$ 中就要包含幂等元素。$\mathcal{L}$ 中的幂等元素正是 $P \mathcal{A}P$ 中的幂等元素，这个元素正是 $P$。那么，我们可以将 $P$ 写成 $P = ax, a \in  P\mathcal{A}P$。考虑到 $P$ 是 $P \mathcal{A} P$ 的单位元，这意味着每个 $P \mathcal{A}P$ 中的元素都有一个逆元，因此 $P \mathcal{A}P$ 是一个除法代数。

我们知道，一个简单代数必然是半简单代数，但是反之却不一定成立。这意味着简单代数似乎比半简单代数更加基本。我们来阐明这一点。

>[!note]
>若 $\mathcal{A}$ 有理想 $\mathcal{B}$，其中包含单位元 $1_{B}$，那么 $\mathcal{A} = \mathcal{B} \oplus \mathcal{J}(1_{B})$

考虑到 $1_{B}$ 是 $\mathcal{A}$ 中的幂等元素，我们做如下分解：
$$
\mathcal{A} = 1_{B} \mathcal{A} 1_{B} \oplus_{V} 1_{B} \mathcal{L}(1_{B}) \oplus_{V} \mathcal{R}(1_{B})1_{B} \oplus_{V}\mathcal{J}(1_{B})  = \mathcal{S}(1_{B })\oplus_{V }\mathcal{J}(1_{B})
$$
由于 $\mathcal{B}$ 是 $\mathcal{A}$ 的理想，容易注意到：$\mathcal{S}(1_{B})$ 的每一部分都是 $\mathcal{B}$ 的子集，那么 $\mathcal{S}(1_{B}) \subseteq B$。反过来，根据上面的分解，取 $b_{1} \in \mathcal{S} (1_{B}), b_{2} \in \mathcal{J}(1_{B})$，令 $b = b_{1} + b_{2}$，两侧同时乘以 $1_{B}$ 得到 $b = b_{1}$，从而 $b \in \mathcal{S}(1_{B})$，从而 $\mathcal{B} \subseteq \mathcal{S}(1_{B})$，从而 $B = \mathcal{S}(1_{B})$。又由于 $\mathcal{J}(1_{B})\mathcal{B} = \mathcal{B} \mathcal{J}(1_{B}) = \{0\}$，得证。

>[!note]
>半简单代数的非零理想是半简单的。

设 $\mathcal{A}$ 是一个半简单代数，$\mathcal{B}$ 是 $\mathcal{A}$ 的非零理想。（由于我们这里讨论的代数都是可交换的），容易发现 $\mathcal{B} \text{Rad} (\mathcal{B}) \mathcal{B}$ 仍然是 $\mathcal{A}$ 的理想，并且其中的元素还是幂零的。因此 $\mathcal{B} \text{Rad} (\mathcal{B}) \mathcal{B} \subset \text{Rad}(\mathcal{B})$。另外容易注意到 $\mathcal{B} \text{Rad} (\mathcal{B}) \mathcal{B}$ 也是 $\mathcal{A}$ 的幂零理想。$\mathcal{A}$ 是半简单的意味着 $\mathcal{B} \text{Rad} \mathcal{B} = \{0\}$。考虑到 $\mathcal{A} \text{Rad}(\mathcal{B}) \mathcal{A} \subset \mathcal{B}$，那么 $\mathcal{A} \text{Rad}(\mathcal{B}) \mathcal{A}  \text{Rad}(\mathcal{B}) \mathcal{A} \text{Rad}(\mathcal{B}) \mathcal{A} \subset \mathcal{B} \text{Rad} \mathcal{B}$，那么：
$$
(\mathcal{A} \text{Rad}(B) \mathcal{A})^{3} \subset \mathcal{A} \text{Rad}(\mathcal{B}) \mathcal{A}  \text{Rad}(\mathcal{B}) \mathcal{A} \text{Rad}(\mathcal{B}) \mathcal{A}  \subset \mathcal{B} \text{rad} (\mathcal{B}) \mathcal{B} = \{0\}
$$
这意味着 $\mathcal{A} \text{Rad}(B) \mathcal{A}$ 是幂零的。由于它是 $\mathcal{A}$ 的理想，并且 $\mathcal{A}$ 是半简单的，那么 $\mathcal{A} \text{Rad}(B) \mathcal{A} = \{0\}$ 。前面已经讨论过，半简单代数 $\mathcal{A}$ 必须含有单位元，因此 $\mathcal{A}$ 不可能是幂零的，只有 $\text{Rad}(\mathcal{B})$ 是幂零的，那么 $\mathcal{B}$ 是半简单的。

>[!note]
一个代数是半简单的，当且仅当它是一些简单代数的直和。

设代数 $\mathcal{A}$ 是一些简单代数的直和，那么根据前面的讨论，$\mathcal{A}$ 的理想只能是这些简单代数，或者包含在这些简单代数中，由于这些代数都是半简单的，所以这些理想都不是 $\mathcal{A}$ 的幂零理想，因此 $\mathcal{A}$ 是半简单的。
反过来，设 $\mathcal{A}$ 是半简单的，如果它没有任何非平凡理想，那么它是简单的。假设 $\mathcal{B}$ 是 $\mathcal{A}$ 的非平凡理想，那么 $\mathcal{B}$ 也是半简单的，其中必有单位元 $1_{B}$。那么我们可以将 $\mathcal{A}$ 写成 $\mathcal{A} = \mathcal{B} \oplus \mathcal{J}(1_{B})$。如果两个成分中的任何一个不是简单的，我们继续这个分解过程即可。

>[!note]
半简单代数到简单代数直和的分解是唯一的。

设 $\mathcal{A}$ 的直和分解是 $\mathcal{A} = \mathcal{A}_{1} \oplus \cdots \mathcal{A}_{r}$，那么 $\mathcal{A}$ 中单位元的分解是 $1_{A}= 1_{1} + 1_{2}  +\cdots + 1_{r}$。现在设 $\mathcal{A}$ 有另一种直和分解的方法：
$$
\mathcal{A} = \mathcal{A}_{1}' \oplus  \cdots  \oplus  \mathcal{A}_{r}'
$$
将单位元直和分解的两侧乘以 $\mathcal{A}_{j}'$ 得到（也就是将 $\mathcal{A}_{j}'$ 进一步分解）：
$$
\mathcal{A}_{j}' = \mathcal{A_{j}}'1_{1} + \cdots + A_{j}'1_{r} = \sum_{i=1}^{r}  A_{ji}'
$$
由于 $\mathcal{A}_{i}$ 是 $\mathcal{A}$ 的理想，因此 $\mathcal{A}_{ji}' \subset \mathcal{A}_{i}$。很容易验证 $\mathcal{A}_{j}'1_{i}$ 是个代数，而且由于 $1_{i}1_{k} = 0(i \not =  k)$，那么 $\mathcal{A}_{ji}' \mathcal{A}'_{jk} = 0 (i \not = k)$，因此上面对于 $A_{j}'$ 的进一步分解也是一个直和分解。从而 $\mathcal{A}_{ji}'$ 是 $\mathcal{A}_{j}'$ 的理想，同时，$A_{ji}'$ 又是 $\mathcal{A}_{i}$ 的子集，那么根据 $\mathcal{A}_{i}$ 的简单性我们有 $\mathcal{A}_{ji}'=\mathcal{A}_{i}$ 或等于 $\{0\}$。由于 $\mathcal{A}_{j}'$ 是简单的，因此它的分解中只有一个非零元素，那么只能是 $\mathcal{A}_{jj}' = \mathcal{A}_{j}$ 这一项。得证。


在前面，我们对半简单的代数（根为零的代数）进行了描述，说明它可以由简单代数的直和构成。那么一般的代数能不能被分解成它的根和一个半简单代数呢？这意味着 $\mathcal{A} = \text{Rad}(\mathcal{A}) \oplus \mathcal{A}  /   \text{Rad}(\mathcal{A})$，然后 $\mathcal{A}  /   \text{Rad}(\mathcal{A})$ 是半简单的。实际上这是可以的，这样，我们就把一般代数的研究转换成了对它的根和半简单代数的研究，半简单代数又可以分解成简单代数，而简单代数可以进一步分解：
>[!note] Wedderburn 分解
>代数 $\mathcal{A}$ 是简单的，当且仅当 $\mathcal{A} = \mathcal{D} \otimes \mathcal{M}_{n} = \mathcal{M}_{n}(\mathcal{D})$，其中 $\mathcal{D}$ 是一个商代数，而 $\mathcal{M}_{n}(\mathcal{D})$ 是 $\mathcal{D}$ 上的全矩阵代数。

使用 $\mathcal{Z}_{n}$ 代表 $\mathcal{M}_{n}$ 的中心，由于 $\mathcal{M}_{n}$ 是中心代数，根据前文，$\mathcal{Z}_{n} = \text{Span}(1_{n})$，换言之，上式可以写成：
$$
\mathcal{Z}(\mathcal{A} ) = \mathcal{Z}(D) \otimes \mathcal{Z}_{n} = \mathcal{Z}(D)
$$

>[!note]
> $\mathbb{C}$ 上的唯一除法代数是 $\mathbb{C}$ 自身。

证明：设 $\mathcal{D}$ 是 $\mathcal{C}$ 上的除法代数，并设 $x$ 是 $\mathcal{D}$ 的非零元素，则在 $n$ 足够大时，由于 $1, x, x^{2},\cdots,x^{n}$ 不可能线性无关，于是必有：
$$
f(x) = x^{n} + \alpha_{n-1} x^{n-1} +\cdots + \alpha_{1}x  + \alpha_{0}1 = 0
$$
将 $n$ 取为使得上式满足的最小值，那么根据代数基本定理，$f(x)$ 至少有一个根 $\lambda$，那么我们有：
$$
f(x) = (x - \lambda 1) g(x) = 0 
$$
那么，$g(x)$ 的次数显然不多于 $n-1$，而且根据对于 $n$ 的假设，$g (x) \not = 0$。这意味着 $x - \lambda 1 = 0$，从而 $\mathcal{D}$ 中的每一个元素 $x$ 都满足 $x = \lambda 1,\lambda\in \mathcal{D}$，这就完成了证明。

前面的讨论给出了下面有趣的结果：
>[!note]
>任意 $\mathcal{C}$ 上的简单代数 $\mathcal{ A}$ 都与 $\mathcal{M}_{n}(\mathcal{C})$ 同构，这样，$\mathcal{A}$ 必须是中心简单的。

在抽象代数中有重要的 Frobenius 定理，它声称 $\mathbb{R}$ 上的商代数只能是 $\mathbb{R},\mathbb{C},\mathbb{H}$，以及它们的张量积。$\mathbb{C}$ 的中心就是其自身，因为它是可交换的，另外，$\mathcal{H}$ 的中心由它的单位元张成。

现在考虑 $\mathbb{R}$ 上的一个简单代数，如果 $\mathcal{A}$ 是中心的（例如 $\mathcal{Z}(\mathcal{A})  = \mathbb{R}$），那么从上面的讨论中可以得到：$\mathbb{R} = \mathcal{Z}(\mathcal{D}) \Rightarrow  \mathcal{D} = \mathbb{R}\ \text{or}\ \mathcal{H}$。如果 $\mathcal{Z}(\mathcal{A}) = \mathbb{C}$，那么 $\mathbb{C} = \mathcal{Z}(\mathcal{D}) \Rightarrow \mathcal{D} = \mathbb{C} \ \text{or} \ \mathbb{C} \otimes \mathbb{H}$。根据这些讨论，我们知道：
>[!note]
>任意 $\mathbb{R}$ 上的简单代数 $\mathcal{A}$ 都与 $\mathcal{D}\otimes \mathcal{M}_{n}$ 同构。如果 $\mathcal{A}$ 的中心与 $\mathbb{C}$ 同构，那么 $\mathcal{D}$ 是 $\mathbb{C}$ 或者 $\mathbb{C} \otimes \mathbb{H}$；如果 $\mathcal{A}$ 是中心的，那么 $\mathcal{D}$ 是 $\mathbb{R}$ 或者 $\mathbb{H}$。

最后，我们再来讨论一些关于简单代数的东西，以及本原幂等元素和极小左理想之间的联系。对于 $\mathcal{A}$ 中的两个幂等元素 $P$ 和 $P'$，我们称它们是相似的，如果存在一个可逆的元素 $s \in \mathcal{A}$ 使得 $P' = sPs^{-1}$。
>[!note]
>设 $P$ 是简单代数 $\mathcal{A}$ 的幂等元素，那么这里必然存在一组相互正交的本原幂等元素 $P_{i}$，使得 $P = \sum_{i=1}^{r}  P_{i}$，这里的整数 $r$ 称为幂等元素 $P$ 的秩。两个幂等元素相似，当且仅当它们有相同的秩。

>[!note]
>设 $P$ 是半简单代数 $\mathcal{A}$ 中的本原幂等元素，那么 $\mathcal{A}P$ 或 $P \mathcal{A}$ 是 $\mathcal{A}$ 的极小左（右）理想。

证明：由于半简单代数是一系列彼此独立的简单代数的直和，不失一般性，我们直接设 $\mathcal{A}$ 是简单的（否则我们也可以将 $\mathcal{A}$ 拆成很多简单代数来研究）。假设 $\mathcal{L} = \mathcal{A}P$ 不是极小的，那么 $\mathcal{L}$ 就要包含 $\mathcal{A}$ 的非零左理想 $\mathcal{L}_{1}$。由于 $\mathcal{A}$ 是半简单的，那么 $\mathcal{L}_{1}$ 必然不可能是幂零的，它就要包含幂等元素 $P_{1}$。如果 $P_{1} = P$，那么 $\mathcal{L} = \mathcal{A}P = \mathcal{A}P_{1} \subseteq \mathcal{L}_{1}$，而 $\mathcal{L}_{1} \subseteq \mathcal{L}$，这意味着 $\mathcal{L}_{1} = \mathcal{L}$，我们的证明结束。如果 $P_{1} \not= P$，那么我们将 $P_{1}$ 拆成一系列互相正交的本原幂等元素的和：$P_{1} = Q_{1} + \cdots Q_{r}$。由于 $P$ 是本原的，那么 $P$ 的秩为 1，$Q_{i}$ 的秩也为 1，因此 $P$ 和 $Q_{i}$ 相似。因此存在一个可逆元素 $s \in \mathcal{A}$，使得 $P=s Q_{1} s^{-1}$。因此，通过将 $P_{1}$ 改写成 $sP_{1}s^{-1}$（同样也是一个幂等元素），可以得到：$P_{1}= P + Q_{2} + \cdots +Q_{r}$，而且显然 $P$ 与其他的 $Q_{i}$ 都正交。两侧同时乘以 $P$，我们得到 $PP_{1} = P$，那么 $\mathcal{L} = \mathcal{A}P$，从而 $\mathcal{L} = \mathcal{A} P = \mathcal{A}PP_{1} \subseteq \mathcal{L}_{1}$，于是同样得到 $\mathcal{L} = \mathcal{L}_{1}$。


