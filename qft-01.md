Quantum Field Theory 01 - Previous Attempts

[Quantum Field Theory (Mark
Srednicki)](http://web.physics.ucsb.edu/~mark/qft.html)

Schroedinger Equation:

$$
i\hbar\frac{\partial}{\partial t}\left|\psi,t\right\rangle = \hat H\left|\psi,t\right\rangle
$$

when the hamiltonian $\hat H$ is:

$$
\hat H = \frac{\hat p^2}{2m}
$$

It reflects a non-relativistic quantum mechanical theory. To combine
(special) relativity here, we need a relativistic hamiltonian.

### 1. Square root the energy

$$
H = +\sqrt{p^2c^2+m^2c^4}
$$

then the Schroedinger equation becomes:

$$
i\hbar\frac{\partial}{\partial t}\psi(x,t) = + \sqrt
{-\hbar^2c^2\nabla^2+m^2c^4}\psi(x, t)
$$

Unfortuneately, if we expand the square root, we get infinite powers of
$\nabla$, meaning the equation is not localize.

### 2. Square both side

$$
-\hbar^2\frac{\partial^2}{\partial t^2}\psi(x,t) =
\left(-\hbar^2c^2\nabla^2+m^2c^4\right)\psi(x,t)
$$

This is the Klein-Gordon equation. It is apparently consistent with
relativity. The problem is that Klein-Gordon equation cannot conserve
probability.

### 3. Square root with higher dimension

Reorder the Klein-Gordon equation:

$$
\left(\nabla^2-\frac{1}{c^2}\frac{\partial^2}{\partial
t^2}\right)\psi=-\frac{m^2c^2}{\hbar^2}\psi
$$

and try something that squares to it. For example:

$$
A\partial_x + B\partial_y + C\partial_z + \frac{i}{c}D\partial_t
$$

by setting

$$
\left \{A,B \right\}=0,... \\
A^2=B^2=...=1
$$

Therefore we need 4 solutions of things that squre to $1$.

If we set:

$$
\gamma^0=\frac{i}{c}D \\
\gamma^{1,2,3}=A,B,C
$$

Then squre root both sides:

$$
i\hbar\gamma^\mu\partial_\mu\,\psi(x,t)=mc\,\psi(x,t)
$$

This is the Dirac equation.


Fortuneately, we can put matrices in those positions. For
$n\times n$ matrices, the wave function has to have $n$ components.

The smallest such $n$ is $4$.

Unfortuneately, the energy eigen values of Dirac equation can be either
positive or negative, which implies partiles with negative energy.


### Root cause of the issues

In these equations, location $\hat x$ is considered an operator, whereas
time is just a label. We either lift time to be an operator, or treat
location to be just a label. Quantum Field Theory treats location to be
a label on a "field" of operators that applies the to a "vacuum state".


