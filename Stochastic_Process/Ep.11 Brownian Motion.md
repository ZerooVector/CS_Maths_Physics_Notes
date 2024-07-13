#StochasticProcess 

在本节中，我们将使用我们之前对随机过程的认知，来研究布朗运动。

我们先给出布朗运动的一些定义：
- 随机过程 $B (0) = 0$，具有独立增量，增量服从高斯分布 $B (t) -B (s) \sim N(0,\sigma^{2}(t-s))$，样本轨道连续。
- 随机过程 $B(0)=0$，是高斯过程，$\mathrm{E}(B(t))=0$，$R_{X}(t,s) = \sigma^{2} \min(t,s)$ ，样本轨道连续。
- 随机过程 $B(0)=0$，$\mathrm{E}(B (0)) =0$，独立且平稳增量， $R_{X}(t,s) = \sigma^{2} \min(t,s)$，样本轨道连续。（注意：独立且平稳增量的随机过程我们只会给出两种：高斯过程和泊松过程。它们的差异只体现在样本轨道是否连续。）

我们现在来做一件事情：从定义（1）中推出布朗运动是高斯过程。也就是 $\forall n,\forall t_{1},\cdots ,t_{n}$，我们希望 $(B (t_{1}),\cdots ,B(t_{n}))^{T} \sim N$。它显然可以通过 $(B(t_{1}),B(t_{2}) - B(t_{1}),\cdots ,B(t_{n}) - B(t_{n-1}))$ 经由线性变换得到。显然我们完成了推理。

## 布朗运动的基本性质
### 真·基本性质
如果 $B(t)$ 是标准布朗运动（$\sigma^{2}=1$），已知 $\mathrm{E}(B (t)) = 0 ,\mathrm{Var}(B (t)) = t$。

假设 $B(t)=x_{0}$，那么 $\mathrm{E}(B (t+s)|B(t)) = x_{0}$ 。这容易证明：
$$
\begin{align*}
\mathrm{E}(B(t+s)|B(t))\\
&= \mathrm{E}(B(t+s) - B(t) + B(t)|B(t))\\
&= \mathrm{E}(B(t+s) - B(t)) + \mathrm{E}(B(t)|B(t))\\
&= x_{0} 
\end{align*}
$$
由于 $B(t)$ 独立增量，我们将已知的部分和未知的部分分开，很容易得到结论。
满足这种特性（“赌场公平性”）的随机过程，我们称作鞅（Martingale）, 在一个鞅上显然是没有套利机会的。

接下来我们算个数作为例子。假设 $B(2)=4$，求 $B(4)>5$ 的概率。这个问题可以直接套用前面的高斯分布的条件均值、条件方差来解决。但是那个计算相当繁琐，注意到：
$$
B(4) = B(4)-B(2)+B(2)
$$
显然可以得到：
$$
B(4) \sim N(4,2)
$$
从而：
$$
P(B(4)>5|B(2)=4) = \dfrac{1}{\sqrt{2\pi}\sqrt 2} \int_{5}^{\infty} \exp\left(-\dfrac{(t-4)^{2}}{4}\right)dt
$$

### 从布朗运动构造其他的随机过程
假定 $B(t)$ 是布朗运动，那么尺度变换之后的 $\dfrac{1}{c} B (c^{2}t) =Y(t)$ 是否是布朗运动？
我们这里试着使用第二条定义验证。我们首先需要验证 $Y(t)$ 是高斯过程！显然
$$
\dfrac{1}{c} (B(c^{2}t_{1}),\cdots B(c^{2}t_{n}))
$$
是联合高斯分布的。得证。其次再检证它的相关函数：
$$
\begin{align*}
\mathrm{E}(Y(t)Y(s))\\
&= \dfrac{1}{c^{2}} \mathrm{E}(B(c^{2}t) B(c^{2}s))\\
&= \dfrac{1}{c^{2}} \min(c^{2}t,c^{2}s)\\
&= \min(t,s)
\end{align*}
$$

再给出一个操作：$Y (t) = t B(\dfrac{1}{t}),Y(0)=0$ ，问 $Y(t)$ 是否是布朗运动？
这里用到我们之前提到的高斯过程的“冷门”判据：一组随机变量服从联合高斯，那么它们的任意线性组合服从一维高斯。那么我们考虑：
$$
\sum_{i} \lambda_{i} t_{i} B(\dfrac{1}{t_{i}})
$$
这显然服从一维高斯分布。（注意跟 $\dfrac{1}{t}$ 没关系，取出来一个时间点只是取出一个高斯分布随机变量）接着验证相关函数：
$$
\begin{align*}
\mathrm{E}(Y(t)Y(s))\\
&= \mathrm{E}\left(ts B\left(\dfrac{1}{t}\right) B(\dfrac{1}{s})\right)\\
&= ts\min(\dfrac{1}{t},\dfrac{1}{s})\\\\
&= \min(t,s)
\end{align*}
$$
因此，“时间反转”之后，布朗运动依然是布朗运动！


