##NLU相关研究方向

1. 知识图谱运用于NLU
   - 背景：借鉴出门问问的方案，希望能结合知识图谱提升各NLU子任务的性能，比如文本分类。
   
   - 已做的工作：调研了graph embedding相关的论文，比较了几种常见embedding方法在小数据集上的表现。
   
   - 后续：1. 持续调研 & 实验
   
     
   
2. 文本补全
   - 背景：目前NLU完全基于单轮，文本补全可以把部分多轮问题转化为单轮；另外文本补全也为下游模块提供更完整的信息。
   
   - 已做的工作：写了一些启发式算法，但效果不佳，还是需要case by case去微调，成本太高；模型方面仍处于调研阶段，缺乏数据，目前从pointer-generator network入手，复现一下文本摘要上的效果，基本还是以seq-to-seq的思路来做这个事情。
   
   - 后续：1. 收集数据 2. 尝试用pg-net做个baseline
   
     
   
3. 主动学习 & 半监督学习 & 文本聚类

   - 背景：线上服务有大量的未标注数据，需要有效利用这些数据。

   - 已做的工作：尝试了self-training和active learning结合的方法来提升模型，发现类似bootstrapping的方法不稳定，还是需要人为干预，active learning实验下来提升显著。

   - 后续：持续迭代active leaning和clustering模块。

     

4. 中文NLU benchmark

   - 背景：英文有完善的NLU benchmark，比如GLUE和SUPER GLUE，能系统性检测整个NLU系统的表现。希望也能慢慢积累一份中文的benchmark

   - 已做的工作：调研了GLUE及Super Glue相关工作，收集了中文NER 60w条数据。

   - 后续：1. 刷英文benchmark 2. 收集中文数据

     

5. 更好利用上下文信息提升文本分类的性能
   - 背景：目前意图标注不仅仅是一个label，还包含了类别和回答，这两者都拥有丰富的语义信息，希望能最大程度利用这些信息
   - 已做的工作：尝试过将多分类转化为2分类问题(将类别文本与输入文本拼接过BERT)，训练会慢很多，效果提升不明显。
   - 后续：1. 尝试multitasking