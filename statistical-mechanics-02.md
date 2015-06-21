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
\frac{\mathrm d \log Z }{\mathrm d\beta} &= -\mathscr E\\
\end{align*}$$

Second, relationship between entropy and $Z$ function:

$$\begin{align*}
S &= -\sum_jP_j\log P_j \\
  &= -\sum_j P_j \log \left(\frac{\exp\left(-\beta E_j\right)}Z\right) \\
  &= -\sum_j P_j \left(-\beta E_j - \log Z\right) \\
  &= \beta \sum_j P_j E_j + \log Z \sum_j P_j \\
  &= \beta \mathscr E+ \log Z \\
\end{align*}$$

If we consider $S$ to be a function of $\mathscr E$ and $\beta$:

$$ \mathrm dS = \mathrm d\beta\mathscr E + \beta\mathrm d\mathscr E - \mathscr Ed\beta = \beta\mathrm d\mathscr E $$
$$ \beta = \frac{\mathrm dS}{\mathrm d\mathscr E} $$

This means that $\beta$ has a specific physical meaning. It equals to the amount of maximum entropy
increases when you put put more energy in it. From thermodynamics, we know that $\beta$ is the inverse
temperature $1/(K_BT)$, where $K_B$ is Boltzmann's constant.

[< Prev](read.php?page=statistical-mechanics-01)