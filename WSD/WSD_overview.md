# WSD

## Introduction

WSD are based on Distributional Hypothesis which works under the assumption that similar words occur in similar contexts (Harris, 1954)[^2]. 



Most of the existing WSD algorithms (Agirre and Edmonds, 2006; Navigli, 2009) are commonly classified into **supervised, unsupervised, semi-supervised[^3], and knowledge-based[^5] techniques**, but hybrid approaches have also been proposed in the literature.



**Standard WSD tasks**:

**- Local-Level WSD**: such as the extended Lesk measure[^4], is designed to assign the appropriate sense, from an existing sense inventory, for a target word in a given context window of a few words. For instance, for the word “sense” in the context “You have a good sense of humor.”, the sense that corresponds to the natural ability rather than the meaning ofa word or the sensation should be chosen by a WSD algorithm. Rather.[^1]

**- Global-Level WSD**: a global WSD approach aims to choose the appropriate sense for each ambiguous word in a text document. The straightforward solution is the exhaustive evaluation of all sense combinations (configurations). Alternatives: a Genetic Algorithm, Simulated Annealing, and Ant Colony Optimization. [^1]

**Strongest baseline**: Most Common Sense (MCS)



---

Others:

all-words exercises (which comprise all words occurring in a running text, and where training data is more scarce) show that only a few systems beat the most frequent sense (MFS) heuristic, with

---



## Features

### Standard WSD features[^3]
- Bag of words for context
- Pos tagging for context
- Local collocations 
- syntactic relations
- LDA
- LSA
- word embedding for context [^3]

## Methods

###Supervised



### Unsupervised

#### 1. ShotgunWSD[^1]

- it requires knowledge in the form of WordNet synsets and relations as well.
- Unsupervised

2. 使用LSTM作LM[^6]，然后使用label propagation来预测[^7]。

###Knowledge-based methods

[^1]: Butnaru, A. M. and Hristea, F. (no date) *ShotgunWSD: An unsupervised algorithm for global word sense disambiguation inspired by DNA sequencing*. Available at: http://ai.fmi.unibuc.ro/Home/Software. (Accessed: 3 March 2019).
[^2]: Bhingardive, S. *et al.* (no date) *Unsupervised Most Frequent Sense Detection using Word Embeddings*. Available at: http://web.eecs.umich.edu/ (Accessed: 4 March 2019).
[^3]: Iacobacci, I., Pilehvar, M. T. and Navigli, R. (no date) Embeddings for Word Sense Disambiguation: An Evaluation Study. Available at: www.paraphrase.org/#/download (Accessed: 2 March 2019).
[^4]: Banerjee, S. and Pedersen, T. (2002) Adapting the Lesk Algorithm for Word Sense Disambiguation to WordNet. Available at: http://www.d.umn.edu/~tpederse/Pubs/banerjee.pdf (Accessed: 4 March 2019).
[^5]: Agirre, E., de Lacalle,  opez and Soroa, A. (2014) ‘Random Walks for Knowledge-Based Word Sense Disambiguation’. doi: 10.1162/COLI.
[^6]: Le, M. *et al.* (no date) *A Deep Dive into Word Sense Disambiguation with LSTM*. Available at: http://aclweb.org/anthology/C18-1030 (Accessed: 6 March 2019).
[^7]: Zhu, X. and Ghahramani, Z. (no date) *Learning from Labeled and Unlabeled Data with Label Propagation*. Available at: https://pdfs.semanticscholar.org/8a6a/114d699824b678325766be195b0e7b564705.pdf (Accessed: 7 March 2019).