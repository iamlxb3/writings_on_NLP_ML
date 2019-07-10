# Automatic labeling

 [^1]把Semantic Parser、Filter Bank、Label Aggregator结合了起来。文中特别提出了为什么不直接用label aggregator取代discriminator的原因：aggregator只用到了LF的信息，把sample本来的信息都丢了，但是一般的discriminator可以包括所有的原始信息。

## Reference

[^1]:Hancock, B. *et al.* (no date) *Training Classifiers with Natural Language Explanations*. Available at: https://nlp.stanford.edu/pubs/hancock2018babble.pdf (Accessed: 7 May 2019).

