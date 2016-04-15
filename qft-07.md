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

---

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

---

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

We need to lift $a(\mathbf k)$ to 4-dimensional by contraint $k^0$ by the delta function that expresses on shell momentum:
$$
A(k) = \theta(k^0)\delta(k^2+m^2)a(\mathbf k).
$$
This lets us re-plug the delta back to $\varphi(x)$:
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\varphi(x)
&= \int \widetilde{dk}\, (a(\k)e^{ikx} + a^*(\k)e^{-ikx}) \\
&= \int \frac{d^4k}{(2\pi)^3}\, \delta(k^2+m^2)\theta(k^0)(a(\k)e^{ikx} + a^*(\k)e^{-ikx})\\
&= \int \frac{d^4k}{(2\pi)^3}\, \delta(k^2+m^2)(\theta(k^0)a(\k)e^{ikx} + \theta(-k^0)a^*(-\k)e^{ikx})\\
&= \int \frac{d^4k}{(2\pi)^3}\, e^{ikx}(A(k)+A^*(-k))\\
\end{align*}$$
Conjugate the Lorentz transformation:
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
U(\Lambda)^{-1}\varphi(x)U(\Lambda)
&= \int \frac{d^4k}{(2\pi)^3}\, e^{ikx}U(\Lambda)^{-1}(A(k)+A^*(-k))U(\Lambda) \\
&= \varphi(\Lambda^{-1}k) \\
&= \int \frac{d^4k}{(2\pi)^3}\, e^{ikx}(A(\Lambda^{-1}k)+A^*(-\Lambda^{-1}k)) \\
\end{align*}$$
Due to the arbitrarity of $x$, the integrand must be equal.
Note that if $\Lambda$ is othorchronous, due to the effect of $\theta(k^0)$ in $A$, $A(\Lambda^{-1}k)$ and $A^*(-\Lambda^{-1}k)$ cannot both be non-zero. Then we have:
$$
U(\Lambda)^{-1}A(k)U(\Lambda) = A(\Lambda^{-1}k)\,,\\
$$
then we get:
$$
\newcommand{k}[0]{\mathbf k}
U(\Lambda)^{-1}a(\k)U(\Lambda) = a(\Lambda^{-1}\k)\,.
$$

Now, $\vert k_1 ... k_n\rangle = a^\dagger(\k_1)...a^\dagger(\k_n)\vert 0 \rangle$,
$$\begin{align*}
U(\Lambda)\vert k_1 ... k_n\rangle
&=U(\Lambda)a^\dagger(\k_1)...a^\dagger(\k_n)\vert 0 \rangle \\
&=U(\Lambda)a^\dagger(\k_1)U(\Lambda)^{-1}U(\Lambda)...U(\Lambda)a^\dagger(\k_n)U(\Lambda)^{-1}U(\Lambda)\vert 0 \rangle \\
&=a^\dagger(\Lambda\k_1)...a^\dagger(\Lambda\k_n)U(\Lambda)\vert 0 \rangle \\
\end{align*}$$

**By postulate**, $U(\Lambda)\vert 0 \rangle = \vert 0 \rangle$, then:
$$
U(\Lambda)\vert k_1 ... k_n\rangle = \vert \Lambda k_1 ... \Lambda k_n\rangle\,.
$$

---

### Problem 3.4
> Recall that $T(a)^{-1}\varphi(x)T(a) = \varphi(x-a)$, where $T(a) \equiv \exp(-iP^\mu a_\mu)$ is the spacetime translation operator, and $P^0$ is identified as the hamiltonian $H$.

---

> a) Let $a^\mu$ be infinitesimal, and derive an expression for $[\varphi(x), P^\mu]$.

We previously postulated that $[P^\mu,\varphi(x)] = i\partial^\mu \varphi(x)$, and proved that the postulation in Srednicki is equivalent to it. To review it, the infinitesimal $T(a)$ is
$$\begin{align*}
T(\delta a) &= \exp(-iP^\mu \delta a_\mu)\\
&= 1 - i \delta P^\mu a_\mu o(\delta^2)\\
T(\delta a)^{-1}\varphi(x)T(\delta a)
&= (1 + i\delta P^\mu a_\mu)\varphi(x)(1 - i\delta P^\mu a_\mu)\\
&= \varphi(x) + i\delta a_\mu [P^\mu, \varphi(x)]\\
\partial^\mu\varphi(x) &= \lim_{\delta \to 0}\frac{\varphi(x+\delta^\mu{}_\nu a^\nu\delta)-\varphi(x)}{\delta a^\nu} \\
&= - i [P^\mu, \varphi(x)]\\
[P^\mu, \varphi(x)] &= i\partial^\mu\varphi(x) \\
[\varphi(x), P^\mu] &= -i\partial^\mu\varphi(x) \\
\end{align*}$$

