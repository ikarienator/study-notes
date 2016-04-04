Quantum Field Theory 04 - Lorentz Invariance (Contd.)

#### Problems
If we apply the infinitesimal Lorentz transformation
$\Lambda= 1 + \varepsilon \omega$ to $\varphi$:
$$\begin{align*}
U(\Lambda)^{-1}\varphi(x)U(\Lambda)
  &= U(1 + \varepsilon \omega)^{-1}\varphi(x)U(1 + \varepsilon \omega) \\
  &=\left(I - \frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}M^{\mu\nu}\right)
    \varphi(x)
    \left(I + \frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}M^{\mu\nu}\right) \\
&= \varphi(x) -\frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}\left[M^{\mu\nu}, \varphi(x)\right] + o(\varepsilon^2) \\
\varphi(\Lambda^{-1}x)
&= \varphi(x + \varepsilon \omega_{\mu\nu} x^\nu) \\
&= \varphi(x) + \varepsilon \omega_{\mu\nu} x^\nu \partial^\mu \varphi(x)\\
\end{align*}$$
Again, compare the two and take the upper half of the matrix:
$$\begin{align*}
-\frac{i}{2\hbar}\omega_{\mu\nu}\left[M^{\mu\nu}, \varphi(x)\right]
&= \omega_{\mu\nu} x^\nu \partial^\mu \varphi(x) \\
-\frac{i}{2\hbar}\sum_{\mu,\nu}\omega_{\mu\nu}\left[M^{\mu\nu}, \varphi(x)\right]
&= \sum_{\mu,\nu}\omega_{\mu\nu} x^\nu \partial^\mu \varphi(x) \\
-\frac{i}{\hbar}\sum_{\mu<\nu}\omega_{\mu\nu}\left[M^{\mu\nu}, \varphi(x)\right]
&= \sum_{\mu<\nu}\omega_{\mu\nu} (x^\nu \partial^\mu - x^\mu \partial^\nu )\varphi(x) \\
-\frac{i}{\hbar}\left[M^{\mu\nu}, \varphi(x)\right]
&= (x^\nu \partial^\mu - x^\mu \partial^\nu )\varphi(x) \\
\left[M^{\mu\nu}, \varphi(x)\right] &= -i\hbar(x^\mu \partial^\nu - x^\nu \partial^\mu)\varphi(x)\\
\end{align*}$$
