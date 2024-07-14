#NLP 

在本节课中，我们提升难度。我们来看依存句法分析任务。
我们知道，语言是有结构的。语言的最小单位是词汇（这里以英语为例），词汇可以组成短语，短语又可以拼接成更大的短语。在语言学中，对于语言的结构有两种不同的理解：
- Context - Free Grammar/Phrase structure Grammar ： 认为短语结构将每个词与其附近的词组织在一起
- Dependency Structure ： 展示每个词依赖于哪些其他词
在 NLP 中，我们通常使用的是第二种。显然，在第二种模式下，理解需要语言需要清楚地认识到每个词正在“修饰”什么，因此我们的模型也必须理解这一点。

