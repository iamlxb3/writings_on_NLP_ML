MLP, thresh = 0.0

> Config:
> repeat:  1
> seed:  28
> debug_N:  500
> epoch:  100
> batch_size:  32
> thresh_linspace:  3
> downstream_model:  mlp
> sim_top_N:  1
> neg_sample_thresh:  0.2
> neg_sample_ratio:  256
> neg_sample_train_ratio:  4
> coarse_topn:  20

| neg_sample_ratio | Pos Macro f1      | Neg f1 |
| :--------------: | ------------------ | ------ |
| 2 | 0.588 | 0.507 |
| 4 | 0.576 | 0.612 |
| 8 | 0.644 | 0.640 |
|        16        | 0.628 | 0.645 |
|        32        | 0.635              | 0.58 |
|        64        | 0.660 | 0.602 |
|        128        |         0.666           |   0.627     |
|        256        |            0.669        |     0.6   |

LR, thresh = 0.0
| neg_sample_ratio | Pos Macro f1      | Neg f1 |
| :--------------: | ------------------ | ------ |
| 64 | 0.650 | 0.687 |

MLP + ATTN, thresh = 0.0
| neg_sample_ratio | Pos Macro f1      | Neg f1 |
| :--------------: | ------------------ | ------ |
| 64 | 0.575 | 0.354 |

Cos sim
| neg_sample_ratio | Pos Macro f1      | Neg f1 |
| :--------------: | ------------------ | ------ |
| 64 | 0.52 | 0.150 |