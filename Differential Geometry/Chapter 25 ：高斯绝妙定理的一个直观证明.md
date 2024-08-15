#DifferentialGeometry 

我们会先从高斯漂亮定理入手：固定在曲面上的一个图形，如果改变曲面在空间中的形状，那么曲面上这个图形的球面像的面积不变。我们先明确一下记号：设 $n$ 是 $\mathcal{S}$ 的单位法向量，$\mathbb{S}^{2}$ 是单位球面，$n:\mathcal{S} \rightarrow \mathbb{S}^{2}$ 是球面映射。$\mathcal{K}_{ext}$ 表示外在曲率，也就是球面映射的放大倍数；$\mathcal{K}$ 表示内蕴曲率。$\mathcal{R}(L)$ 表示回路 $L$ 上的和乐性，而 $\mathcal{\tilde R}(\tilde L)$ 表示回路 $\tilde L$ 上的和乐性。我们已知的事实包括：
$$
\iint_{\Omega} \kappa_{1} \kappa_{2} d \mathcal{A} = \mathcal{K}_{ext}(\Omega) = \mathcal{ \tilde A}(\tilde \Omega)=  \mathcal{ \tilde R}(\tilde L)
$$
现在我们来看一个重要的事实：之前我们说过，平行移动的一种外在构造方式是“一边移动，一边向切平面投影”。考虑向量 $w$ 在 $\mathcal{S}$ 上从 $p$ 移动到 $p+\epsilon$，再向 $T_{p+\epsilon}$ 投影，得到 $w'$ 的过程；与向量 $w$ 在 $\mathbb{S}^{2}$ 上从 $n(p)$ 移动到 $n(p+\epsilon)$，再向 $T_{n(p+\epsilon)}$ 投影，得到 $w''$ 的过程。由于 $T_{p+\epsilon}$ 和 $T_{n(p+\epsilon)}$ 完全一样，所以 $w'$ 和 $w''$ 完全相同。换言之：**球面映射保持平行移动不变**。也就是说，当曲面 $\mathcal{S}$ 的切向量沿着 $L$ 凭心不给移动生成了在 $p$ 处的向量 $w_{\parallel}$ 时，$n(p)$ 处的同一个向量 $w_{\parallel}$ 也是自动由 $\mathbb{S}^{2}$ 的切向量沿着 $\tilde L = n(L)$ 做平行移动生成的向量。从而我们可以延长一下上面的等式：
$$
\mathcal{\tilde R}(\tilde L) =\ \mathcal{R}(L)
$$
由于 $\mathcal{R}(L)$ 是曲面的内蕴几何性质，在等距变换下保持不变，因此 $\mathcal{\tilde A}(\tilde \Omega)$ 也不变。我们证明了高斯漂亮定理。只要将 $\Omega$ 缩小到一个点，我们立刻可以论证绝妙定理，也就是 $\mathcal{K}_{ext} = \kappa_{1} \kappa_{2}$ 的不变性。换言之：
$$
\kappa_{1} \kappa_{2}= \lim_{\Delta_{p} \rightarrow  p} \dfrac{\mathcal{R}(\Delta_{p})}{\mathcal{A}(\Delta _{p})} =  K(p)
$$
（这里利用了 $\mathcal{R}$ 和 $\mathcal{E}$ 的关系。）

换言之，我们原来知道 $\kappa_{1} \kappa_{2}$ 和 $\mathbb{S}^{2}$ 上的面积/角盈/和乐性有关系，现在我们知道球面映射保持平行移动不变，就在 $\mathcal{S}$ 的和乐性（内蕴性质）与 $\mathbb{S}^{2}$ 的和乐性之间建起了桥梁。