Quantum Field Theory 05 - Lorentz Invariance Problems

### Problem 2.1 - 2.6
Detailed in the previous notes.

### Problem 2.7
> What property should be attributed to the translation operator $T(a)$ that could be used to prove eq. (2.20)?

At lease being commutative. Indeed, translation transformations are commutative.
### Problem 2.8
> a) Let $\Lambda = 1 + \delta \omega$ in eq. (2.26):
$$
\newcommand{\L}[2]{U({#2})^{-1}{#1}U({#2})}\newcommand{\LL}[1]{\L{#1}{\Lambda}}
\LL{\varphi(x)}=\varphi(\Lambda^{-1}x)
$$
 and show that
$$
[\varphi(x),M^{\mu\nu}]=\mathcal{L}^{\mu\nu}\varphi(x),
$$
where
$$
\mathcal{L}^{\mu\nu} \equiv -i\hbar(x^\mu\partial^\nu-x^\nu\partial^\mu).
$$

-------------

If we apply the infinitesimal Lorentz transformation
$\Lambda= 1 + \varepsilon \omega$ to $\varphi$:
$$\begin{align*}
U(\Lambda)^{-1}\varphi(x)U(\Lambda)
  &= U(1 + \varepsilon \omega)^{-1}\varphi(x)U(1 + \varepsilon \omega) \\
  &=\left(I - \frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}M^{\mu\nu}\right)
    \varphi(x)
    \left(I + \frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}M^{\mu\nu}\right) \\
&= \varphi(x) +\frac{i}{2\hbar}\varepsilon \omega_{\mu\nu}\left[\varphi(x),M^{\mu\nu}\right] + o(\varepsilon^2) \\
\varphi(\Lambda^{-1}x)
&= \varphi(x + \varepsilon \omega_{\mu\nu} x^\nu) \\
&= \varphi(x) + \varepsilon \omega_{\mu\nu} x^\nu \partial^\mu \varphi(x)\\
\end{align*}$$
Again, compare the two and take the upper half of the matrix:
$$\begin{align*}
\frac{i}{2\hbar}\omega_{\mu\nu}\left[\varphi(x),M^{\mu\nu}\right]
&= \omega_{\mu\nu} x^\nu \partial^\mu \varphi(x) \\
\frac{i}{2\hbar}\sum_{\mu,\nu}\omega_{\mu\nu}\left[\varphi(x),M^{\mu\nu}\right]
&= \sum_{\mu,\nu}\omega_{\mu\nu} x^\nu \partial^\mu \varphi(x) \\
\frac{i}{\hbar}\sum_{\mu<\nu}\omega_{\mu\nu}\left[\varphi(x),M^{\mu\nu}\right]
&= \sum_{\mu<\nu}\omega_{\mu\nu} (x^\nu \partial^\mu - x^\mu \partial^\nu )\varphi(x) \\
\frac{i}{\hbar}\left[\varphi(x),M^{\mu\nu}\right]
&= (x^\nu \partial^\mu - x^\mu \partial^\nu )\varphi(x) \\
\left[\varphi(x),M^{\mu\nu}\right] &= -i\hbar(x^\mu \partial^\nu - x^\nu \partial^\mu)\varphi(x)\\
\end{align*}$$

-------------
> Show that $[[\varphi(x), M^{\mu\nu}], M^{\rho\sigma}]=\mathcal{L}^{\mu\nu}\mathcal{L}^{\rho\sigma}\varphi(x)$

$$\begin{align*}
[[\varphi(x), M^{\mu\nu}], M^{\rho\sigma}] &= [\mathcal L ^{\mu\nu}\varphi(x), M^{\rho\sigma}] \\
&= \mathcal L ^{\mu\nu}[\varphi(x), M^{\rho\sigma}] + [\mathcal L ^{\mu\nu}, M^{\rho\sigma}]\varphi(x)
\end{align*}$$
whereas $\mathcal L$ acts on operators and $M$ acts on vectors, so they commute.
$$\begin{align*}
[\mathcal L ^{\mu\nu}\varphi(x), M^{\rho\sigma}] &= \mathcal L ^{\mu\nu}[\varphi(x), M^{\rho\sigma}] \\
&= \mathcal L ^{\mu\nu}\mathcal L ^{\rho\sigma} \varphi(x)
\end{align*}$$

-------------
> c) Prove Jacobi identity of commutators.

