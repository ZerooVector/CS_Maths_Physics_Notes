#RL  

## 求解末端自由问题
最小化时间问题是一个典型的末端自由问题。这个问题可以被表述为：
$$
\min J = \int_{0}^{T} 1 dt 
$$
我们的约束是：
$$
s.t.\quad \dot x  = f(x,u) \quad x(T) = x_{goal}  \quad  u \in [u_{min},u_{max}]
$$
由于我们要离散地求解这个问题，所以一个小技巧是不改变节点的数量，而是改变积分器中的步长。从而，我们的动力学方程：
$$
x_{i+1} = f(x_{i},\tilde u_{i}) \quad   \tilde u_{i} = \begin{bmatrix}u_{i}\\h_{i}\end{bmatrix}
$$
同时，我们将缩放代价函数：
$$
J(x,u) = \sum_{i} h_{i} l(x_{i},u_{i}) + l_{N}(x_{N})
$$
由于涉及到时间的最小化，这个问题一定是非线性的！求解时注意限制步长 $h$ 的取值范围。

## 直接轨道优化 DTO
DTO 的基本思想是：将连续时间控制问题直接转化成非线性优化问题求解。也就是求解：
$$
\min_{x} f(x) \quad s.t. \ c(x) = 0 \ \ \ d(x) \le 0
$$
其中，$c (x) = 0$ 是动力学约束，$d(x)$ 是其他的约束。我们认为所有函数有二阶连续光滑导数。
常用的求解方法是序贯二次规划方法。这种方法将拉格朗日量进行二阶展开，将约束进行一阶展开，从而将问题转换为二次规划问题：
$$
\min_{\Delta x } f(x) + g^{T}\Delta x  + \frac{1}{2} \Delta x^{T} H \Delta x 
$$
$$
s.t. c(x) + C \Delta x  = 0\quad  d(x)  + D \Delta x  = 0
$$
其中 
$$
H = \frac{\partial^{2}L }{\partial x^{2}} ,g = \frac{\partial L}{\partial x} , C = \frac{\partial c}{\partial x }, D = \frac{\partial d}{\partial x}
$$
通过求解二次规划找到方向，然后使用线搜索即可。这个方法实际上类似于牛顿法。


##### Collocation Method
在之前，我们使用了显式格式：
$$
\dot x  = f(x,u)  \rightarrow x_{i+1}  = f(x_{i},u_{i})
$$
这使得我们可以进行前向递推，但是，现在，我们只需要将这些动力学方程作为等式约束来处理，我们不需要真的递推。我们只需要有：
$$
C(x_{i},u_{i},x_{i+1},u_{i+1}) = 0
$$
即可得到结果。在这里介绍的 Collocation Method 方法中，我们将轨迹表达为样条曲线。一般来说，我们使用三次样条插值处理轨迹，使用分段线性插值处理 $u(t)$ 。我们来介绍最经典的 DIRCOL 算法。
![[Pasted image 20231004171614.png]]
那么：
$$
x(t) = c_{0}+ c_{1} t + c_{2}t^{2} + c_{3}t^{3}
$$
显然有：
$$
\dot x(t) = c_{1} + 2c_{2}t + 3c_{3}t^{2} 
$$
把上面的东西写成矩阵形式：
![[Pasted image 20231004171918.png|400]]
你可以解析地求出这个矩阵的逆：
![[Pasted image 20231004172016.png|400]]

我们来关注中间的"Collocation Point"，根据三次样条插值和分段线性插值的结果：
$$
x_{i+\frac{1}{2}} = x\left(t_{i} + \frac{1}{2} h\right)= \frac{1}{2} (x_{i}+ x_{i+1} ) + \frac{h}{8}(\dot x_{i}-\dot x_{i+1} ) = \frac{1}{2}(x_{i} + x_{i+1}) + \frac{h}{8} (f(x_{i},u_{i}) - f(x_{i+1} ,u_{i+1}))
$$
$$
\dot x_{i + \frac{1}{2}} = -\frac{3}{2h} (x_{i} - x_{i-1}) - \frac{1}{h} (\dot x_{i} + \dot x_{i+1}) = -  \frac{3}{2h} (x_{i} - x_{i+1}) - \frac{1}{h} (f(x_{i},u_{i}) + f(x_{i+1},u_{i+1}))
$$
$$
u_{i + \frac{1}{2}} = u\left(t_{i} + \frac{h}{2}\right) = \frac{1}{2} (u_{i}+ u_{i+1} ) 
$$
我们可以写出动力学约束：
$$
C_{i}(x_{i},u_{i},x_{i+1} ,u_{i+1}) = f\left(x_{i + \frac{1}{2}} ,u_{i + \frac{1}{2}}\right)- \left(- \frac{3}{2h} \left(x_{i} - x_{i+1} \right)  - \frac{1}{h} (f(x_{i},u_{i})+ f(x_{i+1},u_{i+1}))\right)=0
$$
在每一步中，只有 $x_{i},u_{i}$ 是决策变量，$x_{i+1},u_{i+1}$ 并不是。这个步骤叫做"Hermite - Simpson"积分
这个做法的精度和 RK 3 差不多，但是更少地调用了动力学方程。由于 $f(x_{i=1},u_{i+1})$ 可以被重复使用，因此这个算法每推导一步实际上只需要调用两次动力学方程。


