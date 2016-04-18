Quantum Field Theory 08 - Some inspirations from David Tong's material

Link: [http://www.damtp.cam.ac.uk/user/tong/qft.html](http://www.damtp.cam.ac.uk/user/tong/qft.html).

### Causality

Causal theory requres that (anti)-commutators over the fields across the light cone must be zero. Let check if that's true.

Define $\Delta(x) \equiv [\varphi(x), \varphi(0)]$.

We require
$$
\forall\,x. x^2 > 0 \implies \Delta(x) =0\,.
$$

Note that the commutator is trivially a Lorentz scalar in our theory (it will be covariant in non-scalar theories):
$$\begin{align*}
U(\Lambda)^{-1}\Delta(x)U(\Lambda) = \Delta(\Lambda^{-1}x)\\
\end{align*}$$


For all $x$, if it is spacelike we can find a $\Lambda$ that $\Lambda^{-1}x = (0, \mathbf x')$ and we know $U(\Lambda)^{-1}\Delta(x)U(\Lambda) = 0$; for all timelike separation, we can find a $\Lambda$ that $\Lambda^{-1}x = (t, \mathbf 0)$ and the $U(\Lambda)^{-1}\Delta(x)U(\Lambda) = i\delta^3(\mathbf 0)$. Our theory is indeed causal.

### Propagators

We could then ask this question: given a partical found in spacetime point $x'$, what is the amplitute to find it at point $x$? We can calculate this:

$$\begin{align*}
\langle 0 \vert \varphi(x) \varphi(x') \vert 0 \rangle
&=
\left\langle 0 \,\middle\vert\int \widetilde{dk}\widetilde{dk'}\,
(a(\k)e^{ikx} + a^\dagger(\k)e^{-ikx})
(a(\k')e^{ik'x'} + a^\dagger(\k')e^{-ik'x'})
 \,\middle\vert 0 \right\rangle \\
 &=
\left\langle 0 \,\middle\vert\int \widetilde{dk}\widetilde{dk'}\,
a(\k)a^\dagger(\k')e^{ikx - ik'x'}
 \,\middle\vert 0 \right\rangle \\
&= \left\langle 0 \,\middle\vert\int \widetilde{dk}\,e^{ik(x - x')}
 \,\middle\vert 0 \right\rangle \\
&= \int \widetilde{dk}\,e^{ik(x - x')} \\
&= \int d^3\k\,\frac{e^{ik(x - x')}}{(2\pi)^32\omega} \\
&\equiv D(x - x')\\
\end{align*}$$

This is called the **propagator**. It is also a Lorentz scalar in our theory. We can then discuss its value by making $x-x'$ purely space-like or time-like.

For time-like separation, $x - x' = (t,0,0,0)$,
$$\begin{align*}
D(x-x') &= \int d^3\k\,\frac{e^{-i\omega t}}{(2\pi)^32\omega} \\
\end{align*}$$
where $\omega = \sqrt{\k^2+m^2}$. The integrand is spherical symmetric. We can use spherical coordinate:
$$\begin{align*}
D(x-x') &= 4\pi \int_0^\infty d|k| \,\frac{\k^2 e^{-i\omega t}}{(2\pi)^32\omega} \\
&= 4\pi \int_0^\infty d\sqrt{\omega^2-m^2} \,\frac{|k|^2 e^{-i\omega t}}{(2\pi)^32\omega} \\
&= 4\pi \int_0^\infty d\sqrt{\omega^2-m^2} \,\frac{|k|^2 e^{-i\omega t}}{(2\pi)^32\omega} \\
d\sqrt{\omega^2-m^2} &= d\omega\frac{\omega}{\sqrt{\omega^2-m^2}} = d\omega\frac{\omega}{|k|}\\
D(x-x') &= 2\pi \int_m^\infty d\omega  \,\frac{\omega|k|^2 e^{-i\omega t}}{|k|(2\pi)^32\omega} \\
&= 2\pi \int_m^\infty d\omega  \,\frac{|k|e^{-i\omega t}}{(2\pi)^3} \\
&= \frac{1}{(2\pi)^2} \int_m^\infty d\omega  \, \sqrt{\omega^2-m^2} e^{-i\omega t} \\
&= \frac{1}{(2\pi)^2} \int_0^\infty d\omega'  \, \sqrt{\omega'^2-2m\omega'} e^{-i\omega t + imt} \\
&= e^{imt}\frac{1}{(2\pi)^2} \int_0^\infty d\omega'  \, \sqrt{\omega'^2-2m\omega'} e^{-i\omega' t} \\
\end{align*}$$

When $t \to \infty$, $m$ can be ignored in the integrand:
$$\begin{align*}
D(x-x') &\approx e^{imt}\frac{1}{(2\pi)^2} \int_0^\infty d\omega'  \, \omega' e^{-i\omega' t} \\
&= -\frac{e^{imt}}{t^2}
\end{align*}$$

For spacelike separation, $x - x' = (0, r, 0, 0)$,
$$\begin{align*}
D(x-x') &=  \int d^3\k\,\frac{e^{i k_1 r}}{(2\pi)^32\sqrt{\mathbf k^2 + m^2}} \\
\end{align*}$$
This is cylindrical symmetric. We can rewrite this in polar coordinate. Defin $l = \sqrt{k_2^2+k_3^2}$.
$$\begin{align*}
D(x-x') &= \frac{1}{2(2\pi)^2} \int dk_1 dl \, \frac{l e^{ik_1r}}{
\sqrt{k_1^2+l^2+m^2}} \\
&=\frac{1}{4(2\pi)^2} \int_0^\infty dl^2 \, \int dk_1\,\frac{e^{ik_1r}}{
\sqrt{k_1^2+l^2+m^2}} \\
&=\frac{1}{2(2\pi)^2} \int_0^\infty dl^2 \, K_0\left(\sqrt{l^2+m^2}r\right)\\
&= \frac{m}{(2\pi)^2r}K_1(mr)
\end{align*}$$
> Thanks to Mathematica!!

This is non-zero everywhere. It appears that the quantum field is leaking out of the lightcore. But since we've shown that $\Delta(x)$ is zero there, no measurement can propagate out of the lightcone.