Machine Learning Study Node - Hidden Markov Model

[Back to Intro](/read.php?page=machine-learning/intro)

### Discrete Markov Processes

Consider a system at any time isin one of a set of $N$ distinct states: $S_1, S_2, ..., S_N$. The state a time $t$ is denoted as $q_t, t=1,2,...$.

The first-order Markov Model has:
$$
P(q_{t+1}=S_j|q_t=S_i,q_{t-1}=S_k,...)=P(q_{t+1}=S_j|q_t=S_i)
$$

We further simplify the model - that is, regularize - by assuming that these **_transition probabilities_** are independent of time:
$$
P(q_{t_1+1}=S_j|q_{t_1}=S_i) = P(q_{t_2+1}=S_j|q_{t_2}=S_i)\equiv a_{ij}
$$
satisfying
$$
a_{ij}\geq 0 \text{ and }\sum_{j=1}^N a_{ij} = 1
$$

This can be seen as a **_stochastic automaton_**. The **_initial probabilities_**, $\pi_i$, which is the probability that the first state in the sequence is $S_i$:
$$
\pi_i\equiv P(q_1=S_i)
$$
satisfying
$$
\sum_{i=1}^N \pi_i = 1
$$
In an observable Markov mode, the states are observables. At any time $t$, we know $q_t$, and as the system moves from one state to another, we get a sequence of states. Given sequence $Q=\{q_1,q_2,...,q_T\}$, the probability is given as
$$
P(Q|\mathbf A,\boldsymbol \pi) = \pi_{q_1} a_{q_1q_2}... a_{q_{T-1}q_T}
$$

### Hidden Markov Model

In a **_hidden Markove Model_**, the states are not observable, but when we visit a state, an observation $O_t$ is recorded that is a probabilistic function of the state. We assume a discrete observation in each state from the set $\{v_1, v_2, ..., v_M\}$:
$$
b_j(m)\equiv P(O_t=v_m|q_t=S_j)
$$
called the emission probability. The states $Q$ is not observed and can only be inferred from the observables.

In this case of Markov model, there are two sources of randomness: transitional probability $\mathbf A$ and emission probability $\mathbf B$.

To summarize and formalize, an HMM has the following elements:

1. $N$: Number of states in the model
$$
S=\{S_1,S_2,...,S_N\}
$$
2. $M$: Number of distinct observation sybmols in the **_alphabet_**
$$
V=\{v_1,v_2,...,v_M\}
$$
3. State transition probability:
$$
\mathbf A=[a_{ij}]\text{ where }a_{ij}\equiv P(q_{t+1}=S_j|q_t=S_i)
$$
4. Observation probabilities:
$$
\mathbf B=[b_j(m)]\text{ where }b_j(m)\equiv P(O_t=v_m|q_t=S_i)
$$
5. Initial probability
$$
\mathbf \Pi = [\pi_i]\text{ where }\pi_i\equiv P(q_i=S_i)
$$

We can describe an HMM as $\lambda = (\mathbf A, \mathbf B, \mathbf \pi)$

### Three basic problems of HMMs

1. (**_Evaluation Problem_**) Given a model $\lambda$, evaluate the probability of any given observation sequence, $O$, namely $P(O|\lambda)$.
2. (**_State Sequence Problem_**) Given a model $\lambda$, and a observation sequence $O$, try to find the state sequence $Q$ with the highest probability, namely $$\arg\max_Q P(Q|O,\lambda)$$
3. (**_Learning Model Parameters_**) Given a training set of observation sequences, $X=\{O^k\}_k$, learn the model that maximizes the pribability of generating $X$, namely $$\arg\max_\lambda P(X|\lambda)$.

#### Problem 1: Evaluation Problem
$$
P(O|\lambda) = \prod_{t=1}^T P(O_t|q_t,\lambda) = b_{q_1}(O_1)\cdot b_{q_2}(O_2)\cdot...b_{q_T}(O_T)
$$
However since $Q$ is unknown, we need to infer the it first
$$
P(Q|\lambda) = P(q_1)\prod_{t=1}^T P(q_t|q_{t-1})=\pi_{q_1}a_{q_1q_2}...a_{q_{T-1}q_T}
$$
therefore the joint probability is
$$
P(O,Q|\lambda) = \pi_{q_1}b_{q_1}(O_1)a_{q_1q_2}b_{q_2}(O_2)...a_{q_{T-1}q_T}b_{q_T}(O_T)
$$

We can compute $P(O|\lambda)$ by marginalize over the joint:
$$
P(O|\lambda)=\sum_{\text{all possbile }Q}P(O,Q|\lambda)
$$
But this is intractable. Fortunately, there is an efficient procedure to calculate $P(O|\lambda)$ called **_forward-backward procedure_**.

Define **_forward variable_** $\alpha_t(i)$
$$
\alpha_t(i) \equiv P(O_1,...,O_t,q_t=S_i|\lambda)
$$
Then we can calculate it recursively. First
$$\begin{align*}
\alpha_1(i) &= P(O_1, q_1=S_i|\lambda) \\
  &= P(O_1| q_1=S_i,\lambda)P(q_1=S_i|\lambda)\\
  &= b_i(O_1)\pi_i
