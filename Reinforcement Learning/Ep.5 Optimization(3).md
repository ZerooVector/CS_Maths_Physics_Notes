#RL 

## 不等式约束的最优化问题
我们继续来聊不等式约束的最优化问题。考虑：
$$
\min f(x) \qquad s.t. c(x) \le 0 
$$
它的 KKT 条件是：
$$
\nabla f  + (\frac{\partial c}{\partial x})^{T} \lambda = 0 
$$
$$
c(x) \le 0 
$$
$$
\lambda \ge 0 
$$
$$
\lambda \odot c(x) = 0 
$$
我们可以来看一些小细节，例如，如果我们限制 $c (x) \ge 0$，那么目标函数中拉格朗日乘子那一项会变成负号（注意：这一项起到类似于惩罚项的作用）；或者，我们可以限制 $\lambda \le 0$。

我们求解优化问题的方法分为两种：
- Active-Set Methods：猜测哪些约束是激活的，哪些未被激活，然后求解等式约束问题。这种方法其实不常用，因为你需要很好地猜测那些约束是被激活的。
- Barrier / Interior-Point Methods：使用一个对数罚函数来替换那些约束，使得目标函数在边界上变成无穷大，从而阻止我们越过这些边界。这对于求解凸规划问题非常有用。
- Penalty Function Method：使用一个惩罚函数：
$$
\min_{x}f(x) + \frac{p}{2} [\max(0,c(x))]^{2}
$$
**注意：内点法严格限制求解过程中决策变量不能越过边界，罚函数法则允许求解过程中轻微越过边界，再拉回来** 
罚函数法易于实施，但是效果可能不好，这是因为过大的惩罚项可能把目标函数“盖住，因此它达不到太高精度。

### Argumented Lagrangian Method（增广拉格朗日方法）
这个方法就是在罚函数法上增加了一个拉格朗日乘子。我们将目标函数函数写为：
$$
\min f(x) + \tilde \lambda ^{T }c(x)+ \frac{p}{2} [\max(0,c(x))]^{2}
$$
后面这一部分被称为“增广拉格朗日乘子”。我们求导：
$$
\frac{\partial f}{\partial x} + \tilde \lambda \frac{\partial c}{\partial x} + p c(x)^{T }+ \frac{\partial c}{\partial x} + \frac{\partial c}{\partial x} = \frac{\partial f}{\partial x} +[\tilde \lambda  + p c(x)]^{T } \frac{\partial c}{\partial x} =  0
$$
那么我们更新 $\lambda$：
$$
\tilde \lambda \leftarrow   \tilde \lambda + pc(x) 
$$
通过把惩罚项放进约束函数，我们可以强制要求约束得到满足。为了增强效果，我们还可以改变 $p$：
$$
p \leftarrow \alpha p  \quad (\alpha > 1)
$$
这个方法在非凸的问题上效果很好。在这种不断增加惩罚系数的方式下，我们会把当前解逼到可行域内。

### 二次规划问题
一个二次规划问题可以被表述为：
$$
\min \frac{1}{2} x^{T}Qx  + q^T x 
$$
$$
s.t. \  Ax \le b \  ;\ Cx = d
$$

### 有约束情况下的正则化、对偶方法
我们考虑这样的问题：
$$
\min f(x)
$$
$$
s.t. \  c(x) = 0
$$
我们使用罚函数法来解决这个问题：
$$
\min_{x} f(x) + P_{\infty}(c(x))
$$
其中，$P_{\infty}(\cdot )$ 将 0 映射到 0，将非 0 的数值映射到无穷大。这样的方法在实践中效果很差，但是我们可以找到等效的方法：
$$
\min_{x} \max_{\lambda} f(x) + \lambda^{T} c(x)
$$
那么在任何 $c (x) \not = 0$ 的时候，内层函数将走向无穷大，只有在可行域内，此函数才有限。对于不等式约束，只需限制 $\lambda \ge  0$ 即可。
那么，KKT 条件实际上是在 $(x,\lambda)$ 张成的空间中定义了一个鞍点，并且，我们期望最优解位置上的 Hessian 矩阵有 $\mathrm{dim}(x)$ 个正的本征值和 $\mathrm{dim}(\lambda)$ 个负的本征值（**这里个人的理解是：你希望目标函数变小，因此与 $x$ 对应的本征值应该为正，这确保了问题的凸性；但是剩下一半是为什么？这需要仔细查看 KKT 问题的二阶条件**）
因此，在求解 KKT 系统时，我们常用的一种正则化方法是如下改写 Hessian 矩阵：
$$
\begin{bmatrix}H + \beta I & C^{T} \\ C & - \beta I\end{bmatrix}
$$
这种做法仍然会越过最优点，因此我们需要 Line Search 

### Line Search, Merit Function
在进行 Line Search 的时候，我们有一个叫做 Merit Function 的技术，它用来度量我们当前的解到约束条件的距离。例如，我们的约束条件是 $c (x) \le 0$，我们可以定义：
$$
P(x) = \frac{1}{2} ||c(x)||_{2}
$$
那么我们令 $\alpha = 1$，作为初始步长参数，我们要求：
$$
P(x + \alpha \Delta x) < P(x) + b  [\nabla P(x)]^{T} \alpha   \Delta x
$$

否则我们就要回溯！这确保我们不会非常远离约束条件

### 考虑完全的情况
我们将不等式约束和等式约束放在一起看：
$$
L(x,\lambda,\mu) = f(x) + \lambda^{T} c(x) + \mu^{T} d(x)
$$
我们仍然可以定义
$$
P(\lambda,x,\mu) = \frac{1}{2} ||r(x,\lambda,\mu)||^{2}_{2}
$$
这个 Merit Funtion 可以随意定义。你只需要组合 $f$ 和 $c,d$ 即可。这是工程上的事情，此处我们不再继续讨论。



