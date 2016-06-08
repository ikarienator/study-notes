Perfect Fluid in Special Relativity

I was watching a OCW from UC Irvine on GR. It starts with some discussions about special relativistic. [This one](https://www.youtube.com/watch?v=QEr04Q0DWPk&index=5&list=PLqOZ6FD_RQ7ln1ZQPEU9aZQsEj0eyGlT6) about perfect fluid caught me because is not obvious how the Euler equation is derived. So I did it here.

It is an interesting topic in astrophysics since most of the objects we study can be considered (general) relativistic perfect fluid. As a first step, perfect fluid in special relativity is studied.

Starting by write down the stress-energy tensor $T^{\alpha\beta}$ at a point $x_0$. First create the reference frame at that point, and the tensor looks like

$$\begin{align*}
T^{00} &= \rho \\
T^{i0} &= 0 \\
T^{ij} &= p \delta^{ij}\quad. \\
\end{align*}$$

Then generalize it using Lorentz transformation:

$$\begin{align*}
T^{\alpha'\beta'}&=\Lambda^{\alpha'}{}_\alpha\Lambda^{\beta'}{}_\beta T^{\alpha\beta} \\
\end{align*}$$
where consider only the boost
$$\begin{align*}
\Lambda^{0}{}_0 &= \gamma \\
\Lambda^{0}{}_j &= \gamma v_j \\
\Lambda^{i}{}_0 &= \gamma v_i \\
\Lambda^{i}{}_j &= \delta^{i}{}_j + (\gamma-1)v_i v_j / v^2 \\
\end{align*}$$
where $\gamma \equiv 1/\sqrt{1-v^2}$ is the Lorentz factor, then the tensor $T^{\alpha\beta}$ is
$$\begin{align*}

\newcommand{\Lij}[2]{\Lambda^{#1}{}_{#2}}
\newcommand{\Lzz}[0]{Lij 00}
\newcommand{\Lzj}[1]{Lij 0{#1}}
\newcommand{\Liz}[1]{Lij {#1}0}

\newcommand{\LUDzz}[0]{\gamma}
\newcommand{\LUDzj}[1]{\gamma v_{#1}}
\newcommand{\LUDiz}[1]{\gamma v_{#1}}
\newcommand{\LUDij}[2]{\delta^{#1}{}_{#2}+(\gamma-1) v_{#1}v_{#2}/ v^2}

T^{0'0'} &=
  {\Lij 00}{\Lij 00}T^{00}+
  {\Lij 00}{\Lij 0j}T^{0j}+
  {\Lij 0i}{\Lij 00}T^{i0}+
  {\Lij 0i}{\Lij 0j}T^{ij} \\
&=
  \gamma^2 \rho +
  \gamma^2 v^2 p \\
T^{0'b'} &= \Lambda^0{}_0\Lambda^{b'}{}_\beta T^{0\beta} + \Lambda^0{}_i\Lambda^{b'}{}_\beta T^{i\beta} \\
    &= \gamma\Lambda^{b'}{}_\beta T^{0\beta} + \Lambda^0{}_i \Lambda^{b'}{}_\beta p\delta^{i\beta} \\
    &= \gamma\Lambda^{b'}{}_0 T^{00} + p \Lambda^0{}_i \Lambda^{b'}{}_i \\
    &= \rho\gamma^2v_{b'} + p (\LUDzj{i})(\LUDij{b'}{i}) \\
    &= \rho\gamma^2v_{b'} + p (\gamma v_{b'} + \gamma (\gamma -1 )v_{b'}) \\
    &= \rho\gamma^2v_{b'} + p \gamma^2 v_{b'} \\
    &= (\rho + p)\gamma^2v_{b'} \\
T^{a'b'} &=
  {\Lij {a'}0}{\Lij {b'}0}T^{00}+
  {\Lij {a'}0}{\Lij {b'}j}T^{0j}+
  {\Lij {a'}i}{\Lij {b'}0}T^{i0}+
  {\Lij {a'}i}{\Lij {b'}j}T^{ij}
  \\
&=
  \rho{\Lij {a'}0}{\Lij {b'}0}+
  p{\Lij {a'}i}{\Lij {b'}j}\delta^{ij}
  \\
&=
  \rho\gamma^2v_{a'}v_{b'}+
  (\LUDij {a'}i)(\LUDij {b'}i)p
  \\
&=
  \rho\gamma^2v_{a'}v_{b'}+
  p(\delta^{a'b'}+2(\gamma-1)v_{a'}v_{b'}/v^2 + (\gamma-1)^2v_{a'}v_{b'}/v^2)
  \\
&=
  \rho\gamma^2v_{a'}v_{b'}+
  p(\delta^{a'b'}+(\gamma^2-1)v_{a'}v_{b'}/v^2)
  \\
&=
  \rho\gamma^2v_{a'}v_{b'}+
  p(\delta^{a'b'}+\gamma^2v_{a'}v_{b'})
  \quad\quad \text{ since } (\gamma^2 -1) / v^2 = \gamma^2
  \\
&=
  \rho\gamma^2v_{a'}v_{b'}+
  p\delta^{a'b'} \quad.\\
\end{align*}$$

Combine the equations:
$$
T^{\alpha\beta} = p \eta ^{\alpha\beta} + (\rho + p)u^\alpha u^\beta\quad.
$$

To get the equation of motion, we can use the energy-momemtum conservation law:
$$\begin{align*}
\partial_\alpha T^{\alpha\beta}
&=
\partial_\alpha p \eta ^{\alpha\beta} + \partial_\alpha (\rho + p)u^\alpha u^\beta \\
&=\left. (-\dot p, \nabla \mathbf p)^\beta
+ (\dot\rho + \dot p, \nabla \rho + \nabla p)_\alpha u^\alpha u^\beta
+ (\rho + p) \partial_\alpha(u^\alpha u^\beta) \right. \\
&= 0 \quad.
\end{align*}$$
For $\beta=0$,
$$\begin{align*}
\partial_\alpha T^{\alpha0} &=
-\dot p + \gamma^2(\dot\rho + \dot p + (\mathbf v \cdot \nabla) (\rho + p))
+ \gamma^2(\rho + p) \nabla \cdot \mathbf v \\
&=(\gamma^2-1)\dot p + \gamma^2(\dot\rho + (\mathbf v \cdot \nabla) (\rho + p)) + \gamma^2(\rho + p) \nabla \cdot \mathbf v \\
&= 0 \\
v^2\dot p + \dot\rho
&= -(\mathbf v \cdot \nabla) (\rho + p) + (\rho + p) \nabla \cdot \mathbf v \\
&= -\nabla \cdot ((\rho + p)\mathbf v)
\end{align*}$$
For $\beta > 0$,
$$\begin{align*}
\nabla p +
\gamma^2 (\dot\rho + \dot p + (\mathbf v \cdot \nabla) (\rho + p)) \mathbf v
+ (\rho + p) \partial_\alpha(u^\alpha u^\beta) = 0
\end{align*}$$
Define $$\begin{align*}
\partial_\sigma{}(u^\alpha u^\beta) &\equiv \partial_\sigma(u^\alpha u^\beta) \\
\partial_\sigma{}(u^0u^0) &= 0 \\
\partial_\sigma{}(u^iu^0) &= \gamma^2 \partial_\sigma(v^i)\\
\partial_\sigma{}(u^0u^j) &= \gamma^2 \partial_\sigma(v^j)\\
\partial_\sigma{}(u^iu^j) &= \partial_\sigma(\gamma^2 v^iv^j)\\
&= \gamma^2 \partial_\sigma( v^iv^j)
\quad.
\end{align*}$$

$$\begin{align*}
\partial_\alpha(u^\alpha \mathbf v)
&= \gamma^2 \dot {\mathbf v} + \gamma^2 (\nabla \cdot \mathbf v) \mathbf v + \gamma^2 (\mathbf v \cdot \nabla) \mathbf v
\end{align*}$$

---

$$\begin{align*}
(\rho + p) (\gamma^2 \dot {\mathbf v} + \gamma^2 (\nabla \cdot \mathbf v) \mathbf v + \gamma^2 (\mathbf v \cdot \nabla) \mathbf v) &= -\nabla p - \gamma^2 (\dot\rho + \dot p + (\mathbf v \cdot \nabla) (\rho + p) \mathbf v \\
\end{align*}$$

$$\begin{align*}
\dot {\mathbf v}  + (\mathbf v \cdot \nabla) \mathbf v
&= -\frac{1}{\rho+p}\left(\nabla p/\gamma^2  + (\dot\rho + \dot p + \nabla \cdot ((\rho + p)\mathbf v)\right) \mathbf v)\\
&= -\frac{1}{\rho+p}\left(\nabla p/\gamma^2  + (\dot\rho + \dot p - v^2\dot p - \dot\rho\right) \mathbf v)\\
&= -\frac{1}{\rho+p}\left(\nabla p/\gamma^2 + (\dot p - v^2\dot p\right) \mathbf v)\\
&= -\frac{1-v^2}{\rho+p}\left(\nabla p + \dot p \mathbf v \right) \\
\end{align*}$$

This is called _relativistic Euler Equaltion for Fluid Dynamics_.