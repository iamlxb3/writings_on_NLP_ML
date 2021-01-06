Gamebert

Session Title: Modeling Universal Player Behavior  via unsupervised pre-training

Track, Format, and Delivery Format

Presentation Outline: 

玩家的行为在各类游戏中无处不在，数据量庞大。比如在MMORPG中，玩家序列可能包含做新任务，打新副本等代表活跃度很高的行为，也可能包含卖装备、无所事事等预示着玩家对游戏失去兴趣的行为；对于后者，游戏方希望能提前干预，挽留那些想要离开的玩家；另外在FPS类游戏中，鼠标移动的轨迹也是一种行为序列，往往可以被用于外挂检测。在不同游戏中，玩家的行为可能都是某个下游任务的不可或缺的信息。

针对上述任务，一般基于机器学习的方法会对不同的下游任务进行数据收集和标注工作，非常得耗时耗力，并且浪费了大量的无监督的玩家行为序列。基于此，我们提出了一种利用大规模无监督行为序列的方法，能够将行为表示为一个通用的表征，用于多个不同的下游任务，仅需要少量标注数据，其性能就能超越纯监督学习的训练方法10%以上。另外，此方法可以将标注成本降低到原来的10%以下。在JusticePC游戏的实验中，此方法能显著提升三个下游任务的性能，具有广阔的应用场景。

报告主要包含三部分，第一部分，我们在游戏中对行为作无监督预训练任务的原因。第二部分，行为预训练和自然语言预训练的异同点：行为序列没有语义分割标签，长度不受控，预训练任务。第三部分，我们针对游戏中的行为特点，对无监督预训练做的调整，包括用BPE的方式做序列压缩和语义分割、订制基于课程学习的Mask Language model预训练任务。

Session Description (类似于abstract):

玩家的行为在各类游戏中无处不在，数据量庞大。目前机器学习可以检测这些数据并对特定任务作出判断，比如外挂检测或者在玩家对游戏失去兴趣时及时干预，重燃玩家的激情。基于监督学习的方法依赖于大规模的标注语料，需要投入不菲的资金和大量人力；与此同时，大量的无监督数据缺也没有被很好地利用。我们将语言模型的无监督预训练迁移到行为序列的预训练中，基于BPE做了序列压缩和语义分割，特殊订制了预训练任务，并且在MMRORPG JusticePC上做了实验，我们发现此方法能显著提升下游任务的性能、极大降低标注成本，在多个任务上都有良好的表现，有广阔的应用场景。

Attendee Takeaway: 

1. 行为序列和自然语言的区别
2. 如何将自然语言中的预训练方法迁移到游戏领域，包含基于BPE的序列压缩和语义分割方法、如何设计特殊的预训练任务
3. 实验结果，在多个下游任务上GameBert的性能。

Intended Audience:

1. researchers on the topic of user/player behaviour profiling or downstream task that require behaviour profiling.
2. researchers and engineers who works on user behavior problems in Gaming development.

Supporting material:

1. 实验结果
2. 复现代码
3. 模型结构图



我们的实验是在Massively Multiplayer Online Role-Playing Game (MMORPG)完成的，只有玩家在游戏中有动作，行为就会出现，因此这个方法也可以推广到其他类型的游戏中，比如Multiplayer Online Battle Arena (MOBA)，First-Person Shooter (FPS)等

玩家的行为在游戏中无处不在，数据量庞大。如果能很好地利用这些无监督数据，对行为进行建模，我们更好地理解玩家的特点同时也能某几个下有任务的性能，比如外挂检测、流失预测、地图预加载等等，从而在整体上提升玩家游戏体验。

我们选择transformer-encoder来对玩家的行为建模，transformer在对NLP领域有深远的影响，引领了这几年的发展。但是语言和游戏中的行为有很大不同，玩家的行为序列通常很长，包含多个维度的信息（比如时间、行为的补充信息等），最重要的是行为序列没有语义标签。直接套用NLP下的预训练模式显然是不合适的，所以我们量身定制了游戏行为序列特殊的预训练方法，我们采用BPE的方式对序列进行压缩，并且

