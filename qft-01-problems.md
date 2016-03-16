Quantum Field Theory 01 (Problems)

#### Problem 1.1

$$
\begin{align*}
\{\alpha^j,\alpha^k\}_{ab} &=2\delta^{jk}\delta_{ab} \\
\mathrm{tr}(\alpha^i) &= \mathrm{tr}(\alpha^j\alpha^j\alpha^i) \\
                      &= -tr(\alpha^j\alpha^i\alpha^j) \\
                      &= -tr(\alpha^i\alpha^j\alpha^j) \\
\end{align*}
$$

The last step is due to rotation identity of trace. This gives that the
trace of a Dirac matrix is $0$.

$$
\left(\alpha^j\right)^2 = I
$$

This gives that all the eigenvalues of a Dirac matrix are $\pm 1$.


#### Problem 1.2

Consider the first term of $H$:

$$
H = \int dx^3 a^\dagger(x)H_0a(x)
$$

where $H_0 = -\frac{\hbar^2}{2m}\nabla^2+U(x)$ indicates the classical
Hamiltonian, applied to the state:

$$
\left|\psi,t\right\rangle = \int dx_1^3...dx_n^3
\psi(x_1,...x_n;t)a^\dagger(x_1)...a^\dagger(x_n)\left|0\right\rangle
$$

we have

$$
\begin{align*}
H\left|\psi,t\right\rangle = \int dx^3 a^\dagger(x) H_0 a(x) \int
dx_1^3\psi(x_1) a^\dagger(x_1)\left|0\right\rangle
\end{align*}
$$

Note that $\left|0\right\rangle$ is in the Hilbert space of states, whereas
$a(x)$ and $a^\dagger(x)$ are in the quantum field, and $\psi$
is a coeffecients on the quantum field and $H_0$ is an operator that
acts on $\psi$. Therefore they can pass through $a$ and $a^\dagger$ but
they themselves cannot commute.

Reorder the terms, we got:

$$
\begin{align*}
H\left|\psi,t\right\rangle &= \int dx^3 dx_1^3 H_0\psi(x_1) a^\dagger(x) a(x)
a^\dagger(x_1) \left|0\right\rangle \\
    &= \int dx^3 H_0\psi(x) a^\dagger(x)\left|0\right\rangle + \int dx^3 dx_1^3 H_0\psi(x_1)
 a^\dagger(x) a^\dagger(x_1) a(x) \left|0\right\rangle
\end{align*}
$$

Note that for fermions, it takes the minus sign instead of the plus
sign. But the second term vanishes because $a(x)\left|0\right\rangle = 0$:

$$
H\left|0\right\rangle = \int dx^3 H_0\psi(x)
a^\dagger(x)\left|0\right\rangle
$$

On the left hand side:

$$
i\hbar\partial_t\left|\psi,t\right\rangle = \int dx^3
i\hbar\partial_t\psi(x,t)
a^\dagger(x)\left|0\right\rangle
$$

The interaction part can be proved similarly because: 1. we have the
$a^\dagger$ term on the left in the Hamiltonian to correspond to the
$a^\dagger$ on the right in the state; 2. we have the $a$ term on the
right of the Hamiltonian so the commuted term vanishes with vacuum
state.

#### Problem 1.3 (Prove that $[N,H] = 0$)

We start with proving that $\left[N, a^\dagger(x)\right]=a^\dagger(x)$:

$$\begin{align*}
\left[a^\dagger(x)a(x), a^\dagger(y)\right]&=a^\dagger(x)a(x)a^\dagger(y)-a^\dagger(y)a^\dagger(x)a(x) \\
&=a^\dagger(x)a(x)a^\dagger(y)- a^\dagger(x)a^\dagger(y)a(x)\\
&=a^\dagger(x)\left[a(x),a^\dagger(y)\right]\\
&=a^\dagger(x)\delta^3(x-y)\\
\end{align*}$$

$$
\left[N,a^\dagger(x)\right] = \int dy^3 a^\dagger(y) a(y) a^\dagger(x)\delta^3(x-y) = a^\dagger(x)
$$
Similarly, $[N, a(x)] = -a(x)$.
If $\beta$ is a string of $a$ and $a^\dagger$s applying together, that is:

$$\begin{align*}
    \beta = \, &I \, \, \vert \\
    &a(x) \beta \, \, \vert \\
    &a^\dagger(x) \beta
\end{align*}$$

Then recursively, it can be proved that $[N, \beta]$ returns $(n - m)\beta$ where $n$ is the number of $a^\dagger$s in $\beta$ and $m$ is the number of $a$s in $\beta$.

$$\begin{align*}
[N, I] &= 0 \\
\end{align*}$$

if $[N, \beta] = (n - m)\beta$, then
$$\begin{align*}
[N, a^\dagger(x)\beta] &= Na^\dagger(x)\beta - a(x)^\dagger\beta N \\
               & = \left([N, a^\dagger(x)] + a^\dagger(x)N\right)\beta - a^\dagger(x)\beta N \\
               & = a^\dagger(x)\beta + a^\dagger(x)N\beta - a^\dagger(x)\beta N \\
               & = a^\dagger(x)\beta + a^\dagger(x)[N, \beta] \\
               & = \left((n + 1) - m\right)a^\dagger(x)\beta \\
[N, a(x)\beta] &= Na(x)\beta - a(x)\beta N \\
               & = \left([N, a(x)] + a(x)N\right)\beta - a(x)\beta N \\
               & = -a(x)\beta + a(x)N\beta - a(x)\beta N \\
               & = -a(x)\beta + a(x)[N, \beta] \\
               & = \left(n - (m + 1)\right)a(x)\beta \\
\end{align*}$$

Now write down $H$:
$$
H = \int dx^3 H_0 a^\dagger(x)a(x) + \frac{1}{2}\int dx^3 dy^3 V(x-y) a^\dagger(x) a^\dagger(y)a(y)a(x)
$$

Then:
$$\begin{align*}
[N, H] &= \int dx^3 H_0 [N, a^\dagger(x)a(x)] + \frac{1}{2}\int dx^3 dy^3 V(x-y) [N, a^\dagger(x) a^\dagger(y)a(y)a(x)] \\
 &=0\\
\end{align*}$$

  
