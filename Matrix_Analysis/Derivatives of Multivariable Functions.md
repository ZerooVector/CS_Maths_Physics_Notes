#MA 

## 一阶和二阶偏导
### 一阶偏导——梯度
函数的梯度定义为：
$$
\nabla f(x) = [\frac{\partial f(x)}{\partial x_1},\frac{\partial f(x)}{\partial x_2},\cdots,\frac{\partial f(x)}{\partial x_D}]^T
$$
特别地，作为例子，我们来推导二次型的梯度。我们仅仅使用一个简单的例子来演示：
$$
f(x_1,x_{2})= [x_1,x_{2}]\begin{bmatrix} 1 &2   \\ 3 & 4 \end{bmatrix}
\begin{bmatrix}x_1 \\ x_2\end{bmatrix}
$$
那么，将这个二次型展开
$$
\begin{align*}
f(x_1,x_{2}) &= [x_1+3x_{2},2x_{1}+4x_{2}]\begin{bmatrix}x_{1}\\
x_2\end{bmatrix}\\
&= x_{1}^{2}+3x_{1}x_{2}+2x_{1}x_{2}+4x_{2}^{2}
\end{align*}
$$
因此
$$
\frac{\partial f}{\partial x_{1}}=  2x_{1}+5x_{2} = 2x_1+5x_2
$$
$$
\frac{\partial f}{\partial x_{2}}= 3x_1+2x_{1}+8x_{2} = 5x_{1}+8x_{2}
$$
也就是说，梯度矩阵
$$
\nabla f(x_1,x_{2}) = \begin{bmatrix}2 & 5  \\ 5 & 8\end{bmatrix}
$$
容易注意到一个重要结论：
$$
\frac{\partial x^{T}Qx}{\partial x}= (Q+Q^{T})x
$$
梯度向量的方向，也就是函数值变化最快的方向：
![[Pasted image 20230308003454.png|400]]

### 二阶偏导：Hessian Matrix
![[Pasted image 20230308003109.png|400]]
位置 $(i,j)$ 上的元素就是 $f$ 先对 $x_i$ 求偏导，再对 $x_j$ 求偏导的结果。
对于二次型，也有重要结论：
$$
H(x^{T}Qx) = Q+Q^T
$$
## 几何角度：法向量
对于一个多元函数 $y  =f(x)$，我们可以将其写成等式的形式 $f (x)-y = 0$，令：
$$
F(x,y) = f(x)-y
$$
法向量的求法有结论：==但是不知道这个结论是怎么来的== ，曲面的法向量是：
$$
\nabla F(x,y) = [\nabla f(x),-1]^T
$$
直观上理解，当曲面的斜率无穷大时，这个法向量是“横着”的；当曲面的斜率为 0 时，这个法向量是竖直向下的。这个法向量在水平面上的投影就是梯度向量。
![[Pasted image 20230308004155.png|400]]

## 方向导数
方向导数用于求解在某一点上，沿着任意方向，函数的变化率。它的想法来源于一阶泰勒展开
$$
f(x_{1}+\Delta x_{1},x_{2}+\Delta x_{2})- f(x_{1},x_{2}) \approx \frac{\partial f(x)}{\partial x_{1}}\Delta x_{1}+\frac{\partial f(x)}{\partial x_{2}}\Delta x_{2}
$$
也就是说，
$$
\Delta f  \approx [\Delta x_{1} ,\Delta x_{2}][\frac{\partial f(x)}{\partial x_{1}},\frac{\partial f(x)}{\partial x_2}]^T
$$
这也就给出了任意方向上函数值的变化。我们还可以取 $[\Delta x_{1},\Delta x_{2}]  = [\cos \theta_{1},\cos \theta_{2}]$，使之成为单位向量。这个时候：
$$
\nabla_{v}f(x) = \nabla f(x)\cdot v = ||\nabla f(x)||\cos (\theta)
$$
![[Pasted image 20230308010257.png|300]]

## Taylor 展开
一个函数在某点处的泰勒展开，将由一次、二次、三次,... 曲面依次逼近，也就是说：
$$
f(x)\approx f(x_{p})+\nabla f(x_{p})^{T}(x-x_{p})+ \frac{1}{2}(x-x_{p})^{T}\nabla ^{2}f(x_{p})(x-x_{p})
$$
![[Pasted image 20230308010613.png]]

最后的最后，我们来补充一下曲面的切平面的求法。前面我们已经说过，曲面在 $x_{p}$ 点的法向量应当是 $[\nabla f(x_{p}),-1]$，我们只要知道从 $x_p$ 到切平面上任意一点 $x$ 的向量与法向量总是垂直，就能写出切平面的方程了。
