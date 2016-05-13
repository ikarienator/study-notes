Quantum Field Theory 09 - Path Integrals in (classical) Quantum Mechanics - 01

Starting from non-relativistic quantum mechanics of one particle in one dimension; the hamiltonian where the hamiltonian is
$$
\hat H \equiv H(\hat P, \hat Q)=\frac{1}{2m}\hat P^2+V(\hat Q)\,,
$$
where $H$ is a binary function(al), and $\hat P$ and $\hat Q$ are operators with CCR: $[\hat Q, \hat P] = i$, we can evaluate the amplitude for the particle to start from $q'$ at $t'$ and end at $q''$ at $t''$. Then amplitude is $\langle q''\vert e^{-i\hat H(t''-t)}\vert q'\rangle$.

In Heisenberg picture, **if the hamiltonian $\hat H$ does not change over time** the other operators are time dependent and we can write $\hat Q(t) = e^{i\hat Ht}\hat Q(0) e^{-i\hat Ht}$ and $\hat Q(0) = \hat Q$ is the postion operator in Schrödingers picture.

For each $\hat Q(t)$, we can build a **instantaneous eigenstate** $\vert q, t\rangle$ that $\hat Q(t)\vert q, t\rangle = q \vert q, t\rangle$, then $\vert q,t\rangle = e^{i\hat Ht}\vert q\rangle$ where $\hat Q\vert q \rangle = q \vert q \rangle$. The propbability amplitude is $\langle q'',t''\vert q',t'\rangle$.

To calculate this, we can split the time in $N+1$ equal pieces, where $\delta t = T/(N+1)$ and then introduces $N$ position eigenstates $q_i,\,i=1,2,...,N$, also $q_0=q'', q_N=q'$:
$$
\langle q'',t''\vert q',t'\rangle = \int \displaystyle \prod_{k=1}^N dq_k\, \displaystyle \prod_{j=0}^{N} \langle q_{j+1}\vert e^{-i\hat H\delta t}\vert q_j\rangle
$$

