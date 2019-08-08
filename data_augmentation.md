 [^1]提出了Unsupervised Data Augmentation (UDA)，将supervised loss与unsupervised loss结合起来训练模型：

![image-20190702171319718](https://ws3.sinaimg.cn/large/006tNc79ly1g4lm1h4leuj30rr06fq5i.jpg)

 [^1]提出了Training Signal Annealing，主要是为了防止模型在SSL的时候在原始训练数据上过拟合，当模型预测样本正确类的概率大于某个阈值的时候，就把这个样本从这个训练的batch中移除。

 [^2] 提出了基于geometric distribution的同义词替换，原文如下：

> To do synonym replacement for a given text, we need to answer 2 questions: which words in the text should be re- placed, and which synonym from the thesaurus should be used for the replacement. To decide on the first question, we extract all replaceable words from the given text and randomly choose r of them to be replaced. The probability of number r is determined by a geometric distribution with parameter p in which P[r] ∼ pr. The index s of the syn- onym chosen given a word is also determined by a another geometric distribution in which P[s] ∼ qs. This way, the probability of a synonym chosen becomes smaller when it moves distant from the most frequently seen meaning.

 [^3] 中提出了机器翻译中文本增强的方法，主要替换低频词，然后选取N个低频词，用LM打分，再选取最通顺的低频词。其中也提到了LM打分对生成句子的影响：

> While using a large LM to substitute words with rare words mostly results in grammatical sentences, this does not mean that the meaning of the original sentence is preserved. Note that meaning preservation is not an objective of our approach.

> Data augmentation can be performed in data-space or feature-space. We found that it was better to perform data augmentation in *data-space*, as long as label preserving transforms are known. [^5]

### 简单的文本增强的做法[^4]

- 随机增加词
- 随机删词
- 随机改变两个词之间的位置
- 随机替换同义词([^1]也提到了可以根据TF-IDF的值来替换词，高tfidf的词替换的概率低，低tfidf替换的概率高)
- 随机替换同音词



### TODOLIST

- 其实可以考虑用句法分析，做一些特定句式的替换



[^1]: Q. Xie, Z. Dai, E. Hovy, M.-T. Luong, and Q. V Le, “Unsupervised Data Augmentation.”
[^2 ]:  X. Zhang and Y. Lecun, “Text Understanding from Scratch.”
[^3]:  M. Fadaee, A. Bisazza, and C. Monz, “Data Augmentation for Low-Resource Neural Machine Translation,” pp. 567–573.
[^4]: J. Wei and K. Zou, “EDA: Easy Data Augmentation Techniques for Boosting Performance on Text Classification Tasks,” 2019.
[^5]: Understanding data augmentation for classification: when to warp? https://arxiv.org/pdf/1609.08764.pdf