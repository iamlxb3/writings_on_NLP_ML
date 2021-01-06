2020-11-16

1. 阅读Shortcut Learning in Deep Neural Networks
2. 浏览reddit
3. 研究batch fancy indexing
4. 把sinusoidal time embedding调好了

2020-11-17

1. 把三合一(game id, design id, timestamp)的模型训练代码和inference代码写好了
2. 看视频Building machines that learn and think like people | Joshua Tenenbaum

2020-11-18

1. 新增embedder的finetune功能
2. PPL evaluation重新写了一下
3. 数据处理，划分测试集
4. 调了不少bug, reformer, longformer什么的

2020-11-19

1. 开会 * 2
2. 整理paper

2020-11-23

1. 阅读论文 Self-Supervised Learning of Image Features with SwAV 
2. 阅读 Underspecification Presents Challenges for Credibility in Modern Machine Learning
3. 捣鼓词典
4. 专利沟通

2020-11-24

1. 网易价值观小故事
2. 读论文 Self-attention with Functional Time Representation Learning，基本读不太懂
3. 写可视化脚本
4. 找time/temporal embedding相关论文

2020-11-25

1. 读论文（HE KAIMING 那篇孪生网络的印象很深），找论文

2020-11-26

1. 学习LSH
2. 学习kernel + SVM
3. 找论文，想灵感

2020-11-27

1. 听亚东讲座
2. 整理论文 & 想idea
3. Time embedding的小实验

周报：

1. 这周主要还是围绕玩家表征学习开展工作，围绕设计pre-train task、time-bedding、sequence表示进行了论文调研 & 想点子
2. 【设计pre-training task】这一块调研了多个领域落地的一些论文，包括nlp、Music、speech、video、bio。拍脑袋想了几个方案。第一个是基于multi-view的pre-train task，log_id的序列可以算作一个view，design_id, timestamp可以算作另外两个view，那么我们可以mask任意一个view的输入，用另外两个view来预测这个被mask掉的。第二个是基于不同模型的contrastive learning，目前有了几个baseline模型，所以不同模型对同一个sequence可以生成多个表示，可以作为contrastive learning的正样本，最近也看了一篇何凯明有关表示学习的新论文，不需要构建负样本，方法很简洁，推荐阅读：https://arxiv.org/abs/2011.10566
   第三个想法是考虑如何利用PERSON的信息，比如可以把同一人不同天的行为序列构建为postive pair，假设就是同一人不同天的行为相比不同人不同天的行为要相似。
3. 【设计time-embedding】看了下mercer time embedding的论文，偏理论。自己想了一种带门控制的time embedding，门由log_id来控制，motivation就是并非所有行为的持续时间都是重要的，所以考虑把没有用的time embedding过滤掉。
4. 【设计sequence的向量化表示】这一块刚开始调研，看了一些doc2vec的方法，感觉也没有办法直接移植过来。
5. 数据可视化开发

2020-11-30

1. 读论文，先点子

2020-12-01

1. 读论文（document embedding相关），学数学方面的概念，

2020-12-08

1. 和UP组开会 & 研究他们写的代码和数据
2. 看课程学习方面的论文
3. 重新看了下假设检验方面的文章

2020-12-09

1. 整理了一下代码
2. 读课程学习的survey，找论文
3. 做PPT

2020-12-14

1. 把多个Task做课程学习的代码写好了
2. 把多个Task输出inference的代码写好了