---
> b) Show that the time component of your result is quivalent to the Heisenberg equation of motion $i\dot\varphi = [H, \varphi]$.

This is apparent.

---
> c) For a free field, use the Heisenberg equation to derive the Klein-Grodon equation.

$$\begin{align*}
i\dot\varphi&=[\varphi,H]\\
&= \left[\varphi,\int d^3x \, \left(\frac{1}{2}\Pi^2 + \frac{1}{2}(\nabla\varphi)^2+\frac{1}{2}m^2\varphi^2\right)\right] \\
&= \int d^3x \, \left[\varphi,\frac{1}{2}\Pi^2 + \frac{1}{2}(\nabla\varphi)^2+\frac{1}{2}m^2\varphi^2\right] \\
&= \frac{1}{2}\int d^3x \, \left[\varphi,\Pi^2\right] \\
&= i\Pi(x) \\
\Pi(x) &= \dot\varphi(x) \\
[H,\Pi(x)] &= i\ddot\varphi(x) \\
[H,H]&=\int d^3x \, \left[H,\frac{1}{2}\dot\varphi^2 + \frac{1}{2}(\nabla\varphi)^2+\frac{1}{2}m^2\varphi^2\right]\\
&= i\int d^3x \, \left(\ddot\varphi(x)\dot\varphi(x)
    -i[H, \frac{1}{2}\partial^i\varphi(x)\partial_i\varphi(x)]+
    m^2\varphi(x)\dot\varphi(x)\right)\\
&= i\int d^3x \, \left(\ddot\varphi(x)\dot\varphi(x)+
    \partial^i\dot\varphi(x)\partial_i\varphi(x)+
    m^2\varphi(x)\dot\varphi(x)\right)\\
\int d^3x \, \partial^i\varphi(x)\partial_i\dot\varphi(x)
&= - \int d^3x \, \partial^2\varphi(x)\dot\varphi(x)\\
[H,H]&=i\int d^3x \, \left(\ddot\varphi(x)\dot\varphi(x)-
    \partial^2\varphi(x)\dot\varphi(x)+
    m^2\varphi(x)\dot\varphi(x)\right)\\
    &=0\\
0&=\ddot\varphi(x) - \partial^2\varphi(x) + m^2\varphi(x)\\
\end{align*}$$

---

> d) Define a spatial momentum operator
$$
\mathbf P \equiv - \int d^3x \Pi(x)\nabla\varphi(x)\,.
$$

> Use the canonical commutation relations to show that $\mathbf P$ obeys the relation you derived in part (a).

$$\begin{align*}
\newcommand{P}[0]{\mathbf P}
[\P^i, \varphi(y)] &= - \int d^3x \, [\dot\varphi(x)\varphi_i(x), \varphi(y)] \\
&= - \int d^3x \, \left(\dot\varphi(x)\varphi_i(x)\varphi(y) - \varphi(y)\dot\varphi(x)\varphi_i(x) \right)\\
&= - \int d^3x \, \left(\dot\varphi(x)\partial^i(\varphi(x)\varphi(y)) - \dot\varphi(x)\varphi_i(y)\varphi(x) - \varphi(y)\dot\varphi(x)\varphi_i(x) \right)\\
&= - \int d^3x \, \left(\dot\varphi(x)\partial^i(\varphi(x)\varphi(y)) - \dot\varphi(x)\varphi_i(y)\varphi(x) - \dot\varphi(x)\varphi(y)\varphi_i(x) + [\dot\varphi(x),\varphi(y)]\varphi_i(x) \right)\\
&= - \int d^3x \, \left(\dot\varphi(x)\partial^i[\varphi(x),\varphi(y)] + [\dot\varphi(x),\varphi(y)]\varphi_i(x) \right)\\
&= - \int d^3x \, -i\delta^3(x-y) \varphi_i(x)\\
&= i\nabla\varphi(x)\\
\end{align*}$$

