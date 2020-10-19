## Background

GAN has achieved success in computer version, however, the discrete nature of text renders the model non-differentiable, hindering use of GAN in natural language processing tasks.

RL-based and Gumbel-softmax are two common ways to address the non-differentiable issue. Examples of RL-based include SeqGAN, MaliGAN, RankGAN, LeakGAN and MaskGAN. Despite they have promising performance, the biggest disadvantage is that they yield high-variance gradient estimates.

 [^5] address the discrete oupt space problem by simply forcing the discriminator to operate on continuous valued output distribution.
![image-20191210142647177](/Users/jiashupu/writings_on_NLP_ML/image-20191210142647177.png![image-20191210142712770](https://ws4.sinaimg.cn/large/006tNbRwly1g9rm0bjj0mj30hj0gdjsd.jpg)

## Terminology



## Gan methods

### VAE related

- Randomly sample the latent space[^3]

### Terminology

- Mode collapse**: the generator collapses which produces limited varieties of samples.[^1]

### Metrics for evaluating Text Gan[^2]

#### How generated text resemble the natural language

- BLEU
- NLL-oracle
- NLL-test

#### Diversity

- Self-BLEU

### Reference

[^1]: https://medium.com/@jonathan_hui/gan-why-it-is-so-hard-to-train-generative-advisory-networks-819a86b
[^2]: Zhu, Y. et al. (no date) Texygen: A Benchmarking Platform for Text Generation Models. Available at: http://cocodataset.org/ (Accessed: 27 November 2019).
[^3]: https://www.exptechinc.com/machine-learning/fighting-gan-mode-collapse-by-randomly-sampling-the-latent-space/
[^4]:Chen, L. *et al.* (no date) *Adversarial Text Generation via Feature-Mover’s Distance*. Available at: https://papers.nips.cc/paper/7717-adversarial-text-generation-via-feature-movers-distance.pdf (Accessed: 10 December 2019).
[^5]: Subramanian, S. et al. (2017) Adversarial Generation of Natural Language. Available at: https://www.aclweb.org/anthology/W17-2629.pdf (Accessed: 10 December 2019).



### Github Repo

- [Texygen](https://github.com/geek-ai/Texygen/blob/master/docs/doc.md)



一些参考资料:

- [让机器自动生成文本数据--NLP文本数据增强方法简述](https://zhuanlan.zhihu.com/p/75207641)
- 