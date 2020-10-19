## 多标签众包标注算法

## 综述

众包标注的流程包括二步：1、任务分配 2、结果推断

### 任务分配

任务分配一般有两种方式，一种是**并行**，标注员之间互相不知道对方标的是什么，另一种是**串行**，前几轮的标注结果会影响后几轮的标注选项；并行的问题是标注的结果会很稀疏，串行的问题是太过依赖于前几轮的标注，如果前几轮标的很差，会直接带偏后几轮的标注。[^6]中提到了任务分配应该分配前TOP N个最有可能的类和标注人员可能最熟悉的类，方法是根据标注者的混淆矩阵来分配他最有可能答对的题。任务分配的原则就是在预算范围之内，尽最大可能最大化标注的效果。[^7]提出了动态调整标注数量的方法，以最大化利用预算。

 [^6]中提到的训练流程：

![image-20191011150327496](/Users/jiashupu/writings_on_NLP_ML/image-20191011150327496.png)

### 结果推断

1. Majority Voting
2. EM算法

## 众包标注方法

1. Majority Voting[^1]
   - 鼓励多人标注，特别是当单人标注有可能产生噪音时
   - 根据标注不确定性与模型不确定性选择标注的类

1. Dawid and Skene's algorithm (DS)[^2]
2. Homogeneous Dawid-Skene algorithm (HDS) [^3][^4]
   - M-步算法计算每个标注人员的权重，比如给专家更大的权重
   - 把类别的概率引入为隐变量，E-步计算此隐变量
3. GLAD algorithm[^4]
4. ASM & DASM[^5]
   - 引入了二步式标注方法，第一轮标注可以计算熵，如果熵大于某个阈值，则进入第二轮标注，第二轮标注第一轮不确定的那些标签
   - 引入了标注人员权重，标签之间的相似度计算
   - 主要为了解决多人标注标签稀疏化的问题

### 小西机器NLU主动学习实验v0.1

训练数据：老的360个smalltalk意图

测试数据：小草提供的测试集(包含20个多个重点意图)

评价指标：测试集上的macro-average F1 score

实验步骤：

1. 用已训练的模型跑一遍小孩语料
2. 根据熵及置信度对每个类的语料进行排序，选择模型最不确定的语料
3. 众包标注新的语料，并计算标注花费
4. 重新训练模型，得到在测试集上新的f1-score
5. 用相同的标注花费让标注人员"创造"语料，另外训练模型，计算测试集f1值

实验目的：

1. 评估主动学习对模型的提升效果
2. 评估标注语料与创作语料对结果提升的优劣
3. 评估当前众包标注方法的有效性

## Reference

[^1]: Sheng, V. S., Provost, F. and Ipeirotis, P. G. (2008) *Get Another Label? Improving Data Quality and Data Mining Using Multiple, Noisy Labelers*. Available at: http://www.mturk.com (Accessed: 10 October 2019).
[^2]:Algorithm, E. M., Dawid, A. P. and Skene, A. M. (1979) *Maximum Likelihood Estimation of Observer Error-Rates Using the*, *Source: Journal of the Royal Statistical Society. Series C (Applied Statistics)*. Available at: http://crowdsourcing-class.org/readings/downloads/ml/EM.pdf (Accessed: 10 October 2019).
[^3]:Raykar, V. C. *et al.* (2010) *Learning From Crowds 1. Supervised Learning From Multiple Annotators/Experts*, *Journal of Machine Learning Research*. Available at: https://www.mturk.com. (Accessed: 10 October 2019).
[^4]:Gao, C., Lu, Y. and Zhou, D. (2016) *Exact Exponent in Optimal Rates for Crowdsourcing*. Available at: https://arxiv.org/pdf/1605.07696.pdf (Accessed: 10 October 2019).
[^5]: Fang, Y.-L. *et al.* (no date) *Improving the Quality of Crowdsourced Image Labeling via Label Similarity*, *JOURNAL OF COMPUTER SCIENCE AND TECHNOLOGY : 1-Mon. Year J. Comput. Sci. & Technol., Mon.. Year*. Available at: http://jcst.ict.ac.cn (Accessed: 10 October 2019).
[^6]:Servajean, M. *et al.* (2017) ‘Crowdsourcing Thousands of Specialized Labels: A Bayesian Active Training Approach’. Institute of Electrical and Electronics Engineers, 19(6), pp. 1376–1391. doi: 10.1109/TMM.2017.2653763ï.
[^7]: Tran-Thanh, L. *et al.* (no date) *Efficient Budget Allocation with Accuracy Guarantees for Crowdsourcing Classification Tasks*. Available at: www.ifaamas.org (Accessed: 11 October 2019).