Machine Learning Study Note - Baysian Network

[Back to Intro](/read.php?page=machine-learning/intro)

Graphical models are graphs of node and edges, where each node represent a random variable $X$ and corresponding probability of the random variable $P(X)$. If there is an direct arc from node $X$ to node $Y$, this indicates that $X$ has a **_direct influence_** on $Y$. This influence is specified by the conditional probability $P(Y|X)$.

A baysian network is a directed acyclic graph. The canoncial cases for conditional independence include:

1. Head-to-tail
$$
P(X,Y,Z)=P(X)P(Y|X)P(Z|Y)
$$

We say that $Y$ **_blocks_** the path from $X$ to $Z$, or in other words, it **_separates_** them in the sense that if $Y$ is removed, there is no path between $X$ to $Z$.

2. Tail-to-tail
$$
P(X,Y,Z)=P(X)P(Y|X)P(Z|X)
$$

3. Head-to-head
$$
P(X,Y,Z)=P(X)P(Y)P(Z|X,Y)
$$

One major advantage to using a Bayesian network is that we do not need to designate explicitly certain variables as input and certain others as output. Any proportion of the random variables can be observed and we can infer the rest of the variables, and the difference between unsupervised and supervised learning becomes blurry.

There may also be **_hidden variables_** whose values are never known from the evidence.

### Examples of Graphical Models

#### Naive Bayes' Classifier
It is a tail-to-tail baysian network that assumes that the observables are indenpendent:
$$
p(\mathbf x|C) = \prod^d p(x_j|C)
$$

#### Hidden Markov Model

HMMs are examples of baysian network where each observable is associated with a hidden state where each state is linked with previous state described with a transition probability matrix $A$, and observables linked with the current state with a observation probability matrix $B$. There are several variations of HMM:

1. **Input-Output HMM**:
Observable inputs $X^{(i)}$, hidden states $q^{(i)}$ and observable ouputs $O^{(i)}$ with
$$\begin{align*}
q^{(i-1)}, X^{(i-1)} \to q^{(i)} \\
X^{(i)}, q^{(i)} \to O^{(i)}
\end{align*}$$
1. **Fractal HMM**: Observable outputs $O^{(i)}$ and hidden states $q^{(i)}_{k}$:
$$\begin{align*}
q^{(i-1)}_j \to q^{(i)}_j \\
q^{(i)}_1, q^{(i)}_2, ..., q^{(i)}_k \to O^{(i)}
\end{align*}$$

1. **Counpled HMM**: Two types of observable outputs $O^{(i)}_{1,2}$, and two types of hidden states $q^{(i)}_{1,2}$:
$$\begin{align*}
q^{(i-1)}_1 \to q^{(i)}_1 \\
q^{(i-1)}_2 \to q^{(i)}_2 \\
q^{(i)}_1 \leftrightarrow q^{(i)}_2 \\
q^{(i)}_1 \to O^{(i)}_1 \\
q^{(i)}_2 \to O^{(i)}_2 \\
\end{align*}$$

1. **Switching HMM**: In a switching HMM, there are $K$ parallel independent hidden state sequences and the state variable $S$ at any one time picks one of them and the chosen one generates the output. That is, we switch between state sequences as we go along.
$$\begin{align*}
q^{(i-1)}_j \to q^{(i)}_j \\
s^{(i-1)} \to s^{(i)} \\
q^{(i)}_1, q^{(i)}_2, ..., q^{(i)}_k, s^{(i)} \to O^{(i)}
\end{align*}$$

In HMM, observables can take continous values, but states take discrete values. In a **_linear dynamic system_**, also known as the **_Kalman filter_**, both the state and the observations are continuous (although the states them self has discrete labels, $q_1, q_2, ...$). In the basic case, the state at $q_i$ is $q_{i-1}$ plus an additive zero-mean Gaussian noise. The two linear mappings and the covariances of the two covariances of the two noise sources make up the parameters.

#### Linear Regression

Linear regression can be considered a graphical model:
$$
p(\mathbf w) \sim \mathcal N(0,\alpha^{-1}\mathbf I)
$$
$$
p(r^t|\mathbf x^t,\mathbf w) \sim \mathcal N(\mathbf w^T \mathbf x^t, \beta ^{-1})
$$
Then given a new input $x'$, estimate $r'$ as $E[r'|\mathbf x',\mathbf w]$. Then the regression is
$$
\begin{align*}
p(r'|\mathbf x', \{\mathbf r^t, \mathbf x^t\})
&= \int p(r'|\mathbf x', \mathbf w) p(\mathbf w| \{\mathbf r^t, \mathbf x^t\}) d\mathbf w\\
&= \int p(r'|\mathbf x', \mathbf w) \frac{p(\{\mathbf r^t, \mathbf x^t\}|\mathbf w)p(\mathbf w)}{p(\{\mathbf r^t, \mathbf x^t\})} d\mathbf w\\
&= C\int p(r'|\mathbf x', \mathbf w) p(\{\mathbf r^t, \mathbf x^t\}|\mathbf w)p(\mathbf w) d\mathbf w\\
&= C\int p(r'|\mathbf x', \mathbf w) \prod_t p(\mathbf r^t|\mathbf x^t, \mathbf w)p(\mathbf w) d\mathbf w\\
\end{align*}
$$
the last line is due to IID assumption.