### Weyl ordering
* Link: [StackExchange](http://physics.stackexchange.com/questions/57299/weyl-ordering-rule).
* Link: [Wigner–Weyl transform](https://en.wikipedia.org/wiki/Wigner%E2%80%93Weyl_transform).
* Link: [Some notes on Weyl quantisation (Terrace Tao)](https://terrytao.wordpress.com/2012/10/07/some-notes-on-weyl-quantisation/).

Weyl ordering of the $(A^i B^j)_W$ of the monomial $A^iB^j$ is defined to be the average of all the $\binom{i+j}{i}$ ways to multiply $i$ copies of $A$ and $j$ copies of $B$ together:
$$
\newcommand\W[1]{{\left(#1\right)}_W}
\W{A^i B^j} := \frac{1}{\binom{i+j}{i}} \sum_{C_1,\ldots,C_{i+j}} C_1 \ldots C_{i+j}
$$
where $C_1,\ldots,C_{i+j}$ range over all tuples which contain $i$ copies of $A$ and $j$ copies of $B$. For instance, the Weyl calculus works perfectly with respect to powers $(sA+tB+u)^n$ of affine combinations $sA+tB+u$ of $A,B$, where $s,t,u \in {\bf C}$ are scalars:
$$
\W{(sA+tB+u)^n} = (sA+tB+u)^n \\
\W{\exp(sA+tB+u)} = \exp(sA+tB+u)\,.
$$

The last line is surprising but it means an affine map between P and Q in an exponential function is always Weyl ordered. We can then turn any classical hamiltonian into a quantum one obeying Weyl ordering:
$$
H(\hat P,\hat Q)\equiv \int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q) \, e^{ix\hat P+ik\hat Q}.
$$
This trick turns every (well-behaved) function of $p$ and $q$ into a Weyl ordered function of operators $\hat P$ and $\hat Q$.

Note that by [Baker–Campbell–Hausdorff formula](https://en.wikipedia.org/wiki/Baker%E2%80%93Campbell%E2%80%93Hausdorff_formula#The_Hadamard_lemma):

$$\begin{align*}
[\hat P, \hat Q] &= -i\\
\exp(ix\hat P + ik\hat Q) &= \exp(ix\hat P)\exp(ik\hat Q)\exp(ixk/2) \\
\langle q_2 \vert H(\hat P,\hat Q)^n\vert q_1 \rangle
&= \langle q_2 \vert\int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ix\hat P+ik\hat Q} \vert q_1 \rangle\\
&= \langle q_2 \vert\int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ixk/2} e^{ix\hat P}e^{ik\hat Q} \vert q_1 \rangle\\
&= \int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ixk/2} \int dp_1 \,\langle q_2 \vert e^{ix\hat P}\vert p_1 \rangle \langle p_1\vert e^{ik\hat Q} \vert q_1 \rangle\\
&= \int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ixk/2} \int dp_1 \,\langle q_2 \vert e^{ixp_1}\vert p_1 \rangle \langle p_1\vert e^{ikq_1} \vert q_1 \rangle\\
&= \int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ixk/2} \int dp_1 \, e^{ixp_1+ikq_1} \langle q_2 \vert p_1 \rangle \langle p_1\vert q_1 \rangle\\
&= \int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ixk/2} \int dp_1 \, e^{ixp_1+ikq_1} e^{iq_2p_1-ip_1q_1}\\
&= \int \frac{dx}{2\pi}\frac{dk}{2\pi} dp dq\, e^{-ixp-ikq} \, H(p,q)^n \, e^{ixk/2} 2\pi \delta(q_2 - q_1 + x) e^{ikq_1}\\
&= \int \frac{dk}{2\pi} dp dq\, e^{-i(q_2-q_1)p-ikq} \, H(p,q)^n \, e^{i(q_2+q_1)k/2} \\
&= \int \frac{dk}{2\pi} dp dq\, H(p,q)^n e^{-i(q_2-q_1)p-ikq+i(q_2+q_1)k/2}\\
&= \int dp dq\, H(p,q)^n \delta\left(\frac{q_2+q_1}{2}-q\right) e^{-i(q_2-q_1)p}\\
&= \int dp\, H\left(p,\frac{q_2+q_1}{2}\right)^n e^{-i(q_2-q_1)p}\\
\end{align*}$$
This means when we need to change the previous hamilton by changing $q_1$ to $\overline {q_1} \equiv \frac{q_2 + q_1}{2}$:
$$
\langle q_2\vert e^{-i\hat H\delta t}\vert q_1\rangle =
\int \frac{dp}{2\pi}\,e^{-iH(p,\overline {q_1})\delta t}e^{ip(q_2-q_1)}\,.
$$
**We completely removed operators from the equation!**

The total integral now becomes:
$$\begin{align*}
\langle q'',t''\vert q',t'\rangle
&= \int \displaystyle \prod_{k=1}^N dq_k\, \displaystyle \prod_{j=0}^{N} \langle q_{j+1}\vert e^{-i\hat H\delta t}\vert q_j\rangle \\
&= \int \displaystyle \prod_{k=1}^N dq_k\, \displaystyle \prod_{j=0}^{N} \,
   \int \frac{dp_j}{2\pi}\,e^{-H(p_j,\overline {q_j})\delta t}e^{ip_j(q_{j+1}-q_j)} \\
&= \int \displaystyle \prod_{k=1}^N dq_k\, \displaystyle \,
   \int \prod_{j=0}^{N}\frac{dp_j}{2\pi}\,\exp\left[-iH(p_j,\overline {q_j})\delta t + ip_j(q_{j+1}-q_j)\right] \\
\end{align*}$$
Let $\dot q_j \equiv (q_{j+1}-q_j) / \delta t$
$$\begin{align*}
&= \int \displaystyle \prod_{k=1}^N dq_k\, \displaystyle \,
   \int \prod_{j=0}^{N}\frac{dp_j}{2\pi}\,\exp\left[i\delta t\left(p_j\dot q_j - H(p_j,\overline {q_j})\right)\right] \\
&=
\int \mathcal D q \mathcal D p\,\exp\left[i\int dt\,p(t)\dot q(t) - H(p(t),q(t))\right]\\
\end{align*}$$

