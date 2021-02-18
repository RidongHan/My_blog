---
title: ACL 2020 -- Relation Extraction with Explanation
date: 2020-09-05 11:04:15
tags: 
	- ACL 2020
	- Relation Extraction
categories: 
	- Relation Extraction Notes
	- ACL 2020
abbrlink: '20200905'
---

# 摘要

> 最近远程监督关系抽取的NRE模型都是针对每个分包bag，通过学习句子的重要性权重来减轻不相关句子的影响。 
> 目前为止，努力的重点是**提高抽取的准确性**，但对模型的**解释性知之甚少**。

> 本文标注了一个带有**基本事实句子级解释**的测试集，以评估关系提取模型提供的可解释性。 
> 实验证明，用细粒度实体类型（entity type）替换句子中的实体不仅提高了提取的准确性，而且改善了可解释性。 
> 本文还提出**自动生成“干扰”句子，对bag数据增强，并训练模型忽略这些“干扰”句子。 
> 在FB-NYT数据集上，本文取得了SOTA性能，同时提高了模型可解释性。

# 引言

远程监督关系抽取降噪研究：

* 基于attention的模型
* 利用附加资源（additional resources）的模型
* 利用监督数据的模型

> 现有方法，关注于提高模型的准确率（accuracy），而对于模型是因为**正确的推理**还是**某些不相关的偏置/偏见**而正确分类知之甚少。

# Baseline Models

## DirectSup

给定一个分包bag，DirectSup使用具有不同过滤器大小的CNN对每个句子进行编码。
连接具有不同滤波器大小的CNN的输出，以产生句子的编码。


## CNNs+ATT
