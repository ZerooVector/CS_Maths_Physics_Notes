#MLorDS 

***非监督学习学的什么：是 Distribution（分布，也就是数据所包含的统计规律，之后就可以利用贝叶斯的方法将数据区分开），是 Associated Rule（关联规则，也就是挖掘不同事物之间的联系）***

## Clustering ：Learn the Distribution 
In the process of Clustering, we don't know the output, we only dividing the data into clusters according to the similarity between data, and we discovering interesting distributions. 

**三个关键问题：如何度量数据之间的相似性、如何将数据分成不同的几类、如何处理超大规模的或者高维的问题** 

### 度量数据间的相似性
- 最常见的做法是使用距离，距离需要满足：
	- $d (i, j) \ge 0$ 
	- $d (i, i) = 0$
	- $d (i, j) = d(j,i)$
	- $d (i, j) \le d (i, k) + d(k,j)$
常用的可能是 Euclidean , Hamilton, CHebyishev, Minkowski, etc.
- 其他的做法：夹角的余弦值

**实际上，聚类也是有目标的，你要通过搜索的方式找到最优的划分方法，从搜索的方式来看，分为暴力搜索和启发式搜索**

### 启发式聚类系列算法
采用启发式搜索的方式进行聚类的算法有：K-Means, K-medoids
两个算法只有很小的区别，但是它们的核心是相同的：采用 EM 算法，分为 E 步和 M 步。E 步上，要调整每一类的均值；M 步上，要去调节每个点分在哪一类。

#### K-Means
- 随机选择 $k$ 个数据作为每一个 Cluster 中数据的均值
- 将所有的数据划分到离它最近的一簇
- 更新均值
反复迭代以上步骤，直到结果稳定为止。

![[Pasted image 20230313104041.png|450]]

==作业：优化目标是什么？模糊 K-均值聚类又是什么？这需要你自己了解！== 
K-Means 有诸多优缺点：
- 复杂度很低：$O(tkn)$ 的线性复杂度
- 一定可以找到 Local Min，但是也有可能无法达到 Global Min
- 需要指定超参数：$K$ 
- 对于噪声点和初始值敏感！

##### Example : Bag of Visual Words（视觉词典）
- 将每个图象提取特征，然后聚合成 $k$ 类。通过判断图上的点落在哪一类的范围内，我们就可以通过一个 $k$ 维的向量来表征一个图像！
![[Pasted image 20230313105930.png|400]]




