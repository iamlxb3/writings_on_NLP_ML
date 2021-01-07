Gamebert

Session Title: Modeling Universal Player Behavior  via unsupervised pre-training

Track, Format, and Delivery Format

Presentation Outline: 

我们报告的主题是如何利用机器学习，一种针对玩家行为序列的无监督预训练方法，来更好地了解玩家，给玩家提供更好的游戏体验。玩家的行为在各类游戏中无处不在，比如在MMORPG中，玩家序列可能包含做新任务，打新副本等代表活跃度很高的行为，也可能包含卖装备、无所事事等预示着玩家对游戏失去兴趣的行为；对于后者，游戏方会希望找出这些玩家，总结归纳他们失去兴趣的原因，不断优化游戏体验；另外在FPS类游戏中，鼠标移动的轨迹也是一种动作行为序列，往往可以被用于外挂检测。在不同游戏中，玩家的行为序列可能都对某一个下游任务的检测至关重要。

针对上述下游任务，一般基于机器学习的方法会对不同的下游任务进行多次数据收集和标注工作，非常得耗时耗力。同时，大量无标注的玩家行为序列也没有得到很好的利用。我们提出了一种仅需要少量标注数据的无监督预训练方法，它能针对不同的行为序列提取出一个通用型更强的表示，用于多种下游任务。在报告中我们首先会介绍将这种方法从NLP领域迁移到游戏领域的动机，比较行为序列和自然语言的异同点，行为序列更长，没有语义分割。然后我们会分析直接照搬这套方法给行为序列建模会失败的原因，将从序列的异同和硬件条件不允许这两方面来说。

接着我们会着重介绍如何根据上述行为序列的特点来设计基于BPE的序列压缩的方法。另外，序列片段之间的关联可强可弱，直接套用自然语言中的Masked Language Modeling显然是不合适的，我们将介绍一种自适应式的预训练任务Curriculum Masked Language Modeling，他和MLM最大的不同是会根据训练的收敛速度动态调整mask probability，慢慢增大任务难度。之后，我们会介绍我们的方法在真实游戏（JusticePC）数据上的实验结果，在三个下游任务（流失检测、外挂检测和相似玩家发现）上，我们将展示5个以上strong baseline和我们模型比较的结果，包括reformer, longformer等等，实验表明了我们的方法很有效，性能上超越了纯监督学习的方法10%以上，并且能减少80%左右的标注成本。除了这些量化指标外，我们也会讨论预训练任务难易对于结果有何影响，以及如何如何设定预训练任务的超参数。

DeepL translation -> grammly:

Our presentation is about how to use a deep learning technique, unsupervised pre-training applied to player behavior sequences, to better understand players and provide them with a more enjoyable game experience. Player behavior is ubiquitous in all kinds of games. For example, in MMORPGs, actions like actively accepting new assignments or upgrading wildly may indicate the high spirit in the game while behaviors liking selling weapons or wandering aimlessly may indicate loss of interest; in the latter case, the game provider expects to identify these players in time, uncover the reasons and continuously optimize the game experience. Besides, in FPS games, the trajectory of mouse movement is also a sequence of behaviors, which can often be used for plug-in detection. In different types of games, the player's behavior sequence may all be crucial to a downstream task and a certain type of detection.

To improve the performance of downstream tasks in games, more and more machine learning-based approaches are introduced. However, incorporating them into a specific task often requires specific training data, which means the data collection and labeling procedure can be repeated many times. The entire process is quite time-consuming and labor-intensive. Meanwhile, a large number of unlabeled behavior sequences are left unused. To address these issues, we propose an unsupervised pre-training method that exploits those unlabeled behavior sequences. It aims to extract more general representations, to reduce the cost of labeling, and to enhance the performance of multiple downstream tasks at the same time. Its spirit is "train once, extract everywhere".

