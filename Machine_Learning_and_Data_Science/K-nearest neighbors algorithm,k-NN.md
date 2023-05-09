#MLorDS 
# 课前预习

## 基本思想和数学表述
K-NN 算法显然是一种分类算法，这种算法的思想很简单：对于查询点 $q$，找到样本数据 $X$ 中离 $q$ 点最近的 $k$ 个点，进行直接投票即可。从数学上，我们将询问点记为 $q$，预测的标签记为 $\hat y(q)$，那么，kNN 的任务是选择 $k$ 个邻居里面数量最多的那个：

$$
\hat y(q) = \arg \max_{C_k} \sum_{i\in k-NN(q))} I(y^{(i)} = C_k)
$$

## 可视化与结果分析
我们先考虑二分类时最简单的投票情况：
![[Pasted image 20230222162514.png|400]]

三分类的时候也是如此。对于图上的任何一点，我们询问时都可以得到它的类别，那么，一个类别占领一片领地，我们就可以画出决策边界：

![[Pasted image 20230222164727.png|400]]

这里涉及到参数模型/非参数模型的区别，参数模型在这里会试图把区域边界表示成某种简单的形式——直线，二次曲线, etc；但是，非参数模型不会这样做。例如，k-NN 显然是一个非参数模型。

K-NN 的超参数就是 $k$ 值，$k$ 值的大小将显著影响分类的结果！从决策边界来看，$k$ 值越大，决策边界越平滑，分类结果不容易受到局部噪声的影响
![[Pasted image 20230222165950.png]]

通常来说，$k-NN$ 的权重是等权的，使用下面的代码可以改变它的权重
```python
sklearn.neighbors.KNeighborsClassifier(weights = "distance")

# 下面是默认代码
sklearn.neighbors.KNeighborsClassifier(weights = "uniform")
```
此时，算法的优化目标是：
$$
\hat y(q) = \arg \max_{C_k} \sum_i w_iI(y^{(i)}= C_k)
$$
权重的一个计算方法是：
$$
w_i = \frac{\max(d_{NN})-d_i}{\max(d_{NN})-\min(d_{NN})}
$$

## 类似于 K-Means 的算法：最近质心分类
这个算法的思路相当简单：计算询问点到达每个数据中心的距离，离开最近的就是类别。数据质心的定义如下：
$$
\mu_k = \frac{1}{count(C_k)}\sum_{i \in C_k}x^{(i)T}
$$

你可以调用下面的代码来实现最近质心分类：
```python
sklearn.neighbors.NearestCentroid(shrink_thershold = )
```
收缩阈值是控制**样本质心向着总体质心收缩程度的参数**

![[Pasted image 20230222172543.png|400]]


# 如果讲到了，请在下面记笔记

