---
layout:     post
title:      "论文笔记：Keyword-Attentive Deep Semantic Matching"
subtitle:   ""
date:       2021-03-07 15:00:00
author:     "zhangc"
mathjax: true
catalog: false
header-style: text
tags:
  - 语义匹配
  - 关键词典
  - 负采样
---



### Abstract

论文在摘要部分提到一共三部分重要的工作：（1）在 BERT 模型的基础上提出 word-attentive transformer 的结构，这是相对 self-attention transformers layer 的优化；（2） 提出了一种构造 negative sample 的方法，应该是利用一个metrics score。（3）根据不同 domain的 corpus，挖掘得到了一个keyword 词表。

### 带着问题读Paper

问题一：
word-attentive transformer 结构的细节，以及为啥能比 self-attention 方式更加好的抽取文本中的关键信息？
问题二：
自动 negative sample 的在 out-of-domain 可靠性评估如何，以及对应的细节？
问题三：
构造 keyword dict的metrics 是啥，相比strong baseling `TF-IDF` 对比如何？词表仅仅只靠 open-domian 的corpus 就足够了吗？



### Proposed Approach
TODO


### 总结
1. 基于PMI 抽取中文词语， 然后利用diff-idf 判断是否是 domain的关键词。keyword 总的词表还是融合百度百科和维基百科的词条\n
2. Keyword-attention mechanism 的关键是在原始的 attention transformer layers 的top-level 上并行增加一个 keyword-attention 层，保证keyword 的权重不会再传递的过程中被削减。
3. negative sample 方法是通过卡 query&question 之间similariy 的阈值（0.6） 和 query&question 之间的非共同的词和共同的词的比例（0.2）。来确定是否是 negative pairsample。**正样本则是人工审核进行的。**


### reference
[1] [原文：Keyword-Attentive Deep Semantic Matching](https://arxiv.org/pdf/2003.11516.pdf)   
[2] [文中提到的长文本匹配:Semantic Text Matching for Long-Form Documents](https://jyunyu.csie.org/docs/pubs/www2019paper.pdf)  
[3] [信息抽取中的距离特征参考：Relation Extraction Using Supervision from Topic Knowledge of Relation Labels. Proceedings of the Twenty-Eighth International Joint Con-ference on Artificial Intelligence](https://www.ijcai.org/Proceedings/2019/0698.pdf)  
[4] [负采样思路参考：A strong baseline for question relevan-cy ranking](https://arxiv.org/pdf/1808.08836.pdf)
