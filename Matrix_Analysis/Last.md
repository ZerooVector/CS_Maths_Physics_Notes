## 矩阵不等式

##### DEF 矩阵不等式
如果矩阵 $A$ 中每一个元素都大于 0，则称 $A>0$
如果 $A-B>0$，我们就称 $A>B$

##### DEF 矩阵的绝对值
$|A|$ 定义为 $A$ 中每一个元素取绝对值

##### Theory 
对于矩阵的绝对值，有如下性质成立：
$$
|Ax| \le|A||x|
$$
这可以用 Cauchy-Schwartz 不等式证明
其中，等号仅仅在 $A=|A|$ 时取到，这容易根据 C-S 不等式的取等条件得到

同理，对于两个矩阵，也有如下结论成立：
$$
|AB| \le |A||B|
$$
以及
$$
|A^{m}| \le |A|^{m}
$$
这个证明应该使用数学归纳法：
- 当 $m=1$ 时，式子显然成立
- 当 $m>1$ 时，
$$
|A^{m}|  = |A^{m-1}A| \le |A^{m-1}||A|
$$
不断向下递推降阶即可。

还有其他性质：
- $|AB| \le |A||B|$
- $|A^{m}| \le |A|^{m}$
- 若 $|A| \le |B|$，则 $||A|| \le ||B||$

##### Theory
若 $|A| \le B$，则：
$$
\rho (A) \le \rho(|A|) \le  \rho(B)
$$
前面，我们已证：
$$
|A^{m}| \le |A|^{m} \quad 
$$
又因为 $|A| \le B$，因此
$$
|A|^{m} \le B^{m}
$$
也就是说：
$$
||A^{m}|| \le |||A|^{m}|| \le ||B^{m}|| 


$$
也就可以推出：
$$
||A^{m}||^{\frac{1}{m}}\le |||A|^{m}||^{\frac{1}{m}} \le ||B||^\frac{1}{m}
$$
又由于：
$$
\rho(A) = \lim_{k \rightarrow \infty} ||A^{k}||^{\frac{1}{k}}
$$
从而得证。

##### Theory
此外还可以证明：
$$
\min \sum_{j} a_{ij} \le \rho(A) \le \max \sum_{j} a_{ij}
$$
以及
$$
\min \sum_{j} a_{ij} \le \rho(A) \le \max \sum_{j} a_{ij}
$$
也就是说，谱半径的最大行（列）和就是上界；最小行（列）和就是下界

##### Lemma 
若 $A>0$，则 $\rho (A) \le ||\ |A|\ ||_{\infty}=\max_{i}\sum_{j}a_{ij}$，而且，$\rho (A) \le ||A||_{1} = \max_{j}\sum_{i}a_{ij}$ 
若 $A$ 的行和相等，则 $\rho (A) = ||A||_{\infty}$；若 $A$ 的列和相等，则 $\rho_{A} = ||A||_{1}$

根据谱半径的定义，显然可以得到：
$$
|\lambda| \le \rho(A) \le ||A||
$$

这里的证明，主要需要注意到，对于 $A$ 的行和相等的情况下，有一个特征值是 $A$ 的无穷范数

##### PF  
回到对于原定理的证明上来
设 $\alpha = $
==需要补充== 

这提供了一种快速估算谱半径的方法

##### Theory
对于任意向量 $x$ 和非负矩阵 $A$，我们有：
$$
\min_{n} \frac{1}{{x_{i}}} \sum_{j} a_{ij}x_{j} \le \rho(A) \le \max_{n} \frac{1}{x_{i}} \sum_{j} a_{ij} x_{j}  
$$
对各个列，也有类似的情况

## 正的矩阵

##### Thoery
若 $A$ 是正的，那么存在：
$$
Ax = \rho(A)x \quad y^{T}A = \rho(A) y
$$
且：
- $A$ 的谱半径必然大于 0
- $\rho(A)$ 是 $A$ 的代数重数为 1 的特征根
- 上面提到的 $x$ 满足 $\sum_{i}x_{i}=1$，且 $x$ 是正的

## 非负矩阵

##### Theory 
若 $A$ 是非负的，那么 $\rho(A)$ 是 $A$ 的一个特征值，且存在非负的非零向量使得
$$
Ax = \rho (A)x
$$
使得
$$
A(\epsilon) = A+\epsilon I_{n}
$$
且 $x(\epsilon)$ 是 $A(\epsilon)$ 的一个 Perron 向量，$x (\epsilon) >0$ 且 $\sum_{i}x_{i}= 1$，那么存在 $\epsilon_{k} \rightarrow 0$ 的单调序列，使得 $x (\epsilon) \rightarrow x$ 存在，那么
$$
\rho (A(\epsilon_{1})) > \rho (A(\epsilon_{2})) \cdots > \rho(A)
$$
又因为
$$
A(x) = \lim_{k \rightarrow \infty} A(\epsilon_{k})x(\epsilon_{k})  = \rho x
$$
因此 $\rho = \rho (A)$。

总之, 对于一个非负矩阵，其谱半径一定是特征值的上界  

## 状态转移矩阵
性质：每一行的行和都是 1，用来描述马氏链中的转移概率。其性质是
$$
Ae = e
$$
如果是 $e^{T} A= e$，则称为列随机矩阵

行、列上同时具有性质，则称为双随机矩阵