An unnamed operator exponetiation identity

I found this when I tried to prove $T(a)^{-1}\varphi(x)T(a) = \varphi(x-a)$. This is sometimes
referred to as "[an important lemma](https://en.wikipedia.org/wiki/Baker%E2%80%93Campbell%E2%80%93Hausdorff_formula#An_important_lemma)",
or the "[standard operator identity](https://en.wikipedia.org/wiki/Heisenberg_picture#Derivation_of_Heisenberg.27s_equation)".
It goes like this:

If $\mathfrak{g}$ is a Lie group, define [adjoint action](https://en.wikipedia.org/wiki/Adjoint_representation_of_a_Lie_algebra):
$$
\mathrm{ad} : \mathfrak g \rightarrow \mathfrak g \rightarrow \mathfrak g \\
\mathrm{ad}(X)(Y) \mapsto [X, Y]
$$ where $[\cdot,\cdot]$ is the commutator $[X,Y] = XY - YX$.
It is normally written as $\mathrm{ad}_XY$. Then we have:
$$
e^XYe^{-X}=e^{\mathrm{ad}_X}Y
$$
It is proved in a rather interesting way:

Let $f : \mathfrak R \rightarrow \mathfrak g \rightarrow \mathfrak g, f(s)(Y) \mapsto  e^{sX}Y e^{-sX}$, then take the
derivative of $f$ with respect to $s$:
$$\begin{align*}
\frac{d}{ds}f(s)(Y) &= \frac{d}{ds}\left(e^{sX}Y e^{-sX}\right) \\
&= Xe^{sX}Ye^{-sX} - e^{sX}YXe^{-sX} \\
&= Xe^{sX}Ye^{-sX} - e^{sX}Ye^{-sX}X \\
&= \mathrm{ad}_X(e^{sX}Ye^{-sX}) \\
&= \mathrm{ad}_X(f(s)(Y))
\end{align*}$$
Therefore,
$$
f'(s) = \mathrm{ad}_Xf(s), \qquad f(0) = 1, \qquad \implies f(s) = e^{s\mathrm{ad}_X}
$$
set $s=1$ and we get:
$$
e^XYe^{-X}=e^{\mathrm{ad}_X}Y
$$
Explicitly, this means:
$$
e^XYe^{-X}=Y + [X, Y] + \frac{1}{2!}[X, [X, Y]] + \frac{1}{3!}[X, [X, [X, Y]]] ...
$$
