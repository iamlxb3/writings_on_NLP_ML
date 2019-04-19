# Bootstrapping



Data distillation: Data distillation is a simple and natural approach based
on “self-training”[^1]

The fact that no improvement was obtained agrees with previ- ous observations that classifiers that are too accurate cannot be improved with bootstrapping (Pierce and Cardie, 2001)



[Difference between co-training & self-training](https://www.quora.com/Whats-the-difference-between-co-training-and-self-training-in-semi-supervised-learning-2)

TODOLIST：

- 在做新的样本label的时候，尝试用greedy的方法，就是说几个模型的输出结果是一致的时候才标注[^2]。
- bootstrap参数：iteration N, growth size, pool size
- 尝试smoothed co-training，也就是每个iteration的模型都保留下来



### Co-training

Datasets whose features naturally partition into two sets, and algorithms that use this division, fall into the co-training setting[^3].

**Co-training的两个假设[^3]**

- 一个样本可以被任意一个feature所学到的模型所区分出来。
- feature之间是互相条件独立的。

和一般的co-training选择样本的方式不同，[^4]提出了agreement-based co-training的方法，把每次选中样本对模型的提升效果也考虑了进来。"Our agreement-based co-training results support the theoretical arguments of Abney (2002) and Dasgupta et al. (2002), that directly maximising the agreement rates between the two taggers reduces generalisation error. Examination"

### Self-training







[^1]: Radosavovic, I. *et al.* (no date) *Data Distillation: Towards Omni-Supervised Learning*. Available at: http://openaccess.thecvf.com/content_cvpr_2018/papers/Radosavovic_Data_Distillation_Towards_CVPR_2018_paper.pdf (Accessed: 25 March 2019).

[^2 ]: Mihalcea, R. (no date) *Co-training and Self-training for Word Sense Disambiguation*. Available at: https://www.aclweb.org/anthology/W04-2405 (Accessed: 19 April 2019).
[^3 ]: Nigam, K. and Ghani, R. (no date) *Analyzing the Effectiveness and Applicability of Co-training*. Available at: http://www.kamalnigam.com/papers/cotrain-CIKM00.pdf (Accessed: 19 April 2019).
[^4 ]:Clark, S., Curran, J. R. and Osborne, M. (no date) *Bootstrapping POS taggers using Unlabelled Data*. Available at: http://delivery.acm.org/10.1145/1120000/1119183/p49-clark.pdf?ip=103.126.92.84&id=1119183&acc=OPEN&key=4D4702B0C3E38B35.4D4702B0C3E38B35.4D4702B0C3E38B35.6D218144511F3437&__acm__=1555638128_b5fd3bde320387ea072f2e722258d929 (Accessed: 19 April 2019).

[^5]:http://www.cs.upc.edu/~horacio/snlp/bootstrapping-slides2012.pdf  不错的一个PPT