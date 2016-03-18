Quantum Field Theory 02 - Lorentz Invariance


#### Lorentz transformation

Lorentz invariance is about the symmetry upon changing of coordinates.

Suppose we have two sets of coordinates corelated with a Lorentz transformation
$\Lambda^\mu{}_\nu$.It converts $x^\nu$ to $\bar{x}^\mu$:

$$\begin{align*}
\bar{x}^\mu=\Lambda^\mu{}_\nu x^\nu \\
\end{align*}$$

According to relativity, the proper length of the coordinate is conserved:

$$
x_\nu x^\nu = \bar x_\mu \bar x^\mu = -c^2t^2 + x^2
$$

Therefore:

$$\begin{align*}
\bar x^\rho \bar x^\sigma &= g_{\mu\nu}x^\mu x^\nu \\
\Lambda^\rho{}_\mu x^\mu \Lambda^\sigma{}_\nu x^\nu &= g_{\mu\nu}x^\mu x^\nu \\
\Lambda^\rho{}_\mu \Lambda^\sigma{}_\nu x^\mu x^\nu &= g_{\mu\nu}x^\mu x^\nu \\
g_{\rho\sigma} \Lambda^\rho{}_\mu \Lambda^\sigma{}_\nu &= g_{\mu\nu}
\end{align*}$$

The last step is because it has to work for all $x$.

Given an (orthochronous, meaning $\Lambda^\mu{}_\mu=1$) infinitesmial
(propotional to $\Delta \to 0$) Lorentz transformation:

$$\begin{align*}
\Lambda^\mu{}_\nu &= \delta^\mu{}_\nu + \Delta \omega^\mu{}_\nu \\
\Lambda_\mu{}^\rho &= \delta_\mu{}^\rho + \Delta \omega_\mu{}^\rho \\
(\Lambda^{-1})^\rho{}_\mu \Lambda^\mu{}_\nu &= \delta^\rho{}_\nu \\
\Lambda_\mu{}^\rho \Lambda^\mu{}_\nu &= \delta^\rho{}_\nu \\
\end{align*}$$
$$\begin{align*}
\Lambda_\mu{}^\rho \Lambda^\mu{}_\nu &=
    (\delta^\mu{}_\nu + \Delta \omega^\mu{}_\nu)
    (\delta_\mu{}^\rho + \Delta \omega_\mu{}^\rho) \\
&= \delta^\mu{}_\nu \delta_\mu{}^\rho  + \delta^\mu{}_\nu  \Delta \omega_\mu{}^\rho +
\Delta \omega^\mu{}_\nu \delta_\mu{}^\rho + \Delta \omega^\mu{}_\nu\Delta \omega_\mu{}^\rho
\end{align*}$$

The last term $\Delta \omega^\mu{}_\nu\Delta \omega_\mu{}^\rho$ vanishes naturally.
$$\begin{align*}
\Lambda_\mu{}^\rho \Lambda^\mu{}_\nu &=\delta^\mu{}_\nu \delta_\mu{}^\rho +
    \delta^\mu{}_\nu  \Delta \omega_\mu{}^\rho +
\Delta \omega^\mu{}_\nu \delta_\mu{}^\rho \\
&=\delta_\nu{}^\rho +
\Delta \omega_\nu{}^\rho +
\Delta \omega^\rho{}_\nu
\end{align*}$$

Therefore:
$$\begin{align*}
\omega_\nu{}^\rho = -\omega^\rho{}_\nu
\end{align*}$$

Since $\omega$ is a $4\times 4$ matrix, there are $6$ degrees of freedom, and the diagonal elements
are $0$. Thus we have $6$ independent infinitesimal Lorentz transformations, $3$ for rotation and
$3$ for boost.

