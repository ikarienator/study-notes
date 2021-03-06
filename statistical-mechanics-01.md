Statistical Mechanics 01

[> Next](read.php?page=statistical-mechanics-02)

#### Canonical ensemble

Suppose there is a closed system with $N$ subsystems $S_1, S_2, S_3, \ldots S_N$ with conserved
total energy $\mathscr E$ but energy flows among the subsystems. At any given time, the state of the system in
terms of energy can be described as a list $\{E_{S_i}\}$ where $E_{S_i}$ represents the energy of subsystem $S_i$.


Starting with a discrete system where $E_{S_i}$ can be one of $M$ values $E_0, E_1, ...
E_{M-1}$. We can count how many subsystems are of energy $E_0$, and how many are of $E_1$ and so on,
then we got a list $\{K_j\}$ where $K_j$ represents the number of subsystems of $E_j$.
We call the list $K=\{K_j\}$ the **distribution** of the system. Since it is
simply counting the numbers, we have:

$$\begin{equation}\sum_j{K_j}=N\label{counter}\end{equation}$$

also because of summability of energy:

$$\begin{equation}\sum_j{K_jE_j}=\mathscr E\label{total-energy}\end{equation}$$

Under distribution $K$ the **possibility** of picking a subsystem it ends up having energy $E_j$ is:

$$\begin{equation}P_j=\frac{K_j}{N}\end{equation}$$

The definition of **entropy** is:

$$\begin{equation}S=-\sum_j{P_j\ln{P_j}}\end{equation}$$

We can further transform it into:

$$\begin{align*}
    S &=-\frac 1N\sum_j{K_j\ln\frac{K_j}N} \\
     &=-\frac 1N\sum_j(K_j\ln K_j - K_j\ln N) \\
     &= -\frac 1N\sum_j K_j\ln K_j + \frac 1N \sum_j K_j\ln N \\
     &= -\frac 1N\sum_j K_j\ln K_j + \ln N
\end{align*}$$

which is apparently an unitless positive quantity.

#### Maximal likelihood distribution and max entropy

It is assumed that the likelihood of a distribution $\{K_j\}$ is proportional to the number of ways the same
distribution can be assembbled from a combination of $E_j$s. This is a blunt assumption but it is just
like rolling a (possibly unfair) die $N$ times. And the likelihood of the distribution (which is likewise defined by
the number of times a certain number is produced) $K = \{K_1, K_2, ..., K_6\}$ will be
intuitively proportional to the number of different series of die rolling result (called "configuration")
of a particular distribution. This relies on the fact that we are rolling exactly the same die,
and likewise, we can assume all the subsystems are essentially equivalent (since we don't have any
knowledge on the subsystems).

The total number of different **permutations** that assembles the distribution will be: $N!$. Since we
are recounting all the **combination**, we have to divide it by the permutations of the same state.
So we get:

$$ \Omega = \frac{N!}{\prod_j{K_j!}} $$

It's a function of $K$. Take the logarithm of $Q$:

$$ \ln \Omega = \ln N!-\sum_j{\ln K_j!} $$

Using [Stirling's approximation](https://en.wikipedia.org/wiki/Stirling%27s_approximation):

$$ \ln n! = n \ln n - n + \mathcal{O}(\ln n) $$

ignoring the [big O](https://en.wikipedia.org/wiki/Big_O_notation):

$$
\begin{align*}
  \ln \Omega &= N \ln N - N - \sum_j \Big(K_j \ln K_j - K_j \Big) \\
      &= N \ln N - \sum_j K_j - \sum_j \Big(K_j \ln K_j - K_j \Big) \\
      &= N\ln N - \sum_j K_j \ln K_j \\
      &= \sum_jK_j\ln N - \sum_j K_j \ln K_j \\
      &= \sum_jK_j\ln\frac{N}{K_j} \\
      &= -N\sum_jP_j\ln P_j \\
      &= NS
\end{align*}
$$

In other words, entropy is (approximately) proportional to (therefore a measurement of) the
logarithm of likelihood of a distribution.


Now let's work out the distribution.

#### Distribution of max entropy.
[Lagrangian multiplier](https://en.wikipedia.org/?title=Lagrange_multiplier) is an algorithm to find
the maxima or minima of a function subject to equality constraints (which is visited in undergrad
level calculas). Our problem is to maximize entropy $S$ with respect of $K$, with constrains
$\eqref{counter}$ and $\eqref{total-energy}$. Since we have two constraints, we introduce two
multipliers $\alpha$ and $\beta$, and we got:

$$S'=S-\alpha\sum_j\big({K_j}-N\big)-\beta\sum_j\big({K_jE_j}-\mathscr E\big)$$

The sign for $\beta$ is completely conventional, so its numeric value can be positive.
The partial derivatives with respect of each $K_j$ must be zero:

$$\begin{align*}
    \frac{\partial}{\partial K_j}S - \alpha - \beta E_j &= 0 \\
    \frac{\partial}{\partial K_j}\big(-\frac 1N K_j \ln K_j\big) &= \alpha + \beta E_j \\
    \ln K_j + 1 &= -N\big(\alpha + \beta E_j\big) \\
    K_j &= C\exp(-\beta E_j)
\end{align*}$$

where $C$ is an coefficient that can be determined later. This gives us a close form of the
distribution of $K$.

[> Next](read.php?page=statistical-mechanics-02)