In our presentation, we will first introduce the motivation for migrating this approach from the Natural Language Processing (NLP) to the game domain, comparing the similarities and differences between behavioral sequences and natural language. Then we will analyze the reasons why directly copying this approach from NLP to model behavioral sequences will fail, both in terms of the sequence discrepancies and the hardware limitations. Afterward, we will focus on introducing the highlights of our method, including a sequence compression method and a special pre-training task. The sequence compression method is based on Byte Pair Encoding (BPE); it can also segment sequences as a byproduct of compression. The special pretraining-task is called Curriculum Masked Language Modeling. Dynamic masking probability is introduced because we reckon setting a constant value may limit the learning potential of our model, for example, setting the value at 0.15 may be too easy a task if a segment can be effortlessly recovered from its context. In the last section, experimental results and discussions are presented; the real-world experimental data are from an MMORPG JusticePC. On three downstream tasks (churn detection, plugin detection, and similar player discovery), we will show the results of our method along with 5 strong baselines, including reformer, longformer, etc. Our approach outperforms purely supervised learning methods by more than 10% concerning performance and reduces the labeling cost by 80%. In addition to these quantitative analyses, we will also discuss how the difficulty of the pretraining task may affect performances.

---

Session Description (类似于abstract):

玩家的行为序列在各类游戏中无处不在，数据量庞大。目前部分游戏会利用这些数据和机器学习算法来提升玩家的游戏体验，比如进行外挂检测或者在玩家对游戏失去兴趣时及时分析原因或进行干预，让玩家能重新享受游戏。但是基于监督学习的方法依赖于大规模的标注语料，需要投入不菲的资金和大量人力；与此同时，大量的无标签数据缺也没有得到很好的利用。我们提出了一种针对玩家行为序列的无监督预训练方法，在提升下游任务性能的同时，能大幅减少标注成本。此方法用BPE做了序列压缩和语义分割，并且特殊订制了Curriculum Masked Language Modeling的预训练任务，在真实游戏中显著提升了外挂检测、流失预测等任务的性能。

DeepL translation -> grammly:

Player behavior sequences are ubiquitous in all kinds of games and the amount of data is usually huge. Currently, such data can be harnessed by machine learning algorithms to improve players' gaming experience, such as performing bot detection or intervening in time when players lose interest in the game so that they can enjoy the game again. However, supervised learning-based approaches rely on large-scale annotated data, which requires significant investment and manpower; at the same time, the large amount of unlabeled data is left unused. We propose an unsupervised pre-training method for player behavior sequences, to reduce the annotation cost and improve the performance of downstream tasks. Our method involves a sequence compression and semantic segmentation procedure with BPE, and a novel pre-training task, Curriculum Masked Language Modeling. The strength of the method is presented according to its performance on three downstream tasks of an MMORPG game.

---

Attendee Takeaway: 

如何将自然语言中的预训练方法迁移到玩家行为序列的建模，包括如何用BPE进行行为序列压缩和语义分割，如何设计特殊的预训练任务。实验结果方面，我们将展示5种以上的预训练模型在3个预训练任务上的性能，分析预训练任务超参对结果的影响。

DeepL translation -> grammly:

How to migrate unsupervised pre-training methods in natural language processing to model player behavior, including how to perform behavior sequence compression and semantic segmentation with BPE. Insights from experiments will also be discussed, including the impact of the difficulty of pre-training task and the probability of masking.

---

Intended Audience:

Researchers on the topic of user/player behavior profiling or downstream task that require behavior profiling. Background knowledge of deep learning is required.

---

Supporting material:

1. 实验结果
2. 复现代码
3. 模型结构图

----------

我们的实验是在Massively Multiplayer Online Role-Playing Game (MMORPG)完成的，只有玩家在游戏中有动作，行为就会出现，因此这个方法也可以推广到其他类型的游戏中，比如Multiplayer Online Battle Arena (MOBA)，First-Person Shooter (FPS)等

玩家的行为在游戏中无处不在，数据量庞大。如果能很好地利用这些无监督数据，对行为进行建模，我们更好地理解玩家的特点同时也能某几个下有任务的性能，比如外挂检测、流失预测、地图预加载等等，从而在整体上提升玩家游戏体验。

我们选择transformer-encoder来对玩家的行为建模，transformer在对NLP领域有深远的影响，引领了这几年的发展。但是语言和游戏中的行为有很大不同，玩家的行为序列通常很长，包含多个维度的信息（比如时间、行为的补充信息等），最重要的是行为序列没有语义标签。直接套用NLP下的预训练模式显然是不合适的，所以我们量身定制了游戏行为序列特殊的预训练方法，我们采用BPE的方式对序列进行压缩，并且

