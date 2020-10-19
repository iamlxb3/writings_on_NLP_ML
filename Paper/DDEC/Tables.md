

\begin{table*}[t]
  \centering

  \caption{The statistics of the datasets}
  \label{tab:1}
\end{table*}



----



\begin{tabular}{llrrrrrr}
\toprule
{} & Lang &  Num.Intent &  Avg.Text &  Std.Text &  Avg.Text Length &  Std.Text Length &  Num.Unique Token \\
Dataset     &      &             &           &           &                  &                  &                   \\
\midrule
CLINC150 &   en &         150 &       150 &         0 &               40 &               16 &              6391 \\
DBpedia  &   en &         219 &      1566 &       995 &              121 &               70 &            418737 \\
IWSDS    &   en &          68 &       377 &       321 &               35 &               16 &             10585 \\
SMP2019     &   cn &          23 &       156 &       477 &                9 &                4 &              3482 \\
AgentDialog &   cn &         354 &        21 &        16 &                7 &                3 &              2883 \\
THUCNews    &   cn &          14 &     59720 &     52347 &               20 &                5 &            266060 \\
HumanDialog &   cn &        1226 &        15 &        10 &                6 &                2 &              2790 \\
\bottomrule
\end{tabular}



---

```
\begin{tabular}{llllllll}
\toprule
{} & \multicolumn{7}{l}{score/coverage/adjusted\_rand\_score} \\
dataset &                           CLINC150 &          DBpedia &            IWSDS &         THUCNews & new\_smalltalk\_0303 &    old\_smalltalk &         smp\_2019 \\
method     &                                    &                  &                  &                  &                    &                  &                  \\
\midrule
BaseLeaner &                    0.533$\pm$0.009 &  0.325$\pm$0.018 &  0.494$\pm$0.073 &  0.267$\pm$0.215 &    0.871$\pm$0.022 &  0.643$\pm$0.043 &  0.521$\pm$0.305 \\
CDAC+      &                    0.203$\pm$0.002 &  0.287$\pm$0.044 &  0.119$\pm$0.044 &              NaN &                NaN &              NaN &              NaN \\
OPTICS     &                    0.247$\pm$0.079 &  0.185$\pm$0.063 &  0.199$\pm$0.111 &  0.375$\pm$0.176 &    0.759$\pm$0.058 &  0.348$\pm$0.122 &  0.487$\pm$0.195 \\
\bottomrule
\end{tabular}
```



```
\toprule
{} & \multicolumn{7}{l}{score/coverage/adjusted_rand_score} \\
dataset &                           CLINC150 &          DBpedia &            IWSDS &         THUCNews & new_smalltalk_0303 &    old_smalltalk &         smp_2019 \\
method     &                                    &                  &                  &                  &                    &                  &                  \\
\midrule
BaseLeaner &                    0.533$\pm$0.009 &  0.325$\pm$0.018 &  0.494$\pm$0.073 &  0.267$\pm$0.215 &    0.871$\pm$0.022 &  0.643$\pm$0.043 &  0.521$\pm$0.305 \\
CDAC+      &                    0.203$\pm$0.002 &  0.287$\pm$0.044 &  0.119$\pm$0.044 &              NaN &                NaN &              NaN &              NaN \\
OPTICS     &                    0.247$\pm$0.079 &  0.185$\pm$0.063 &  0.199$\pm$0.111 &  0.375$\pm$0.176 &    0.759$\pm$0.058 &  0.348$\pm$0.122 &  0.487$\pm$0.195 \\
\bottomrule
```