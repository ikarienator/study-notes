Statistical Mechanics 02

[< Prev](read.php?page=statistical-mechanics-01)

#### Partition function $Z$

We can re-express $P_j$ now to eliminate $C$.

$$\begin{align*}
    N &= \sum_j K_j \\
      &= \sum_j C\exp(-\beta E_j) \\
      \\
  P_j &= \frac{K_j}{N} \\
      &= \frac{\exp(-\beta E_j)}{\sum_j\exp(-\beta E_j)}
\end{align*}$$

This gives us a feeling that $C$ (or $\alpha$) is not important to our problem. Now we define a function $Z(\beta)$:

$$Z = \sum_j\exp(-\beta E_j) $$
$$P_j = \frac 1Z \exp(-\beta E_j)$$

It is the normalization factor if we set $C$ to be one.

An observation is that:

$$\begin{align*}
\frac{\mathrm dZ}{\mathrm d\beta} &= \sum_j \frac{\mathrm d}{\mathrm d\beta} \exp(-\beta E_j)\\
    &= - \sum_j \exp(-\beta E_j) E_j \\
    &= - \sum_j P_j Z E_j \\
    &= - Z \mathscr E \\
\end{align*}$$

therefore

$$\begin{align*}
\frac{\mathrm dZ}{Z\mathrm d\beta} &= -\mathscr E\\
\frac{\mathrm d \ln Z }{\mathrm d\beta} &= -\mathscr E\\
\end{align*}$$

Second, relationship between entropy and $Z$ function:

$$\begin{align*}
S &= -\sum_jP_j\ln P_j \\
  &= -\sum_j P_j \ln \left(\frac{\exp\left(-\beta E_j\right)}Z\right) \\
  &= -\sum_j P_j \left(-\beta E_j - \ln Z\right) \\
  &= \beta \sum_j P_j E_j + \ln Z \sum_j P_j \\
  &= \beta \mathscr E+ \ln Z \\
\end{align*}$$

If we consider $S$ to be a function of $\mathscr E$ and $\beta$:

$$\begin{align*}
    \mathrm dS &= \mathscr E\mathrm d\beta + \beta\mathrm d\mathscr E + \mathrm d \ln Z \\
               &= \beta\mathrm d\mathscr E + \mathscr E\mathrm d\beta + (-\mathscr E\mathrm d \beta) \\
               &= \beta\mathrm d\mathscr E
\end{align*}$$

$$\beta = \frac{\mathrm dS}{\mathrm d\mathscr E}$$

From thermodynamics, we defined temperature $T$ as:

$$T=\frac{\mathrm d \mathscr E}{\mathrm d S}$$

so

$$ T = \frac 1\beta $$

This gives us the physical meaning of $\beta$.

#### Re-expressing things with $\beta$ and $E_j$

$$\begin{align}
P_i &= \frac 1Z \exp(-\beta E_j) \\
Z &= \sum_j \exp(-\beta E_j) \\
\mathscr E &= -\frac{\mathrm d \ln Z }{\mathrm d\beta} \\
T &= \frac 1\beta\\
S &= \beta\mathscr E + \ln Z \\
\end{align}$$


[< Prev](read.php?page=statistical-mechanics-01)