---

> e) Express $\mathbf P$ in terms of $a(\mathbf k)$ and $a^\dagger(\mathbf k)$.

$$
\newcommand{k}[0]{\mathbf k}
\newcommand{P}[0]{\mathbf P}
\varphi(x) = \int \widetilde{dk}(e^{ikx}a(\k) +e^{-ikx}a^\dagger(\k)) \\
\partial^\mu\varphi(x) = \int \widetilde{dk}(e^{ikx}ik^\mu a(\k) + e^{-ikx}(-ik^\mu)a^\dagger(\k))$$

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{P}[0]{\mathbf P}
\P^i&=-\int d^3x\,\partial^0 \varphi(x) \partial^i\varphi(x)\\
&=-\int d^3x\,\left(
    \int \widetilde{dk}\,(e^{ikx}ik^0 a(\k) + e^{-ikx}(-ik^0)a^\dagger(\k))
\right)\\
&\phantom =\left(
    \int \widetilde{dk}\,(e^{ikx}ik^i a(\k) + e^{-ikx}(-ik^i)a^\dagger(\k))
\right)\\
&=-\omega \int d^3x\widetilde{dk}\widetilde{dk}'\, k'^i \left(
    (e^{ikx} a(\k) - e^{-ikx}a^\dagger(\k))
    (e^{ik'x}a(\k') - e^{-ik'x}a^\dagger(\k'))
\right)\\
&=-\omega \int d^3x\widetilde{dk}\widetilde{dk}'\, k'^i \left(
    (e^{ikx} a(\k) - e^{ikx}a^\dagger(-\k)e^{-2i\omega t})
    (e^{-ik'x}a(-\k')e^{2i\omega t} - e^{-ik'x}a^\dagger(\k'))
\right)\\
&=-\omega \int d^3x\widetilde{dk}\widetilde{dk}'\, k'^i e^{i(k-k')x}\left(
    (a(\k) - a^\dagger(-\k)e^{-2i\omega t})
    (a(-\k')e^{2i\omega t} - a^\dagger(\k'))
\right)\\
&=-\omega (2\pi)^3 \int \widetilde{dk}\widetilde{dk}'\, \delta^3(k-k')k'^i \left(
    (a(\k) - a^\dagger(-\k)e^{-2i\omega t})
    (a(-\k')e^{2i\omega t} - a^\dagger(\k'))
\right)\\
&=-\omega (2\pi)^3 \int \widetilde{dk}\frac{1}{(2\pi)^32\omega}\, k^i \left(
    (a(\k) - a^\dagger(-\k)e^{-2i\omega t})
    (a(-\k)e^{2i\omega t} - a^\dagger(\k))
\right)\\
&=-\frac{1}{2}\int \widetilde{dk} \, k^i \left(
    a(\k)a(-\k)e^{2i\omega t}
    -a(\k)a^\dagger(\k)
    -a^\dagger(-\k)a(-\k)
    +a^\dagger(-\k)e^{-2i\omega t}a^\dagger(\k)
\right)\\
\end{align*}$$
Remove the odd terms,
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{P}[0]{\mathbf P}
P^i&=\frac{1}{2}\int \widetilde{dk} \, k^i \left(
    a(\k)a^\dagger(\k)+a^\dagger(-\k)a(-\k)\right)\\
&=\frac{1}{2}\int \widetilde{dk} \, k^i \left(a(\k)a^\dagger(\k)+a^\dagger(\k)a(\k)\right)\\
&=\frac{1}{2}\int \widetilde{dk} \, k^i \left(2a(\k)a^\dagger(\k)-[a(\k),a^\dagger(\k)]\right)\\
&=\frac{1}{2}\int \widetilde{dk} \, k^i \left(2a(\k)a^\dagger(\k)
-(2\pi)^32\omega\delta^3(0)\right)\\
&=\int \widetilde{dk} \, \k a^\dagger(\k)a(\k)\\
\end{align*}$$

---

