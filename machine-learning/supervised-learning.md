Machine Learning Study Note - Supervised Learning Algorithm Overview

[Back to Intro](/read.php?page=machine-learning/intro)

### Formilizing Supervised Learning Algorithm

Given a sample
$$
\mathcal X = \{(x^t, r^t)\}_{t=1}^N
$$
The sample is IID: independently draw from the the same distribution $\mathcal p(x, r)$. $r$ is a $K$-dimsional exclusive binary vector (where exactly one of the dimensions is $1$ and others $0$).

The aim is to build a approximation to $r^t$ using the model $g(x^t|\theta)$. There are three decisions we must make:

1. _Model_ $g(\cdot)$ where $x$ is the input, and $\theta$ is call the parameter. $g(\cdot)$ defines the hypothesis class $\mathcal H$.
2. _Loss function_, $L(\cdot)$, to compute the difference between the desired output $r^t$ and our approximation $g(x^t|\theta)$. The _appoximation error_, or _loss_, is the sum of losses over the individual instances
$$
E(\theta|\mathcal X) = \sum_{(x,r)\in\mathcal X} L(r, g(x|\theta))\,.
$$
3. _Optimization procedure_ to find $\theta^*$ that minimizes the loss
$$
\theta^* =\arg\min_\theta E(\theta|\mathcal X)
$$


## Bayesian Decision Theory

The information in the world is not alway known to the observer. The extra knowledge we do not have access to are named the _unobservable variables_. Otherwise, called _observable variables_. Denoting the unobservables by $\mathbf z$ and the observable as $x$, in reality we have
$$
x = f(\mathbf z)
$$
where $f$ is a deterministic function that defines the outcome from the  unobservable piece of knowledge.

Since we cannot model the world this way, we define the outcome as a random variable $X$ drawn from a probability distribution $P(X)$. $P(X)$ can be described as a cumulative distribution function (CDF) $c(x) \equiv P(X < x)$, or a probablity density function (PDF) $p(x)$ such that:

$$c(x) = \int_{-\infty}^x p(t) dt$$

or in the case of discrete variable, probability mass function (PMF) $P(x)$ such that:
$$
c(x) = \sum_{t<x} P(t)
$$

> Note: The two are related by the Dirac delta function $\delta(x)$ defined as the PDF of the unit step CDF, that is, the distribution function of a random variable that always equals to zero. From physics and signal processing perspective:
$$
\delta(x) = \int_{-\infty}^{\infty}e^{-2i\pi xt}dt
$$
> which is not well-defined at $x=0$. But we can integrate it around zero by allowing iterated integral. For all $\epsilon > 0$:

$$\begin{align*}

\int_{-\epsilon}^{\epsilon}\delta(x)dx
&=\int_{-\epsilon}^{\epsilon}\int_{-\infty}^{\infty}e^{-2i\pi xt}\,dt\,dx \\
&\equiv\int_{-\infty}^{\infty}\int_{-\epsilon}^{\epsilon}e^{-2i\pi xt}dx\,dt\\
&=\int_{-\infty}^{\infty}\left(\left.\frac{e^{-2i \pi xt}}{x}\right\vert_{-\epsilon}^{\epsilon}\right)\,dt\\
&=\int_{-\infty}^{\infty}\frac{\sin(2\pi t \epsilon)}{\pi t}\,dt\\
&=\frac{1}{\pi}\int_{-\infty}^{\infty}\frac{\sin(t)}{t}\,dt\\
&=1
\end{align*}$$
> This mean it is indeed the PDF of unit step CDF.
> We can then describe a PMF in terms of PDF:
$$
p(x) = \delta(t-x)P(t)
$$
> and keeps the CDF unchanged.

If we do not know $P(X)$, we want to estimate this from a given sample $\mathcal X$. The goal is to build an estimator $\hat p(x)$ that given an instance $x$, estimates its likelihood.

In the case of classification, given classes $\mathcal C=\{C_i\}^K$, and sample $\{x^t,C^t\}$, we want to estimate the conditional probability of the class given $x$, $P(C|x)$. Using Bayes' rule, it can be written as
$$
P(C_i|x) = \frac{P(C_i)p(x|C_i)}{p(x)}\,.
$$
$P(\mathcal C)$ is called the _prior_. $P(C_i|x)$ is call the _posterior_. $P(x|C_i)$ is called the _class likelihood_. $p(x)$ is calle the _evidence_. We can rewrite this equation as
$$
\text{posterior} = \frac{\text{prior}\times\text{likelihood}}{\text{evidence}}
$$

