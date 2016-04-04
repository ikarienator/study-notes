Quantum Field Theory 03 - Lorentz Invariance (Contd.)

### Poincaré algebra

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
Again, sum up the upper-right half:
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
The commutation relationship can therefore be descibed as:
$$\begin{align*}
[J_i, J_j] &= i\hbar \epsilon_{ijk}J_k \\
[J_i, K_j] &= i\hbar \epsilon_{ijk}K_k \\
[K_i, K_j] &= -i\hbar \epsilon_{ijk}J_k \tag{S 2.17} \label{S 2.17} \\
\end{align*}$$
##### Proof
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
The relation ship with angular momentum and boost:
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

Back to the Lorentz transformation of momentum operators:
$$\begin{align*}
U(\Lambda)^{-1}P^\mu U(\Lambda) &= \Lambda^\mu{}_\sigma P^\sigma \tag{S 2.15}
\end{align*}$$
Again, let $\Lambda = 1 + \Delta\omega$:
$$\begin{align*}
U(\Lambda)^{-1}P^\mu U(\Lambda) &=
    \left(I-\frac{i}{2\hbar}\Delta \omega_{\rho\sigma} M^{\rho\sigma}\right)
    P^\mu
    \left(I+\frac{i}{2\hbar}\Delta \omega_{\rho\sigma} M^{\rho\sigma}\right)\\
&= P^\mu + \frac{i}{2\hbar}\Delta \omega_{\rho\sigma}[P^\mu, M^{\rho\sigma}]
+ o(\Delta^2) \\
\end{align*}$$

$$\begin{align*}
\Lambda^\mu{}_\sigma P^\sigma &= (\delta + \Delta \omega)^\mu{}_\sigma P^\sigma \\
    &= P^\mu + \Delta \omega^\mu{}_\sigma P^\sigma \\
\end{align*}$$
Compare the two
$$\begin{align*}
\frac{i}{2\hbar}\Delta \omega_{\rho\sigma}[P^\mu, M^{\rho\sigma}]
    &=\Delta \omega^\mu{}_\sigma P^\sigma \\
\omega_{\rho\sigma}[P^\mu, M^{\rho\sigma}] &= -i2\hbar \omega^\mu{}_\sigma P^\sigma \\
    &= -i2\hbar \omega_{\rho\sigma}g^{\mu\rho}P^\sigma \\
\end{align*}$$
Using the same trick, write this down as summation:
$$\begin{align*}
\sum_{\rho,\sigma}\omega_{\rho\sigma}[P^\mu, M^{\rho\sigma}] &=
    2\sum_{\rho<\sigma}\omega_{\rho\sigma}[P^\mu, M^{\rho\sigma}] \\
-i2\hbar\sum_{\rho,\sigma} \omega_{\rho\sigma}g^{\mu\rho}P^\sigma &=
    -i2\hbar\left(
        \sum_{\rho<\sigma} \omega_{\rho\sigma}g^{\mu\rho}P^\sigma +
        \sum_{\rho>\sigma} \omega_{\rho\sigma}g^{\mu\rho}P^\sigma
    \right)\\
&= -i2\hbar\left(
        \sum_{\rho<\sigma} \omega_{\rho\sigma}g^{\mu\rho}P^\sigma +
        \sum_{\rho<\sigma} \omega_{\sigma\rho}g^{\mu\sigma}P^\rho
    \right)\\
&= -i2\hbar\left(
        \sum_{\rho<\sigma} \omega_{\rho\sigma}\left(g^{\mu\rho}P^\sigma - g^{\mu\sigma}P^\rho\right)
    \right)\\
\end{align*}$$
Now we have independent $\omega_{\rho\sigma}$'s at our disposal.
$$\begin{align*}
[P^\mu, M^{\rho\sigma}] &= i\hbar \left(g^{\mu\sigma}P^\rho - g^{\mu\rho}P^\sigma\right) \tag{S 2.18} \\
\end{align*}$$

The relationship with $M$:
$$\begin{align*}
[J_i, H] &= \left[\frac{1}{2}\epsilon_{ijk}M^{jk}, P^0\right] \\
        &= -\frac{1}{2}\epsilon_{ijk}[P^0,M^{jk}] \\
        &= -\frac{1}{2}\epsilon_{ijk}\left(i\hbar\left(
             g^{0k}P^j - g^{0j}P^k
            \right)\right) \\
        &= 0 \\
\end{align*}$$
 The last line because indices of $\epsilon$ goes from $1$ to $3$.
$$\begin{align*}
[J_i, P_j] &= \left[\frac{1}{2}\epsilon_{ikl}M^{kl}, P^j\right] \\
        &= -\frac{i\hbar}{2}\epsilon_{ikl}\left(g^{jl}P^k - g^{jk}P^l\right) \\
        &= -\frac{i\hbar}{2}\left(\epsilon_{ikj}P^k - \epsilon_{ijl}P^l\right) \\
        &= \frac{i\hbar}{2}\left(\epsilon_{ijk}P^k + \epsilon_{ijl}P^l\right) \\
        &= i\hbar\epsilon_{ijk}P^k \\
\end{align*}$$
$$\begin{align*}
[K_i, H] &= [M^{i0}, P^0] \\
        &= -i\hbar \left(g^{00}P^i - g^{0i}P^0\right) \\
        &= i\hbar P^i
\end{align*}$$
$$\begin{align*}
[K_i, P_j] &= [M^{i0}, P^j] \\
        &= -i\hbar \left(g^{j0}P^i - g^{ji}P^0\right) \\
        &= i\hbar \delta_{ij} H \tag{S 2.19} \label{S 2.19}
\end{align*}$$

Also components of $P$ should commute:
$$\begin{align*}
[P^\mu,P^\nu] &= 0 \tag{S 2.20} \label{S 2.20}
\end{align*}$$

$\eqref{S 2.17}$, $\eqref{S 2.19}$ and $\eqref{S 2.20}$ are called the
_Lie algebra of the Poincaré group_, or simply, **Poincaré algebra**.
