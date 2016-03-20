On minimal uncertainty wavepacket

A minimal uncertainty wavepacket is the a solution of the Schrödinger equation 
where the production of variance of position and momentum takes exactly the minimum value 
$\hbar^2/4$.

Variance of an observable $o$ is defined as below:
$$\begin{align*}
\mathrm{Var}(o) &= \langle \big(o - \langle o \rangle\big)^2 \rangle \\
 &= \langle o - \langle o \rangle \vert o - \langle o \rangle \rangle
\end{align*}$$

where the $\langle o\rangle$ term is just a number.
Let $\bar x = x - \langle\bar x \rangle$ and $\bar p = p - \langle\bar p \rangle$.
Therefore the variance of position becomes:  
$$\begin{align*}
\mathrm{Var}(x) &= \langle \bar x^2\rangle \\
\mathrm{Var}(p) &= \langle \bar p^2\rangle \\
\end{align*}$$
$$\begin{align*}
[\bar x,\bar p] &= \bar x\bar p - \bar p\bar x \\
    &= (x - \langle\bar x\rangle)(p - \langle\bar p\rangle)
      -(p - \langle\bar p\rangle)(x - \langle\bar x\rangle) \\
    &= [x,p] \\
    &= i\hbar \\ 
\end{align*}$$

Let $Q=\bar x-\lambda \bar p$ where $\lambda$ is a complex number. Naturally
$\langle Q \vert Q \rangle \geq 0$, whereas:
$$\begin{align*}
\langle Q \vert Q \rangle &= \langle \bar x - \lambda \bar p \vert \bar x - \lambda \bar p \rangle \\
    &= \langle \bar x\vert \bar x\rangle
     + \vert \lambda\vert ^2\langle \bar p\vert \bar p \rangle 
     -\lambda \langle \bar x\vert \bar p\rangle
     -\lambda^* \langle \bar p\vert \bar x\rangle\\
&\text{set } \lambda = 
    \frac{\langle \bar p \vert \bar x\rangle}{\langle \bar p \vert \bar p \rangle} 
    \text{ so } \langle \bar p\vert Q\rangle = 0:\\
\langle Q \vert  Q \rangle &= \langle \bar x\vert \bar x\rangle
    + \frac{\left| \langle \bar x\vert \bar p\rangle\right| ^2}{\langle \bar p\vert \bar p\rangle}
    - \frac{\langle \bar p\vert \bar x\rangle}{\langle \bar p\vert \bar p\rangle} \langle \bar x\vert \bar p\rangle
    - \frac{\langle \bar x\vert \bar p\rangle}{\langle \bar p\vert \bar p\rangle} \langle \bar p\vert \bar x\rangle \\
    &= \langle \bar x\vert \bar x\rangle - \frac{\vert \langle \bar x\vert \bar p\rangle\vert ^2}{\langle \bar p\vert \bar p\rangle} \\
\end{align*}$$
Reorder and $\langle Q|Q\rangle \geq 0$:
$$\begin{align*}
\langle \bar x\vert\bar x\rangle &\geq \frac{\left| \langle\bar x\vert\bar p\rangle \right | ^2}{\langle\bar p\vert\bar p\rangle} \\
\langle \bar x\vert\bar x\rangle \langle\bar p\vert\bar p\rangle & \geq \left| \langle\bar x\vert\bar p\rangle\right| ^2
\end{align*}$$
$$\begin{align*}
\left| \langle\bar x\vert\bar p\rangle\right| ^2 &= \langle\bar x\vert\bar p\rangle\langle\bar p\vert\bar x\rangle \\
    &= \left(\frac{\langle\bar x\vert\bar p\rangle + \langle\bar p\vert\bar x\rangle}{2}\right)^2 
    - \left(\frac{\langle\bar x\vert\bar p\rangle - \langle\bar p\vert\bar x\rangle}{2}\right)^2 \\
    &\geq -\left(\frac{\langle\bar x\bar p -\bar p\bar x\rangle}{2}\right)^2 \\
    &= \frac{\hbar^2}{4}
\end{align*}$$

The condition for the production to reach the minimum is $\vert Q \rangle$ is $0$,
and $\langle \left\{x,\bar p\right\} \rangle = 0$. For $\langle \left\{\bar x,\bar p\right\} \rangle = 0$,
we get that $\lambda$ is purely imaginary. Let $\lambda = -i\sigma^2/\hbar$.
If $Q=0$:
$$\begin{align*}
\bar x\varphi &= \lambda\bar p \varphi \\
(x - x_0)\varphi &= (-i\hbar \lambda \nabla - \lambda p_0)\varphi \\ 
    \text{ where } x_0 = \langle x \rangle &\text{ and } p_0 = \langle p \rangle\\
(x - x_0 + \lambda p_0)\varphi &= -i\hbar \lambda \nabla\varphi \\
\frac{i}{\hbar}\left(\frac{x - x_0}{-i\sigma^2/\hbar} + p_0\right)\varphi &= \nabla\varphi \\
\left(-\frac{x - x_0}{\sigma^2} + \frac{ip_0}{\hbar}\right)\varphi &= \nabla\varphi \\
\varphi &= A\,\mathrm{exp}\left(-\frac{(x-x_0)^2}{2\sigma^2}\right)\mathrm{exp}\left(-i\frac{p_0x}{\hbar}\right) \\
\langle A^2 \rangle &= \sigma \sqrt{\pi} \\
\varphi &= \frac{1}{\sqrt{\sigma\sqrt{\pi}}}\,\mathrm{exp}\left(-\frac{(x-x_0)^2}{2\sigma^2}\right)\mathrm{exp}\left(-i\frac{p_0x}{\hbar}\right) \\
\end{align*}$$
Also:
$$\begin{align*}
\left\vert\langle\bar x\vert\bar p\rangle\right\vert^2 &= 
    \langle\bar x\vert\bar x\rangle\langle\bar p\vert\bar p\rangle\\
    &= \frac{1}{\left\vert\lambda\right\vert^2}\langle\bar x\vert\bar x\rangle^2\\
    &= \left\vert\lambda\right\vert^2\langle\bar p\vert\bar p\rangle^2\\
    &= \frac{\hbar^2}{4} \\
\langle\bar x\vert\bar x\rangle &= \frac{\vert\lambda\vert \hbar}{2} = \frac{\sigma^2}{2}  \\
\langle\bar p\vert\bar p\rangle &= \frac{\hbar}{2\vert\lambda\vert} = \frac{\hbar^2}{2\sigma^2}  \\
\end{align*}$$

Serveral notes on this:

1. This gives rise to the position-momentum uncertainty principle, but can be generalized
to other forms of uncertainty principles.
2. When the minimal uncertainty is reached, $\vert x \rangle$ is proportional to
$\vert p \rangle$.