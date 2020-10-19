







##Large-Scale Classification

 [^1] mentions instead of using one classifier, we can split into K classifier with p classes, K = log_p_N. It's like a N-ary tree. This paper also said "When the class number is much bigger than the dimension of the last but one layer of the network, it is better to split into K classifier".

> One of the most popular classifiers for highly multiclass learning is one-vs-all linear
> SVMs.An alternate parallelizable approach is to train all one-vs-one SVMs, and let them vote for the best class (also known as round-robin and
> all-vs-all)

> One of the reasons why multi-class classification succeeds is that selection of appropriate features from a large sparse p-dimensional vector becomes easier when the number of classes is growing. We assume that only a subset of truly significant features really contribute to separation between classes (sparsity).[^5]

> The simplest transformation of this type is to encode labels by sequences of bits. The length of the sequence does not have to be the same for each label. Then, by choosing a proper dependence structure between bits and using appropriate training and inference methods one can get a very compact representation of an extreme classification problem. In this new reduction framework, we can formulate the problem as optimizing the predictive performance under limited time and space budged.[^6]

> Classification problems with thousands or more classes often have a large range of class- confusabilities, and we show that the more-confusable classes add more noise to the em- pirical loss that is minimized during training.[^7]

## Methods

1. ECOC: to combine several binary classifiers to solve multi-class classification problems.[^4]
2. ALL-Paris
3. One-Against-all
4. represent labels as binary sequences[^6]

ECOC:

![image-20190710175451767](https://ws3.sinaimg.cn/large/006tNc79ly1g4uw76bcisj30ix0bbjtz.jpg)



## Zero shot learning

 [^8]中提到了利用semantic knowledge，这篇paper的前提是类别分为seen和unseen，seen的class就是train的时候看得到的模型，包括word embeddings, class descriptions, class hierarchy和general knowledge graph。提出了两步走的思路，首先用一个粗的分类器来决定文本属于seen class还是unseen class；如果是seen class，就过一个CNN的分类器，如果是unseen class，就过一个zero-shot分类器，zero-shot的分类器将标签信息和文本信息作为输入，0或1作为输出，只用了seen data来训练。也提出了结合ConceptNet来作feature augmentation。

![image-20190725105456808](https://ws2.sinaimg.cn/large/006tNc79ly1g5bwd1tgeoj30fm0l80vs.jpg)











## Refrence

[^1]: Q. Zhang, H. Bao, A. Grooup, and W. Li, “Large scale classification in deep neural network with Label Mapping 4 th Yuan You 5 th Dongbai Guo.”
[^2]: J. Liu, W.-C. Chang, Y. Wu, and Y. Yang, “Deep Learning for Extreme Multi-label Text Classification,” 2017.
[^3 ]:  A. Berger, “Error-Correcting Output Coding for Text Classification.”
[^4]: https://www.youtube.com/watch?v=6kzvrq-MIO0 : Machine Learning: Multiclass Classification
[^5]:  F. Abramovich and M. Pensky, “Classification with many classes: challenges and pluses,” 2017.
[^6]: K. Jasińska, K. Dembczyński, and N. Karampatziakis, “Extreme classification under limited space and time budget,” *Schedae Informaticae*, vol. 1/2016, no. December, pp. 9–23, 2017.
[^7]: Gupta, M. R., Bengio, S. and Weston, J. (2014) *Training Highly Multiclass Classifiers*, *Journal of Machine Learning Research*. Available at: http://jmlr.org/papers/volume15/gupta14a/gupta14a.pdf (Accessed: 11 July 2019).7 
[^8]: Zhang, J., Lertvittayakumjorn, P. and Guo, Y. (no date) Integrating Semantic Knowledge to Tackle Zero-shot Text Classification. Available at: https://arxiv.org/pdf/1903.12626.pdf (Accessed: 25 July 2019).