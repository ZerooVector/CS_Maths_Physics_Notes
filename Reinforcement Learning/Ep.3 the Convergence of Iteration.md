#RL 

首先我们说明，在 Infinite Horizon 的情况下，Bellman Equation 退化为一个线性方程组：
$$
V(s) = R(s,\pi(s)) + \gamma_{s'}P(s'|s,\pi(s)) V(s)
$$
这里我们固定了 $a$，我们可以进行策略评估，以评估我们固定的这个策略有多好（我们暂时不考虑“最大化”这个操作）。所以，我们的求解过程是迭代求出方程不动点的过程。这个方程可以简化地写为：
$$
V = R +\gamma TV 
$$
由于 $T$ 经常欠秩，所以我们一般不会直接求解这个线性方程组。而且时间复杂度非常高。

##### 引理 1
我们将
$$
H(V) = R + \gamma T V 
$$
称为“策略评估算子”。我们想要证明这个算符是一个压缩映射，也就是说：
$$
||H(V') - H(V) ||  \le a ||V ' - V || \quad a \in [0,1] 
$$
这显然得证。
引理 1 保证了经过算子 $H$ 的一次映射之后，空间中的两个点之间的距离必然缩小。这确保了上面的策略评估方程有唯一不动点。

##### 定理 1 
$$
\lim_{n \rightarrow \infty} H^{(n)} (V) = V^\pi
$$
证明的关键在于我们首先要任意利用上式指定一个不动点，此后证明任意一点趋向于不动点即可。

##### 定理 2 
显然，若
$$
||H^{(n)} (V) - H^{(n-1)}(V) || \le \epsilon 
$$
那么：
$$
||H^{(n)}(V)  - V^{\star} || \le \dfrac{\epsilon}{1-\gamma }
$$

仿照我们上文在策略评估过程中对于 $H$ 的定义，我们可以在值迭代过程中定义 Bellman 算符：
$$
H^{\star}  (V) =  \max_{a} R + \gamma T V 
$$
可以类似地证明，$H^\star$ 是压缩映射
