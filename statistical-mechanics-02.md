Statistical Mechanics 02

[< Prev](read.php?page=statistical-mechanics-01)

#### Partition function $Z(\beta)$

We can re-express $P_j$ now to eliminate $C$.

$$\begin{align*}
    N &= \sum_j K_j \\
      &= \sum_j C\exp(-\beta E_j) \\
      \\
  P_j &= \frac{K_j}{N} \\
      &= \frac{\exp(-\beta E_j)}{\sum_j\exp(-\beta E_j)}
\end{align*}$$

This gives us a feeling that $C$ or ($\alpha$) is not important to our problem. Now we define a function $Z(\beta)$:

$$Z(\beta) = \sum_j\exp(-\beta E_j) $$
$$P_j = \frac 1Z \exp(-\beta E_j)$$

It is the normalization factor if we set $C$ to be one.

An observation is that:

$$\begin{align*}
\frac{\mathrm dZ}{\mathrm d\beta}
    &= \sum_j \frac{\mathrm d}{\mathrm d\beta} \exp(-\beta E_j)\\
    &= - \sum_j \exp(-\beta E_j) E_j \\
    &= - \sum_j P_j Z E_j \\
    &= - Z \mathscr \\
\end{align*}$$

therefore

$$\begin{align*}
\frac{\mathrm dZ}{Z\mathrm d\beta} &= -\mathscr \\
\frac{\mathrm d}{\mathrm d\beta} \log Z &= -\mathscr \\
\end{align*}$$

Second, relationship between entropy and $Z$ function:

$$\begin{align*}
S &= -\sum_jP_j\log P_j \\
  &= -\sum_j P_j \log \left(\frac{\exp\left(-\beta E_j\right)}Z\right) \\
  &= -\sum_j P_j \left(-\beta E_j - \log Z\right) \\
  &= \beta \mathscr E+ N \log Z \\
\end{align*}$$

This means max entropy is determined by $\beta$ in this configuration.
[< Prev](read.php?page=statistical-mechanics-01)