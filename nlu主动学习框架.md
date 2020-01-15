## 背景

自然语言理解是聊天机器人框架中的重要一环，目前并不存在一个大一统模型或者一种迁移学习的算法能直接应用于所有的场景，所以数据的质量与数量会直接影响最后的模型效果。"标注"后的数据往往是稀缺的，但是"未标注"的数据则非常充足；研究者们提出主动学习框架，将"人工标注"与"机器再学习"迭代进行，形成一个闭环，但是如何选出"高价值"的样本在研究领域一直没有定论，仍然是一个开放问题，[^2]中实验中比较了多种"选样本"算法，但结论是在某些情况和随机选样本没有区别，[^1]提出了用模型来学习模型在哪些样本上更容易犯错。找到"学习效率高"的样本对监督学习算法有极大价值。



多轮机器人对话目前面临诸多挑战，比如聊天中机器人"无法记忆用户说的话"，"缺乏人类先验知识"等，其中也包括"很难保持时间、空间和逻辑的一致性"；一致性差的原因包括训练集中包含了不同的人的对话，一个解码器总是选择最大似然的应答等等。[2] 提出了将人设信息引入模型的方法，能产生符合特定人设的回答，但是依然会存在一些逻辑前后矛盾的情况。[1] 提出了通过NLI对相同人设的句子进行两两配对并找到它们之间的关系（矛盾、中性、支持），然后根据关系对候选输出进行重新排序的方法，能降低人设相关的不一致性。多轮对话的问题需要各个击破，解决对话一致性将是一个重大突破。



## Reference

[^1]: https://medium.com/pytorch/active-transfer-learning-with-pytorch-71ed889f08c1
[^2 ]: Lowell, D., Lipton, Z. C. and Wallace, B. C. (no date) *Practical Obstacles to Deploying Active Learning*. Available at: https://arxiv.org/pdf/1807.04801.pdf (Accessed: 31 October 2019).
[^3]: Welleck, S. *et al.* (no date) *Dialogue Natural Language Inference*. Available at: https://arxiv.org/pdf/1811.00671.pdf (Accessed: 15 January 2020).
[^4]: Zhang, S. *et al.* (no date) *Personalizing Dialogue Agents: I have a dog, do you have pets too?* Association for Computational Linguistics. Available at: https://github.com/facebookresearch/ (Accessed: 15 January 2020).