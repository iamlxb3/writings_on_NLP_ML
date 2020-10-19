Title: Discovering New Intents via Constrained Deep Adaptive Clustering with Cluster Refinement [10/10]

Year: 2019

Venue: AAAI

Author: Lin, Ting-En Xu, Hua Zhang, Hanlei

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

Title: Dialog Intent Induction with Deep Multi-View Clustering [4/10]

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

Title: Deep unknown intent detection with margin loss

Year: 2019

Author: Lin, Ting En Xu, Hua

Problem: Identifying the novel intent and discriminate the existing intent from the unlabeled data is challenging

Venue: ACL

Dataset: SNIPS, ATIS (Airline Travel Information System) 2

Contribution: The author proposed a two-stage method for unknown intent detection. The first stage is to train BilSTM with margin loss and the second stage is to detect unknown intents by leveraging local outlier detector. It is based on the intuition that sample with local density than its neighbors has a higher chance of being unknown intents

Novelty:

Merits:

Weakness:

1. This method can only discriminate unknown intents from known ones, however, the possible intent structure in the unknown intents is not exploited.

---

Title: Enhancement of Short Text Clustering by Iterative Classification [3/10]

Year: 2020

Author: Rakib, Md Rashadul Hasan Zeh, Norbert Jankowska, Magdalena Milios, Evangelos

Problem: Clustering of short texts is challenging task

Contribution: 

The author proposed an iterative clustering process. In each iteration, a classifier is trained with non-outlier samples, then the outliers are reclustered by the classifier's prediction.

Remark:

I stopped reading this paper because its presentation is quite messy: the notation is not clear.

---

