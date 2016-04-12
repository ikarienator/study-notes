Quantum Field Theory 07 - Canonical Quantization of Scalar Fields (Problems)

### Problem 3.1
> Derive eq. (3.29) from eqs.(3.21), (3.24), and (3.28).

(3.21):$$a(\mathbf k) = \int d^3\, x e^{-ikx}(\omega\varphi(x) + i\partial_0\varphi(x)).$$
(3.24):$$\Pi(x)=\dot\varphi(x).$$
(3.28):$$\begin{align*}
[\varphi(\mathbf x, t), \varphi(\mathbf x', t)]&=0\,, \\
[\Pi(\mathbf x, t), \Pi(\mathbf x', t)]&=0\,, \\
[\varphi(\mathbf x, t), \Pi(\mathbf x', t)]&=i\delta^3(\mathbf x - \mathbf x')\,.
\end{align*}$$

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
\int d^3\x \, e^{\pm i\k\cdot\x}\, f(\k) &= (2\pi)^3\delta^3(\k) f(\k)\\
a(\k) &= \int d^3\x \, e^{-i\k\cdot \x+i\omega t} (\omega \varphi(\x)+ i\dot\varphi(\x))\\
a^*(\k) &= \int d^3\x \, e^{i\k\cdot \x-i\omega t} (\omega \varphi^*(\x) -i\dot\varphi^*(\x))\\
&=\int d^3\x \, e^{i\k\cdot \x-i\omega t} (\omega \varphi(\x) -i\dot\varphi(\x))
\end{align*}$$
The last line is because $\varphi$ is a real field.
$$\begin{align*}
[a(\k),a^*(\k')]
&= \int d^3\x d^3\x' \, e^{-i\k\cdot \x+i\omega t + i\k'\cdot \x'-i\omega' t}(
        [\omega \varphi,\omega' \varphi']
        -i\omega [\varphi,\dot\varphi']
        +i\omega'[\dot\varphi,\varphi']
        +[\dot\varphi,\dot\varphi']
    )\\
&=\int d^3\x d^3\x' \, e^{-i\k\cdot \x+i\omega t + i\k'\cdot \x'-i\omega' t} (
        \omega \omega' [\varphi,\varphi']
        -i\omega [\varphi,\Pi']
        +i\omega'[\Pi,\varphi']
        +[\Pi,\Pi']
    )\\
&=\int d^3\x d^3\x' \, e^{-i\k\cdot \x+i\omega t + i\k'\cdot \x'-i\omega' t} (\omega \delta^3(\x-\x') + \omega' \delta^3(\x-\x'))\\
&=\int d^3\x \, (\omega+\omega') e^{-i(\k-\k')\cdot \x+i(\omega-\omega') t}\\
&=(\omega+\omega')(2\pi)^3\delta^3(\k-\k') e^{i(\omega-\omega') t}\\
&=2\omega(2\pi)^3\delta^3(\k-\k')\\
\end{align*}$$

### Problem 3.2
> Use the commutation relations, eq. (3.29), to show explicitly that a state of the form
$$
\newcommand{k}[0]{\mathbf k}
\vert k_1 ... k_n\rangle \equiv a^\dagger(\k_1)...a^\dagger(\k_n)\vert 0 \rangle
$$

> is a eignestate of the hamiltonian, eq. (3.30), with eigenvalue $\omega_1 + ... + \omega_n$. The vacuum $\vert 0 \rangle$ is annihilated by $a(\mathbf k)$, and we take $\Omega_0 = \mathcal E_0$ in eq. (3.30).

Eq. (3.29):
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
[a(\k),a(\k')]&=0\,,\\
[a^\dagger(\k),a^\dagger(\k')]&=0\,,\\
[a(\k),a^\dagger(\k')]&=(2\pi)^3 2\omega \delta^3(\k-\k')\,.\\
\end{align*}$$

Eq. (3.30) with th condition $\Omega_0 = \mathcal E_0$:
$$
\newcommand{k}[0]{\mathbf k}
H= \frac{1}{2}\int d^3\k\,a^\dagger(\k)a(\k)\,.
$$

> Note: This looks awfully like the counting operator $N$ in [section 1](?page=qft-01-problems).

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
H\vert 0 \rangle &= 0 \,,\\
H a^\dagger(\k_1) &= \frac{1}{2} \int d^3k\, a^\dagger(\k)a(\k) a^\dagger(\k_1)\\
&= \frac{1}{2} \int d^3k \, a^\dagger(\k)\left(a^\dagger(\k_1)a(\k)+[a(\k),a^\dagger(\k_1)]\right)\\
&= \frac{1}{2} \int d^3k \, a^\dagger(\k)\left(a^\dagger(\k_1)a(\k)+2\omega(2\pi)^3\delta^3(\k-\k_1)\right)\\
&= (2\pi)^3\omega_1 a^\dagger(\k_1) +  \frac{1}{2} \int d^3k \, a^\dagger(\k)a^\dagger(\k_1)a(\k)\\
&= (2\pi)^3\omega_1 a^\dagger(\k_1) + a^\dagger(\k_1)  \,,\\
[H, a^\dagger(\k)] &= (2\pi)^2 \omega(\k) a^\dagger(\k) \,,\\
H a^\dagger(\k_1)a^\dagger(\k_2) &= (2\pi)^3\omega_1 a^\dagger(\k_1)a^\dagger(\k_2)
 + a^\dagger(\k_1) H a^\dagger(\k_2)\\
 &= (2\pi)^3\omega_1 a^\dagger(\k_1)a^\dagger(\k_2)
 + (2\pi)^3\omega_2 a^\dagger(\k_1)a^\dagger(\k_2)
 + a^\dagger(\k_1) a^\dagger(\k_2) H \\
 &= (2\pi)^3(\omega_1+\omega_2) a^\dagger(\k_1)a^\dagger(\k_2)
 + a^\dagger(\k_1) a^\dagger(\k_2) H  \,,\\
H \vert k_1 ... k_n \rangle &=
(2\pi)^3(\omega_1 + ... + \omega_n) a^\dagger(\k_1)...a^\dagger(\k_n) \vert 0 \rangle + a^\dagger(\k_1)...a^\dagger(\k_n) H \vert 0 \rangle \\
&= (2\pi)^3(\omega_1 + ... + \omega_n) a^\dagger(\k_1)...a^\dagger(\k_n) \vert 0 \rangle\\
&= (2\pi)^3(\omega_1 + ... + \omega_n) \vert k_1 ... k_n \rangle  \,.\\
\end{align*}$$

### Problem 3.3
> Use $U(\Lambda)^{-1}\varphi(x)U(\Lambda) = \varphi(\Lambda^{-1}x)$ to show that
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
U(\Lambda)^{-1}a(\k)U(\Lambda) &= a(\Lambda^{-1}\k) \,,\\
U(\Lambda)^{-1}a^\dagger(\k)U(\Lambda) &= a^\dagger(\Lambda^{-1}\k) \,,\\
\end{align*}$$

> and hence that
$$
U(\Lambda)\vert k_1 ... k_n\rangle = \vert \Lambda k_1 ... \Lambda k_n\rangle\,,
$$

> where $\vert k_1 ... k_n\rangle = a^\dagger(\k_1)...a^\dagger(\k_n)\vert 0 \rangle$.

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
U(\Lambda)^{-1}\varphi(x)U(\Lambda) &= \varphi(\Lambda^{-1}x) \\
U(\Lambda)^{-1}\partial^\mu\varphi(x)U(\Lambda) &= \Lambda^\mu{}_\nu\overline{\partial^\nu}\varphi(\Lambda^{-1}x) \\
\end{align*}$$

Write down the fourier transformation of $\varphi(x)$:
$$
\widetilde\varphi(k) = \int d^4x\, e^{ikx} \varphi(x)\\
\varphi(x) = \int \frac{d^4x}{(2\pi)^4}\, e^{ikx} \tilde\varphi(k)
$$

---

$$\begin{align*}
U(\Lambda)^{-1}\widetilde\varphi(k)U(\Lambda)
&= \int d^4x\, e^{ik_\mu x^\mu} \varphi(\Lambda^{-1}x)\\
&= \int d^4x\, e^{ik_\mu \Lambda^\mu{}_\nu x^\nu} \varphi(x) \\
&= \int d^4x\, e^{i (\Lambda^{-1})_\nu{}^\mu k_\mu x^\nu} \varphi(x) \\
&= \int d^4x\, e^{i (\Lambda^{-1}k)x} \varphi(x) \\
&= \widetilde \varphi(\Lambda^{-1}k)
\end{align*}$$

---

$$
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
a(\k) = i \int d^3\x e^{-i\k\cdot\x+i t \omega} (\omega\varphi(x) - i \partial_0\varphi(x))
$$
