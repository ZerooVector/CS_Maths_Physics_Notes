#CV 

- 一种最简单的图像分类器是 KNN 分类器
![[Pasted image 20230926203908.png]]
这种方式有很多问题，例如，若数据集中有 $N$ 张样本，那么预测的时间复杂度是 $O(N)$ 的
此外，用范数获得的距离并不能很好地描述图像的视觉差距；这个方法还要求数据点必须均匀地分布在整个空间中，否则一个图像的附近可能几乎没有点，严重影响效果。