$$\begin{align*}
\sum_i^K P(C_i) &= 1\\
\sum_i^K P(C_i|x) &= 1\\
\end{align*}$$

Also, the Law of total probability:
$$
p(x) = \sum_i^K P(C_i)p(x|C_i)
$$
We can then rewrite the Bayes' rule as
$$
P(C_i|x) = \frac{P(C_i)p(x|C_i)}{\sum_i^K P(C_i) p(x|C_i)}\,.
$$

A Bayes' classifier chooses the class with the highest posterior probability
$$
\arg\max_{C\in\mathcal C} P(C|x)
$$

## Losses and Risks
It may be the case the decisions are not equally good or costly. Let us define action $\alpha_i$ as the decision to assign the input to class $C_i$ and $\lambda_{ik}$ be the _loss_ for taking action $\alpha_i$ when the input actually belongs to $C_k$. Then _expected risk_ for taking action $\alpha_i$ is
$$
R(\alpha_i|x)=\sum_i^K \lambda_{ik}P(C_k|x)\quad,
$$
and we choose the action with minimum risk:
$$
\arg\min_\alpha R(\alpha|x)
$$

If we consider all mistakes to have the same loss, we get the 0/1 loss functions:

$$\begin{align}
\lambda_{ik} &= 1 - \delta_{ik}\\
R(\alpha_i|x)&=1-P(C_i|x)
\end{align}$$

Thus to minimize risk, we choose the most probable case.

In some applications, wrong decisions have very high cost, we can add a _reject_ or _doubt_ action $\alpha_{K+1}$to th the actions. A possible loss function is
$$
\lambda_{ik} = \begin{cases}
\lambda & i = K+1\\
0 &i = k\\
1 &\text{otherwise}\\
\end{cases}
$$
where $0 < \lambda < 1$. The decision rule becomes
$$\begin{align*}
C_i &\quad \text{if} & \max P(\alpha_i|x) > 1 - \lambda \text{ and }
 P(\alpha_i|x) \geq P(\alpha_k|x)\\
\text{reject} &\quad otherwise
\end{align*}$$
in other words, reject if the maximum likelihood does not exceed certain threshold $1 - \lambda$.

## Discriminant functions
Classification can also be seen as a set of _Discriminant functions_, $g_i(x)$ such that we
$$
\text{choose } C_i\text{ if } g_i(x) = \max_k g_k(x)\,.
$$

It is equivalent to Bayes' classifier for we can define the discrimitant function as
$$
g_i(x) = - R(\alpha_i|x)\,.
$$
When using 0/1 loss, we have:
$$
g_i(X)=P(C_i|x)
$$
or
$$
g_i(x)=p(x|C_i)P(C_i)
$$
This divides the feature space into $K$ _decision regions_ $\mathcal R_1, ..., \mathcal R_K$, where $R_i = \{x|g_i(x) = \max_k g_k(x)\}$. The regions are separated by _decision boundaries_.

When there is only one case, we can define a single discriminant
$$
g(x) = g_1(x) - g_2(x)
$$
and we
$$
\text{choose }\begin{cases}
C_1& \text{if } g(x)>0\\
C_2& \text{otherwise}
\end{cases}$$

When $K = 2$, the classification system is called a dichotomizer and for $K \geq 3$, it is a polychotomizer.

## Utility Theory

We now generalize expected risk to _utility theory_, which is concerned with making rational decisions when we are uncertain about the state.

Given evidence $x$, the probability of state $S_k$ is calculated as $P(S_k|x)$. If we define a _utility function_ $U_{ik}$, which measures how good it is to take action $\alpha_i$ when the state is $S_k$. The _expected utility_ is
$$
EU(\alpha_i|x) = \sum_k U_{ik}P(S_k|x)
$$

A rational decision maker chooses the action that maximizes the expected utility.

In the context of classification, maximizing the EU is equivalent to minimize expected risk.

