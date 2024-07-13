#Quantum_Mechanics 

先来谈谈规范变换。对于同一个场，它可以取的标势和矢势都有无穷多种。假定我们令一个场的势作如下变换：
$$
\phi' = \phi - \dfrac{1}{c} \dfrac{\partial }{\partial t} X \quad A' = A + \nabla X
$$
那么：
$$
\begin{align*}
E' &=  - \nabla  \phi ' - \dfrac{1}{c} \dfrac{\partial }{\partial t}A'\\
&= - \nabla  \left(\phi - \dfrac{1}{c} \dfrac{\partial }{\partial t}X\right) - \dfrac{1}{c} \dfrac{\partial }{\partial t}(A + \nabla X) \\
&= - \nabla  \Phi - \dfrac{1}{c} \dfrac{\partial }{\partial t}A + \dfrac{1}{c} \dfrac{\partial }{\partial t} \nabla X - \dfrac{1}{c} \dfrac{\partial }{\partial t} \nabla X\\
&= E
\end{align*}
$$
在磁场一边也容易做相似的验证。

我们介绍常用的库伦规范。在库伦规范中，我们要求：
$$
\nabla  \cdot A = 0 
$$
有时候，我们会再增加 $\phi = 0$ 的限制，这样的问题被称为“辐射规范”。

另一种规范被称为洛伦兹规范，它要求：
$$
\nabla \cdot A + \dfrac{1}{c} \dfrac{\partial }{\partial t} \phi = 0
$$
这是闵可夫斯基空间中的散度。

