Quantum Field Theory 06 - Canonical Quantization of Scalar Fields

### Relativisitic Generalization of a non-relativistic scalar field
For a hamiltonian for free particles:
$$\begin{align*}
H&=\int d^3x\, a^\dagger(\mathbf x)(-\frac{1}{2m}\nabla^2)a(\mathbf x)\\
 &=\int d^3p\, \frac{1}{2m}\mathbf p^2 \tilde a^\dagger(\mathbf p) a(\mathbf p)\,,\\
\end{align*}$$
where
$$
\tilde a(\mathbf p) = \int \frac{d^3x}{(2\pi)^{3/2}} \exp (-i \mathbf p \mathbf x) a(\mathbf x)\,.
$$
We define the (abstract) creation and annihilation operators with these (anti-)commutation relations:
$$\begin{align*}
[\tilde a(\mathbf p), \tilde a(\mathbf p')]_\mp &= 0\,,\\
[\tilde a^\dagger(\mathbf p), \tilde a^\dagger(\mathbf p')]_\mp &= 0\,,\\
[\tilde a(\mathbf p), \tilde a^\dagger(\mathbf p')]_\mp &= \delta^3(\mathbf p - \mathbf p')\,,
\end{align*}$$
also, an annihilation operator action on $\vert0\rangle$ gives $0$:
$$
\tilde a(\mathbf p) \vert0\rangle = 0\,,
$$
so the energy eigenvalue is zero. The other eigenstates of $H$ are all of the form $\tilde a^\dagger(\mathbf p_1)...\tilde a^\dagger(\mathbf p_n)\vert0\rangle$, and the energy eigenvalue is $E(\mathbf p_1)+...+E(\mathbf p_n),$ where $E(\mathbf p)=\frac{1}{2m}\mathbf p^2$.

The relativisitic generalization of this theory is to use the relativistic energy formula $E(\mathbf p)=+\sqrt{\mathbf p^2+m^2}$:
$$
H=\int d^3p\, \sqrt{\mathbf p^2 + m^2} \tilde a^\dagger(\mathbf p) a(\mathbf p)
$$

### A case of classical Lorentz-invariant scalar field
#### Lagrangian
Rather than check if this is indeed Lorentz invariant, we can reconstruct this theory from a different point of view, that emphasizes Lorentz invariance from the beginning.

Starting from a _**classical**_ real scalar field $\varphi(x)$ that is Lorentz invariant. Note that $\varphi$ is not an operator. One possible theory is the Klein-Gordon equation, $$(-\partial^2+m^2)\varphi(x)=0\,.$$

The equation of motion can be derived from the least action principle where action $S=\int d^4x\, \mathcal L$, where $\mathcal L$ is the lagrangian density, or just lagrangian. $d^4x$ is manifestily Lorentz invariant. Thus for the action to be Lorentz invariant, the lagrangian density must be a Lorentz scalar. For example, we can define
$$\mathcal L = -\frac 12 \partial^\mu\varphi\partial_\mu\varphi -\frac 12 m^2\varphi^2+\Omega_0,$$ where $\Omega_0$ is an arbitrary constant. The equation of motion according to the [Euler-Lagrangian equation](https://en.wikipedia.org/wiki/Euler%E2%80%93Lagrange_equation) is
$$\begin{align*}
0&=\delta S\\
 &=\int\,d^4x\,\left[
     \left(-\frac 12 \partial^\mu(\varphi+\delta\varphi)\partial_\mu(\varphi+\delta\varphi) -\frac 12 m^2(\varphi+\delta\varphi)^2 + \Omega_0\right)
     -\\
     \left(-\frac 12 \partial^\mu\varphi\partial_\mu\varphi -\frac 12 m^2\varphi^2 + \Omega_0\right)
     \right]\\
 &=\int\,d^4x\,\left[
     -\frac 12 \partial^\mu\delta\varphi\partial_\mu\varphi
     -\frac 12 \partial^\mu\varphi\partial_\mu\delta\varphi
     - m^2\delta\varphi^2\right]\\
 &=\int\,d^4x\,[\partial^2\varphi-m^2\varphi]\delta\varphi.
\end{align*}$$
For $\delta\varphi$ being an arbitrary function, we again get $$\partial^2\varphi = m^2 \varphi.$$

One solution of the Klein-Gordon equation is a plane wave of the form $\exp(i\mathbf k\cdot\mathbf x\pm i\omega t)$, where $\mathbf k$ is an arbitrary real wave-vector, and $$\omega=\sqrt{\mathbf k^2+m^2}.$$
The general solution is then
$$
\varphi(x)=\int{\frac{d^3k}{f(k)}\left[
    a(\mathbf k) \exp(i\mathbf k\cdot\mathbf x + i\omega t)+
    b(\mathbf k) \exp(i\mathbf k\cdot\mathbf x - i\omega t)
    \right]}
$$
where $a$ and $b$ are arbitrary **complex** functions of the wave vector $\mathbf k$ and $f(k)$ is  a **real** function we inserted for later. For $\varphi$ being real, we have $\varphi^*=\varphi$, where
$$\begin{align*}
\varphi^*(x)&=\int{\frac{d^3k}{f(k)}\left[
    a^*(\mathbf k) \exp(-i\mathbf k\cdot\mathbf x - i\omega t)+
    b^*(\mathbf k) \exp(-i\mathbf k\cdot\mathbf x + i\omega t)
    \right]}\\
    &=\int{\frac{d^3k}{f(k)}\left[
    a^*(-\mathbf k) \exp(i\mathbf k\cdot\mathbf x - i\omega t)+
    b^*(-\mathbf k) \exp(i\mathbf k\cdot\mathbf x + i\omega t)
    \right]}.\\
\end{align*}$$
Comparing the two, $b^*(-\mathbf k) =a(\mathbf k)$. We can then rewrite $\varphi$ as
$$\begin{align*}
\varphi(x) &= \int\,\frac{d^3x}{f(k)}\,\left[
    a(\mathbf k) e^{ikx} + a^*(\mathbf k) e^{-ikx}
    \right],
\end{align*}$$
where $kx=k^\mu x_\mu$ is Lorentz-invariant porduct of the four-verctors.

> Note that a four-momentum $k^\mu$ that obeys $k^2=-m^2$ is called _on the mass shell_, or just _on shell_ for short.

Now, a clear intent is to make $a$ a scalar field, then in order to make $\varphi$ Lorentz-invariant, we need to choose $f$ so that $d^3 k/f(k)$ is Lorentz invariant. **This can be done because the mass of the particle is fixed**. Another analog is that we can transform an integration over time to an integration over proper time by multiply the measure with a boost factor.

We start with a manifestily Lorentz invariant 4-dimensional measure that can be integrated into a 3-dimensional measure. This can be done by multiply the measure with a Dirac delta with a Lorentz invariant parameter. On example is $d^4k\delta(k^2+m^2)\theta(k^0)$, where $\theta(x)$ is the unit step function to pick the positive energy:
$$\begin{align*}
\int \, d^4k \,\delta(k^2+m^2)\theta(k^0) &=
    \int\,d^3k d k_0 \, \delta(-k_0^2 + \mathbf k^2 +m^2)\theta(k^0) \\
    &= \int\,d^3k \frac{1}{(|-2k_0|)_{k^2+m^2=0}} \\
    &= \int\, \frac{d^3k}{2\omega} \\
\end{align*}$$
This means any $f(k) \propto \omega$ will make $d^3 k/f(k)$ Lorentz invariant. We now define the **Lorentz-invariant differential** measure to be (with normalization in mind):
$$
\widetilde{dk} \equiv \frac{d^3k}{(2\pi)^32\omega} = \frac{d^3k}{(2\pi)^32\sqrt{\mathbf k^2+m^2}}
$$
Thus the field will be:
$$\begin{align*}
\varphi(x) &= \int\,\widetilde{dk}\,\left[a(\mathbf k)e^{ikx}+a^*(\mathbf k)e^{-ikx}\right]\\
&=\int\,\widetilde{dk}\,e^{ikx}\left[a(\mathbf k)+e^{2i\omega t}a^*(-\mathbf k)\right]\\
\end{align*}$$
Take the partial derivative with respect to time:
$$
\partial_0\varphi(x) = \int\,\widetilde{dk}\,e^{ikx}\left[-i\omega a(\mathbf k)+i\omega e^{2i\omega t}a^*(-\mathbf k)\right]
$$
We can then retrieve $a$ from $\varphi$:
$$\begin{align*}
\int\,d^3x\, e^{-ikx}\varphi(x) &＝
\int\,d^3xd^3k'\,\frac{e^{ik'x}}{(2\pi)^32\omega'}\left[a(\mathbf k')+e^{2i\omega t}a^*(-\mathbf k')\right] \\
&= \frac{1}{2\omega} a(\mathbf k) + e^{2i\omega t} a^*(-\mathbf k)\\
\int\,d^3x\, e^{-ikx}\partial_0\varphi(x)
&＝ -\frac{i}{2}a(\mathbf k)+\frac{i}{2}e^{2i\omega t} a^*(-\mathbf k)\\
a(\mathbf k) &= \int\,d^3x\, e^{-ikx}[\omega\varphi(x) + i\partial_0\varphi(x)]\\
&=i\int\,d^3x\,[e^{-ikx}, \varphi(x)]_{\partial_0},
\end{align*}$$

where $[f, g]_{\partial_0} \equiv f(\partial_0g) - (\partial_0f)g$. Note that $a(\mathbf k)$ is time independent.

#### Derive hamiltonian
The momentum field of a lagrangian $\mathcal L(\varphi, \dot\varphi)$ is:
$$\begin{align*}
\Pi(x)\equiv\frac{\partial\mathcal L}{\partial \dot\varphi}
\end{align*}$$
and the hamiltonian density is:
$$\begin{align*}
\mathcal H=\Pi(x)\dot\varphi-\mathcal L
\end{align*}$$

In our example,
$$\begin{align*}
\Pi(x) &= \dot\varphi(x)\\
\mathcal H&=\Pi(x)\dot\varphi(x)-\mathcal L \\
&= \dot\varphi(x)^2 -\mathcal L \\
&= \frac{1}{2} \dot\varphi^2 + \frac{1}{2}(\nabla\varphi)^2 + \frac{1}{2}m^2\varphi^2 - \Omega_0
\end{align*}$$

Replace $\varphi$ with $a$ and compute the total hamiltonian over a volume $V$:
$$
H = \int_V d^3x \mathcal H = -\Omega_0V+\frac{1}{2}\int \widetilde{dk}\,\omega
\left(a^*(\mathbf k)a(\mathbf k) + a(\mathbf k)a^*(\mathbf k)\right).
$$

Then let's blindly consider this is result for the quantum theory (at a certain time point $t$) as well. We can go from calssical to quantum mechanics via _canonical quantization_ by lifting $\varphi(x)$ and $\Pi(x)$ into quantum fields. In our case, we introduce some extra commutation relations between $\varphi(x)$ and $\Pi(x)$:
$$\begin{align*}
[\varphi(\mathbf x,t), \varphi(\mathbf x',t)] &= 0,\\
[\Pi(\mathbf x,t), \Pi(\mathbf x',t)] &= 0,\\
[\varphi(\mathbf x,t), \Pi(\mathbf x',t)] &= i\delta^3(\mathbf x - \mathbf x').\\
\end{align*}$$
These relations are called **canonical commutation relations**. And the commutation relations of  field $a$ (now a quantum field):
$$\begin{align*}
[a(\mathbf k), a(\mathbf k')] &= 0\,,\\
[a^\dagger(\mathbf k), a^\dagger(\mathbf k')] &= 0\,,\\
[a(\mathbf k), a^\dagger(\mathbf k')] &= (2\pi)^32\omega\delta^3(\mathbf k - \mathbf k')\,,
\end{align*}$$

**This indicates that we can only have a theory for bosons from the Kleine-Gordon equation.**

Now we rewrite the hamiltonian as:
$$\begin{align*}
H&= -\Omega_0V+\frac{1}{2}\int \widetilde{dk}\,\omega
\left(2a^\dagger(\mathbf k)a(\mathbf k) + [a(\mathbf k),a^\dagger(\mathbf k)]\right)\\
&=-\Omega_0V+\int \widetilde{dk}\,\omega
\left(a^\dagger(\mathbf k)a(\mathbf k) + (2\pi)^3\omega\delta^3(0)\right)\\
&=
\int_{V_E} \widetilde{dk}\,\omega\,a^\dagger(\mathbf k) a(\mathbf k) + (\mathcal E_0-\Omega_0)V,
\end{align*}$$
where
$$
\mathcal E_0=\frac{1}{2}\int_{V_E} d^3k\omega.
$$
where $V_E$ is the "volume" to integrate momentum over. When $V_E$ is infinite, the $\mathcal E_0$ will be infinite as well, and we get a infinite amount of energy for is the total zero-point energy on the vacuum state. If we constraint the possible momentum to be less than $\Lambda$,called the "**ultraviolet cutoff**", we can constraint the total zero-point energy into a finite value. The we can set $\Omega_0$ in a way if we apply hamiltonian to the vacuum state, we get $0$. Then the hamiltonian becomes simply $$H=\int_{V_E} \widetilde{dk}\,\omega\,a^\dagger(\mathbf k) a(\mathbf k).$$
We can then define $a(\mathbf k) =  \sqrt{(2\pi)^32\omega}\widetilde a(\mathbf k)$, and $$H=\int\,d^3k\,\omega \widetilde a^\dagger(\mathbf k) \widetilde a(\mathbf k).$$
This is exactly what we expected from the beginning of the section!