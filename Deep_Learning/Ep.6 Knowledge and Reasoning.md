#DL 

在这一部分中，我们要求 AI 具有**推理**的能力：**Ability and Process of making decision based on facts and knowledge.**
- 我们主要需要讨论：推理的机理和策略
- 推理的机理：
	- 从逻辑上来说：归纳式 (Induction)、演绎式 (Deduction)
	- 从推理是否确定来说：确定性的 (Certainty)、不确定的 (Uncertainty)
	- 单调性的和非单调性的（推理的后续结论会推翻之前的结论吗？传统逻辑中进行的推理都是单调推理，因为新的知识必须与旧有的知识相匹配）
- 推理的策略：
	- 事实到结论、结论到事实、双向推理
	- 冲突消解 (Conflict Resolution)
	- 搜索的策略

## Production Rule and System （生成式规则和系统）
在这种推理系统中，我们需要存储既定的事实和规则、以及一个推断系统。我们从一个事实出发，使用相应的规则进行推演，推导出更多的事实，从而启动更多的规则进行推理，直到达到停止条件为止。
![[Pasted image 20230424102910.png|400]]

我们通常使用四元组 (Quaternion)来表达一条断言 (Proposition)：
例如，"Snow is White"可以被表达为 *Attribute, object, value, certification factor* 的形式，也就是*Color, Snow, White ,0.99*
或者，四元组表达两个事物之间的关系 *Relation, Object 1, Object 2, Certification factor* 

我们使用*IF THEN, C*F式的语句表达一条规则。例如
*IF An animal has sharp teeth THEN it's carnivore , 0.8*

基于以上两点，我们可以进行推理。一个典型的生成式规则和系统如下：
![[Pasted image 20230424103651.png|400]]


## First Order Logic（一阶逻辑）
>Logics are formal languages for representing information such that conclusions can be drawn, can be used as a tool for knowledge representation and reasoning.

- Propositional Logic ： 命题逻辑（将一句话当作一个命题，判断其 True/False）
- 更复杂的逻辑是 First Order Logic（一阶逻辑/一阶谓词逻辑）

一阶谓词逻辑的基本构成要素包括：
- Constants , Variables and Functions 
- 谓词（Predicates）：谓词是用于表示个体之间的关系或某个个体的性质。例如，“是红色的”可以表示为一个一元谓词，而“比……大”可以表示为一个二元谓词
- 量词（Quantifiers）：量词是用于表达泛指性的语句。一阶谓词逻辑中有两个基本的量词：全称量词（Universal quantifier，表示为 $\forall$）和存在量词（Existential quantifier，表示为 $\exists$）。全称量词用于表示“对于所有的……都满足……”这样的语句，而存在量词用于表示“存在……满足……”
- 逻辑连接词（Logical Connectives）：逻辑连接词与命题逻辑中的连接词类似，用于构建复合语句。常见的逻辑连接词包括：与（∧）、或（∨）、非（¬）、蕴含（→）和等价（↔）

- 只有一个谓词的语句称为简单句
- 复杂的语句通过对简单句使用逻辑连接符得到，这包括取反 (negation)、合取 (Conjunction)、析取 (disjunction)、蕴含 (implication)、等价 (biconditional)

量词对偶性：加两个取反符号，可以将存在（全称）量词转换成全称（存在）量词

精确推理所需的几个性质：
- Validity and Satisbility 
>A sentence is valid if it is true in all interpretations  
>A sentence is satisfiable if it is true in some interpretations 
>A sentence is unsatisfiable if it is true in no interpretations

- Equivalence and Entailment 
>Two sentences are logically equivalent if they have same truth in all interpretations.
>A sentence P entails another sentence Q if and only if P→Q is valid.
>Logical equivalence, entailment, and other rules including P rule, T rule, CP rule, and reduction to absurdity are fundaments of inference in first-order logic。

- 替换和统一：目的是将替换两个 FOL 表达式中的变量名，来使得两个表达式完全一致
![[Pasted image 20230424111505.png|400]]

- 一些概念
>❖Literal Atomic sentences and their negation 
>❖Clause disjunction of literals 
>❖Empty clause (also □ or NIL ) unsatisfiable 
>❖Conjunctive Normal Form (CNF) conjunction of clauses


### 归谬法推理
![[Pasted image 20230424114510.png|400]]
![[Pasted image 20230424112753.png|400]]
推出空子句意味着有一个假

### 将逻辑表达式转换成合取范式 (Conjunction Normal Form)
![[Pasted image 20230424113751.png|400]]
![[Pasted image 20230424114252.png|400]]

##### Example
![[Pasted image 20230424115501.png|400]]

## Knowledge Graph （知识图谱）
知识图谱是一个语义网络。每条边代表一个关系，每个节点是一个实体。
需要 4 个步骤：
- 实体抽取
- 关系抽取：语法结构或者机器学习
- 冲实体突消解
- 指代消解

使用知识和推理增强 ML：
- Inference about a particular object is facilitated by using relations to other objects in an image.
- GNN
- 神经网络中引入推理机制