### d-Separation
We now generalize the concept to blocking and separation under the name of _d-separation_, and we defined it in a way so that for arbitrary subsets of nodes $A$, $B$, and $C$, we can check if $A$ and $B$  are independent given $C$. This is called a **_Bayes' Ball_**.

To check whether $A$ and $B$ are d-separated given $C$, we consider all possible paths between any node in $A$ and any node in $B$. Any such path is _blocked_ if

1. the direction of the edges on the path either meed head-to-tail or tail-to-tail and the node it passes through is in $C$, or
1. the direction of the edges meet head-to-head and neither that node nor any of its descendant is in $C$.

If all paths are blocks, we say that $A$ and $B$ are d-separated, that is, conditioanl independent given $C$.

### Belief Propagation

Given a graph, we now are interested in an algorithm that can answer the queries of $P(X|W)$ where $X$ is any **_query node_** in the graph given some **_evidence nodes_** $E$.

#### Chains
If the evidence is in the ancestors of query, we can just do a diagnostic inference and propagate evidence down the chain. Otherwise we do a causal inference and propagate upwade using Bayes' rule. For example:
$$
E_1 \to T_1 \to T_2 ... \to T_a \to X \to U_1 \to U_2 ... \to U_b \to E_2
$$

Since $X$ blocks $E_1$ and $E_2$, we have
$$
P(E_1,E_2|X) = P(E_1|X) P(E_2|X)
$$

Then

$$\begin{align*}
P(X|E_1, E_2) &= \frac{P(E_1, E_2|X)P(X)}{P(E)}\\
&=\frac{P(E_1|X) P(E_2|X)P(X)}{P(E)}\\
&=\frac{P(X|E_1) P(E_2|X) P(E_1)}{P(E)}\\
&=\alpha P(X|E_1) P(E_2|X)
\end{align*}$$
where $\alpha$ is normalizing constant that does not depend on $X$.

In order to calculate $P(X|E_1)$, we recursively use the marginalization

$$\begin{align}
P(X|E_1) &= \sum_{T_a}P(X|T_a)P(T_a|E_1)\\
P(E_2|X) &= \sum_{T_a}P(E_2|U_1)P(U_1|X)
\end{align}$$

We define a $\pi(A) \equiv P(A|E_1)$ and $\lambda(A) \equiv P(E_2|A)$. When evidence nodes are set to a value, they initiate traffic and nodes continue updating util there is convergence.

> Note: this looks like path integral!

#### Trees
Given a graphical model that forms a tree, the same belief propagation also applies. $\lambda_Y(X)$ denoting the message $X$ receives from its child $Y$, and sends different $\pi$-messages to its children, $\pi_Y(X)$ denoting the message $X$ sends to its child $Y$.

Again if $X$ separates two parts of the evidence $E_X^+$ and $E_X^-$ we can have
$$
P(X|E) = \alpha \pi(X)\lambda(X)
$$
To compute the two terms, to propagate up:
$$\begin{align*}
\lambda(X) &= \prod_{Y\in child(X)} \lambda_Y(X)\\
\end{align*}$$
if $U$ is a parent of $X$, $$\lambda_X(U) = \sum_X\lambda(X)P(X|U).$$

Then, to compute propagagte down:
$$
\pi(X)\equiv P(X|E^+_X) = \sum_{U\in child(X)} P(X|U)\pi_X(U)
$$
The trick to compute $\pi_X(U)$ is as follows. Given $Y_i$ as children of $X$:
$$\begin{align*}
\pi_{Y_j}(X)=P(X|E_Y^+)&=P(X|E_X^+,E_{Y_{i\neq j}}^-)\\
&=P(X|E_X^+)P(X|E_{Y_{i\neq j}}^-)\\
&=\alpha \pi(X)\prod_{i!=j}\lambda_{Y_i}(X)
\end{align*}$$

#### Polytrees
#### Juction Trees

### Undirected Graph: Markov Random Field

The treatment of undirected graphs is simpler. It is much easier to check if $A$ and $B$ are independent given $C$, by checking if removing $C$ removes all the path through $A$ and $B.

To turn a directed graph to an undirected one, we **_moralize_** the graph by adding links bewteen nodes that have common children.

The belief propagation algorithm is conducted by converting it into a [factor graph](https://en.wikipedia.org/wiki/Factor_graph) and uses the sum-product algorithm.