### 布朗运动的最大值与首达时间
接下来介绍 Levy 的一个工作。令：
$$
M(t) = \max_{0 \le s \le t} B(s)
$$
构成一个新的随机过程。我们现在希望给出这个随机过程的分布。Levy 的解决方案是考虑 $T_{x}$，即布朗运动第一次“击中” $x$ 处的时间（首达时间）：
$$
T_{x} = \min\{s|B(s) = x\}
$$
我们给出如下的计算：
$$
\begin{align*}
P(M(t)>x) &= P(T_{x}<t)
\end{align*}
$$
我们现在研究 $B (t) > x$ 这一事件。假定 $B(T_{x})=x$ 已经发生过，从而：
$$
B(t) = B(t) - B(T_{x}) +B(T_{x}) = B(t) -B(T_{x})+x
$$
而 $B (t) - B(T_{x})$ 是一个零均值高斯变量。从而完成下面的计算：
$$
\begin{align*}
P(B(t) > x) &=  P(B(t)>x|T_{x}<t ) P(T_{x} < t) + P(B(t)>x|T_{x}>t)P(T_{x}>t)\\
&= P(B(t)>x|T_{x}<t ) P(T_{x} < t)\\
&= \dfrac{1}{2} P(T_{x}<t)
\end{align*}
$$
从而我们直接得到：
$$
F_{T_{x}}(t) = P(T_{x}<t) = 2 P(B(t) >x)
$$
代入 $B(t)$ 的高斯分布结果即可。我们已经求出了 $M(t)$ 的分布：
$$
P(M(t) > x) = 2 P(B(t)>x)
$$

### 二次变差
接下来我们考虑一个来自维纳的结果。假设我们有一个布朗运动 $B (t)\sim N(0,t)$，那么显然有 $\mathrm{E}(B^{2} (t)) = t$。我们发现方差是线性地随着时间增大的，我们要从两个角度说明这件事情。假定我们现在给出 $[0,t]$ 的一个划分：$\left(0,\dfrac{t}{n},\dfrac{2t}{n} ,\cdots ,\dfrac{n-1}{n}t,t\right)$，从而形成布朗运动的 $n$ 个增量 $\Delta B\left(\dfrac{k}{n}\right)= B\left (\dfrac{k}{n}t\right)- B\left(\dfrac{k-1}{n}t\right)$。我们要来计算 $\sum_{k}\left(\Delta B\left(\dfrac{k}{n}\right)\right)^{2}$，并说明其在 $n \rightarrow \infty$ 均方收敛到 $t$。注意到 $\Delta B$ 在平方后加起来才有界，那么没平方的时候加起来是不收敛的（注意：这使得我们无法使用正常的微积分）。现在开始我们的计算：
$$
\begin{align*}
\mathrm{E}\left(\sum_{k=1}^{n} \left(\Delta B\left(\dfrac{k}{n}\right)\right)^{2} -t  \right)^{2} \\
&= \mathrm{E}\left(\sum_{k}  \left(\Delta B\left(\dfrac{k}{n}\right)\right)^{2} - \sum _{k}\dfrac{t}{n}\right)^{2}\\
&= \mathrm{E}\left(\sum_{k}\left(\left(\Delta B\left(\dfrac{k}{n}\right)\right)^{2} - \dfrac{t}{n}\right)\right)^{2}\\
&= \sum_{k} \mathrm{E}\left((\Delta B)^{2}-\dfrac{t}{n}\right)^{2} + \sum_{i \not=j}\mathrm{E}( \left((\Delta B)^{2}-\dfrac{t}{n}\right)\left((\Delta B)^{2}-\dfrac{t}{n}\right))\\
&=  \sum_{k} \mathrm{E}\left((\Delta B)^{2}-\dfrac{t}{n}\right)^{2} \quad \text{注意：交叉项那边很容易消去}\\
&= \sum_{k} \mathrm{E} \left((\Delta B)^{4}\right ) -2 \mathrm{E}((\Delta B)^{2} \dfrac{t}{n} )) + \left(\dfrac{t}{n}\right)^{2}\\
&= \sum_{k} \mathrm{E} \left((\Delta B)^{4}\right)- \left(\dfrac{t}{n}\right)^{2}\\
&= \sum_{k} 3\left(\dfrac{t}{n}\right)^{2} - \left(\dfrac{t}{n}\right)^{2} \\
&= \sum_{k} 2\left(\dfrac{t}{n}\right)^{2}\\
&= 2 \dfrac{t^{2}}{n} \rightarrow 0
\end{align*}
$$
从而完成了证明。

