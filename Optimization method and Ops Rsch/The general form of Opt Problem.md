#OPTandOR 

目标函数：
$$
\min f(x)
$$
约束条件：
$$
\begin{aligned}
s.t. \quad g_i(x)i\leq & 0 \quad i=1,2,...,n \\
h_j(x_j) = &0 \quad j = 1,2,...,n
\end{aligned}
$$
决策变量：
$$
var. \quad x_i
$$

不是标准形式的，需要先转化到标准形式，最大值/最小值可以用加负号的方式。
**这里必考** 

- 可行解：满足可行域和约束条件
- 最优解：
- 全局最优解：在全局上，有  $f (x^\star)<f(x)$
- 局部最优解：在 $||x-x^\star||<\delta$ 范围之内，有 $f (x^\star)<f(x)$
