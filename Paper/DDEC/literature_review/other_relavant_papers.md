Title: **Deep unknown intent detection with margin loss**

ID: 90521586562ef699a295ff3f33ef1cb1f67b5b3c

Has been read 1 times.

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

