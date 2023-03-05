#Research #KD 

目的：将大模型简化，以便部署在终端，进行实时的边缘计算
一些可能的库：模型压缩库 MMRazor: Pruning, KD, 神经架构搜索、量化
MMDeploy: 模型部署库
Github. Com/Hobbitlong/RepDistiller

这篇笔记来自*Distilling the knowledge in a neural network*

## Introduction
如何定义知识？一定不是指模型中的权重，因为这样我们根本无法改变模型的结构。我们认为，模型输出值之间的相对大小（正确类别和错误类别的相对大小）已经包含了知识。