Quantum Field Theory 04 - Lorentz Invariance (Contd.)

### Spacetime Translation Operator
In Heisenberg picture, time evolution is defined as a unitary transformation
of the wave function:
$$
e^{iHt/\hbar}\varphi(x,0)e^{-iHt/\hbar} = \varphi(x, t)
$$
Note that this $\varphi$ is a **vector in Hilbert space** indexed by spacetime coordinate.

An obvious relativistic generalization of it should be:
$$
e^{-iPx/\hbar}\varphi(0)e^{iPx/\hbar} = \varphi(x)
$$
where $Px$ is defined as $P^\mu x_\mu$.
We can define a spacetime translation operator:
$$
T(a) \equiv \mathrm{exp}(-iP^\mu a_\mu/\hbar)
$$
Then we have
$$\begin{align*}
T(a)^{-1}\varphi(x)T(a) &=
\mathrm{exp}(-iP^\mu a_\mu/\hbar)\varphi(x)\mathrm{exp}(iP^\mu a_\mu/\hbar) \\
&=
\left(\sum_k \frac{1}{k!}\left(\frac{-iP^\mu a_\mu}{\hbar}\right)^k\right)
\varphi(x)
\left(\sum_k \frac{1}{k!}\left(\frac{iP^\mu a_\mu}{\hbar}\right)^k\right) \\
&=
\left(\sum_k \frac{1}{k!}\left(-a_\mu\partial^\mu \right)^k\right)
\varphi(x)
\left(\sum_k \frac{1}{k!}\left(a_\mu\partial^\mu \right)^k\right) \\
\end{align*}$$


If we apply Lorentz transformation on the translation operator:
$$\begin{align*}
T(a) &= \mathrm{exp}\left(-i P^\mu a_\mu / \hbar \right) \\
     &= \sum_n \frac{1}{n!}\left(\frac{-iP^\mu a_\mu}{\hbar}\right)^n\\
\end{align*}$$
Since $[P^\mu, P^\nu] = 0$:
$$\begin{align*}
U(\Lambda)^{-1}T(a)U(\Lambda) &= \sum_n \frac{1}{n!}\left(\frac{-iU(\Lambda)^{-1}P^\mu U(\Lambda) a_\mu}{\hbar}\right)^n\\
    &= \sum_n \frac{1}{n!}\left(\frac{-i\Lambda^\mu{}_\nu P^\nu a_\mu}{\hbar}\right)^n\\
    &= T(\Lambda^\mu{}_\nu a_\mu)\\
    &= T(\Lambda^{-1} a)\\
\end{align*}$$

Therefore,
$$\begin{align*}
U(\Lambda)^{-1}\varphi(x)U(\Lambda) &= T(-\Lambda^{-1}x)^{-1}U(\Lambda)\varphi(0)U(\Lambda)^{-1}T(-\Lambda^{-1}x) \\
\end{align*}$$

For an infinitesimal translation,
$$
T(\Delta a) = I -\Delta\frac{i}{\hbar}P^\mu a_\mu
$$
Therefore

$$\begin{align*}
U(\Lambda)^{-1}T(\Delta a)U(\Lambda) &=
    I - \Delta \frac{i}{\hbar}U(\Lambda^{-1})P^\mu a_\mu U(\Lambda)\\
    &= I - \Delta \frac{i}{\hbar}\Lambda^\mu{}_\nu P^\nu a_\mu \\
    &= I - \Delta \frac{i}{\hbar} P^\nu (\Lambda^\mu{}_\nu a_\mu) \\
    &= T(\Delta \Lambda^\mu{}_\nu a_\mu)
\end{align*}$$
the unitary operator added an linear factor on the translate operator.