#### Lorentz covariance unitary operators
Symmetry in quantum theory is represented by unitary or anti-unitary operators through
[Wigner's theorem](https://en.wikipedia.org/wiki/Wigner%27s_theorem). This means the
Lorentz group is represented by a unitary operator $U$, that every Lorentz transformation
$\Lambda$ corresponds to a operator $U(\Lambda)$ that obeys composition rule:

$$
U(\Lambda')U(\Lambda) = U(\Lambda'\Lambda)
$$

Some properties of $U$:
$$\begin{align*}
U(I)U(I) = U(I) = I \\
U(\Lambda^{-1})U(\Lambda) = U(I) = I \\
U(\Lambda^{-1}) = U(\Lambda)^{-1}
\end{align*}$$

For an infinitesmial Lorentz transformation, we can define a **collection of operators**
$M^{\mu\nu}$ such that:

$$\begin{align*}
U(I+\Delta\omega)&=I+\frac{i}{2\hbar}\Delta\omega_{\mu\nu} M^{\mu\nu} \\
\end{align*}$$

due to symmetry, $M^{\mu\nu} = -M^{\nu\mu}$.

Starting with $U(\Lambda)^{-1}U(\Lambda')U(\Lambda) = U(\Lambda^{-1}\Lambda'\Lambda)$,
setting $\Lambda'^\rho{}_\sigma = \delta^\rho{}_\sigma + \Delta \omega'^\rho{}_\sigma$:

$$\begin{align*}
U(\Lambda)^{-1}U(\Lambda')U(\Lambda) &=
U(\Lambda)^{-1}
\left(I+\frac{i}{2\hbar}\Delta\omega'_{\mu\nu} M^{\mu\nu}\right)
U(\Lambda) \\
&= I +\frac{i}{2\hbar}\Delta\omega'_{\mu\nu} U(\Lambda)^{-1}M^{\mu\nu}U(\Lambda) \\
\end{align*}$$

$$\begin{align*}
U(\Lambda^{-1}\Lambda'\Lambda) &= U\left(\Lambda^{-1}\left(\delta + \Delta \omega'\right)\Lambda\right) \\
&= U(\delta^\rho{}_\mu + \Delta\Lambda^{-1}\omega'\Lambda) \\
&= I+\frac{i}{2\hbar}\Delta\left(\Lambda^{-1}\omega'\Lambda\right)_{\mu\nu} M^{\mu\nu} \\
&= I+\frac{i}{2\hbar}\Delta\left((\Lambda^{-1})_\rho{}^\mu\omega'_{\mu\nu}\Lambda^\nu{}_{\sigma}\right) M^{\rho\sigma} \\
&= I+\frac{i}{2\hbar}\Delta\left(\Lambda^\mu{}_\rho\omega'_{\mu\nu}\Lambda^\nu{}_{\sigma}\right) M^{\rho\sigma} \\
&= I+\frac{i}{2\hbar}\Delta\omega'_{\mu\nu}\Lambda^\mu{}_\rho\Lambda^\nu{}_{\sigma}M^{\rho\sigma} \\
\end{align*}$$

$$
\omega'_{\mu\nu} U(\Lambda)^{-1}M^{\mu\nu}U(\Lambda) = \omega'_{\mu\nu}\Lambda^\mu{}_\rho\Lambda^\nu{}_{\sigma}M^{\rho\sigma}
$$

Since $\omega'$ is arbitrary:
$$
U(\Lambda)^{-1}M^{\mu\nu}U(\Lambda) = \Lambda^\mu{}_\rho\Lambda^\nu{}_{\sigma}M^{\rho\sigma}
$$

In fact, this is a general result: for operator $O$, $U(\Lambda)^{-1}O^\mu U(\Lambda)=\Lambda^\mu{}_\nu O^\nu$

#### Commutation properties of the generator of Lorentz transformation

Let's compute $[M^\mu{}^\nu, M^\rho{}^\sigma]$:

$$\begin{align*}
U(\Lambda)^{-1}M^{\mu\nu}U(\Lambda) &=
    \left(I-\frac{i}{2\hbar}\Delta\omega_{\rho\sigma}
    M^{\rho\sigma}\right) M^\mu{}^\nu
    \left(I+\frac{i}{2\hbar}\Delta\omega_{\rho\sigma} M^{\rho\sigma}\right)
    \\
&= M^\mu{}^\nu + \frac{i}{2\hbar}\Delta\omega_{\rho\sigma}[M^\mu{}^\nu, M^\rho{}^\sigma] \\
\end{align*}$$

$$\begin{align*}
\Lambda^\mu{}_\rho\Lambda^\nu{}_{\sigma}M^{\rho\sigma} &=
\left(\delta + \Delta \omega\right)^\mu{}_\rho \left(\delta + \Delta \omega\right)^\nu{}_\sigma M^{\rho\sigma} \\
&= \left(\delta^\mu{}_\rho \left(\delta + \Delta \omega\right)^\nu{}_\sigma  +
\Delta \omega^\mu{}_\rho \left(\delta + \Delta \omega\right)^\nu{}_\sigma \right) M^{\rho\sigma} \\
&= \left(\delta^\mu{}_\rho \delta ^\nu{}_\sigma + \delta^\mu{}_\rho \Delta \omega^\nu{}_\sigma  +
\Delta \omega^\mu{}_\rho \delta^\nu{}_\sigma + o(\Delta^2)\right) M^{\rho\sigma} \\
&= M^{\mu\nu} + \Delta (\omega^\nu{}_\sigma M^{\mu\sigma} - \omega_\rho{}^\mu M^{\rho\nu}) \\
&= M^{\mu\nu} + \Delta (g^\nu{}^\rho\omega_\rho{}_\sigma M^{\mu\sigma} - g^\mu{}^\sigma\omega_\rho{}_\sigma M^{\rho\nu}) \\
&= M^{\mu\nu} + \Delta \omega_\rho{}_\sigma (g^\nu{}^\rho M^{\mu\sigma} - g^\mu{}^\sigma M^{\rho\nu}) \\
\end{align*}$$

Compare the two
$$\begin{align*}
\omega_{\rho\sigma}[M^\mu{}^\nu, M^\rho{}^\sigma] &= -2i\hbar \omega_\rho{}_\sigma (g^\nu{}^\rho M^{\mu\sigma} - g^\mu{}^\sigma M^{\rho\nu}) \\
    & = 2i\hbar \omega_\rho{}_\sigma (g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\rho M^{\mu\sigma}) \\
\end{align*}$$
Since not all the $\omega_{\rho\sigma}$ are independent, we cannot simply divide all the $\omega_{\rho\sigma}$s.
But all the $\omega_{\rho\sigma}$ are independent. We can try to write the sum of the upper-right
half (not using Einstein notation for now):
$$\begin{align*}
\sum_{\rho,\sigma}\omega_{\rho\sigma}[M^\mu{}^\nu, M^\rho{}^\sigma] &= 2\sum_{\rho<\sigma} \omega_{\rho\sigma}[M^\mu{}^\nu, M^\rho{}^\sigma]\\
\sum_{\rho,\sigma}
    2i\hbar \omega_\rho{}_\sigma
    (g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\rho M^{\mu\sigma}) &=
    2i\hbar \sum_{\rho,\sigma} \omega_\rho{}_\sigma (g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\rho M^{\mu\sigma}) \\
 &= 2i\hbar \sum_{\rho<\sigma}  \big(\omega_\rho{}_\sigma(g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\rho M^{\mu\sigma}) + (\rho \leftrightarrow \sigma)\big) \\
 &= 2i\hbar \sum_{\rho<\sigma} \omega_\rho{}_\sigma \big((g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\rho M^{\mu\sigma}) - (\rho \leftrightarrow \sigma)\big) \\
\end{align*}$$

Now we can cancel $\omega$ altogether:

$$\begin{align*}
[M^\mu{}^\nu, M^\rho{}^\sigma] &= i\hbar\big((g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\rho M^{\mu\sigma}) - (g^\mu{}^\rho M^{\sigma\nu} - g^\nu{}^\sigma M^{\mu\rho})\big) \\
  &= i\hbar \big((g^\mu{}^\sigma M^{\rho\nu} + g^\nu{}^\sigma M^{\mu\rho}) - (g^\mu{}^\rho M^{\sigma\nu} - g^\nu{}^\rho M^{\mu\sigma}) \big) \\
  &= i\hbar \big((g^\mu{}^\sigma M^{\rho\nu} + g^\nu{}^\sigma M^{\mu\rho}) - (\rho \leftrightarrow \sigma) \big) \\
  &= i\hbar \big((g^\mu{}^\sigma M^{\rho\nu} - g^\nu{}^\sigma M^{\rho\mu}) - (\rho \leftrightarrow \sigma) \big) \\
  &= i\hbar \Big(\big(g^\mu{}^\sigma M^{\rho\nu} - (\mu \leftrightarrow \nu)\big) - \big(\rho \leftrightarrow \sigma\big) \Big) \\
  &= -i\hbar \Big(\big(g^\mu{}^\rho M^{\sigma\nu} - (\mu \leftrightarrow \nu)\big) - \big(\rho \leftrightarrow \sigma\big) \Big) \\
  &= i\hbar \Big(\big(g^\mu{}^\rho M^{\nu\sigma} - (\mu \leftrightarrow \nu)\big) - \big(\rho \leftrightarrow \sigma\big) \Big) \\
\end{align*}$$

Here we can identify angular momentum operator $J$ as $J_i = \frac{1}{2}\epsilon_{ijk}M^{jk}$ and boost operator $K_i = M^{i0}$. Here the indices are 3 dimensional labels.
$$\begin{align*}
J_1 &= \frac{1}{2}\epsilon_{1jk}M^{jk} = \frac{1}2{}(M^{23}-M^{32}) = M^{23} \\
J_2 &= M^{31} \\
J_3 &= M^{12} \\
M^{ij} &= \begin{pmatrix}
0 & K_1 & K_2 & K_3 \\
-K_1 & 0 & J_3 & -J_2 \\
-K_2 & -J_3 & 0 & J_1 \\
-k_3 & J_2 & -J_1 & 0 \\
\end{pmatrix} \\
\end{align*}$$

$$\begin{align*}
[J_i, J_j] &= \left[\frac{1}{2}\epsilon_{ikl}M^{kl}, \frac{1}{2}\epsilon_{jmn}M^{mn}\right] \\
    &= \frac{1}{4}\epsilon_{ikl}\epsilon_{jmn}[M^{kl}, M^{mn}] \\
    &= \frac{i\hbar}{4}\epsilon_{ikl}\epsilon_{jmn}
    \Big(\left(g^{km}M^{ln}-(k\leftrightarrow l)\right)-(m \leftrightarrow n)\Big) \\
\end{align*}$$

when indices are 3 dimensional, $g^{ij}$ is $\delta^{ij}$.

$$\begin{align*}
& \frac{i\hbar}{4}\epsilon_{ikl}\epsilon_{jmn}
  \Big(\left(g^{km}M^{ln}-(k\leftrightarrow l)\right)-(m \leftrightarrow n)\Big)\\
=& \frac{i\hbar}{4}
\Big(\left(\epsilon_{ikl}\epsilon_{jmn}g^{km}M^{ln}+(k\leftrightarrow l)\right)+(m \leftrightarrow n)\Big)
\\
=& \frac{i\hbar}{4}
\Big(\left(\epsilon_i{}^m{}_l\epsilon_{jmn}M^{lm}+(k\leftrightarrow l)\right)+(m \leftrightarrow n)\Big)
\\
=& \frac{i\hbar}{4}
\Big(\left(M^{ll} - M^{ji}+(k\leftrightarrow l)\right)+(m \leftrightarrow n)\Big)
\\
=& \frac{i\hbar}{4}
\Big(\left(M^{ij}+(k\leftrightarrow l)\right)+(m \leftrightarrow n)\Big)
\\
=& i\hbar M^{ij}\\
=& i\hbar \epsilon_{ijk}J_k\\
[J_i, J_j]=&i\hbar \epsilon_{ijk}J_k
\end{align*}$$
The relation ship with angular  momentum and boost:
$$\begin{align*}
[J_i, K_j] &= \left[\frac{1}{2}\epsilon_{ikl}M^{kl}, M^{j0}\right] \\
&= \frac{1}{2}\epsilon_{ikl}\left[M^{kl}, M^{j0}\right] \\
&= \frac{i\hbar}{2}\epsilon_{ikl}\Big((g^{kj}M^{l0}-(k \leftrightarrow l)) - (j \leftrightarrow 0) \Big) \\
&= \frac{i\hbar}{2}\epsilon_{ikl}\Big((g^{kj}M^{l0}-(k \leftrightarrow l)) - (j \leftrightarrow 0) \Big) \\
\end{align*}$$
The second term vanishes because $g^{k0}=0$:
$$\begin{align*}
[J_i, K_j]
&= \frac{i\hbar}{2}\epsilon_{ikl}\Big(g^{kj}M^{l0}-(k \leftrightarrow l)\Big) \\
&= \frac{i\hbar}{2}\Big(\epsilon_{ikl}g^{kj}M^{l0}+(k \leftrightarrow l)\Big) \\
&= \frac{i\hbar}{2}\Big(\epsilon_{ijl}M^{l0}+(k \leftrightarrow l)\Big) \\
&= i\hbar\epsilon_{ijl}M^{l0} \\
&= i\hbar\epsilon_{ijk}K_k \\
\end{align*}$$

The commutator between boost operators:
$$\begin{align*}
\require{cancel}
[K_i, K_j] &= [M^{i0},M^{j0}] \\
  &= i\hbar\Big(\big(g^{ij}\cancel{M^{00}} - \cancel{g^{0j}}M^{i0}\big) - \big(\cancel{g^{i0}}M^{0j} - g^{00}M^{ij}\big)\Big)\\
  &= -i\hbar M^{ij}\\
  &= -i\hbar\epsilon_{ijk}J_k\\
\end{align*}$$
This means a series of boosts can be a rotation.

#### Commutation properties of the generator of Lorentz transformation II
TBD
