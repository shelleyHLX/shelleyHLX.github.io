---
layout: post
title:  "Hierarchical Attention Networks for Document Classification"
date:   2018-12-2
categories: Text Classification
tags: HAN
---
* content
{:toc}

## Abstract
提出具有层次级的注意力网络进行文本分类，模型有两个重要特点：

1 层次级结构表示文本的层级结构
2 应用在词级和句子级的注意力机制，在构造文本表示时可以捕获不同的内容。

## 1 Introduction
文本分类是自然语言处理的任务之一，目标是给文本贴标签，有广泛的应用，比如话题打标签，情感分类，垃圾检测。表示文本的传统方法是使用稀疏的词法特征，比如n-gram，然后在这个表示上使用线性模型或是核方法。现在更多的是使用深度学习，比如CNN，RNN，LSTM，进行文本表示的学习。

![image](http://shelleyHLX.github.io/assets/TextClassification/han_1.png)

虽然基于网络的方法很有效，本文提出的假设在模型架构中的文档结构的知识可以获得更好的表示，灵感源于不是文档的每部分对于分类都有用，而且决定相关部分涉及到词语之间的交互，不仅仅他们孤立的出现。

我们的贡献是提出新的网络，层次级的注意力网络，可以捕获文档的两级特征。

首先，文档有两级特征（词到句子，句子到文档），所以先构造句子的表示再把他们变成文档的表示。

第二，不同的词语和句子在文档中有不同的信息。而且重要的词和句子是文本信息独立的，比如相同的单词或是句子在不同的文本中有不同的信息。

我们的模型包含两层的注意力机制，一个是单词级，一个是句子级，这让模型对于单个词有不同的敏感度。 比如figure 1的单词中，delicious，amazing有更强的信息，对于评论有积极的影响。

注意力有两个好处，有更好的性能外，而且考虑了词和句子对于分类决定的贡献。

## Hierarchical Attention Networks
整个模型包括几部分：

词序列的编码器，词级的注意力层，句子的编码器，句子级的注意力层。

![image](http://shelleyHLX.github.io/assets/TextClassification/han_2.png)

其中\\(t_k\\)和\\(s_l\\)是特征函数，\\(\lambda_k\\)和\\(\mu_l\\)是对应的权值。求和是在所有可能的输出序列上进行的。\\(t_k\\)是转移特征，依赖于前一个位置和当前位置。\\(s_l\\)是状态特征，依赖于当前位置。通常特征函数\\(t_k\\)和\\(s_l\\)定义为1或0，满足特征取1，不满足则取0. 条件随机场完全由特征函数\\(t_k\\)，\\(s_l\\)和对应的权值\\(\lambda_k\\)，\\(\mu_l\\)确定。

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