$$
[[A,B],C]+[[B,C],A] +[[C,A],B] =\\
(ABC-BAC-CAB+CBA)+\\
(BCA-CBA-ABC+ACB)+\\
(CAB-ACB-BCA+BAC) \\
= 0
$$

-------------
> d) Use (b) and (c) to show that $[\varphi(x), [M^{\mu\nu},M^{\rho\sigma}]]=[\mathcal{L}^{\mu\nu},\mathcal{L}^{\rho\sigma}]\varphi(x)$

$$\begin{align*}
[\varphi(x),[M^{\mu\nu},M^{\rho\sigma}]] &=
[[M^{\rho\sigma},\varphi(x)],M^{\mu\nu}] +
[[\varphi(x),M^{\mu\nu}],M^{\rho\sigma}] \\
&= [[\varphi(x),M^{\mu\nu}],M^{\rho\sigma}] -
[[\varphi(x), M^{\rho\sigma},],M^{\mu\nu}] \\
&= [\mathcal{L}^{\mu\nu},\mathcal{L}^{\rho\sigma}]\varphi(x) \\
\end{align*}$$

-------------
> e) Simplify the right-hand side of eq. (2.31) as much as possible.

$$\begin{align*}
[\mathcal{L}^{\mu\nu},\mathcal{L}^{\rho\sigma}]
&= (-i\hbar)^2\left(
    (x^\mu\partial^\nu - x^\nu\partial^\mu)(x^\rho\partial^\sigma - x^\sigma\partial^\rho)
   -(x^\rho\partial^\sigma - x^\sigma\partial^\rho)(x^\mu\partial^\nu - x^\nu\partial^\mu)
   \right)\\
x^\mu\partial^\nu x^\rho\partial^\sigma &= x^\mu (x^\rho\partial^\nu+\delta^{\nu\rho})\partial^\sigma  \\
[\mathcal{L}^{\mu\nu},\mathcal{L}^{\rho\sigma}] / (-i\hbar)^2
&=
  x^\mu\partial^\nu x^\rho\partial^\sigma
- x^\mu\partial^\nu x^\sigma\partial^\rho
- x^\nu\partial^\mu x^\rho\partial^\sigma
+ x^\nu\partial^\mu x^\sigma\partial^\rho \\
&\phantom{=} - x^\rho\partial^\sigma x^\mu\partial^\nu
+ x^\rho\partial^\sigma  x^\nu\partial^\mu
+ x^\sigma\partial^\rho x^\mu\partial^\nu
- x^\sigma\partial^\rho x^\nu\partial^\mu
\\
&=
x^\mu x^\rho [\partial^\mu, \partial^\sigma]
- x^\mu x^\sigma [\partial^\nu, \partial^\rho]
- x^\nu x^\rho [\partial^\mu, \partial^\sigma]
+ x^\nu x^\sigma [\partial^\mu, \partial^\rho]\\
&\phantom{=} + \delta^{\nu\rho}(x^\mu \partial^\sigma - x^\sigma \partial^\mu)
- \delta^{\nu\sigma}(x^\mu \partial^\rho - x^\rho \partial^\mu)\\
&\phantom{=} - \delta^{\mu\rho}(x^\nu \partial^\sigma - x^\sigma \partial^\nu)
+ \delta^{\mu\sigma}(x^\nu \partial^\rho - x^\rho \partial^\nu)
\\
&= \delta^{\nu\rho}(x^\mu \partial^\sigma - x^\sigma \partial^\mu)
- \delta^{\nu\sigma}(x^\mu \partial^\rho - x^\rho \partial^\mu) - (\mu \leftrightarrow \nu) \\
&= \Big(\delta^{\nu\rho}(x^\mu \partial^\sigma - x^\sigma \partial^\mu) - (\mu \leftrightarrow \nu)\Big)
 - (\rho \leftrightarrow \sigma) \\
