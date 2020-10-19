## Introduction

​	AI对话系统可以被分为两类，一类是垂直领域的对话系统，比如订机票订饭店等，这一类对话系统依赖于特殊订制的意图和回答；另一类是开放域的对话，AI会根据上下文做出最合适的回答，目前一般通过生成式模型来生成对话，但是这种模式有几个缺点，首先生成文本的内容都会倾向于pretrain的语料，其次单模型很难应用于多人设等需要可控文本生成的场景，所以我们认为当前的对话系统还是需要人的干预，最直接的方法是人工写特定的意图和回答，但是这种方法会随着意图量的增大变得越来越不可控。所以我们可以逆向思维一下，不去猜玩家会说什么，而是从玩家的日常聊天中发掘高频的问题。

​	如果拥有一个的通用意图数据集，我们就可以满足大部分场景下的单轮高频意图，比如“你好”，“再见“等；我们认为一个足够大（比如1万个意图）的意图集可以应对对话系统的大部分可单轮回答的问题，所以”新意图发现“对于提升对话质量有着重要的意义。

​	”新意图发现“的方法通常是通过在没有标签的数据中聚类完成的，而”文本的表示“与”聚类算法“的会同时影响聚类的质量。目前文本的表示通常会通过预训练语言模型来抽取句向量，但是当LM预训练的数据分布与需要聚类的数据分布不同时，文本的表示就会不准确，从而导致不佳的聚类效果；聚类算法的选择同样重要，比如K-means偏向于球状的簇，而密度型聚类算法dbscan则有自动去除离群点的优势，每一种数据分布都有最合适的聚类算法。显然，通过人眼从百万级数据中观测数据分布并判断最佳的聚类算法是不可行的。

![image-20200716152255862](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716152255862.png)

​					图1. 新意图发现的一种迭代方式，CA代表clustering algorithm, LM代表language model

​	所以我们通过精标的分类数据（从无标签的数据中标注得来）来调整LM的句子表示和选择最合适的聚类算法及超参，这两者的学习与选择可以独立进行的，也可以是同时进行，互相有关联的—比如让模型尽量学习到一种更适合Dbscan聚类算法的表示，这两者的学习对应图1中的步骤1。在实际新意图发现的，我们会碰到两个问题：第一个问题是我们没有办法一次性拿到所有的精标数据，数据量是慢慢递增的（迭代的流程可以参考图1），我们需要了解在不同数据量下聚类的效果；其次数据的分布可能与精标数据不同，比如我们有一批游戏的精标数据，但是要着手开始在体育方面的新意图发现，相同domain时有效的聚类方法在跨domain时是否依然有效？

**Main Contribution**:

1. （已做部分实验）在5个中文数据集上，比较了5种以上聚类方法的效果，包括近期CV领域中的一些通过模型而非传统聚类算法完成聚类这个目标的一些方法。这一块贡献有两部分，第一是数据集的意图数量较多，之前paper中比较聚类时一般类别最多就20类，我数据量最多达到1000多；第二是我动态测试了不同数量精标数据对聚类结果的影响，这一方面的实验之前的paper我印象里也很少。
2. （已做部分实验）测试精标数据和待聚类数据在不同domain时的聚类效果，目前的结论是会劣化效果。
3. （设想1，还未做实验）提出一种方法，能让LM学习时同时兼顾精标的分类数据和后续的聚类算法，前者的loss就是简单的分类cross entropy；后者的loss可以是验证集上的聚类指标（比如adjusted rand index），但是这个loss是不可微分的，可能要尝试一些强化学习的方法，如果这一块能做出效果，可能会有一点novelty。
4. （设想2，还没有好的点子）设计一种聚类算法，能让LM的表示能更好地跨Domain去做聚类

## Related works



## Methods

### Datasets

| Dataset              | Language | Num. class | Utterance length | Num. total unique tokens | Remark |
| -------------------- | -------- | ---------- | ---------------- | ------------------------ | ------ |
| SMP2018              | CN       | 31         | 8.3 +- 3.7       | 2887                     |        |
| SMP2019              | CN       | 23         | 8.6 +- 3.5       | 3482                     |        |
| THUC News            | CN       | 14         | 19.1 +- 4.1      | 19943                    |        |
| FUXI smalltalk (old) | CN       | 354        | 6.4 +- 2.5       | 2883                     |        |
| FUXI smalltalk (new) | CN       | 1226       | 5.2 +- 1.7       | 2790                     |        |

### Clustering algorithm

#### Baseline1: LM不做任何微调，直接聚类

![image-20200716163430193](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716163430193.png)

​																			图2

#### Baseline2: LM不做任何微调，用LM计算相似度，在unlabeled data上生成软标签，再通过DEC loss在软标签的基础上生成聚类结果

![image-20200716163407264](https://tva1.sinaimg.cn/large/007S8ZIlly1ggswdru7cpj30h90fs0ty.jpg)

​																					图3

#### Algorithm 1: 仅用金标数据来finetune LM，对应图1

#### Algorithm 2: 用金标数据 + 聚类后的pseudo label来finetune LM，属于semi-supervised clustering，这里的pseudo label可以是hard label，也可以根据相似度生成soft label，然后用KL-loss去进行训练，两个实验都做了

![image-20200716165108478](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716165108478.png)

​																					图4

### Experiment design

**实验1. 测试不同聚类算法在不同大小的数据上的效果**

实验分别在不同的5个数据集上进行。在每个数据集上，会测试在不同数据量下算法的表现，我们设定了8档，每一档对应了数据中类别的数量，包括4、8、16、32、64、128、256、512个类；在相同的数据量下，每一次实验数据都会分割3次，生成不同的train/test，比例控制在0.8/0.2

Algorithm 1的部分实验结果：

![image-20200716171629967](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716171629967.png)

![image-20200716171639584](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716171639584.png)

Algorithm 2的部分实验结果：

![image-20200716171700806](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716171700806.png)

![image-20200716171709430](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716171709430.png)

**实验2. 测试跨domian聚类的效果**

在smalltalk(new)数据集上fine-tune了LM，然后在其他其他数据集上测试效果，用了上文提到的Algorithm 1。对比的LM用了在其他数据集上pretrain但是没有在分类任务上finetune的LM。

部分实验结果（可以看到在3个数据集上，finetune的LM都劣化了结果）：

![image-20200716170413290](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716170413290.png)

![image-20200716170422969](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716170422969.png)

![image-20200716170442390](/Users/jiashupu/Documents/writings_on_NLP_ML/image-20200716170442390.png)



### Evaluation metric

1. 假设我们知道测试集有多少类，大部分聚类的paper都是用的这种假设，我们可以用K-means等需要明确指定K大小的聚类算法进行验证聚类的效果，指标有多种选择，adjusted_rand_index, normalized mutual information, bcubed F1等。
2. 假设我们是不知道测试集有多少类的，这个假设和现实中遇到的情况比较类似，我们需要考虑两个指标，一个是丢弃掉outlier之后的覆盖率，另一个时剩下样本的聚类质量，（这个可以参考1），然后可以像计算F1值一直计算两者的hormonic mean。