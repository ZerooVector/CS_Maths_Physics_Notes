#NLP 

## 任务简介：命名实体识别 (NER)
一个非常原始的命名实体识别算法是使用逻辑回归。我们在文章中放置一个滑动窗口，将窗口中词的词向量拼接起来，然后进行逻辑回归。这是一个极其简单的神经网络。

## 数学回顾
- 多输入多输出函数的梯度：Jacobian 矩阵
$$
\begin{bmatrix}\frac{\partial f_{1}}{\partial x_{1}} & \cdots & \frac{\partial f_{1}}{\partial x_{n}}  \\  \cdots  & \cdots & \cdots   \\  \frac{\partial f_{m}}{\partial x_{1}} & \cdots & \frac{\partial f_{m}}{\partial x_{n}} \end{bmatrix}
$$
我们记作：
$$
\frac{\partial \mathbf{f}}{\partial \mathbf{x}} = \frac{\partial f_{i}}{\partial x_{j}}
$$
Jacobian 矩阵可以使用链式法则：
$$
\mathbf{h} = f(\mathbf{z}), \ \mathbf{z } = g(\mathbf{x})
$$
那么我们有：
$$
\frac{\partial \mathbf{h}}{\partial \mathbf{x}} = \frac{\partial \mathbf{h}}{\partial \mathbf{z}} \frac{\partial \mathbf{z}}{\partial \mathbf{x}}
$$
![[Pasted image 20230924231045.png|400]]

假定我们有一个简单的逻辑回归模型：
$$
h = f(z)\quad z = Wx + b \quad s = u^{T}h 
$$
让我们计算梯度：
$$
\frac{\partial s}{\partial b} = \frac{\partial s}{\partial h} \frac{\partial h}{\partial z}\frac{\partial z}{\partial b} = u^{T}\mathrm{diag}(f'(z)) I = u^{T}\odot f'(z)
$$
或者（注意到我们可以避免一些重复运算）：
$$
\frac{\partial s}{\partial W} = \frac{\partial s}{\partial h}\frac{\partial h}{\partial z}\frac{\partial z}{\partial W} = \delta \frac{\partial z}{\partial W} = \delta^{T} x^{T} 
$$

## 深度学习框架中的反向传播
深度学习中用一张有向图来建模这个神经网络，其中，源点是输入，其余的节点是算符。我们沿着计算图正向传播，就能得到计算结果。如果沿着连边反向传播，我们就得到了梯度。
![[Pasted image 20230926143156.png]]
例如，我们考虑图中的 $f$ 节点，我们将 $\frac{\partial s}{\partial h}$ 称为“上游梯度”, 将 $\frac{\partial s}{\partial z}$ 称为“下游梯度”，将 $\frac{\partial h}{\partial z}$ 称为“本地梯度”
显然，它们之间应该满足关系：
$$
\frac{\partial s }{\partial z} = \frac{\partial s}{\partial h}\frac{\partial h}{\partial z}
$$
对于多入多出的神经元（例如，带有权重和偏置），做法也是一样的。
估计梯度时，我们一般使用中心差分格式：
$$
f'(x) = \frac{f(x+h ) - f(x-h)}{2h}
$$




