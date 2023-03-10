#DCorMCU 

引例：分析下面的电路
![[Pasted image 20230314141900.png|200]]
![[Pasted image 20230314141931.png|200]]

## 常用的组合电路 
### 半加器和全加器
![[Pasted image 20230314142042.png|400]]
$$
S = A \oplus B \quad C = AB
$$
功能：$S$ 是和，$C$ 是进位。这种电路没有考虑进位的输入，因此称为“半加器”
![[Pasted image 20230314142321.png|200]]

当我们考虑从低位进入的进位时，电路也就成为“全加器”

#### 一位的全加器实现多位的全加器
![[Pasted image 20230314142826.png|350]]
这是一种最简单的多位全加器，其中，这样的设计会使得进位的效率非常低。但是这不是我们的重点

一种全加器的应用如下所示（3 倍乘法器）：
![[Pasted image 20230314143216.png|400]]
这个电路相当于将输入的每一位左移 1 维然后再加 1 ，所以是乘 3

减法器：
![[Pasted image 20230314143606.png|400]]

A 原码+（B 原码取反）得到的是所有位都为 1 的二进制数
A 原码+（B 原码取反+1）得到的是 A-B

##### Example 四位二进制全加器实现下面的电路 ：
有一个控制变量 $M$，当 $M=0$，电路实现加法，当 $M=1$，电路实现减法
- 显然，先把 $CI$ 接到 $M$ 上
- 其次，有一个加数不用变
- 最后，另一个加数
在 $M=0$ 时，写成 $B = BM'$，在 $M=1$ 时，写成 $B = B'M$，那么，我们统一写成 $B = BM'+B'M$
这可以使用异或门实现

### 数据选择器
功能：在选择信号作用下，从多路信号中选择一个输出



