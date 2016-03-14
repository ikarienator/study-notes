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
\Lambda_\mu{}^\rho \Lambda^\mu{}_\nu &= (\delta^\mu{}_\nu + \Delta \omega^\mu{}_\nu)(\delta_\mu{}^\rho + \Delta \omega_\mu{}^\rho) \\
&= \delta^\mu{}_\nu \delta_\mu{}^\rho  + \delta^\mu{}_\nu  \Delta \omega_\mu{}^\rho +
\Delta \omega^\mu{}_\nu \delta_\mu{}^\rho + \Delta \omega^\mu{}_\nu\Delta \omega_\mu{}^\rho
\end{align*}$$

The last term $\Delta \omega^\mu{}_\nu\Delta \omega_\mu{}^\rho$ vanishes naturally.
$$\begin{align*}
\Lambda_\mu{}^\rho \Lambda^\mu{}_\nu &=\delta^\mu{}_\nu \delta_\mu{}^\rho  + \delta^\mu{}_\nu  \Delta \omega_\mu{}^\rho +
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
[Wigner's theorem](https://en.wikipedia.org/wiki/Wigner%27s_theorem). This means the Lorentz group is
represented by a unitary operator $U$, that every Lorentz transformation $\Lambda$ corresponds to a
operator $U(\Lambda)$ that obeys composition rule:

$$
U(\Lambda')U(\Lambda) = U(\Lambda'\Lambda)
$$

Some properties of $U$:
$$\begin{align*}
U(I)U(I) = U(I) = I \\
U(\Lambda^{-1})U(\Lambda) = U(I) = I \\
U(\Lambda^{-1}) = U(\Lambda)^{-1}
\end{align*}$$

For an infinitesmial Lorentz transformation, we can define a **matrix of operators** $M^{\mu\nu}$ such that:

$$\begin{align*}
U(I+\Delta\omega)&=I+\frac{i}{2\hbar}\Delta\omega_{\mu\nu} M^{\mu\nu} \\
\end{align*}$$

$M$ has to be antisymmetric:
$$\begin{align*}
U(I+\Delta\omega)U(I-\Delta\omega)&=\left(I+\frac{i}{2\hbar}\Delta\omega_{\mu\nu}M^{\mu\nu}\right)\left(I-\frac{i}{2\hbar}\Delta\omega_{\mu\nu}M^{\mu\nu}\right) \\
    &= I - \frac{1}{4\hbar^2} \Delta^2 \left(\omega_{\mu\nu}^2M^{\mu\nu}\right)^2 \\
\end{align*}$$
