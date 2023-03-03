#MA 

这一章中，我们着重介绍特征值分解的应用

## 应用 1：方阵的开方
这个原理如下：
首先，如果一个方阵可以被开平方，意思是它可以被写成：
$$
A= BB
$$
那么我们对 $A$ 特征值分解：
$$
A  = V\Lambda V^{-1}
$$
现在令：
$$
B = V\Lambda^{1/2}V^{-1}
$$
那么可以注意到：
$$
B^2 = V\Lambda V^{-1}= A
$$
那么我们得到：
$$
A^{1/2} = V\Lambda^{1/2}V^{-1}
$$
这个式子可以被推广到
$$
A^p = V\Lambda^pV^{-1}
$$

## 应用 2 ：计算矩阵指数
矩阵指数是利用收敛幂级数定义的，例如：
$$
e^A = \exp(A) = I + \sum_i \frac{1}{i!}A^i
$$
那么如果使用特征值分解，显然可以简化计算：
$$
e^A = \exp(A) = V(I + \sum_i \frac{1}{i!}A^i)V^{-1}
$$
那么
![[Pasted image 20230303163021.png|400]]

## 应用 3：用矩阵加速递推
斐波那契数列的递推可以写成矩阵形式：
$$
x_{k+1} = \begin{bmatrix}
0 & 1 \\
1 & 1
\end{bmatrix}x_k
$$
显然可以通过将 $A$ 特征值分解后，快速计算斐波那契数列的高阶项，还可以得到通项公式：
![[Pasted image 20230303163358.png|250]]

## 应用 4：Markov Chain 的平稳状态
马氏链的转移写为：
$$
T\pi_k = \pi_{k+1}
$$
显然，稳定状态是：
$$
T\pi = \pi
$$
这说明 $\pi$ 是 $T$ 的特征向量。而且对应的特征值为 1。
==注意：这里 $\pi$ 中的几个元素仅代表每一部分的比例，不是每一部分的百分比==

## 应用 5：瑞丽商 (Rayleigh quotient)
参见北京理工大学矩阵分析第一周作业 [[Week 1 Homework for Matrix Analysis]]
瑞丽商是对于一个实对称矩阵 $A$ 定义的：
$$
R(x) = \frac{x^TAx}{x^Tx}
$$
它的取值范围在最小特征值和最大特征值之间。我们给出一个简短的证明：
$$
\begin{aligned}
\max R(x) &= \frac{(V^Tx)^T\Lambda (V^Tx)}{x^Tx}\\
& = \frac{\sum_j y_j^2\lambda_j}{\sum_i x_i^2}\\
s.t.& \sum_i x_i^2 = 
\end{aligned}

$$






