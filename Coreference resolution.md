# Coreference resolution

## 简介

###CR的分类：

- Zero Pronoun Resolution(零回指)[^2]

  > 苏小姐跟鲍小姐同舱，睡的是下铺，比鲍小姐方便得多，不必每天爬上爬下。

- anaphora Resolution[^1]

- Pronouns Resolution

### CR数据集

- ontonote5.0
- CoNLL 2011 shared task

### CR metric[^8]

- MUC
- B-cubed
- CEAF_e

### Rule based Coreference resolution

 [^7]和[^8]都属于rule based的方法

### Baselines of Coreference resolution

- STANFORD sieves[^7]
- BERKELEY mention ranking[^5]
- MENTRANKER ranking-based[^6]

### Difficulty of pronoun resolution[^3]

Pronoun resolution可以被分为traditional anaphora和Winograd schemas。[^3]

> a. The outlaw shot the sheriff, but he did not shoot the deputy.
>
> b. The outlaw shot the sheriff, but he shot back.

这种情况被称为"Winograd Schema"[^4], [^3]提出了用narrative chains和page counts returned by a search engine来解决，但是都有一定的局限性。Winograd Schema的另一个例子：

> The trophy would not fit in the brown suitcase because it was too big (small). What was too big (small)?

## 未整理

> Shallow semantic attributes (e.g., gender and number) and grammatical relations would be useful for the traditional anaphora resolution. [^3]

> Coreference resolution is a multi-faceted task: hu- mans resolve references by exploiting contextual and grammatical clues, as well as semantic infor- mation and world knowledge. [^5]
>
> Coreference resolution, the task of identifying which mentions in a text refer to the same real-world entity, is fundamentally a clustering problem.[]

###其他

Bridging Anaphora:

> We went to see **a concert** last night. **The tickets** were really expensive.

CS224N提到了Anaphora和coref应该区分开来的理由：

> Anaphora的人称代词仅仅会指向最近的一个代词，而coref则很有可能会把某个人称代词和很多其他mention整合在一起。
>
> ![image-20190529175503793](https://ws4.sinaimg.cn/large/006tNc79ly1g3ic6jztq6j30l40eqwmc.jpg)



### 开源软件

- [Hugging Face 仅英文](https://github.com/huggingface/neuralcoref)
- Standford CoreNLP

## Reference

[^1]: [coreference resolution和anaphora resolution的区别](https://linguistics.stackexchange.com/questions/11506/what-is-the-difference-between-coreference-resolution-and-anaphora-resolution)
[^2]: [wiki上对于零回指的解释](https://zh.wikipedia.org/wiki/零回指)
[^3]: C. Kruengkrai, N. Inoue, J. Sugiura, and K. Inui, “An Example-Based Approach to Difficult Pronoun Resolution,” 2014.
[^4]: http://commonsensereasoning.org/winograd.html
[^5]:G. Durrett and D. Klein, “Easy Victories and Uphill Battles in Coreference Resolution,” 2013.
[^6]: A. Rahman and V. Ng, “Resolving Complex Cases of Definite Pronouns: The Winograd Schema Challenge,” Association for Computational Linguistics, 2012.
[^7]:  H. Lee, Y. Peirsman, A. Chang, N. Chambers, M. Surdeanu, and D. Jurafsky, “Stanford’s Multi-Pass Sieve Coreference Resolution System at the CoNLL-2011 Shared Task,” Association for Computational Linguistics, 2011.
[^8]: A. Rahman and V. Ng, “Resolving Complex Cases of Definite Pronouns: The Winograd Schema Challenge,” Association for Computational Linguistics, 2012.
[^9]: K. Clark and C. D. Manning, “Improving Coreference Resolution by Learning Entity-Level Distributed Representations.”