\end{align*}$$
Then given $\alpha_{t-1}$:
$$
\begin{align*}
\alpha_t(i) &= P(O_1, O_2,..O_t, q_t=S_i|\lambda) \\
            &= \sum_j P(O_t,q_t=S_i|q_{t-1}=S_j\lambda) P(O_1, O_2,..O_{t-1}, q_{t-1}=S_j|\lambda) \\
            &=  b_i(O_i) \sum_j a_{ji} \alpha_{t-1}(j)
\end{align*}
$$
And eventually, the probability of an observable sequence is:
$$
P(O|\lambda) = \sum_{i=1}^N P(O, q_t=S_i|\lambda) = \sum_{i=1}^N \alpha_T(i)
$$

Computing $\alpha$ is $\mathcal O(N^2 T)$. We can similarly define a backward sequence:
$$\begin{align*}
\beta_t(i) &\equiv P(O_{t+1}...O_T|q_t=S_i,\lambda) \\
\beta_T(i) &\equiv 1
\end{align*}$$

This can be computed as
$$
\beta_t(i) = \sum_{j=1}^N a_{ji}b_j(O_{t+1})\beta_{t+1}(j)
$$

#### Problem 2: State Sequence Problem

Define
$$\begin{align*}
\gamma_t(i) &\equiv P(q_t=S_i|O,\lambda)\\
&= P(q_t=S_i,O|\lambda)/P(O|\lambda)\\
&= P(q_t=S_i,O_1,O_2,...,O_t,O_{t+1},...,O_T|\lambda)/P(O|\lambda)\\
&= C P(q_t=S_i,O_1,O_2,...,O_t|\lambda)P(O_{t+1},...,O_T|q_t=S_i,\lambda)\\
&= C \alpha_t(i) \beta_t(i)\\
\end{align*}$$
The last line is because $q_t$ blocks the observables by d-separation.

Given
$$
\sum_{i=1}^N \gamma_t(i) = 1
$$
We can determine $C$, and $$\begin{align*}
\gamma_t(i) = \frac{\alpha_t(i) \beta_t(i)}{\sum_{j=1}^N \alpha_t(j) \beta_t(j)}
\end{align*}$$

However, this cannot be used to find the highest probable sequence, for the states are not independent. For that we need the **_Viterbi algorithm_**.

Given state sequence $Q$ and observation sequence $O$, we define $\delta_t(i)$ as the probability of the highest probablity path at time $t$ that accounts for the first $t$ observations and ends in $S_i$:

$$
\delta_t(i)\equiv \max_{q_1,q_2,...,q_{t-1}} p(q_1,q_2,...,q_{t-1},q_t=S_i,O_1,...,O_t|\lambda)
$$

Then recursively calculate $\delta_{t+1}(i)$ as follows:
$$\begin{align*}
\delta_t(i) = \begin{cases}
\pi_ib_i(O_1) &t=1\\
\max_j \delta_{t-1}(j)a_{ij} b_j(O_t)&\text{otherwise}
\end{cases}
\end{align*}$$

Once we obtained the $\delta_T$, we can trace back and obtain the path.

#### Problem 3: Learning Model Parameters

We define $\xi_t(i,j)$ as the probability of being in $S_i$ at time $t$ and in $S_j$ at time $t+1$, given the whole observation $O$ and $\lambda$:
$$
\xi_t(i,j)\equiv P(q_t=S_i,q_{t+1}=S_j|O,\lambda)
$$
which can be computed as
$$\begin{align*}
\xi_t(i, j) &= P(q_t=S_i,q_{t+1}=S_j|O,\lambda) \\
&= C P(q_t=S_i,q_{t+1}=S_j,O|\lambda) \\
&= C P(q_t=S_i,O_1,O_2,...O_t|\lambda) P(q_{t+1}=S_j,O_{t+1},O_{t+2},...,O_T|q_{t}=S_i,\lambda) \\
&= C \alpha_t(i)a_{ij}b_j(O_{t+1})\beta_{t+1}(j)
\end{align*}$$
subject to:
$$
\sum_{i,j} \xi_t(i,j) = 1
$$

> Note: this can also be derived by seeing the model as a Baysian network.

In unsupervised learning, we have EM algorothm. In here we have **_Baum-Welch algorithm_**. It is an EM procedure. We first compute $\xi_t(i,j)$ and $\gamma_t(i)$ given current model $\lambda$, then  in the M-step, we recalculate $\lambda$ given $\xi_t(i, j)$ and $\gamma_t(i)$. These two steps are alternated until convergence during which, it has been shown, $P(O|\lambda)$ never decreases.

The estimations are
$$\begin{align*}
\hat a_{ij} &\propto \sum_k \sum_t \xi_t^{(k)}(i,j) \\
\hat b_{i}(m) &\propto \sum_k \sum_t \gamma_t^{(k)}(i)\mathbf 1(O_t^{(k)} = v_m) \\
\hat \pi_i &\propto \sum_k \gamma_1^{(k)}(i)
\end{align*}$$
subject to
$$\begin{align*}
\sum_j \hat a_{ij} &= 1 \\
\sum_m \hat b_i(m) &= 1 \\
\sum_i \hat \pi_i &= 1
\end{align*}$$

### Continuous Observations

If the inputs are continous, one possibility is to