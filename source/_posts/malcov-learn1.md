---
title: 隐马尔科夫模型学习笔记
date: 2017-06-04 10:18:39
tags:
---
隐马尔科夫模型在股票量化交易中有应用，最早我们找比特币交易模型了解到了这个概念，今天又看了一下《统计学习方法》里的隐马尔科夫模型一章。    
隐马尔科夫模型从马尔科夫链的概念而来，马尔科夫链是指下一个状态只和当前的n个状态有关，和历史状态无关的一个时间上的事件链，隐马尔科夫模型在这个状态链的基础上，让每一个状态都能产生观测值，从而可以产生一个可观测的数据链，让原来的状态链变成了幕后产生数据的状态链，称为因马尔科夫链。    
隐马尔科夫链应用比较广泛，主要能够处理三类问题：
* 一个是给定了马尔科夫模型参数和观测序列，计算这种序列出现的概率，即概率计算问题；
* 二是给定观测序列或者给定观测序列和隐含状态序列，分别来估算隐马尔科夫模型的参数，也就是参数估计问题，可以理解为机器学习的问题。前者没有给出隐含状态（Y），只给了观测状态（X），采用的是非监督学习方法。后者有X和Y，可以理解为监督学习的问题。
* 第三个问题是给定了模型参数和观测序列，求出隐含状态序列的问题，可以理解为预测问题或者是解码问题。

目前对股票量化交易上的应用还没有研究，网上说法大概就是应用到了隐马尔科夫模型的机器学习和预测这两个方面来实现    
http://www.voidcn.com/blog/baskbeast/article/p-6012357.html    
隐马尔科夫模型进行监督学习的算法比较简单，因为统计马尔科夫模型的参数就是状态转移概率和观测概率，如果既有状态转移链，又有观测链，直接统计出训练数据的这些概率值即可，但是一般难以一一统计海量观测数据的类型信息，也就是状态信息，因此对于此种类型的问题（如新闻分类，新闻是观测，新闻所属类型为状态），一般会采用非监督学习，也就是隐马尔科夫应用机器学习更多为非监督学习。    
由此猜测可能如何选择一个问题用监督学习还是非监督学习来进行训练，其中要考虑的原因包括了下面的两项：第一是是否能够提供出一一对应的训练观测值和观测值产生的结果的Map，二是这个问题是否有可能简化到可以进行非监督学习，例如简化成一个隐马尔科夫链能处理的问题    