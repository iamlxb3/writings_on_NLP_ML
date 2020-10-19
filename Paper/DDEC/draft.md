## Abstract

The problem of discovering novel categories in collections of documents or texts is difficult because the answer to categories is not unique and different intentions can lead to different result. Hence, we assume we have access to prior knowledge of similar but different text categories. We proposed to inject outliers in the evaluation phase to make the task more realistic and challenging. Our ensemble-based method encourages base learners to be diverse and accurate; from labeled data, each base learner tries to learn a suitable representation and search hyper-parameters of a density-based clustering algorithm afterwards. The final partition is obtained through a consensus function. We extensively evaluate our method on various settings - by changing size of training set and outlier ratios. The results on seven datasets shows our method substantially outperforms state-of-the-art techniques. 

## Introduction

With the increasing computing power and the fast-evolving deep learning technology, supervised learning is progressing fast; the state-of-the-art model has surpassed human performances on several tasks of Glue benchmark [] and is approaching human's ability on Super Glue Benchmark []. However, with little or no supervision, machine's ability in an open-world setting is still limited. Taking the task of discovering novel text category as an example,  humans can easily find new categories in texts by different intentions:  sentiment, topic, domain, etc. To test machine's ability on this task, we can hope it to generate solutions as many as possible without any supervision or we can guide the machine with a small amount of data and hope it to find a similar solution. In this paper, we adopted the later method as text classification datasets can be easily used for evaluation and no extra annotation is needed. Unlike other works [], we assume the raw data may contain outliers, so during the construction of test set, we deliberately injected outliers of various ratios. We consider this setting more closer to real open set data and hope machine can extract clusters with little outliers for purer clusters may easier to be processed afterwards. Finding new categories in this noisy setting is essential in many scenarios, for example, we may want to find novel intents in human-human conversations [], or provide relevant information to users in Internet forums [].

We proposed a method called dense-based deep ensemble clustering (DDEC) to tackle the problem. The motivation is to extract knowledge from labeled data as much as possible by means of constructing diverse base learners and apply a consensus function afterwards that takes advantages of individual results. For a base learner, a part of labeled data is used to learn a better representation, while the rest is used to tune proper hyper-parameters of a density-based clustering algorithm. This process can be repeat $K$ times and forms a set of base learners, from which a consensus partition is combined. \textbf{We summarized our contribution as follows}: first, our proposal of incorporating outliers to data is a new evaluation setting for category discovery. Moreover, DDEC is proved robust when we varies the size of the training data and the ratio of outlier. We also compared our method with strong baselines on seven datasets of two languages, where DDEC outperforms all other methods with a large margin.

## Problem formulation: the intent discovery task

The task is to discovery new intents in unknown data, however, the interpretation of intent is diverse. For example, you can group texts by several different aspect, such as by sentiment or topic. There is no absolute answer. However, if we have some intent data in advance, it is possible to exploit the hidden information in these data and find similar patterns in the unknown data. In this scenario, we can use text classification data, split them and used for evaluation. To formalize,  given a text classification data $D=\left(X, Y\right)$, where $X$ is the set of text instances and $Y$ is the corresponding label, we could split $D$ into data with $D_{L}$ and $D_{UL}$, where $D_{L}$'s label is available to us and $D_{UL}$ label is unknown and only used for evaluation, and $\left\{Y_{L}\right\} \neq\left\{Y_{UL}\right\}$, which means we hope to evaluate the ability of finding non-overlapping new intents. Unlike other works, we further expand $D_{UL}$ to contain outliers, which make this task more difficult and, the expansion will be discussed in the following section.

The problem can be redefined as follows: how could we better leveraging the knowledge contained in $D_{L}$ such that we can find a partition $\hat{Y_{UL}}$ that best resemble $Y_{UL}$.

### Method

We propose a set of ensemble based clustering methods for new intent discovery: given as input an unlabeled dataset $D_{UL}$ = \{$x_{i}$, i = 1,...,N\} and labeled dataset $D_{L}$ = \{($x_{i}$, $y_{i}$), i = 1,...,N\} of texts, our goal is to assign each text in $D_{UL}$ with a pseudo label $\hat{y_{i}}$ such that the partition $\hat{Y_{UL}}$ = \{$\hat{y_{i}}$\} best resembles the true label $Y_{UL}$.



### Related Works

Most works of new class discovery incorporates two phrases, first a model or representation is learned, then clustering is conducted based on the knowledge extracted in the first phase. 

\textbf{Knowledge transfer}:

[1] [2] [3] all proposed distill knowledge from then labeled data by training a model which predicts pair-wise similarity. [4] update representation by training on the union of labeled and unlabeled data with a classification head. [7] trained a CNN for text representation. In contrast,  [5] learns Smooth Inverse Frequency embeddings for simplicity. The labeling process can also be dynamic, [8] learn representation by alternating views of dialog.

\textbf{New Class discovery}:

[1] proposed to learn clustering by setting the number of clusters of a second network at its output layer, then train it on weak labels produced by the first-phase model. [2] share the same spirit of [1] and only replace the KL divergence loss with multi-class cross-entropy loss when training the second network. [3] and [5] both use the Deep Embedding Analysis method [9] during the clustering phase. [4] use ranking statistics as guidance for similarity and learns clusters similar to [1] [2]. [7] is a Kmeans based semi-supervised method which simultaneously learn representation and do clustering.



1. Neural network-based clustering using pairwise constraints
2. Y. C. Hsu, Z. Lv, J. Schlosser, P. Odom, and Z. Kira, “Multi-class classification without multi-class labels,” 2019. Accessed: May 25, 2020. [Online]. Available: https://github.com/GT-RIPL/L2C.
3. T.-E. Lin, H. Xu, and H. Zhang, “Discovering New Intents via Constrained Deep Adaptive Clustering with Cluster Refinement,” 2019. doi: 10.1609/aaai.v34i05.6353.
4. K. Han, S.-A. Rebuffi, S. Ehrhardt, A. Vedaldi, and A. Zisserman, “Automatically Discovering and Learning New Visual Categories with Ranking Statistics,” 2020. Accessed: May 22, 2020. [Online]. Available: http://arxiv.org/abs/2002.05714.
5. A. Hadifar, L. Sterckx, T. Demeester, and C. Develder, “A Self-Training Approach for Short Text Clustering,” 2019. doi: 10.18653/v1/w19-4322.
6. 
7. Z. Wang, H. Mi, and A. Ittycheriah, “Semi-supervised clustering for short text via deep representation learning,” 2016. doi: 10.18653/v1/k16-1004.
8. H. Perkins and Y. Yang, “Dialog intent induction with deep multi-view clustering,” 2020. Accessed: Mar. 17, 2020. [Online]. Available: https://github.com/asappresearch/.
9. DEA

## 3. The ensemble clustering method

3.1 density based clustering algorithm

3.2 Representation enhanced ensemble clustering

3.3 Semantic enhanced ensemble clustering

## Experiments

### Datasets



