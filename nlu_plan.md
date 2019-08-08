# NLU_PLAN

## Overview

| Task                   | Dataset                                                      | Progress | Result    | Sota      |
| ---------------------- | ------------------------------------------------------------ | -------- | --------- | --------- |
| Text Classification    | LSHTC (英文)                                                 |          |           |           |
|                        | [amazon (中文)](https://github.com/SophonPlus/ChineseNlpCorpus/blob/master/datasets/yf_amazon/intro.ipynb) |          |           |           |
|                        |                                                              |          |           |           |
| NER                    | MSRA (中文)                                                  | 100%     | 91.2 (F1) |           |
|                        | 人民日报1998 (中文)                                          |          |           |           |
|                        | 人民日报2004 (中文)                                          |          |           |           |
|                        | boson数据 (中文)                                             |          |           |           |
|                        | SIGHAN Bakeoff 2005 (中文)                                   |          |           |           |
|                        | 混合                                                         |          |           |           |
|                        | [CoNLL 2003 (英文)](https://paperswithcode.com/sota/named-entity-recognition-ner-on-conll-2003) |          |           |           |
|                        | [Ontonotes v5 (英文)](https://paperswithcode.com/sota/named-entity-recognition-ner-on-ontonotes-v5) |          |           |           |
| Coreference Resolution | CoNLL2012 英文                                               |          |           | 73.0 (F1) |
|                        | CoNLL2012 中文                                               |          |           |           |
| Ellipsis Resolution    | Converse (2006)                                              |          |           |           |
|                        | OntoNote5.0                                                  |          |           |           |
| Text Augmentation      | /                                                            |          |           |           |
| Text Clustering        | /                                                            |          |           |           |
|                        |                                                              |          |           |           |
|                        |                                                              |          |           |           |
|                        |                                                              |          |           |           |
|                        |                                                              |          |           |           |
|                        |                                                              |          |           |           |
|                        |                                                              |          |           |           |
|                        |                                                              |          |           |           |



### Text Classification

#### THUCTC

**Links**

\- [THUCNews 中文](http://thuctc.thunlp.org)

###Coreference Resolution

#### \- CoNLL 2012 English

​	**Sota**:

​	\- Sota Avg F1: 73.0

​	\- Sota Paper: [Higher-Order Coreference Resolution with Coarse-to-Fine Inference](https://www.aclweb.org/anthology/N18-2108)

​	**Papers with code**:

​	\- [(Pytorch) End-to-end Neural Coreference Resolution](https://github.com/shayneobrien/coreference-resolution)

​	\- [(Tf) Higher-order Coreference Resolution with Coarse-to-fine Inference *SOTA](https://github.com/kentonl/e2e-coref)

​	**Links**:

​	\- [CoNLL Dataset Download](http://conll.cemantix.org/2012/data.html)

​	\- [CoNLL Result & code](https://paperswithcode.com/sota/coreference-resolution-on-conll-2012)

​	\- [CoNLL Dataset Paper](https://www.aclweb.org/anthology/W12-4501)

#### \- **CoNLL 2012 Chinese**

​	Papers:

​	\- [Improving Coreference Resolution by Learning Entity-Level Distributed Representations](https://arxiv.org/pdf/1606.01323.pdf)

#### \- Reference



### Text Clustering

**Papers with code**:

\- [(tf) Self-Taught Convolutional Neural Networks for Short Text Clustering](https://github.com/jacoxu/STC2)

\- [STTM: A Library of Short Text Topic Modeling](https://github.com/qiang2100/STTM)



### GLUE

|                                                              | Description                                                  | Src                                                          | Example                                                      | Metric                                                       | progress | result | Sota |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | :----------------------------------------------------------- | ------------------------------------------------------------ | -------- | ------ | ---- |
| [CoLA](<br />https://nyu-mll.github.io/CoLA/)                | Gramma acceptability Binary Classification<br />Input: English Sentence<br />Output: (acceptable / not acceptable) | 22 books and journal articles on linguistic theory           | Label1: The book was written by John. <br />Label0: Books were sent to each other by the students. | Matthews correlation coefficient                             |          |        |      |
| [SST-2](https://nlp.stanford.edu/sentiment/)                 | Binary Classification<br />Input: English Sentence<br />Output: (positive / negative) | Movie reviews                                                | Label1:The actors are fantastic.<br/>Label0: This movie was actually neither that funny, nor super witty. | /                                                            |          |        |      |
| [MPRC](https://www.microsoft.com/en-us/download/details.aspx?id=52398) | Determine semantic equivalence.<br />Input:                  | Online news sources                                          | /                                                            | accuracy and F1                                              |          |        |      |
| [QQP](https://www.kaggle.com/quora/question-pairs-dataset)   | Determine semantic equivalence.<br />                        | Quora question pairs                                         | Duplicate: [What does manipulation mean? \| What does manipulation means?]<br />Not Duplicate:[How much is 30 kV in HP? \| Where can I find a conversion chart for CC to horsepower?] | accuracy and F1                                              |          |        |      |
| [STS-B](http://ixa2.si.ehu.es/stswiki/index.php/STSbenchmark) | compare among meaning representation                         | image captions, news headlines and user forums               | Similarity5: [A man with a hard hat is dancing. \| A man wearing a hard hat is dancing.]<br />Similarity0.0: [The man is riding a horse. \| A woman is using a hoe.] | Pearson and Spearman correlation coefficient                 |          |        |      |
| [MNLI](https://www.nyu.edu/projects/bowman/multinli/)        | to predict whether the premise entails the hypothesis.       | It is crowd-sourced collection of 433k sentence. The corpus is modeled on the [SNLI corpus](https://nlp.stanford.edu/projects/snli/), but differs in that covers a range of genres of spoken and written text | *neutral*:[**Premise** The Old One always comforted Ca'daan, except today. \| **Hypothesis **Ca'daan knew the Old One very well.]<br />*entailment*: [**Premise** At the other end of Pennsylvania Avenue, people began to line up for a White House tour. \| **Hypothesis** People formed a line at the end of Pennsylvania Avenue.] | [Average of Mathews correlation, Accuracy and Pearson correlation](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/language-unsupervised/language_understanding_paper.pdf) |          |        |      |
| QNLI                                                         | Input: question and  sentence pair<br />To determine whether the context sentence contains the answer to the question | The Stanford Question Answering Dataset SQuAD. We automatically convert the original [SQuAD](https://rajpurkar.github.io/SQuAD-explorer/) dataset into a sentence pair classification task by forming a pair between a question and each sentence in the corresponding context. The | /                                                            | /                                                            |          |        |      |
| [RTE](https://aclweb.org/aclwiki/Textual_Entailment_Resource_Pool) | to predict whether the premise entails the hypothesis. We convert all the data to a two-class split (entailment or not entailment, where we collapse neutral and contradiction into not entailment for challenges with three classes) for consistency. | RTE1, RTE2, RTE3, RTE5, [RTE description](https://tac.nist.gov/2009/RTE/RTE5_Main_Guidelines.pdf) | Similar to MNLI                                              |                                                              |          |        |      |
| [WNLI](http://commonsensereasoning.org/winograd.html)        | The Winograd Schema Challenge. To convert the problem into a sentence pair classification task, we construct two sentence pairs per example by replacing the ambiguous pronoun with each possible referent. The task (a slight relaxation of the original Winograd Schema Challenge) is to predict if the sentence with the pronoun substituted is entailed by the original sentence. | [collection](https://cs.nyu.edu/faculty/davise/papers/WinogradSchemas/WSCollection.xml) | Similar to MNLI                                              |                                                              |          |        |      |

**Links**

\- [CoLA Dataset](https://nyu-mll.github.io/CoLA/)



### Super Glue