[\mathcal{L}^{\mu\nu},\mathcal{L}^{\rho\sigma}] &=
i\hbar\Big(\delta^{\mu\rho}\mathcal L^{\nu\sigma} - (\mu \leftrightarrow \nu)\Big) - (\rho \leftrightarrow \sigma)\\
\end{align*}$$
This is exactly like $M$.

-------------
> f)  Use your results from part (e) to verify eq. (2.16), up to the possibility of a term on the right-hand side that commutes with $\varphi(x)$ and its derivatives. (Such a term, called a _central charge_, in fact does not arise for the Lorentz algebra.)

To verify (2.16), we add a term $R$ to the equation:
$$\begin{align*}
[M^{\mu\nu},M^{\rho\sigma}] &= i\hbar(\delta^{\mu\rho}M^{\nu\sigma} - (\mu \leftrightarrow \nu)) - (\rho \leftrightarrow \sigma) + {\color{red}R} \\
\end{align*}$$
Then try to calculate the commutator with $\varphi(x)$:
$$\begin{align*}
[\varphi(x), [M^{\mu\nu},M^{\rho\sigma}]]
&= i\hbar\Big(\delta^{\mu\rho}[\varphi(x), M^{\nu\sigma}] - (\mu \leftrightarrow \nu)\Big) - (\rho \leftrightarrow \sigma) + [\varphi(x), R] \\
&= i\hbar\Big(\delta^{\mu\rho}\mathcal L^{\nu\sigma}\varphi(x)  - (\mu \leftrightarrow \nu)\Big) - (\rho \leftrightarrow \sigma) + [\varphi(x), R] \\
&= [\mathcal{L}^{\mu\nu},\mathcal{L}^{\rho\sigma}]\varphi(x) + [\varphi(x), R] \\
&= [\varphi(x), [M^{\mu\nu},M^{\rho\sigma}]] + [\varphi(x), R] \\
[\varphi(x), R]&= 0\\
\end{align*}$$

