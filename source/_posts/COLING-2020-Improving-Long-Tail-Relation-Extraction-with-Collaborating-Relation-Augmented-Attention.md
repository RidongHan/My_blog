---
title: COLING 2020 -- Improving Long-Tail Relation Extraction with Collaborating Relation-Augmented Attention
date: 2020-11-01 16:41:07
tags: 
	- COLING 2020
	- Relation Extraction
categories: 
	- Relation Extraction Notes
	- COLING 2020
abbrlink: '20201101'
---

# 摘要

在关系抽取中，远程监督引起两个主要挑战：

* 错误标签
* 长尾关系（NYT数据集中，41个关系类别（共53个）只有不到1000个训练样例）

最近的工作通过“**多实例学习的选择性注意力**”减轻错误标签影响，

但即使引入**关系的层次结构**来共享知识，也不能很好地处理长尾关系。

为解决上述问题，本文提出一种新的神经网络，即协作关系增强的注意力（Collaborating Relation-augmented Attention，CoRA）。

> 具体如下：
>
> * 首先提出**关系增强注意力网络**(relation-augmented attention network)，作为 base model。
>   * bag级别的sentence-to-relation注意力机制，最大程度减少错误标记的影响。
> * 基于 base model，引入**在关系的层次结构中，各关系间共享的协同特征**（collaborating relation features）
>   * 促进关系增强过程
>   * 平衡长尾关系的训练数据

主要训练目标: 
* 预测句子bag的关系

辅助目标：
* 指导关系增强过程，以获得更准确的bag级特征表示

CoRA在数据集NYT上进行的实验在 $Precision@N$，$AUC$ 和  $Hits@K$ 指标上均达到SOTA。

对比实验的进一步分析也证明了CoRA在处理长尾关系方面的卓越能力。

# 引言

在关系抽取中，远程监督引起两个主要挑战：

* 错误标签
* 长尾关系（NYT数据集中，41个关系类别（共53个）只有不到1000个训练样例）

1. 对于错误标签问题：

> 最近的工作大多是通过“**多实例学习的选择性注意力**”减轻错误标签影响 

2. 对于long-tail问题：



