Quantum Field Theory 04 - Lorentz Invariance (Contd.)

### Quantum scalar field under Lorentz transformation
#### Relationship between components of a scalar field
In this section, let's discuss how a quantum scalar field $\varphi$ would
transform under Lorentz transformation.
In Heisenberg picture, time evolution is defined as a unitary transformation
of operator:
$$
\newcommand{\L}[2]{U({#2})^{-1}{#1}U({#2})}\newcommand{\LL}[1]{\L{#1}{\Lambda}}
\varphi(\mathbf x, t) \equiv e^{iHt/\hbar} \varphi(\mathbf x, 0) e^{-iHt/\hbar}
$$
An obvious relativistic generalization is:
$$
\varphi(x) \equiv e^{-ixP/\hbar}\varphi(0)e^{ixP/\hbar} \\
$$
where $xP$ is defined as $x_\mu P^\mu$.
Note that this $\varphi$ is an **operator** indexed by spacetime coordinate.
Equivalently, we can postulationally define $P^\mu$ in such a way that
$[P^\mu,\,\cdot\,]=i\hbar\partial^\mu$, with the help of
[an important unnamed lemma](?page=standard-operator-identity).
Note that this $\partial^\mu$ is a partial differentiation on **operator**s.

First of all, $[P^\mu,P^\nu]=0$,
then the summation $xP$ can passthrough each other in the exponentiation function.
Then
$$\begin{align*}
e^{-ixP/\hbar}\varphi(0)e^{ixP/\hbar}
&= e^{\frac{-ix_\mu}{\hbar}[P^\mu,\,\cdot\,]}\varphi(0) \\
&= \sum_n\left(\frac{-ix_\mu}{\hbar}[P^\mu,\,\cdot\,]\right)^n \varphi(0)\\
&= \sum_n\left(x_\mu\partial^\mu\right)^n \varphi(0)\\
&= \varphi(x) \\
\end{align*}$$
The other way around:
$$\begin{align*}
\partial^\mu \varphi(x) &= \lim_{\varepsilon \to 0}\frac{\varphi(x^\nu+\varepsilon\delta^\mu{}_\nu)-\varphi(x)}{\varepsilon}\\
&= \lim_{\varepsilon \to 0} \left(
    \frac{
        e^{-i \varepsilon \delta^\mu{}_\nu P^\nu/\hbar}
        \varphi(x)
        e^{i \varepsilon \delta^\mu{}_\nu P^\nu/\hbar}
        -\varphi(x)
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

#### Spacetime Translation Operator
We can define a spacetime translation operator:

$$\begin{align*}
T(a) &\equiv \mathrm{exp}(-ia_\mu P^\mu/\hbar) \\
    &= \sum_n \frac{1}{n!}\left(-\frac{i}{\hbar} a_\mu P^\mu\right)^n\\
T(a)^{-1}\varphi(x)T(a) &= \varphi(x - a)
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
This is similar to Lorentz transformation, so we expect the following **as an axiom**:
$$
U(\Lambda)^{-1}\varphi(0)U(\Lambda) = \varphi(0)
$$
Then we can apply Lorentz transformation on all the field component:
$$\begin{align*}
U(\Lambda)^{-1}\varphi(x)U(\Lambda) &= U(\Lambda)^{-1}T(-x)^{-1}\varphi(0)T(-x)U(\Lambda) \\
  &= T(-\Lambda^{-1}x)U(\Lambda)^{-1}\varphi(0)U(\Lambda)T(-\Lambda^{-1}x) \\
  &= T(-\Lambda^{-1}x)\varphi(0)T(-\Lambda^{-1}x) \\
  &= \varphi(\Lambda^{-1}x) \\
\end{align*}$$

#### Derivatives
We mentioned that the spatial derivative of the corresponding momentum operator:
$$
\partial^\mu = -\frac{i}{\hbar}[P^\mu,\,\cdot\,]
$$
If we apply the Lorentz transformation on the derivative:
$$\begin{align*}
\LL{\partial^\mu \varphi(x)} &= -\frac{i}{\hbar}\LL{[P^\mu, \varphi(x)]} \\
&=-\frac{i}{\hbar}[\LL{P^\mu}, \LL{\varphi(x)}] \\
&= -\frac{i}{\hbar}\Lambda^\mu{}_\nu [P^\nu, \varphi(\Lambda^{-1}x)] \\
&= \Lambda^\mu{}_\nu \overline{\partial^\nu} \varphi(\Lambda^{-1}x) \\
\end{align*}$$
note that $\overline{\partial^\nu}$ works not on $x$, but on the **argment** $\overline x = \Lambda^{-1} x$.

Transforming the Laplacian:
$$\begin{align*}
\LL{\partial^2\varphi(x)} &= \LL{[P_\mu,[P^\mu,\varphi(x)]]} \\
    &= [\LL{P_\mu},[\LL{P^\mu},\LL{\varphi(x)}]] \\
    &= \Lambda_\mu{}^\nu\Lambda^\mu{}_\rho [P_\nu,[P^\rho,\varphi(\Lambda^{-1}x)]] \\
    &= \left(\Lambda^{-1}\right)^\nu{}_\mu\Lambda^\mu{}_\rho [P_\nu,[P^\rho,\varphi(\Lambda^{-1}x)]] \\
    &= [P_\nu,[P^\nu,\varphi(\Lambda^{-1}x)]] \\
    &= \overline{\partial^2} \varphi(\Lambda^{-1}x)
\end{align*}$$

Therefore it's also invariant.

### Summary
1. We use unitary operators to describe **symmetry**. When unitary operators $X$ is used to transform an operator $Y$ _unitarily_ (namely $X \to X^{-1}YX$), the "situation" does not change. To study the symmetry of an operators, one could study how this unitary transformation changes the operator.
1. For each tensor index on an (unlabelled) operator, an Lorentz transformation is applied to it after a Lorentz transformation. Namely:
$$\begin{align*}
\LL{A}&=A \\
\LL{A^\mu}&=\Lambda^\mu{}_\nu A^\nu \\
\LL{A^{\mu\nu}}&=\Lambda^\mu{}_\rho \Lambda^\nu{}_\sigma A^{\rho\sigma} \\
\LL{A_\mu}&=\Lambda_\mu{}^\nu A_{\nu} \\
... \\
\end{align*}$$
1. We normally study the properties of continuous transformations by studying the infinitesimal ones. A infinitesimal Lorentz transformation is $1 + \varepsilon \omega$, where $\omega$ is a antisymmetric matrix.
1. Lorentz transformation has 6 degrees of freedom. 3 rotations, 3 boots.
1. A Lorentz transformation $\Lambda$ corresponds to a unitary operator $U(\Lambda)$. The infinitesimal transformation $1+\varepsilon \omega$ maps to $I+\frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}M^{\mu\nu}$ where each $M^{\mu\nu}$ is an operator. The rank-2 tensor $M$ is exactly:
$$
\begin{pmatrix}
0 & K_x & K_y & K_z \\
-K_x & 0 & J_z & -J_y \\
-K_y & -J_z & 0 & J_x \\
-k_z & J_y & -J_x & 0 \\
\end{pmatrix}
$$
where $K$s are boot operators and $J$s are rotation operators.
1. Spacetime translation of $a$ corresponds to a unitary operator $T(a) = \mathrm{exp}(-iaP/\hbar)$. The infinitesimal transformation $\varepsilon a$ maps to $I - i\varepsilon aP/\hbar$.
1. $P$ does not look like the one in Schrödinger picture anymore. It is defined so that $[P^\mu,\,\cdot\,]=i\hbar\partial^\mu$. $P$ is a rank-1 tensor.
1. A scalar field $\varphi(x)$ transforms to $\varphi(\Lambda^{-1}x)$.
1. The partial derivatives of the said scalar field is a rank-1 tensor. It transforms to $\Lambda^\mu{}_\nu\overline{\partial^\nu}\varphi(\Lambda^{-1}x)$. The Laplacian $\partial^2$ is a scalar.
### See also
This section is related to [Wightman axiom W2](https://en.wikipedia.org/wiki/Wightman_axioms#W2_.28transformation_law_of_the_field.29) on the Poincaré transformation on a scalar field.
