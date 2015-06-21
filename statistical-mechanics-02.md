Statistical Mechanics 02

#### Partition function $Z$

We can re-express $P_j$ now to eliminate $C$.

$$\begin{align*}
    N &= \sum_j K_j \\
      &= \sum_j C\exp(-\beta E_j) \\
      \\
  P_j &= \frac{K_j}{N} \\
      &= \frac{\exp(-\beta E_j)}{\sum_j\exp(-\beta E_j)}
\end{align*}$$

This gives us a feeling that $C$ is not important to our problem. Now we define a function $Z(\beta)$:

$$Z(\beta) = \sum_j\exp(-\beta E_j) $$
