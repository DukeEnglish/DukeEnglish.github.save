---
layout: post
title:  "机器学习性能评估"
date:   2017-09-19 
tags: 机器学习
---

针对分类问题的结果，我们可以建立一个混淆矩阵。而混淆矩阵就是一个用来描述分类模型在测试集上的分类性能的表格。（fr wiki）。虽然混淆矩阵不难理解，但是关于它的术语特别容易混淆。唔哈哈哈，就是很难记得住！明明复习过了，面试还是不记得，干嘛要记住啊，不用怎么会记得住。

Well，for example。我们对猫狗进行分类，一共有十只猫，十只狗（对就说有十个你）：
![CM1][1]

这里我们定义四个术语：
True Positive(真真):正确地识别了正值
True Negative（真假）:正确地识别了假值
False Positive（假真）:错误地识别了成了真值（应该是假）
False Negative（假假）:错误地识别了成了假值（应该是假值）

有一些绕，你可以这么理解：第一个单词代表被预测样本的预测对错，第二个单词代表被预测样本的真实值。对于我们上面的例子就是（假设猫为真）：
TP=8
TN=6
FP=2
FN=4
![CM2][2]
那么我们可以用这四个术语来推导出什么东西来评定我们的模型性能呢：

准确率（accuracy）是什么：就是给出的答案里面有多少是对的。
即判断正确的个数除以总个数：（TP+TN）/TOTAL=（14）/20=0.7
这是一个我们平时会见到的概念，但是他不够用，为什么呢？因为如果当整个样本中正的数量远远大于负的数量（猫99，狗1），那么分类器这个时候直接判断所有的都为猫，准确率为0.99，但我们知道这个分类器是不好的。。他的结果都是猫，所以还有两个新的概念：
精确率（precision）＝检索出的相关信息量 / 检索出的信息总量
召回率（recall）＝检索出的相关信息量 / 系统中的相关信息总量

比较难理解。一般这两个概念都是针对我们的“positive”而言的。第一个问的就是正值里面究竟有多少真的是正值，即：
precision：TP/(TP+FP)判定为正的里面判定对的比例（精确，就是你命中的那里面哪些是对的）
recall：TP/(TP+FN)所有为正的里面，被找出来的比例（召回就是说成功的被召唤出来多少你想要的东东）
另外有人提出了以下的公式将precision和recall结合了起来。
F1 Score = P*R/2(P+R)，其中P和R分别为 precision 和 recall。

  [1]: https://raw.githubusercontent.com/DukeEnglish/DukeEnglish.github.io/master/Pic-blog/CM1.png
  [2]: https://raw.githubusercontent.com/DukeEnglish/DukeEnglish.github.io/master/Pic-blog/cm2.png
