# Semi-supervised, active learning for NLP

## Abstract



## Introduction



### Methods

#### 1. Bootstrapping



The fact that no improvement was obtained agrees with previous observations that classifiers that are too accurate cannot be improved with bootstrapping (Pierce and Cardie, 2001)

[10]中提到了”the performance of bootstrapping approaches crucially depends on the size of the seed set“

##### self-training

Data distillation: Data distillation is a simple and natural approach based on “self-training”[^1]



##### co-training

Datasets whose features naturally partition into two sets, and algorithms that use this division, fall into the co-training setting[^3].

co-training的两个假设[^3]:

- 一个样本可以被任意一个feature所学到的模型所区分出来。

  > two views are individually sufficient for classification
- feature之间是互相条件独立的。

  > the two views are conditionally independent given the class.

和一般的co-training选择样本的方式不同，[^4]提出了agreement-based co-training的方法，把每次选中样本对模型的提升效果也考虑了进来。提出agreement-based的motivation文中也有提到，"Our agreement-based co-training results support the theoretical arguments of Abney (2002) and Dasgupta et al. (2002), that directly maximising the agreement rates between the two taggers reduces generalisation error. "

![0](https://ws4.sinaimg.cn/large/006tNc79ly1g2g1k05zjbj30d908k0ud.jpg)



### 2. Graph-based

 [^6]中提到了把domain knowledge加入到graph里面，比如edge可以代表颜色、时间等等(监控视频的任务)。

### Combine with Active Learning

![image-20190426153315020](https://ws4.sinaimg.cn/large/006tNc79ly1g2g2mojmmpj30fr07ndgm.jpg)





### 3. Active Learning

[10]提出了结合self-training和AL的方法，首先AL会根据整个句子来选择最不确定的样本(训练几个周期)，然后再切换到partial AL，也就是说每个词的实体都会计算不确定性，确定性高的就使用模型进行自动标注，不确定的才会让人去标注。



### 4. Noisy-label

 [^13]这个repo详细列出了有关noisy-label的paper， [^11][^12]都提到了noisy-label的问题，[^12]主要比较了噪音对不同分类器（NB、C4.5、IBk、SMO）的影响。

噪音的几个来源（或者是这几个来源的组合）：

- Input attributes
- Output class
- Training data
- Test dat



## TODOLIST：

- 在做新的样本label的时候，尝试用greedy的方法，就是说几个模型的输出结果是一致的时候才标注[^2]。

- bootstrap参数：iteration N, growth size, pool size

- 尝试smoothed co-training，也就是每个iteration的模型都保留下来

  

## Reference



[Difference between co-training & self-training](https://www.quora.com/Whats-the-difference-between-co-training-and-self-training-in-semi-supervised-learning-2)



[^1]: Radosavovic, I. *et al.* (no date) *Data Distillation: Towards Omni-Supervised Learning*. Available at: http://openaccess.thecvf.com/content_cvpr_2018/papers/Radosavovic_Data_Distillation_Towards_CVPR_2018_paper.pdf (Accessed: 25 March 2019).

[^2 ]: Mihalcea, R. (no date) *Co-training and Self-training for Word Sense Disambiguation*. Available at: https://www.aclweb.org/anthology/W04-2405 (Accessed: 19 April 2019).
[^3]:Nigam, K. and Ghani, R. (no date) *Analyzing the Effectiveness and Applicability of Co-training*. Available at: http://www.kamalnigam.com/papers/cotrain-CIKM00.pdf (Accessed: 19 April 2019).
[^4]: Clark, S., Curran, J. R. and Osborne, M. (no date) *Bootstrapping POS taggers using Unlabelled Data*. Available at: http://delivery.acm.org/10.1145/1120000/1119183/p49-clark.pdf?ip=103.126.92.84&id=1119183&acc=OPEN&key=4D4702B0C3E38B35.4D4702B0C3E38B35.4D4702B0C3E38B35.6D218144511F3437&__acm__=1555638128_b5fd3bde320387ea072f2e722258d929 (Accessed: 19 April 2019).
[^5]:http://www.cs.upc.edu/~horacio/snlp/bootstrapping-slides2012.pdf  不错的一个PPT
[^6]:Zhu, X. (no date) *Semi-Supervised Learning Literature Survey*. Available at: http://pages.cs.wisc.edu/~jerryzhu/pub/ssl_survey.pdf (Accessed: 18 April 2019).
[^7 ]: (bootstrap相关的很好的blog)[http://ruder.io/semi-supervised/index.html#selfensembling]

[^8]: Edu, M., Minton, S. and Knoblock, C. A. (no date) Active + Semi-Supervised Learning = Robust Multi-View Learning Ion Muslea. Available at: http://usc-isi-i2.github.io/papers/muslea02-icml-robust.pdf (Accessed: 26 April 2019).
[^9]: A two-phase hybrid of semi-supervised and active learning approach for sequence labeling 没找到下载的地方
[^10]: Tomanek, K. and Hahn, U. (2009) *Semi-Supervised Active Learning for Sequence Labeling*, *ACL and AFNLP*. Available at: http://delivery.acm.org/10.1145/1700000/1690291/p1039-tomanek.pdf?ip=103.126.92.84&id=1690291&acc=OPEN&key=4D4702B0C3E38B35.4D4702B0C3E38B35.4D4702B0C3E38B35.6D218144511F3437&__acm__=1556265333_8e311e382c00fed597997ea21ab2944a (Accessed: 26 April 2019).
[^11]: Natarajan, N. *et al.* (no date) *Learning with Noisy Labels*. Available at: https://papers.nips.cc/paper/5073-learning-with-noisy-labels.pdf (Accessed: 10 March 2019).
[^12]:Nettleton, D. F. *et al.* (2010) ‘A study of the effect of different types of noise on the precision of supervised learning techniques’, *Artif Intell Rev*, 33, pp. 275–306. doi: 10.1007/s10462-010-9156-z.
[^13]: https://github.com/GuokaiLiu/Noisy-Labels-Problem-Collection