By the way, combining with $H$, we have:

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
P^\mu &= \int \widetilde{dk}\, k^\mu a^\dagger(\k)a(\k) \,.\\
\end{align*}$$
Since
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
U(\Lambda)^{-1}P^\mu U(\Lambda) &= \int \widetilde{dk}\, k^\mu a^\dagger(\Lambda^{-1}\k)a(\Lambda^{-1}\k) \\
&= \int \widetilde{dk}\, \Lambda^\mu{}_\nu k^\nu a^\dagger(\k)a(\k) \\
&= \Lambda^\mu{}_\nu P^\nu\,,
\end{align*}$$

they form a 4-vector of operators. Since the hamiltonian is the total energy of the system, $P^\mu$ is the total momentum of the system.

---

### Problem 3.5
> Consider a complex (that is, nonhermitian) scaler field $\varphi$ with a lagrangian density
$$
\mathcal L = -\partial^\mu\varphi^\dagger\partial_\mu\varphi - m^2\varphi^\dagger\varphi + \Omega_0\,.
$$

---

> a) Show that $\varphi$ obeys the Klein-Gordon equation.

Let's add an infinitesimal variance term $\delta\psi$ to $\varphi$ and accordingly, $\delta\psi^\dagger$ is added to $\varphi^\dagger$:
$$\begin{align*}
\delta \mathcal L
    &= -\partial^\mu \delta\psi^\dagger\partial_\mu\varphi
       -\partial^\mu \varphi^\dagger\partial_\mu\delta\psi
       -m^2(\delta \psi^\dagger\varphi + \varphi^\dagger\delta \psi) \,,
    \\
\delta S &= \int d^4 x \, \left(
    -\partial^\mu \delta\psi^\dagger\partial_\mu\varphi
    -\partial^\mu \varphi^\dagger\partial_\mu\delta\psi
    -m^2(\delta \psi^\dagger\varphi + \varphi^\dagger\delta \psi)
    \right)\\
    &= \int d^4 x \, \left(
    \delta\psi^\dagger\partial^\mu \partial_\mu\varphi
    +\partial_\mu\partial^\mu\varphi^\dagger\delta\psi
    -m^2(\delta \psi^\dagger\varphi + \varphi^\dagger\delta \psi)
    \right)\\
    &= \int d^4 x \,
    (\partial^2\varphi - m^2\varphi)\delta\psi^\dagger
    +(\partial^2\varphi^\dagger - m^2\varphi^\dagger)\delta\psi\\
    &= 0 \,,\\
\end{align*}$$
$$\begin{align*}
(\partial^2\varphi - m^2\varphi)\delta\psi^\dagger+(\partial^2\varphi^\dagger - m^2\varphi^\dagger)\delta\psi &= 0\,.
\end{align*}$$
Now, $\delta\psi$ and $\delta\psi^\dagger$ are not independent. But we know that
$\delta\psi + \delta\psi^\dagger \equiv \alpha$ and $\delta\psi - \delta\psi^\dagger \equiv \beta$ are indeed indepdent.
We can reorder this into:
$$
\delta\psi = \frac{1}{2}(\alpha + \beta)\\
\delta\psi^\dagger = \frac{1}{2}(\alpha - \beta)\\
$$
$$
(\partial^2\varphi - m^2\varphi)(\alpha + \beta)
+(\partial^2\varphi^\dagger - m^2\varphi^\dagger)(\alpha - \beta) = 0 \,\\
$$
We can re-order it by $\alpha$ and $\beta$ and remove them from the equation since they are arbitrary:
$$
(\partial^2\varphi - m^2\varphi) + (\partial^2\varphi^\dagger - m^2\varphi^\dagger) = 0\,\\
(\partial^2\varphi - m^2\varphi) - (\partial^2\varphi^\dagger - m^2\varphi^\dagger) = 0\,\\
$$
Therefore, it is clear that $$\partial^2\varphi - m^2\varphi = 0$$ and $$\partial^2\varphi^\dagger - m^2\varphi^\dagger = 0\,.$$

---

> b) Treat $\varphi$ and $\varphi^\dagger$ as independent fields, and find the conjugate momentum for each. Complute the hamiltonian density in terms of thease conjugate momenta and the fields themselves (but not their time derivatives).

Conjugate momentum of $\varphi$ is
$$\begin{align*}
\Pi(x) &= \frac{\partial\mathcal L}{\partial \dot\varphi(x)}\\
&= \dot\varphi^\dagger(x)\,,
\end{align*}$$
similarly, $\Pi^\dagger(x) = \dot\varphi(x)$.