### Problem 2.9
> Let us write
$$\begin{align}
\newcommand{Sv}[2]{S_\mathrm{V}^{#1#2}}
\newcommand{Svud}[4]{(\Sv{#1}{#2})^#3{}_#4}
\Lambda^\rho{}_\tau=\delta^\rho{}_\tau +\frac{i}{2\hbar}\varepsilon\omega_{\mu\nu}\Svud\mu\nu\rho\tau \tag{S 2.32} \label{S 2.32}
\end{align}$$
where
$$\begin{align}
\newcommand{SvDef}[4]{g^{#1#3}\delta^#2{}_#4 - g^{#2#3}\delta^#1{}_#4}
\Svud\mu\nu\rho\tau \equiv -i\hbar(
    \SvDef\mu\nu\rho\tau
) \tag{S 2.33} \label{S 2.33}
\end{align}$$
are matrices which constitutes the _verctor representation_ of the Lorentz generators.

-------------
> a) Let $\Lambda = 1+ \varepsilon \omega$ in eq. (2.27), and show that
$$\begin{align}
\newcommand{Sv}[2]{S_\mathrm{V}^{#1#2}}
\newcommand{Svud}[4]{(\Sv{#1}{#2})^#3{}_#4}
[\partial^\rho\varphi(x), M^{\mu\nu}] &=
\mathcal L^{\mu\nu}\partial^{\rho}\varphi(x)
 + \Svud\mu\nu\rho\tau\partial^\tau \varphi(x).
\tag{S 2.34} \label{S 2.34}
\end{align}$$

-------------
$$\begin{align*}
\newcommand{Sv}[2]{S_\mathrm{V}^{#1#2}}
\newcommand{Svud}[4]{(\Sv{#1}{#2})^#3{}_#4}
[\partial^\rho\varphi(x), M^{\mu\nu}]
&= -\frac{i}{\hbar}[[P^\rho, \varphi(x)], M^{\mu\nu}]\\
&= -\frac{i}{\hbar}([P^\rho,[\varphi(x),M^{\mu\nu}]]+[\varphi(x),[M^{\mu\nu},P^\rho]])\\
&= -\frac{i}{\hbar}([P^\rho,\mathcal{L}^{\mu\nu}\varphi(x)]-[\varphi(x),i\hbar(g^{\rho\nu}P^\mu-(\mu \leftrightarrow \nu))]) \\
&= \mathcal{L}^{\mu\nu}\partial^{\rho}\varphi(x)
+\frac{i}{\hbar}[P^\rho, \mathcal{L}^{\mu\nu}]\varphi(x)
-(g^{\nu\rho} \partial^\mu - (\mu \leftrightarrow \nu))\varphi(x)\\
&= \mathcal{L}^{\mu\nu}\partial^{\rho}\varphi(x)
 + \Svud\mu\nu\rho\tau\partial^\tau \varphi(x).
\end{align*}$$
The last line is again because $\mathcal L$ acts on operators and $P$ acts on vectors.

-------------
> b) Show that the matrices $
\newcommand{Sv}[2]{S_\mathrm{V}^{#1#2}}
\newcommand{Svud}[4]{(\Sv{#1}{#2})^#3{}_#4}\Sv\mu\nu$ must have the same commutation relations as the operators $M^{\mu\nu}$.

$$\begin{align*}
\newcommand{Sv}[2]{S_\mathrm{V}^{#1#2}}
\newcommand{Svud}[4]{(\Sv{#1}{#2})^#3{}_#4}
\newcommand{SvDef}[4]{g^{#1#3}\delta^#2{}_#4 - g^{#2#3}\delta^#1{}_#4}
[\Sv\mu\nu, \Sv\rho\sigma]^\alpha{}_\beta &=
\Svud\mu\nu\alpha\tau \Svud\rho\sigma\tau\beta -
\Svud\rho\sigma\alpha\tau \Svud\mu\nu\tau\beta \\
&=
(-i\hbar)^2(\SvDef\mu\nu\alpha\tau) (\SvDef\rho\sigma\tau\beta) -\\
&\phantom{=} (-i\hbar)^2(\SvDef\rho\sigma\alpha\tau) (\SvDef\mu\nu\tau\beta) \\
&= (-i\hbar)^2(
    g^{\mu\alpha}\delta^\nu{}_\tau g^{\rho\tau}\delta^\sigma{}_\beta
    -g^{\sigma\alpha}\delta^\rho{}_\tau g^{\nu\tau}\delta^\mu{}_\beta
    - (\mu \leftrightarrow \nu)
)
- (\rho \leftrightarrow \sigma)\\
&= (-i\hbar)^2 (
    g^{\mu\alpha}g^{\rho\nu}\delta^\sigma{}_\beta
    -g^{\sigma\alpha}g^{\nu\rho}\delta^\mu{}_\beta
    - (\mu \leftrightarrow \nu)
)
- (\rho \leftrightarrow \sigma)\\
&= -i\hbar (
    g^{\rho\nu}(\SvDef\mu\sigma\alpha\beta)
    -(\mu \leftrightarrow \nu)
)
- (\rho \leftrightarrow \sigma)\\
&= -i\hbar (
    g^{\rho\nu}\Svud\mu\sigma\alpha\beta
    -(\mu \leftrightarrow \nu)
)
- (\rho \leftrightarrow \sigma)\\
&= i\hbar (
    g^{\rho\mu}\Svud\nu\sigma\alpha\beta
    -(\mu \leftrightarrow \nu)
)
- (\rho \leftrightarrow \sigma)\\
\end{align*}$$

-------------
> c) For a rotation by an angle $\theta$ about the $z$ axis, we have
$$
\Lambda^\mu{}_\nu = \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & \cos \theta & -\sin \theta & 0 \\
0 & \sin \theta & \cos \theta & 0 \\
0 & 0 & 0 & 1 \\
\end{pmatrix}.
$$
Show that
$$
\Lambda = \mathrm{exp}(-i\theta S_\mathrm{V}^{12}/\hbar).
$$

write down $S_\mathrm{V}^{12}$:
$$
\text{Let }S= -\frac{i}{\hbar}S_\mathrm{V}^{12} \\
S = \begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 &-1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 \\
\end{pmatrix}
$$

To find the diagnalize the matrix:
$$\begin{align*}
S\beta &= \lambda\beta \\
\beta_0 &= 0 \\
\beta_1 &= -\lambda \beta_2 \\
\beta_2 &= \lambda \beta_1 \\
\beta_3 &= 0 \\
\lambda &= \pm i\\
V &= \begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 &-i & i \\
0 & 0 & 1 & 1 \\
1 & 0 & 0 & 0 \\
\end{pmatrix}\\
V^{-1} &= \begin{pmatrix}
0 & 0 & 0 & 1 \\
1 & 0 & 0 & 0 \\
0 & i/2 & 1/2 & 0 \\
0 & -i/2 & 1/2 & 0 \\
\end{pmatrix}\\
S &= V\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & -i & 0 \\
0 & 0 & 0 & i \\
\end{pmatrix}V^{-1}\\
\mathrm{exp}(\theta S) &= V\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & e^{-i\theta} & 0 \\
0 & 0 & 0 & e^{i\theta} \\
\end{pmatrix}V^{-1}\\
&=\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 & -ie^{-i\theta} & ie^{i\theta} \\
0 & 0 & e^{-i\theta} & e^{-i\theta} \\
0 & 0 & 0 & 0 \\
\end{pmatrix}V^{-1}\\
&=\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & \cos \theta & -\sin \theta & 0 \\
0 & \sin \theta & \cos \theta & 0 \\
0 & 0 & 0 & 0 \\
\end{pmatrix}
\end{align*}$$

-------------
> d) For a boost by rapidity $\eta$ in the $z$ direction, we have
$$
\Lambda^\mu{}_\nu = \begin{pmatrix}
\cosh \eta & 0 & 0 & \sinh \eta \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
\sinh \eta & 0 & 0 & \cosh \eta \\
\end{pmatrix}.
$$
Show that
$$
\Lambda = \mathrm{exp}(+\frac{i}{\hbar}\eta S_\mathrm{V}^{30}).
$$

$$\begin{align*}
\text{Let }S &= iS_\mathrm{V}^{30}/\hbar\\
S &= \begin{pmatrix}
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
1 & 0 & 0 & 0 \\
\end{pmatrix}\\
S\beta&=\lambda\beta\\
\lambda&=\pm 1\\
V&= \begin{pmatrix}
-1 & 0 & 0 & -1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
1 & 0 & 0 & -1 \\
\end{pmatrix}\\
V^{-1}&= \begin{pmatrix}
-1/2 & 0 & 0 & 1/2 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
-1/2 & 0 & 0 & -1/2 \\
\end{pmatrix}\\
S&=V\begin{pmatrix}
-1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 \\
\end{pmatrix}V^{-1} \\
\mathrm{exp}(\eta S)&=V\begin{pmatrix}
e^{-\eta} & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & e^\eta \\
\end{pmatrix}V^{-1} \\
&= \begin{pmatrix}
-e^{-\eta} & 0 & 0 & -e^\eta \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
e^{-\eta} & 0 & 0 & -e^\eta \\
\end{pmatrix}V^{-1} \\
&= \begin{pmatrix}
\cosh \eta & 0 & 0 & \sinh \eta \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
\sinh \eta & 0 & 0 & \cosh \eta \\
\end{pmatrix} \\
\end{align*}$$