If $H(p, q)$ only has up to quadratic terms of $p$, then let $p\dot q - H(p, q) = A p^2 + B p + C$,
$$\begin{align*}
\int \frac{dp}{2\pi} \exp\left[i\delta t\left(p\dot q_j - H(p,\overline {q_j})\right)\right])
&= \int \frac{dp}{2\pi} \exp\left[i\delta t \left(A p^2 + B p + C\right)\right] \\
&= \int \frac{dp}{2\pi} \exp\left[i\delta t \left(A\left(p + \frac{B}{2A}\right)^2 + C-\frac{B^2}{4A}\right)\right] \\
&= \exp\left(-i\delta t \frac{B^2}{4A}\right) \exp\left(i\delta t C\right)\int \frac{dp}{2\pi} \exp\left[i\delta t Ap^2\right] \\
&= \exp\left(-i\delta t \frac{B^2}{4A}\right) \exp\left(i\delta t C\right)
   \sqrt{-\frac{1}{4\pi i \delta t A}} \\
\end{align*}$$
In our case
$$\begin{align*}
A &= -\frac{1}{2m} \\
B &= \dot q \\
C &= -V(q) \\
\int \frac{dp}{2\pi} \exp\left[i\delta t\left(p\dot q_j - H(p,\overline {q_j})\right)\right])
&= \sqrt{\frac{m}{2\pi i \delta t}}\exp\left[i\delta t \left(\frac{m\dot q_j^2}{2} - V(q_j)\right)\right]\,,\\
\end{align*}$$
which is independent of $p$.
$$\begin{align*}
\int \prod_{j=0}^{N}\frac{dp_j}{2\pi}\,\exp\left[i\delta t\left(p_j\dot q_j - H(p_j,\overline {q_j})\right)\right]
&= \left(\frac{m}{2\pi i \delta t}\right)^{(N+1)/2}\exp\left[i\delta t \sum_{j=0}^N \frac{m \dot q_j^2}{2} - V(q_j)\right] \\
&= \left(\frac{m}{2\pi i \delta t}\right)^{(N+1)/2}\exp\left[i \int_{t''}^{t'} dt \frac{m \dot q_j(t)^2}{2} - V(q_j(t))\right] \\
\end{align*}$$

---

Now we want to derive lagrangian $L(q, \dot q)$ from hamiltonian $H(p, q)$. Note that $H(p, q) = p\dot q - L(q, \dot q)$ and that lagrangian does not depend on momentum (since momentum is derived from lagrangian). To do so, we need to solve $p$ in terms of $\dot q$ and $q$ by equating the partial derivative of $L$ with respect with $p$ with $0$:
$$\begin{align*}
\partial_p L(q, \dot q) &= \partial_p (p\dot q - H(p,q)) = 0 \\
\dot q &= \partial_p H(p, q) \\
\end{align*}$$
In our case:
$$\begin{align*}
H(p, q) &= \frac{p^2}{2m} + V(q) \\
\dot q &= \partial_p H(p, q) = \frac{p}{m} \\
p &= m \dot q \\
L(q, \dot q) &= p\dot q - H(p, q) \\
 &= \frac{m \dot q^2}{2} - V(q) \\
\end{align*}$$

---

Therefore,
$$\begin{align*}
\langle q'',t''\vert q',t'\rangle &= \int \displaystyle \left(\frac{m}{2\pi i\delta t}\right)^{(N+1)/2} \prod_{k=1}^N dq_k\, \displaystyle \,
\exp\left[i\int_{t''}^{t'}L(q(t),\dot q(t))\,dt\right]
\end{align*}$$

Conventionally, we denote the measure $\displaystyle \left(\frac{m}{2\pi i\delta t}\right)^{(N+1)/2} \prod_{k=1}^N dq_k$ as $\mathcal D q$, meaning "_each path $q(t)$ from $t''$ to $t'$_":

$$\begin{align*}
\langle q'',t''\vert q',t'\rangle &= \int \mathcal Dq \, \displaystyle \,
\exp\left[i\int_{t''}^{t'}L(q(t),\dot q(t))\,dt\right]
\end{align*}$$

The constant in $\mathcal Dq$ varies with the hamiltonian. This is the ***Path Intergral*** formulation.
