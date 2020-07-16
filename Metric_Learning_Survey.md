# Metric Learning Related Works

We are interested in the following problem: Suppose texts and clusters are corrected and labeled by users, how can we learn a distance metric that better respects those labeled data and yield a better clustering result afterward? Metric Learning maybe one answer.

The goal of metric learning is to learn a new metric to bring similar objects closer while increasing the distance of dissimilar objects. In the process of constructing a high-quality SLU smalltalk dataset, a new distance metric can be learned from the previous human-labeled clusters in each turn. The term "metric learning" is somewhat misleading as most of the researches focus on "representation learning" rather than learning a new distance metric [[1]](#1) .  

Literature of metric learning can be roughly divided into two categories: one that projects samples of same class to a single point and the other one which respect the intra-class variants.

## Intra-class variants are omitted

One traditional method of the first category is learning with Mahalanobis distance. It linearly projects the data to a new space with higher discrimination power. Although the method can be solved in convex optimization, the linear transformation has limited representation capabilities. 

![image-20200506151306699](https://tva1.sinaimg.cn/large/007S8ZIlly1gennimiouhj30hj01t0sq.jpg)

Unlike those linear models, deep learning can better interpret non-linear properties in data [[1]](#1). Contrastive loss with Siamese network [[5]](#5) uses pairs of similar and dissimilar samples to encode distance relationship, but it has drawbacks that positive samples and negative samples are optimized independently. 

![Figure. Siamese Architecture](https://tva1.sinaimg.cn/large/007S8ZIlly1gennirx4cxj30fx0cywf2.jpg)
<center>Figure. Siamese Architecture [[2]](#2) </center>

To address the above issue, Triplot loss [[6]](#6) is proposed, which consists of one anchor sample, one positive sample and one negative sample.

![image-20200506154739880](https://tva1.sinaimg.cn/large/007S8ZIlly1gennistbfqj30fm0i174y.jpg)
<center>Figure. Triplot Net Architecture</center>

![image-20200506155000695](https://tva1.sinaimg.cn/large/007S8ZIlly1gennit7vk5j30eh0713yx.jpg)
<center>Figure. Triplot Loss (left) vs N-pair loss (right)</center>

 Similar approaches include Quadruplet loss [[11]](#11) and N-pair loss [[10]](#10).  Built on above mentioned methods, lifted structured feature embedding [[12]](#12) replace the hinge loss with a smooth loss using exponential weighting, aiming to push all negative point farther than a margin.

![image-20200506200924449](https://tva1.sinaimg.cn/large/007S8ZIlly1genniwhpjwj30g6046glt.jpg)
<center>Figure. lifted structured feature embedding</center>

 Angular loss [[13]](#13) improve on the basis of N-pair loss and provide scale invariance on the embedding. 

However, they all face the same problem: data has to be prepared before training. Sampling method includes hard sampling and semi-hard sampling.


![image-20200506153839656](https://tva1.sinaimg.cn/large/007S8ZIlly1gennis9xr0j309p09n0su.jpg)
<center>Figure. Sample strategy [[1]](#11) </center>

Structured clustering loss [[7]](#7), softmax loss [[8]](#8) do not require **data preparation**. Clustering loss aims to find a representation which leads to a clustering result being as close as possible to the actual label, and it also incorporates NMI in the loss function; the motivation is to overcome the downsides of local metric learning, which is shown in below figures.

![image-20200506155736703](https://tva1.sinaimg.cn/large/007S8ZIlly1gennivjmzuj30gx0amjtc.jpg)

![image-20200506155752048](https://tva1.sinaimg.cn/large/007S8ZIlly1genniw1hr4j30h30e8tbd.jpg)

Although literatures of Siamese-network and others claimed better results, their superiority is not fully explained, [[8]](#8) argued that , in contrary to what is claimed in each paper, optimizing a softmax classifier can yield significant better result in many settings, which question the necessity to prepare data and learning a new representation by a Siamese like network; the author hypothesizes the unstable training of Siamese like network may contribute to the inferior performance because negative samples are changing each round  while the whole training data remain fixed for the softmax classifier.

Prototypical loss and proxy loss [[4]](#4) compute a representation point for class as "proxy" point; samples used for computing are sampled randomly so the cost of **data preparation** process is quite trivial. A soft-max is formed over classes, which is optimized based on the euclidean distance in the new transformed space. Because proxy points are fewer than samples, strong regularization are needed to avoid overfitting.

![image-20200507102009979](https://tva1.sinaimg.cn/large/007S8ZIlly1gennito00fj30cy02e0sr.jpg)

## Intra-class variants are considered

The first category tries to squeeze all samples of one class to a single point, disregarding intra-class variants. [[14]](#14) proposed magnet loss which tries to separate dense region while retaining intra-class variants.

![image-20200506200132414](https://tva1.sinaimg.cn/large/007S8ZIlly1genniutjtyj30wr0e7gp1.jpg)

![image-20200506200048689](https://tva1.sinaimg.cn/large/007S8ZIlly1gennix1jypj30s80can05.jpg)

 [^15] proposed ranked list loss that learns a hyper-sphere for each class by constraining the distance of all positive samples below a certain threshold while pushing those neg samples farther away.

![image-20200506201347132](https://tva1.sinaimg.cn/large/007S8ZIlly1gennixfbe8j30yu0893zi.jpg)

 [[18]](#18) suggested an assumption: embedding features of the samples of the same classes consists of two parts; one that represents intra-class invariance and the other represents intra-class variance which obeys the identical distribution across different classes. By introducing a VAE-like generator, the intra-class variance is represented by a multi-variational Gaussian distribution, from which synthetic samples are generated. And those samples are added to the loss function to improve generalization. The motivation is that simple samples have little contribute to decision boundary, but can be utilized to learn a proper intra-class variance.

An overview of loss functions:

![image-20200507094314520](https://tva1.sinaimg.cn/large/007S8ZIlly1genniu63fuj30mj0hhju6.jpg)

## Other methods

The essence of Ensemble learning [[4]](#4) [[16]](#16) is to form a strong model with many weak ones. A strong representation can also be formed by many weak ones; each model sees a subset of data partitioned on class labels and the final embedding is derived by concatenating each independent embeddings.

Methods mentioned above are all supervised,  [[3]](#3) proposed a way of **unsupervised representation learning**. Instead of optimizing weights, the model (Siamese network) directly output features and distances of intra-class and inter-class are minimized and spread out respectively. The training data is compose as follows: the positive samples are constructed by typical image augmentation method while negative samples are randomly chosen.

![image-20200506130718432](https://tva1.sinaimg.cn/large/007S8ZIlly1gennixw44rj30bx02rmx6.jpg)

## Reference

<a id="1">[1]</a> _Kulis, B. (2012) ‘Metric Learning: A Survey [cite: 599]’, *Foundations and Trends R in Machine Learning*, 5(4), pp. 287–364. doi: 10.1561/2200000019._ 
<a id="2">[2]</a> _Xing, E. P. *et al.* (2002) *Distance metric learning, with application to clustering with side-information [cite: 3143]*. Available at: https://ai.stanford.edu/~ang/papers/nips02-metric.pdf (Accessed: 21 April 2020)._
<a id="3">[3]</a> _Ye, M. et al. (2019) Unsupervised Embedding Learning via Invariant and Spreading Instance Feature. Available at: http://openaccess.thecvf.com/content_CVPR_2019/papers/Ye_Unsupervised_Embedding_Learning_via_Invariant_and_Spreading_Instance_Feature_CVPR_2019_paper.pdf (Accessed: 25 April 2020)._
<a id="4">[4]</a> _Fehérvári, I., Ravichandran AWS, A. and Appalaraju Amazon, S. (2019) Unbiased Evaluation of Deep Metric Learning Algorithms [cite: 1]. Available at: https://mxnet.apache.org/ (Accessed: 28 April 2020)._
<a id="5">[5]</a> _Chopra, S., Hadsell, R. and Lecun, Y. (no date) Learning a Similarity Metric Discriminatively, with Application to Face Verification. Available at: http://yann.lecun.com/exdb/publis/pdf/chopra-05.pdf (Accessed: 6 May 2020)._
<a id="6">[6]</a> _Hoffer, E. and Ailon, N. (2014) DEEP METRIC LEARNING USING TRIPLET NETWORK [cite: 657]. Available at: https://arxiv.org/pdf/1412.6622.pdf (Accessed: 23 April 2020)._
<a id="7">[7]</a> _Oh Song, H. et al. (2016) Deep Metric Learning via Facility Location [cite: 153]. Available at: http://xxx.itp.ac.cn/pdf/1612.01213.pdf (Accessed: 30 April 2020)._
<a id="8">[8]</a> _Horiguchi, S., Ikami, D. and Aizawa, K. (2017) ‘Significance of Softmax-Based Features Over Metric Learning-Based Features [cite:22]’, pp. 1–10._
<a id="9">[9]</a> _Hoffer, E. and Ailon, N. (2014) DEEP METRIC LEARNING USING TRIPLET NETWORK [cite: 657]. Available at: https://arxiv.org/pdf/1412.6622.pdf (Accessed: 23 April 2020)._
<a id="10">[10]</a> _Sohn, K. (2016) Improved Deep Metric Learning with Multi-class N-pair Loss Objective [cite: 374]. 
<a id="11">[11]</a> _Law, M. T., Thome, N. and Cord, M. (2017) ‘Learning a Distance Metric from Relative Comparisons between Quadruplets of Images [cite: 22]’, International Journal of Computer Vision. Springer US, 121(1), pp. 65–94. doi: 10.1007/s11263-016-0923-4._
<a id="12">[12]</a> _Song, H. O. et al. (2013) Deep Metric Learning via Lifted Structured Feature Embedding [cite: 477]. Available at: https://arxiv.org/pdf/1511.06452.pdf (Accessed: 25 April 2020)._
<a id="13">[13]</a> _Wang, J. et al. (2017) Deep Metric Learning with Angular Loss [cite: 153]. Available at: http://xxx.itp.ac.cn/pdf/1708.01682.pdf (Accessed: 30 April 2020)._
<a id="14">[14]</a> _Rippel, O. et al. (2015) METRIC LEARNING WITH ADAPTIVE DENSITY DISCRIMINATION [cite: 126]. Available at: https://arxiv.org/pdf/1511.05939.pdf (Accessed: 25 April 2020)._
<a id="15">[15]</a> _Wang, X. et al. (2019) Ranked List Loss for Deep Metric Learning [cite: 19]. Available at: https://github.com/XinshaoAmosWang/ (Accessed: 1 May 2020)._
<a id="16">[16]</a> _Xuan, H., Souvenir, R. and Pless, R. (2018) Deep Randomized Ensembles for Metric Learning. Available at: https://github.com/littleredxh/DREML (Accessed: 28 April 2020)._
<a id="17">[17]</a> _Lin, X. et al. (2018) Deep Variational Metric Learning. Available at: https://github.com/XudongLinthu (Accessed: 28 April 2020)._
<a id="17">[18]</a> Lin, X. *et al.* (2018) *Deep Variational Metric Learning*. Available at: https://github.com/XudongLinthu (Accessed: 28 April 2020).