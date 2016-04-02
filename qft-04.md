Quantum Field Theory 04 - Lorentz Invariance (Contd.)

### Spacetime Translation Operator
In Heisenberg picture, time evolution is defined as a unitary transformation
of the wave function:
$$
\varphi(\mathbf x, t) \equiv e^{iHt/\hbar}\varphi(\mathbf x,0)e^{-iHt/\hbar}
$$
Note that this $\varphi$ is an **operator** indexed by spacetime coordinate.
An obvious relativistic generalization should be:
$$
\varphi(x) \equiv e^{-ixP/\hbar}\varphi(0)e^{ixP/\hbar}
$$
where $xP$ is defined as $x_\mu P^\mu$. This can be alternatively done by
postulationally defining $P^\mu$ in such a way that
$[P^\mu,\,\cdot\,]=i\hbar\partial^\mu$ using the
[unnamed lemma](?page=standard-operator-identity). First of all, $[P^\mu,P^\nu]=0$,
then the summation $xP$ can passthrough each other. Then
$$\begin{align*}
e^{-ixP/\hbar}\varphi(0)e^{ixP/\hbar}
&= e^{\frac{-ix_\mu}{\hbar}[P^\mu,\,\cdot\,]}\varphi(0) \\
&= \sum_n\left(\frac{-ix_\mu}{\hbar}[P^\mu,\,\cdot\,]\right)^n \varphi(0)\\
&= \sum_n\left(x_\mu\partial^\mu\right)^n \varphi(0)\\
&= \varphi(x) \\
\end{align*}$$
From the over way around:
$$\begin{align*}
\partial^\mu \varphi(x) &= \lim_{\varepsilon \to 0} \left(
    \frac{
        e^{-i \varepsilon \delta^\mu{}_\nu P^\nu/\hbar}
        \varphi(x)
        e^{i \varepsilon \delta^\mu{}_\nu P^\nu/\hbar}
        - \varphi(x)
    }{
        \varepsilon
    }\right) \\
 &= \lim_{\varepsilon \to 0} \left(
    \frac{
        \varphi(x)
        -i \varepsilon \delta^\mu{}_\nu [P^\nu, \varphi(x)]/\hbar
        - \varphi(x)
    }{
        \varepsilon
    }\right) \\
 &= -i \delta^\mu{}_\nu [P^\nu, \varphi(x)]/\hbar \\
 &= -i [P^\mu, \varphi(x)]/\hbar
\end{align*}$$

We can define a spacetime translation operator:

$$\begin{align*}
T(a) &\equiv \mathrm{exp}(-ia_\mu P^\mu/\hbar) \\
    &= \sum_n \frac{1}{n!}\left(-\frac{i}{\hbar} a_\mu P^\mu\right)^n\\
T(-a)^{-1}\varphi(x)T(-a) &= \varphi(x - a)
\end{align*}$$
This translates the field by $a$.

Again, spacetime translation operator transforms properly under Lorentz transformation:
$$\begin{align*}
U(\Lambda)^{-1}T(a)U(\Lambda) &= \sum_n \frac{1}{n!}\left(-\frac{i}{\hbar} a_\mu U(\Lambda)^{-1}P^\mu U(\Lambda)\right)^n\\
    &= \sum_n \frac{1}{n!}\left(-\frac{i}{\hbar} \Lambda^\mu{}_\nu a_\mu P^\nu\right)^n\\
    &= \mathrm{exp}(-i\Lambda^\mu{}_\nu a_\mu P^\nu)^n\\
    &= T(\Lambda^\mu{}_\nu a_\mu)\\
    &= T(\Lambda^{-1} a)\\
\\
U(\Lambda)^{-1}T(a)^{-1}U(\Lambda) &= (U(\Lambda)^{-1}T(a)U(\Lambda))^{-1} \\
&= T(\Lambda^{-1}a)^{-1}
\end{align*}$$
For an infinitesimal translation,
$$
T(\varepsilon a) = I - \frac{i}{\hbar}\varepsilon a_\mu P^\mu
$$
This is similar to Lorentz transformation. If we apply the infinitesimal Lorentz transformation
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