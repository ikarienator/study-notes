Quantum Field Theory 10 - Path Integrals in (classical) Quantum Mechanics - 02


### Generalization

Let's generalize the previous result:
$$
\left\langle q'',t'\vert q',t'\right\rangle =
\int \mathcal Dp\mathcal Dq\,
\exp\left[
  i\int_{t'}^{t''}dt\, \left(p(t)\dot q(t) - H(p(t),q(t))\right)
\right]\\
$$
Let $S[p,q] \equiv \int_{t'}^{t''}dt\, \left(p(t)\dot q(t) - H(p(t),q(t))\right)$, then
$$
\left\langle q'',t'\vert q',t'\right\rangle = \int \mathcal Dp\mathcal Dq\, e^{iS[p,q]}
$$
We derived this from Weyl orderinig where:
$$
H(\hat P, \hat Q) = \int \frac{dx}{2\pi}\frac{dk}{2\pi}\, e^{ix\hat P+ik\hat Q}\,
\int dp dq \, e^{-ixp-ikq}H(p,q)\,.
$$

> The dimension of $S[p,q]$ is $[1]$.

For example, we can examine $\langle q(t_a) \rangle \equiv \left\langle {q'',t'}\middle\vert \hat Q(t_a)\middle\vert q',t'\right\rangle$, that is, the expected position of the particle at $t_1$, given by:
$$\begin{align*}
\left\langle {q'',t''} \middle \vert \hat Q(t_a) \middle \vert {q',t'}\right\rangle
&=
\left\langle {q''} \middle \vert e^{-i\hat Ht''}e^{i\hat Ht_a}\hat Qe^{-i\hat Ht_a}e^{-i\hat Ht'} \middle \vert q'\right\rangle \\
&=
\left\langle {q''} \middle \vert e^{-i\hat H(t''-t_a)}\hat Qe^{-i\hat H(t_a-t')} \middle \vert q'\right\rangle \\
&=
\int dq_b dq_a\,
\left\langle {q''} \middle \vert e^{-i\hat H(t''-t_a)} \vert q_b\right\rangle
\left\langle q_b \middle \vert \hat Q \middle \vert q_a\right\rangle
\left\langle q_a \middle \vert
e^{-i\hat H(t_a-t')} \middle \vert q'\right\rangle \\
&=
\int dq_b dq_a\,
\left\langle {q''} \middle \vert e^{-i\hat H(t''-t_a)} \middle \vert q_b\right\rangle
q_a\delta(q_b - q_a)
\left\langle q_a \middle \vert
e^{-i\hat H(t_a-t')} \middle \vert q'\right\rangle \\
&=
\int dq_a\,
q_a
\left\langle {q''} \middle \vert e^{-i\hat H(t''-t_a)} \vert q_a\right\rangle
\left\langle q_a \middle \vert e^{-i\hat H(t_a-t')} \middle \vert q'\right\rangle \\
&=
\int dq_a\,
q_a
\int \underset{q_a,t_a \to q'',t''}{\mathcal Dp\mathcal Dq} \, e^{iS[p,q]}
\int \underset{q',t' \to q_a,t_a}{\mathcal Dp\mathcal Dq} \, e^{iS[p,q]}\\
&=
\int \mathcal Dp\mathcal Dq\, q(t_a) \, e^{iS[p,q]}
\end{align*}$$

Furthermore, If we want to calculate $\langle q(t_a) \rangle \equiv \left\langle {q'',t'}\middle\vert \hat Q(t_a) \hat Q(t_b)\middle\vert q',t'\right\rangle$, then in order to plugin the operators, we need to first order them by time. This results in
$$
\int \mathcal Dp\mathcal Dq\, q(t_a) q(t_b) \, e^{iS[p,q]} =
\left\langle {q'',t'}\middle\vert T \hat Q(t_a) \hat Q(t_b)\middle\vert q',t'\right\rangle\,.
$$
In order to further develop this methods, we need to understand functional derivatives.

### Functional derivatives
A **functional** is a mapping that maps a function to a number (either real or complex). For example, the mapping
$$
x_0 \to f(x_0)
$$
is a function, where $x_0$ is an **argument** of function $f$. The other part:
$$
f \to f(x_0)
$$
is a functional, where $x_0$ is a **parameter**. Usually written as $F[f] = x_0$. In here, we write it as $F: (\mathbb C \to \mathbb C) \to \mathbb C$.

Functionals are often defined as definite integrals involving functions and their derivatives. And in variation calculus, we are often interested in _extremal_ functions, where the derivate of a fuctional is $0$.

Consider the functional:
$$
J[f] = \int_a^b\,L[x,f,f']\,dx\,
$$
we can add an arbitrary function $\phi$ times a infinitesimal positive number $\delta$ on $f$ then:

$$\begin{align*}
J[f+\delta\phi] - J[f]&= \int_a^b\,L[x,f+\delta\phi,f' + \delta\phi']\,dx - J[f] \\
&= \int_a^b\,\frac{\partial}{\partial f} L\delta\phi\,dx
 + \int_a^b\,\frac{\partial}{\partial f'} L\delta\phi'\,dx \\
&= \int_a^b\,\frac{\partial}{\partial f} L\delta\phi\,dx
 + \int_a^b\,\frac{\partial}{\partial f'} L\,d\delta\phi \\
&= \int_a^b\,\frac{\partial}{\partial f} L\delta\phi\,dx
 + \left(\int_a^b\,\frac{\partial}{\partial f'} L\,d\delta\phi\right) \\
&= \int_a^b\,\frac{\partial}{\partial f} L\delta\phi\,dx
 + \left(\left.\frac{\partial}{\partial f'} L\delta\phi\,\right\vert_a^b-\int_a^b\,\delta\phi\,d\left(\frac{\partial}{\partial f'} L\right)\right) \\
 &= \left.\frac{\partial}{\partial f'} L\delta\phi\,\right\vert_a^b +
 \int_a^b\,\left(\frac{\partial}{\partial f} L
 -\frac{d}{dx}\frac{\partial}{\partial f'} L\right)\delta\phi\,dx \\
\end{align*}$$

If we are trying to look for the case where the derivative is $0$, we can require $\delta\phi$ to be $0$ at $a$ and $b$, then we have the Euler-Lagrangian equation:
$$
\frac{\partial}{\partial f} L
 -\frac{d}{dx}\frac{\partial}{\partial f'} L = 0
$$

> **NOTE** ***Fundamental lemma of calculus of variations***: If a continuous function $f$ on a open interval $(a, b)$ satisfies
$$
\int_a^b f(x)h(x)\,dx =0
$$
for all compactly supported smooth function $h$ on $(a, b)$, then $f$ is identically zero.

---

**Definition (Functional derivative)**: Given a manifold $M$ representing function $\rho$, and a functional $F$ defined as:
$$
F: M \to \mathbb R\quad\text{or}\quad F:M \to \mathbb C\,,
$$
the **functional derivative** of $F[\rho]$, denoted $F_\rho\equiv\frac{\delta F}{\delta \rho}: M \to \mathbb R$, is defined by
$$
\begin{align*}
 \int \frac{\delta F}{\delta\rho}(x) \phi(x) \; dx
&= \lim_{\varepsilon\to 0}\frac{F[\rho+\varepsilon \phi]-F[\rho]}{\varepsilon} \\
&= \left.\frac{d}{d\varepsilon}F[\rho+\varepsilon \phi]\right|_{\varepsilon=0},
\end{align*}
$$
where $\phi$ is an arbitrary function. and $\varepsilon\phi$ is called the variation of $\rho$.

We can then replace $\phi$ with Dirac delta $\delta(x - x_0)$ to get $F_\rho(x_0)$:
$$
\begin{align*}
\frac{\delta F}{\delta\rho}(x_0) &=
\int \frac{\delta F}{\delta\rho}(x) \delta(x - x_0) \; dx \\
&= \left.\frac{d}{d\varepsilon}F[\rho+\varepsilon \delta(x - x_0)]\right|_{\varepsilon=0},
\end{align*}
$$

For a special case: $F[\rho] = \rho(x_1)$, that is, a functional that picks a value out of a function, then we have
$$
\begin{align*}
\frac{\delta F}{\delta \rho}(x_0)
&=
\left.\frac{d}{d\varepsilon}\left(\rho(x_1) + \varepsilon\delta(x_1 - x_0)\right)\right|_{\varepsilon=0}\\
&= \delta(x_1-x_0)
\end{align*}
$$

> **NOTE** I think this is an abuse of notation, but normally we define:
$$
\frac{\delta F}{\delta \rho}(x_0) \equiv \frac{\delta F}{\delta \rho(x_0)}
$$

> This notation does not make sense. $\rho(x_0)$ is a number. We can simply
say
$$
\frac{\delta F}{\delta \rho} \equiv \lambda x_0. \frac{\partial F[\rho]}{\partial\rho(x_0)}
$$
If we think about $\rho$ as an vector. But then this will also be an abuse of notation.
So we are going to write it the normal way from now on.

Now we can add some more terms in the hamiltonian:
$$
H'(p,q)[f,h] = H(p,q) - f(t)q(t) - h(t)p(t)
$$

Then $\left\langle q'',t'\vert q',t'\right\rangle$ becomes a functional as well:
$$
\left\langle q'',t'\vert q',t'\right\rangle[f,h]
= \int \mathcal Dp\mathcal Dq\, \, \exp[i\int_{t'}^{t''}\,(p\dot q - H(p,q) + fq + hp)]
$$
Then
$$
-i\frac{\delta}{\delta f(t_1)}\left(\left\langle q'',t'\vert q',t'\right\rangle[f,h]\right)
= \int \mathcal Dp\mathcal Dq\, \, q(t_1)\exp[i\int_{t'}^{t''}\,(p\dot q - H(p,q) + fq + hp)]
$$