## 随机微积分
### 伊藤公式
我们希望看一看这会在微积分上产生什么样的变化。假设我们有函数 $g(t,B(t))$，我们希望求出它对时间的一阶导数：
$$
dg(t,B(t)) = \dfrac{\partial g}{\partial t}dt + \dfrac{\partial g}{\partial B}dB
$$
是这样吗？还能这样吗？这是不对的。直观上来看，$dB$ 是一个“半阶小量”。而我们在做一阶微分的时候，我们必须把一阶量暴露出来！那么，我们需要建立一套新的微积分体系，这套体系称为随机微积分。
我们重新做这个微分 （利用上面二阶变差求解过程中的步骤）：
$$
\begin{align*}
dg &= \dfrac{\partial g}{\partial t}dt + \dfrac{\partial g}{\partial B}dB + \dfrac{1}{2}\dfrac{\partial^{2} g}{\partial B^{2}} (dB)^{2}\\
&=\dfrac{\partial g}{\partial t}dt + \dfrac{\partial g}{\partial B}dB + \dfrac{1}{2}\dfrac{\partial^{2} g}{\partial B^{2}} dt 
\end{align*}
$$
我们将这个公式称为伊藤公式，在金融工程中有重要应用！
我们利用它一下：求积分 $\int_{0}^{1} B(t)dt$。注意：
$$
d\left(\dfrac{1}{2} B^{2}(t)\right)= B(t) dB(t) + \dfrac{1}{2} \cdot 1 \cdot dt 
$$
从而，这个积分被修正到：
$$
\int_{0}^{1} B(t) dt = \dfrac{1}{2} B^{2}(t) |_{0}^{1} - \dfrac{1}{2} t|_{0}^{1} = \dfrac{1}{2}B^{2}(1)-\dfrac{1}{2}
$$

### 期权定价模型
人们很早就注意到了股票价格和布朗运动之间的联系。之后，著名经济学家萨缪尔森使用几何布朗运动为股票价格进行了建模：
$$
S(t) = \exp( \mu t + B(t))
$$
这样，它防止了股票价格小于 $0$，同时也加入了一个线性项（趋势项）。
在 1970 年，Black-Scholes-Merton 专门研究金融衍生品，衍生品的价格是股票价格与时间的某个函数 $V = V(t,S(t))$。
现在假定股票期权的价格为 $V$，我在做多一份看涨期权的同时，做空 $\alpha$ 份股票来进行对冲。我的投资组合的价值为 $V (t, S (t)) - \alpha S (t) = P(t)$，我们希望 $dP (t) = rP \cdot dt$，其中 $r$是银行利率。通过这样的方式，我们就可以确定期权的价格。
我们来做这个微分：
$$
dS = S\left(\mu dt + dB + \dfrac{1}{2}dt \right)\Rightarrow (dS)^{2}= S^{2}dt 
$$
$$
\begin{align*}
dP(t) &= dV(t,S(t)) - \alpha dS(t) \\
&= \dfrac{\partial V}{\partial t}dt + \dfrac{\partial V}{\partial S} dS + \dfrac{1}{2} (dS)^{2}- \alpha dS(t)\\
&= \dfrac{\partial V}{\partial t}dt + \dfrac{\partial V}{\partial S} dS +  \dfrac{1}{2} S^{2}dt - \alpha dS(t) \\
&= r (V - \alpha S) dt
\end{align*}
$$
我们需要对冲掉所有的不确定性，因此我们会使得上式中的 $dS$ 全部消去：
$$
\alpha = \dfrac{\partial V}{\partial S}
$$
这就是我们所采用的对冲策略。将这个策略代入后整理上式：
$$
\dfrac{\partial V}{\partial t} + \dfrac{1}{2}S^{2}\dfrac{\partial^{2} V}{\partial S^{2}} +  r \cdot S \cdot  \dfrac{\partial V}{\partial S} - rV=0
$$
这就是 BSM 期权定价方程。该方程在 1997 年被提出。










