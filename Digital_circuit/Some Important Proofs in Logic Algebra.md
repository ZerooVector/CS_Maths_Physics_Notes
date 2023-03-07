#DCorMCU 

## 逻辑代数中结论的证明

##### 分配律
定律：
$$
(A+B)\cdot(A+C) = A+BC
$$
证明：
$$
(A+B)(A+C) = AA+AB+AC+BC = A(1+B+C)+BC = A+BC
$$
其中，用到了 $AA=A$，以及 $1+B+C = 1$ 的结论


##### 吸收律
$$
A+AB = A 
$$
证明：
$$
A+AB=A(1+B) = A
$$
***记忆：一个加数中包含了另一个加数，则可以只取被包含者***

##### 吸收律 2
$$
A(A+B) = A
$$
证明：
$$
AA+AB =A+AB = A
$$
***记忆：展开成吸收律 1***
##### 吸收律 3
$$
A+\bar AB = A+B
$$
证明：
$$
A+\bar AB = (A+\bar A)(A+B) = A+B
$$
***记忆：这一类的特征是，一个加数里面包含另一个加数取反***
##### 吸收律 4
$$
AB+\bar AC+BC =  AB+\bar AC
$$
证明：
$$
=AB+\bar AC+(A+\bar A)BC = AB(1+C)+\bar AC(1+B) = AB+\bar AC
$$
***记忆：没有很好的记忆方式，但是你能在式子里看到一种“互补”的特性***
##### 结合律 1 
$$
AB+A\bar B = A
$$
证明：这是显然的，因为：
$$
A(B+\bar B) = A
$$
##### 结合律 2
$$
(A+B)(A+\bar B) = A
$$
证明：这也是显然的，因为：
$$
(A+B)(A+\bar B) =A+B\bar B = A
$$


## 逻辑函数的化简方法
这一部分来自清华电子系的教材。
### 并项法
##### 介绍和证明
并项法利用的是：
$$
B+B' = 1
$$
的特性，一般的通式是：
$$
AB+AB' = A
$$
##### 例题
除了利用正反变量相消之外，还有许多可以利用的关系，例如：异或和同或可以相消。
$$
\begin{aligned}
Y & = BC'D+BCD'+BC'D'+BCD\\
 &= B(C'D+CD')+B(C'D'+CD)\\ 
 & = B(C\oplus D)+B(C\oplus D)'\\
  & = B
\end{aligned}
$$

### 吸收法
##### 介绍和证明 
吸收法利用两种吸收律：
- 标准吸收律：$A+AB = A$，从式子中吸取一个 $B$，这个式子的意义是，A 必然发生，不需要在乎 B 了
- 反向吸收律：$A+\bar AB = A+B$，从式子中吸取一个 $\bar A$，这是说，只有 $A$ 和 $B$ 中只能有一个对结果有贡献

##### 例题
$$
\begin{aligned}
Y &=A+(A'(BC)')'(A'+(B'C'+D)')+BC\\
&=A+(A'(B'+C'))'(A'+(B'C'+D)')+BC\\
&= A+(A+BC)(A'+(B'C'+D)')+BC\\
 &= (A+BC)(1+(A'+(B'C'+D)'))\\
 &= A+BC
\end{aligned}
$$

### 消项法
##### 介绍和证明
消项法利用两种规律，从式子中抽掉一项：
- 抽掉两个变量：$AB+\bar AC +BC = AB+\bar AC$，消去一项 $BC$，这说明这一项对结果没有贡献（结果已经被 $A$ 和 $A'$ 控制了）
- 抽掉三个变量：$AB +\bar AC +BCD = AB+\bar AC$

##### 例题
$$
\begin{aligned}
Y &=AC+A'D+C'D\\
 & = AC+(A'+C')D \\
 & = AC+(AC)'D\\
 &= AC+D
\end{aligned}
$$
（注意：这里出现了反用反演律的情形）

### 配项法
##### 介绍和证明
配项法是给公式添加项的手法，主要包括以下两点：
- 利用 $A+A=A$ 重复写入某一项
- 利用 $A+A'=1$ 将其中的某一项不断乘上类似 $A+A'$ 的一项

##### 例题
$$
\begin{aligned}
Y &= A'BC'+A'BC+ABC\\
&= A'BC'+(A'BC+A'BC)+ABC\\
&= A'B(C+C')+BC(A+A')\\
&= A'B+BC
\end{aligned}
$$
$$
\begin{aligned}
Y &=AB'+A'B+BC'+B'C\\
&= AB'+A'B(C+C')+BC'+(A+A')B'C\\
&= (AB'+AB'C)+(BC'+A'BC')+(A'BC+A'B'C)\\
&= AB'+BC'+ A'C
\end{aligned}
$$