The hamiltonian is:
$$\begin{align*}
\mathcal H &= \sum \Pi(x)\dot\varphi(x) - \mathcal L \\
    &= \dot\varphi^\dagger\dot\varphi + \dot\varphi\dot\varphi^\dagger
        +\partial^\mu\varphi^\dagger\partial_\mu\varphi + m^2\varphi^\dagger\varphi - \Omega_0 \\
    &= \dot\varphi\dot\varphi^\dagger + \nabla \varphi^\dagger \nabla \varphi + m^2\varphi^\dagger\varphi - \Omega_0 \\
    &= \Pi^\dagger\Pi + \nabla \varphi^\dagger \nabla \varphi + m^2\varphi^\dagger\varphi - \Omega_0 \\
\end{align*}$$

---

> c) Write the mode expansion of $\varphi$ as
$$
\varphi(x) = \int \widetilde{dk}\left[a(\mathbf k)e^{ikx} + b^\dagger(\mathbf k)e^{-ikx}\right]\,.
$$

> Express $a(\mathbf k)$ and $b(\mathbf k)$ in terms of $\varphi$ and $\varphi^\dagger$ and their time derivative.

The point is this is quite similar to the real scalar field. Let's consider the **on shell** Fourier transformation of the field at time $t$.
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
\newcommand{tv}[0]{\widetilde\varphi}
\newcommand{tdv}[0]{\widetilde{\dot\varphi}}
\widetilde\varphi(\k', t) &= \int dx^3\, e^{-ik'x}\varphi(x) \\
&= \int \frac{d\x^3 d^3\k}{(2\pi)^3\omega}\,e^{-ik'x}\left[a(\mathbf k)e^{ikx} + b^\dagger(\mathbf k)e^{-ikx}\right]\\
&= \int \frac{d\x^3 d^3\k}{(2\pi)^32\omega}\,e^{-i(\k'-\k)\x + i(\omega'-\omega)t}\left[a(\mathbf k) + b^\dagger(-\mathbf k)e^{2i\omega t}\right]\\
&= \int \frac{d^3\k}{2\omega}\,\delta^3(\k'-\k)e^{i(\omega'-\omega)t}\left[a(\mathbf k) + b^\dagger(-\mathbf k)e^{2i\omega t}\right]\\
&= \frac{1}{2\omega}\left[a(\mathbf k') + b^\dagger(-\mathbf k')e^{2i\omega t}\right]\\
\\
\tdv(\k',t) &= \int d\x^3\, e^{-ik'x}\varphi(x) \\
&= \frac{i}{2}\left[-a(\mathbf k') + b^\dagger(-\mathbf k')e^{2i\omega t}\right] \\
\end{align*}$$
$$
a(\k) = \omega\widetilde\varphi(\k, t)+i \widetilde{\dot\varphi}(\k, t)\\
$$
It is time independent. Then the hermitian conjugate of $\varphi(x)$
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\varphi^\dagger(x) &= \int \widetilde{dk}\left[a^\dagger(\mathbf k)e^{-ikx} + b(\mathbf k)e^{ikx}\right] \\
&= \int \widetilde{dk}\left[b(\mathbf k)e^{ikx} + a^\dagger(\mathbf k)e^{-ikx}\right]\,,\\
\end{align*}$$
which means $a$ and $b$ are swapped when $\varphi \to \varphi^\dagger$. We got:
$$
b(\k) = \omega\widetilde\varphi^\dagger+i \widetilde{\dot\varphi}^\dagger\,.\\
$$

---

> d) Assuming canonical commutation relations for the fields and their conjugate momenta, find the commutation relations obeyed by $a(\mathbf k)$ and $b(\mathbf k)$ and their hermitian conjugates.

