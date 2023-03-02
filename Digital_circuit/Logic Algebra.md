#DCorMCU 

## 基本的逻辑关系
规定：两个输入同时为真时，结果才为真。这是与逻辑。记为：
$$
Y  = A \land B= A \& B=A\cdot B = AB 
$$

![[Pasted image 20230228134317.png|300]]

规定：只要有至少一个输入为真，结果就为真。这是或逻辑。记为：
$$
Y = A \lor B = A|B = A+B 
$$
![[Pasted image 20230228134604.png|300]]

规定：输出与输入相反，则为非逻辑。记为：
$$
Y = \bar A
$$
![[Pasted image 20230228134900.png|300]]

### 运算的优先级
- 单变量上的非运算拥有最高的优先级
- 与运算高于或运算
- 使用括号可以提高优先级
- 多变量上的非运算相当于加括号

## 逻辑函数
- 逻辑函数的相等：若两个逻辑函数的输入变量相同，且对于任意的一组变量都有相同的函数值

典型的逻辑函数：例如同或
$$
T = AB+\bar A\bar B
$$

### 逻辑代数的基本定律
- 0-1 律：$A\cdot 0=0,A+1=1$
- 自等率：$A\cdot 1=A,A+0=A$
- 互补律：$A\cdot \bar A=0, A+\bar A=1$
- 交换律
- 结合律
- 分配律：比代数运算中增加了：$A+B\cdot C=(A+B)(A+C)$
- 重叠律：$A\cdot A=A,A+A=A$
- 反演律：
$$
\bar{A+B} = \bar A\cdot \bar B \quad ; \quad \bar{A\cdot B} = \bar A+\bar B
$$
##### PF：分配律
$$
A+B\cdot C  = \bar{\bar{A+BC}} = \bar{\bar A\cdot \bar{BC}}=\bar{\bar A\cdot(\bar B+\bar C)} = \bar{\bar A\cdot \bar B+\bar A\cdot \bar C } = (A+B)(A+C)
$$
***注意：逻辑关系中没有减法和除法，不能两边同时除以一个东西或者同时减一个东西***

### 逻辑运算的三个规则
-  **带入规则**：任何一个逻辑等式，两侧相同的逻辑变量使用相同的逻辑函数替换，等式依然成立。
- 反函数：若 $F$ 和 $G$ 的输入变量相同，在任何一组输入组合的情况下，输出值都相反，则称 F 和 G 互为反函数。
- **反演规则**：对于任意函数 F，可以通过以下操作求得反函数：（1）将或运算变成与运算、与运算变成或运算；（2）将常量 0 变 1，1 变 0；（3）所有变量取反
例子：
$$
F = A\bar B+C\bar D
$$
则其反函数是：
$$
\bar F = (\bar A+B)\cdot (\bar C+D)
$$
在反演规则中，需要注意：不能打乱原有方程的运算顺序。在原变量变成反变量的过程中，多变量上的非号不能变！

- 对偶函数：将所有运算和常数反向，变量不需要取反
- **对偶规则**：如果两个函数相等，则它们的对偶式也相等。

### 逻辑运算的四个定理
- 合并定理：$AB+A\bar B=1, (A+B)(A+\bar B)=A$
- 吸收定理：$A+AB=A, A+\bar AB=A, A (A+B)=A, A (\bar A+B)=A$
- 添加项定理：$AB+\bar AC+BC=AB+\bar AC$
- ??? 定理：$\bar{AB+\bar AC}= A\bar B+\bar {AC}$
##### PF: 用结论补充一项的技巧！构造公因式！
$$
A+\bar AB=A+AB+\bar AB=A+B(A+\bar A)=A+B
$$
$$
AB+\bar AC+BC=AB+\bar AC+(\bar A+A)BC=AB+\bar AC
$$
以上结论到底如何证明，常见的逻辑函数如何化简，请参照[[Some Important Proofs in Logic Algebra]]













