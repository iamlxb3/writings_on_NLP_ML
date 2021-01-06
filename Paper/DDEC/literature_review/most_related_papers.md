**Title: Discovering New Intents via Constrained Deep Adaptive Clustering with Cluster Refinement**

ID: 4910fec58496606b1723308c31e9faf53bee787b

Has been read 5 times.

Problem:  The definition of intents is versatile, the prior knowledge needs to be properly leveraged. Existing methods requires intensive feature engineering.

Dataset: SNIPS, DBPedia, StackOverflow

Contribution:

1. The author purposed an end-to-end clustering method that is insensitive to the number of clusters.
2. The method shows significant improvement on the above datasets compared with strong baselines.

Novelty:

1. The author proposed a method to binarize self-labeled similarity by a certain threshold. The threshold is gradually changed so that only the most "certain" pairs were labeled 1 at the beginning but the degree of certainty gradually decreases as the training process.

Merit: 

1. A comprehensive strong baselines are compared.
2. The author somehow managed  to fuse two ideas and yield good results.

Weakness: 

1. Datasets are small, with the average of classes being around 12.
2. By merging two existing methods with little modification, the novelty is questionable.
3. The implementation detail is vague, lacking a simple example to demonstrate the whole process.
4. How the self-labeling process would change the result is not fully analyzed and discussed.
5. The question to address is too general, the author failed to mention previous works on this question and build on top of the previous papers.

---

Title: **Dialog Intent Induction with Deep Multi-View Clustering**

ID: fc8ba1082c5c7311656f0127f75694d4098f29a0

Has been read 4 times.

Year: 2020

Venue: EMNLP, IJCNLP

Author: Perkins Hugh, Yang Yi

Problem: Dialog data has multi-turn questions and responses, when doing clustering of user utterance, the  context of which are usually omitted.

Dataset: Twitter airline customer support, AskUbuntu

Contribution:

1. Proposed a novel multi view K-means clustering techniques for inducing the dialog intent and the instance representation is changed iteratively by shifting the view, to be more specific, by shifting between the query and its contexts. The pseudo-label of the view is used to update the representation.
2. Fill the gap of the intent discovery of multi turn intent discovery

Novelty:

Merit:

Weakness:

---

**Title: Supervised Clustering of Questions into Intents for Dialog System Applications**

ID: 9d2f9442e3226cc071ea09a9f7f1eaa0114714b2

Has been read 1 times, still a bit confused

Problem:  detect intents of user questions

Dataset: 

Contribution:

1. They claim annotated data can explicitly provide the notion of intent, in other words, to learn definitions from examples 
2. Providing a tool to help dialog manager to build intent more easily
3. Can dynamically cluster questions with the same semantics without any concept annotation.

Method: 

I didn't fully understand all the details. First the text's feature is extracted by some traditional means, like td-idf, etc. Then pair-wise similarity is caculated by a function, but in the paper that function is not mentioned. Next, a graph partition method is applied, and the resulting pseudo label served as latent variables, lastly Structural learner LSSVM is used to label "the sequence".

Novelty:

Merit: 

Weakness: 

Other take aways:

1. In related works, the paper mentioned other two ways of data-driven model. The first method relies on tree structure  and maps a Natural Language query to it, but it has a weakness as new intent trees is required for new domains. The other way takes advantages of external knowledge bases such as Wikipedia and Freebase.
2. 