Obviously, $a$ and $b$ commutes with themselves in the same way as in the case of real scalar field. This leaves us to the next 2 options:
$$
\newcommand{k}[0]{\mathbf k}
[a(\k),b(\k')] \\
[a^\dagger(\k),b(\k')]\,. \\
$$
And
$$
\newcommand{k}[0]{\mathbf k}
[a(\k),b^\dagger(\k')] = -[a^\dagger(\k), b(\k')]^\dagger \\
[a^\dagger(\k),b^\dagger(\k')] = -[a(\k), b(\k')]^\dagger \,.\\
$$

Now,
$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
\newcommand{tv}[0]{\widetilde\varphi}
\newcommand{tdv}[0]{\widetilde{\dot\varphi}}
[a(\k),b(\k')]
&=[\omega\tv+i\tdv,\omega{\tv^\dagger}'+i{\tdv^\dagger}'] \,.\\
&=i\omega(
    [\tv,{\tv^\dagger}'] +
    [\tdv,{\tv^\dagger}'] +
    [\tv,{\tdv^\dagger}'] +
    [\tdv,{\tdv^\dagger}']) \,.\\
\end{align*}$$

Due to causality, commutators are $0$ in space-like distances.

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
\newcommand{tv}[0]{\widetilde\varphi}
\newcommand{tdv}[0]{\widetilde{\dot\varphi}}
[\varphi(\x,t), \varphi^\dagger(\x',t)] &= \mathbf 1_{\x=\x'}([\varphi(\x,t), \varphi^\dagger(\x,t)]) = 0 \\
[\Pi(\x, t), \Pi^\dagger(\x', t)] &= 0 \\
\\
[\tv,{\tv^\dagger}'] &= \int d^3xd^3x'\, e^{-ikx+ik'x'}[\varphi(\x, t), \varphi^\dagger(\x', t)] \\
&= 0 \\
[\tdv,{\tdv^\dagger}'] &= \int d^3xd^3x'\, e^{-ikx+ik'x'}[\dot\varphi(\x, t), \dot\varphi^\dagger(\x', t)]\\
    &=  \int d^3xd^3x'\, e^{-ikx+ik'x'}[\Pi^\dagger(\x, t), \Pi(\x', t)] \\
    & = 0 \\
\\
[\tv,{\tdv^\dagger}'] &= \int d^3xd^3x'\, e^{-ikx+ik'x'}[\varphi(\x, t), \dot\varphi^\dagger(\x', t)] \\
&= \int d^3x d^3x'\, e^{-i(k-k')x+ik(x-x')}[\varphi(\x, t), \Pi(\x', t)] \\
&= \int d^3x d^3x'\, e^{-i(k-k')x+ik(x-x')}i\delta^3(\x-\x') \\
&= i\int d^3x \, e^{-i(k-k')x}\\
&= i\delta^3(\k-\k')\\
[\tdv,{\tv^\dagger}'] &= [\tv,{\tdv^\dagger}']^\dagger = -i\delta^3(\k-\k') \\
\\
[a(\k),b(\k')] &= 0 \\
[a(\k),b^\dagger(\k')] &= 0 \\
\end{align*}$$

---

> e) Express the hamiltonian in terms of $a(\mathbf k)$ and $b(\mathbf k)$ and their hermitian conjugates. What value must $\Omega_0$ have in order for the ground state to have zero energy?

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
\newcommand{tv}[0]{\widetilde\varphi}
\newcommand{tdv}[0]{\widetilde{\dot\varphi}}
\mathcal H &= \Pi^\dagger\Pi + \nabla\varphi^\dagger\nabla\varphi + m^2\varphi^\dagger\varphi - \Omega_0 \\
\\
\varphi(x) &= \int \widetilde{dk}\, (a(\k)e^{-ikx} + b^\dagger(\k)e^{ikx}) \\
    &= \int \widetilde{dk}\, (a(\k)e^{-ikx} + b^\dagger(-\k)e^{-ikx-2i\omega t}) \\
    &= \int \widetilde{dk}\, e^{-ikx}(a(\k) + b^\dagger(-\k)e^{-2i\omega t}) \\
\varphi^\dagger(x) &= \int \widetilde{dk}\, e^{ikx}(a^\dagger(\k) + b(-\k)e^{2i\omega t}) \\
\Pi(x) &= \dot\varphi^\dagger(x) \\
    &= -i\omega \int \widetilde{dk}\, e^{ikx}(a^\dagger(\k) - b(-\k)e^{2i\omega t}) \\
\Pi^\dagger(x)
    &= i\omega \int \widetilde{dk}\, e^{-ikx}(a(\k) - b^\dagger(-\k)e^{2i\omega t}) \\
\nabla\varphi(x) &= \int \widetilde{dk}\, \nabla e^{-ikx}(a(\k) + b^\dagger(-\k)e^{-2i\omega t}) \\
    &= -i\int \widetilde{dk}\, \k e^{-ikx}(a(\k) + b^\dagger(-\k)e^{-2i\omega t}) \\
\nabla\varphi^\dagger(x)
    &= i\int \widetilde{dk}\, \k e^{ikx}(a^\dagger(\k) + b(-\k)e^{2i\omega t}) \\
\\
\int \widetilde{dk}\widetilde{dk'}d^3x\, e^{i(k-k')x} f(x, k, k')
&= (2\pi)^3 \int \widetilde{dk}\widetilde{dk'} \delta^3(\k-\k')\, f(x, k, k')\\
&= \int \widetilde{dk}\, \frac{1}{2\omega} f(x, k, k)\\
\\
\int d^3x\, \varphi^\dagger(x)\varphi(x)
&= \int \widetilde{dk}\, \frac{1}{2\omega}
    \left(
        a^\dagger(\k)a(\k) + b(-\k)b^\dagger(-\k) + \\
        a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} + \\
        b(-\k)a(\k) e^{2i\omega t} +
    \right) \\
\\
\int d^3x\, \nabla\varphi^\dagger(x)\nabla\varphi(x)
&= \int \widetilde{dk}\, \frac{\k^2}{2\omega}
    \left(
        a^\dagger(\k)a(\k) + b(-\k)b^\dagger(-\k) + \\
        a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} + \\
        b(-\k)a(\k) e^{2i\omega t} +
    \right) \\
\\
\int d^3x\, \Pi^\dagger(x)\Pi(x)
&= \int \widetilde{dk}\, \frac{\omega^2}{2\omega}
    \left(
        a(\k)a^\dagger(\k) + b(-\k)b^\dagger(-\k) \\
        - a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} \\
        - b(-\k)a(\k) e^{2i\omega t} +
    \right) \\
&= \int \widetilde{dk}\, \frac{\omega^2}{2\omega}
    \left(
        a^\dagger(\k)a(\k) + b^\dagger(-\k)b(-\k) \\
        +[a, a^\dagger] + [b, b^\dagger] \\
        - a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} \\
        - b(-\k)a(\k) e^{2i\omega t} +
    \right) \\
&=  2\int \widetilde{dk}\, \frac{\omega^2}{2\omega}
    (2\pi)^3(2\omega)\delta^3(0)
    \\&\phantom{=}
    +\int \widetilde{dk}\, \frac{\omega^2}{2\omega}
    \left(
        a^\dagger(\k)a(\k) + b^\dagger(-\k)b(-\k) \\
        - a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} \\
        - b(-\k)a(\k) e^{2i\omega t} +
    \right) \\
&=  V_k\int d^3k\, \frac{\omega}{(2\pi)^3}
    + \int \widetilde{dk}\, \frac{\omega^2}{2\omega}
    \left(
        a^\dagger(\k)a(\k) + b^\dagger(-\k)b(-\k) \\
        - a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} \\
        - b(-\k)a(\k) e^{2i\omega t} +
    \right) \\
\end{align*}$$

$$\begin{align*}
\newcommand{k}[0]{\mathbf k}
\newcommand{x}[0]{\mathbf x}
\newcommand{tv}[0]{\widetilde\varphi}
\newcommand{tdv}[0]{\widetilde{\dot\varphi}}
H &= \int \widetilde{dk}\, \frac{m^2+\k^2+\omega^2}{2\omega}
    \left(a^\dagger(\k)a(\k) + b^\dagger(-\k)b(-\k)\right) \\&\phantom{=}
    +\int \widetilde{dk}\, \frac{m^2+\k^2-\omega^2}{2\omega}
    \left(a^\dagger(\k)b^\dagger(-\k) e^{-2i\omega t} +
        b(-\k)a(\k) e^{2i\omega t}
    \right) \\&\phantom{=}
    + V_k\int d^3k\,\frac{\omega}{(2\pi)^3} - \Omega_0V_k \\
&= \int \widetilde{dk}\, \omega \left(a^\dagger(\k)a(\k) + b^\dagger(-\k)b(-\k)\right)
    + V_k\int d^3k\,\frac{\omega}{(2\pi)^3} - \Omega_0V_k \\
\end{align*}$$
Within the ultraviolet cuttoff, we can set
$$
\Omega_0 = \int d^3k\,\frac{\omega}{(2\pi)^3}
$$
in order for the vacuum to have zero energy.