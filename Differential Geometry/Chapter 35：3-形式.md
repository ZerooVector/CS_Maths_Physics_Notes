#DifferentialGeometry 

我们之前已经说过，3-形式是一个完全反对称的 $(0,3)$ 阶张量 $\Xi_{ijk} = \Xi(e_{i},e_{j},e_{k})$。显然，价格三个 1-形式张量积起来是不能得到 3-形式的，为了得到它，我们考虑一个 2-形式与一个 1-形式的楔积，这需要我们推广楔积的定义。注意到一个合理的定义是：
$$
(\Psi \wedge \sigma)(v_{1},v_{2},v_{3}) = \Psi(v_{1},v_{2})\sigma(v_{3}) - [\Psi(v_{1},v_{3})\sigma(v_{2} ) - \Psi(v_{2},v_{3})\sigma(v_{1})]
$$
对于 $(\sigma\wedge \Psi)$，定义是类似的。尽管 3-形式是完全反对陈的，但是根据定义，一个 2-形式和一个 1-形式的楔积却对称：
$$
\Psi \wedge \sigma = \sigma\wedge \Psi 
$$
在一般的情况下，若 $\Psi$ 是 $p$ -形式，而 $\Omega$ 是 $q$ -形式，那么我们有：
$$
\Psi \wedge \Omega = (-1)^{p+q}   \Omega  \wedge \Psi 
$$
这很容易通过将 $\Psi,\Omega$ 展开，并将 $\Psi$ 中的 1-形式一个个地移动到表达式右侧完成。

我们现在定义体积 3-形式：
$$
\mathcal{V} = (\mathbf{d} x^{1} \wedge  \mathbf{d}x^{2}) \wedge \mathbf{d}x^{3}
$$
为什么被称为“体积 3-形式”？因为考虑三维空间中 $u, v, \underline{\Omega}$ 生成的平行六面体：
$$
\begin{align*}
\mathcal{V}(u,v ,\underline{\Omega}) &= (\mathbf{d}x^{1} \wedge \mathbf{d}x^{2}) (u,v) \mathbf{d}x^{3}(\underline{\Omega}) + (\mathbf{d}x^{1} \wedge \mathbf{d}x^{2}) (v,\underline{\Omega}) \mathbf{d}x^{3}(u) + (\mathbf{d}x^{1} \wedge \mathbf{d}x^{2}) (\underline{\Omega},u) \mathbf{d}x^{3}(v) \\
&= \Omega^{1}(u^{2}v^{3} - u^{3}v^{2}) + \Omega^{2}(u^{3}v^{1} - u^{1}v^{2}) + \Omega^{3}(u^{1}v^{2} - u^{2} v^{1})\\
 &= \Omega(u,v)
\end{align*}
$$
注意：三个 1-形式的楔积服从结合律，因此你可以将体积 3-形式写成别的写法。

上面我们推过极坐标中的体积 3-形式，同理，我们可以推出球坐标中的体积 3-形式：
$$
\mathbf{d}x \wedge \mathbf{d}y \wedge \mathbf{d}z = r^{2} \sin \phi  \mathbf{d}r \wedge  \mathbf{d}\phi \wedge  \mathbf{d} \theta
$$
只要给这个 3-形式输入三个分别沿着 $e_{r}, e_{\theta}, e_{\phi}$ 的向量，它就退回到一般的极坐标面积微元写法。

现在我们考虑 $p$ 个 1-形式的楔积。$p$ 个 1-形式可以将一个向量 $v$ 映射到 $\mathbb{ R}^{p}$ 中的向量 $w_{i}$，我们将这 $p$ 个 1-形式的楔积就定义为 $w_{1},\cdots ,w_{p}$ 这个区域的体积算子：
$$
[\sigma_{1} \wedge \cdots  \wedge  \sigma_{p}](v_{1},\cdots ,v_{p}) =  \det [F(v_{1}) \cdots F(v_{p})]
$$
如何把向量抽离出来，只观察 1-形式本身的形式？这还是要用到张量积。我们这里直接给出结论：$p$ 个 1-形式的楔积是所有偶排列的张量积之和减去所有奇排列的张量积之和。

现在我们给出 3-形式的基底。显然，它的基底应该是 $\{\mathbf{d}x^{i}\wedge \mathbf{d}x^{j} \wedge \mathbf{d}x^{k}\}$。在三维空间中只有一个基底，也就是所谓体积 3-形式；而在四维空间中则有四个基底。

