Machine Learning Study Notes - Bayesian Estimation

[Back to Intro](/read.php?page=machine-learning/intro)

We assume the sample is drawn from a distribution which is controled by a small number of parameters. For example, if we assume the sample is drawn from normal distributionm then we can use mean and variance to describe it. The parameters are called the _sufficient statistics_ of the distribution. We estimate the paramter by maximum likelihood estimation.

We start with density estimation, which is the general case of estimating $p(x)$.

## Maximum likelihood estimation

Let $\mathcal X = \{x^t\}^N$ be a sample drawn from IID that
$$
x^t \sim p(x|\theta)
$$

We want to find $\theta$ that makes sample $\mathcal X$ as likely as possible. The likelihood of parameter $\theta$ will be
$$
l(\theta|\mathcal X)\equiv p(\mathcal X | \theta) = \prod_N p(x^t|\theta)
$$

To maximize this is equivalent toe maximize its log, but more computationally tractable. The log likelihood is defined as
$$
\mathcal L(\theta|x)\equiv \log l(\theta|x) = \sum_N \log p(x^t|\theta)
$$

### Bernoulli Density
If the distribution is Bernoulli with a single parameter $p$:
$$
P(\mathcal X) = p^x(1-p)^(1-x)
E[X]= p
Var(x) = p(1-p)
$$

The log likelihood is
$$
\mathcal L(p|\mathcal X) = \sum_t x^t \log p + \left(N - \sum_t x^t\right) \log (1-p)
$$
to maximize $\mathcal L$, we solve $d \mathcal L / dp = 0$. The estimate $\hat p$ is
$$
\frac{d\mathcal L}{dp} = \frac{\sum_t x^t}{p} - \left(N - \sum_t x^t\right)\frac{1}{1-p} = 0\\
$$
$$\begin{align*}
\frac{\sum_t x^t}{p} &= \left(N - \sum_t x^t\right)\frac{1}{1-p}\\
(1-p)\sum_t x^t &= p\left(N - \sum_t x^t\right)\\
(1-p)\sum_t x^t &= pN - p\sum_t x^t\\
\sum_t x^t &= pN\\
\hat p &= \frac{\sum_t x^t}{N}
\end{align*}$$

Note that the estimate is a function of the sample and is another random variable.

### Multinomial Density
$$
P(x_1, x_2, ..., x_k) = \prod_{i=1}^k p^{x_i}
$$
The MLE of $p_i$ is
$$
\hat p_i = \frac{\sum_t x_i^t}{N}
$$

### Gaussian Density
The density function is
$$
p(x)=\frac{1}{\sqrt{2\pi}\sigma} \exp\left[-\frac{(x-\mu)^2}{2\sigma^2}\right]\\
\mathcal L(\mu, \sigma|\mathcal X)=-\frac{N}{2}\log(2\pi)-N\log \sigma - \frac{\sum(x-\mu)^2}{2\sigma^2}
$$
The MLE is obtained by makeing partial derivatives of the log likelihood zero:
$$\begin{align*}
\frac{\partial \mathcal L}{\partial \mu} &= 0\\
\frac{\partial \mathcal L}{\partial \sigma} &= 0\\
\frac{2\sum{(x-\mu)}}{2\sigma^2} &=0\\
-\frac{N}{\sigma}+\frac{\sum(x-\mu)^2}{\sigma^3} &=0\\
\sum_t{(x^t-\mu)} &=0\\
\frac{\sum_t(x^t-\mu)^2}{\sigma^2}&=N\\
\end{align*}$$
$$\begin{align*}
\hat \mu &= \frac{\sum_t x^t}{N}\\
\hat \sigma^2 &= \frac{\sum(x^t-m)^2}{N}
\end{align*}$$

### Evaluating the esimator: bias and variance

An estimator $d(\mathcal X)$ is a random variable based on a sample. To evaluate the quality of an estimator we need to evaluate the mean squire err (MSE)
$$
r(d,\theta) = E[(d(\mathcal X) - \theta)^2]
$$
where $\theta$ is the real parameter $\mathcal X$ is drawn from.

The bias of an estimator is
$$
b_\theta(d) = E[d(\mathcal X)]-\theta
$$

If $b_\theta(d) = 0$ for all $\theta$ values, we say that $d$ is an _unbiased estimator_ of $\theta$.
Now let's check the $\hat \sigma^2$.
$$\begin{align}
E[(x^t)^2]=\sigma^2/N+\mu^2 \\
E[\hat\sigma^2]=(\frac{N-1}{N})\sigma^2
\end{align}$$

So the MLE of $\sigma^2$ is not unbiased. However when $N$ is large, the difference is negligable. This is called an _asymptotically unbiased estimator_.

The MSE can be written as
$$
r(d, \theta) = Var(d)+ (b_\theta(d))^2
$$

## Bayes' Estimator

Sometimes we have some prior information about the $\theta$ we try to estimate. This is called the _prior densiy_. We combine the data and get the _posterior density_ of $\theta$
$$
p(\theta|\mathcal X) = \frac{p(\mathcal X|\theta)p(\theta)}{p(\mathcal X)} = \frac{p(\mathcal X|\theta)p(\theta)}{\int p(\mathcal X|\theta')p(\theta')d\theta'}
$$
Then we estimate the density at $x$
$$\begin{align}
p(x|\mathcal X) &= \int p(x|\theta, \mathcal X)p(\theta|\mathcal X)d\theta\\
&= \int p(x|\theta)p(\theta|\mathcal X)d\theta
\end{align}$$

$p(x|\theta,\mathcal X)=p(x|\theta)$ because $\theta$ is the sufficient statistics. When the integral is intractable, we can assume the peak of $p(\theta|\mathcal X)$ is narraw and we only use the _maximum a posteriori estimate_ (MAP):

$$\begin{align*}
\theta_{MAP} &= \arg\max_\theta p(\theta|\mathcal X)\\
p(\theta) &= \delta(\theta - \theta_{MAP})
\end{align*}$$

If we have no prior reason to favor some values of $\theta$, then the prior density is flat and the posterior will have the same form as the maximum likelihood.
$$\begin{align*}
\arg\max_\theta p(\theta|\mathcal X) &= \arg\max_\theta \frac{p(\mathcal X|\theta)p(\theta)}{p(\mathcal X)} \\
&= \arg\max_\theta \frac{p(\mathcal X|\theta)}{p(\mathcal X)} \\
&= \arg\max_\theta p(\mathcal X|\theta) \\
&\equiv \theta_{ML}
\end{align*}$$

Another estimator is the Bayes' estimator, which is defined as expected value of the posterior density
$$
\theta_{Bayes} = E[\theta|\mathcal X] = \int \theta p(\theta|\mathcal X)d\theta
$$

In the case of normal density, if the prior density of $\theta$ is $\mathcal N(\mu_0, \sigma_0^2)$, and $x^t\sim\mathcal N(\theta,\sigma^2)$, then
$$\begin{align}
p(\mathcal X|\theta) &= \frac{1}{(2\pi)^{N/2}\sigma^N}\exp\left[\frac{-\sum(x^t-\theta)^2}{2\sigma^2}\right]\\
p(\theta) &= \frac{1}{\sqrt{2\pi}\sigma_0}\exp\left[-\frac{(\theta-\mu_0)^2}{2\sigma_0^2}\right]
\end{align}$$
then the Bayes' estimator
$$\begin{align}
p(\theta|\mathcal X) &= \frac{p(\mathcal X|\theta)p(\theta)}{p(\mathcal X)}\\
&=\frac{1}{(2\pi)^{N/2}\sigma^N}\exp\left[\frac{-\sum(x^t-\theta)^2}{2\sigma^2}\right] \frac{1}{\sqrt{2\pi}\sigma_0}\exp\left[-\frac{(\theta-\mu_0)^2}{2\sigma_0^2}\right]/p(\mathcal X)\\
&=C\exp\left[\frac{-\sum(x^t-\theta)^2}{2\sigma^2}-\frac{(\theta-\mu_0)^2}{2\sigma_0^2}\right]\\
&=C\exp\left[-\frac{\sum(x^t-\theta)^2\sigma_0^2+(\theta-\mu_0)^2\sigma^2}{2\sigma^2\sigma_0^2}\right]\\
&=C\exp\left[-\frac{
  (N\sigma_0^2 + \sigma^2)\theta^2 - 2(\sigma^2\mu + \sigma_0^2\sum x^t) \theta
}{2\sigma^2\sigma_0^2}\right]\\
\end{align}$$

Since we know this is a proper distribution density, this means
$$\begin{align}
P(\theta|\mathcal X) &\sim \mathcal N\left(\frac{\sigma^2\mu+\sigma_0^2\sum x^t}{N\sigma_0^2 + \sigma^2},\frac{\sigma^2\sigma_0^2}{N\sigma_0^2 + \sigma^2}\right) \\
E(\theta|\mathcal X) &= \frac{\sigma^2\mu+N\sigma_0^2m}{\sigma^2 + N\sigma_0^2} \\
&= \frac{\sigma^2}{\sigma^2 + N\sigma_0^2}\mu + \frac{N\sigma_0^2}{\sigma^2 + N\sigma_0^2}m \\
\end{align}$$

Thus the Bayes' estimator of $\theta$ is the weighted mean of prior and posterior mean.

Both MAP and Bayes' estimators reduce the whole posterior density to a single point and lose information unless the posterior is unimodal and makes a narrow peak around these points. We can instead use a Monte Carlo approach that generates samples from the posterior density. There are also approximation methods to evaluate the full integral.

## Estimating the Parameter of a Distribution

### Discrete Variables

Given a multinomial variable taking one of $K$ distinct values, let $x_i^t=1$ if instance $t$ takes value $i$, or $x_i^t=1$ otherwise. The parameter we need to estimate is a vector $\mathbf q = [q_1,q_2,...,q_k]^T\in \mathbb R^K$. The likelihood is
$$
p(\mathcal X|\mathbf q) = \prod_t^N\prod_i^K q_i^{x^t_i}
$$

The prior distribution we use is the Dirichlet distribution

$$
\text{Dirichlet}(\mathbf q|\mathbf \alpha) = \frac{1}{B(\alpha)}\prod_i^K q_i^{\alpha_i-1}
$$
where the normalization factor $B(\alpha)$ is the multivariate Beta function
$$
B(\alpha) = \frac{\prod_i^K\Gamma(\alpha_i)}{\Gamma(\alpha_0)}
$$
$$
\alpha_0 \equiv \sum_i^K \alpha_i
$$
where $\mathbf\alpha = [\alpha_1,...\alpha_K]^T$ is the parameters of the prior, called _hyperparameters_. $\Gamma(x)$ is the Gamma Function defined as
$$
\Gamma(x) = \int_0^\infty u^{x-1}e^{-u}du
$$
> Note $n! = \Gamma(n+1)$.

Given the prior and the likelihood, we can derive the posterier
$$\begin{align*}
p(\mathbf q|\mathcal X) &\propto p(\mathcal X|\mathbf q) p(\mathbf q | \mathbf \alpha) \\
&\propto \prod_i^K q_i^{N_i+\alpha_i-1}
\end{align*}$$
where $N_i = \sum_{t=1}^N x^t$.

We can see that the posterior distribution and prior distribution is of the same form. We call these priors _conjugate priors_. We have
$$
p(\mathbf q|\mathcal X) = \text{Dirichlet}(\mathbf q|\mathbf \alpha + \mathbf n)
$$
where $\mathbf n = [N_1,...,N_K]^T$. $|\mathbf n|_1=N$.

Look at the posterior, we can obtain the intuition of hyperparameters $\alpha_i$. Just as $n_i$ are counts of occurrences of value $i$ in a sample of $N$, we can view $\alpha_i$ as the imaginary samples of $\alpha_0$ instances. Note that larger $\alpha_0$ implies that we have a higher confidence (a more peaked distribution) in our subjective proportions.

When the variable is binary, multinomial becoms Bernoulli and Dirichlet distribution becomes Beta distribution.

### Continous Variables
When $p(x) \sim \mathcal N (\mu, \sigma^2)$, with parameter $\mu$ and $\sigma^2$. The likelihood is
$$
p(\mathcal X|\mu,\sigma^2)=\prod_t^N\frac{1}{(2\pi)^{N/2}\sigma^N}\exp\left[-\frac{(x^t-\mu)^2}{2\sigma^2}\right]
$$
The conjugate prior for $\mu$ is Gaussian $p(\mu) \sim \mathcal N(\mu_0^2, \sigma_0^2)$ and the posterior is
$$
p(\mu|\mathcal X) \propto \mathcal N(\mu_N,\sigma_N)
$$
where
$$\begin{align*}
\mu_N &= \frac{\sigma^2}{\sigma^2 + N\sigma_0^2}\mu + \frac{N\sigma_0^2}{\sigma^2 + N\sigma_0^2}m \\
\sigma_N^2 &= \frac{\sigma^2\sigma_0^2}{N\sigma_0^2 + \sigma^2}\text{, or}\\
\frac{1}{\sigma_N^2} &= \frac{1}{\sigma_0^2}+\frac{N}{\sigma^2}
\end{align*}$$
where $m=\sum_t^Nx^t/N$ is the sample average. The prior meaning is as if we have done some imaginary experiments as well.

It is more intuitive to work with the reciprocal of the variance than then variance it self. Let $\lambda = 1/\sigma^2$. The likelihood is written as:
$$\begin{align*}
p(\mathcal X|\lambda) &= \prod_t^N \sqrt{\frac{\lambda}{2\pi}}\exp\left[-\frac{\lambda}{2}(x^t-\mu)^2\right]\\
&= \sqrt{\frac{\lambda}{2\pi}}^N \exp\left[-\frac{\lambda}{2}\sum_t^N(x^t-\mu)^2\right]
\end{align*}$$

The conjugate prior for precision is the _Gamma distribution_:
$$
p(\lambda)\sim\text{Gamma}(a_0, b_0)=\frac{1}{\Gamma(a_0)} b_0^{a_0}\lambda^{a_0-1}\exp(-b_0\lambda)
$$
The posterior is
$$\begin{align*}
p(\lambda|\mathcal X) &\propto p(\mathcal X | \lambda) p(\lambda) \\
&= \sqrt{\frac{\lambda}{2\pi}}^N \exp\left[-\frac{\lambda}{2}\sum_t^N(x^t-\mu)^2\right]
\frac{1}{\Gamma(a_0)} b_0^{a_0}\lambda^{a_0-1}\exp(-b_0\lambda)\\
&= C\lambda^{a_0-1+N/2}\exp\left[-\frac{\lambda}{2}\sum_t^N(x^t-\mu)^2-b_0\lambda\right]\\
&\sim \text{Gamma}(a_0+\frac{N}{2}, b_0+Ns^2/2)
\end{align*}$$

where $s^2 = \sum(x^t-\mu)^2/N$ is the sample variance.

## Bayesian Estimation of a Parameters of a Function
### Regression

Given  a linear regression model:
$$
r = \mathbf w^T\mathbf x + \epsilon\text{ where }\epsilon\sim\mathcal N(0,\beta^{-1})
$$
where $\beta$ is the precision of the additive noise.

The paramters are the weights $\mathbf w\in \mathbb R^d$ and we have a sample $\mathcal X = \{(\mathbf x^t \in \mathbb R^d, r^t)\}_t^N$. We can break down the sample in to a matrix of inputs a vector of desired outputs as $\mathcal X = [\mathbf X, \mathbf r]$ where each row of $\mathbf X$ is an instance. We have
$$
p(r^t|\mathbf x^t, \mathbf w,\beta) \sim \mathcal N(\mathbf w^T \mathbf x^t, \beta^{-1})
$$
and log likelihood is
$$
\mathcal L(\mathcal X|\mathbf w)=\log p(\mathbf r|\mathbf X,\mathbf w) + \log p(\mathbf X)
$$
$$\begin{align*}
\log p(\mathbf r|\mathbf X,\mathbf w) &= \log\prod_t^N p(r^t|\mathbf x^t,\mathbf w,\beta) \\
&= -N \log(2\pi)/2+ N\log\beta - \frac{\beta}{2}\sum_t^N(\mathbf r^t - \mathbf w^T \mathbf x^t)^2
\end{align*}$$

For the case of ML estimate, we find $\mathbf w$ that maximize the likelihood, or equivalently, minimizes the last term as is the sum of squared error
$$
E = (\mathbf r - \mathbf X \mathbf w)^T(\mathbf r - \mathbf X \mathbf w)
$$
Taking the derivative with respect to $\mathbf w$ and setting it to $0$, we get the maximum likelihood estimator
$$
\mathbf w_{ML} = (\mathbf X^T\mathbf X)^{-1}\mathbf X^T\mathbf r
$$
The predicted result in test set is
$$
r' = \mathbf w_{ML}^T \mathbf x'
$$

In the case of Bayesian approach, we define a indenpendent Gaussian prior
$$
p(\mathbf w) \sim \mathcal N(\mathbf 0, \mathbf \alpha^{-1}\mathbf I)
$$
the posterior is
$$
p(\mathbf w|\mathcal X)\sim \mathcal N(\mathbf \mu_N, \mathbf \sigma_N)
$$
where
$$\begin{align*}
\mathbf \mu_N &= \beta \mathbf \sigma_N \mathbf X^T \mathbf r \\
\mathbf \sigma_N &= (\beta \mathbf X^T\mathbf X + \alpha I)^{-1}
\end{align*}$$
The mean output is
$$
E(r'|\mathbf x', \mathcal X) = \int \mathbf w^T \mathbf x' p (\mathbf w|\mathcal X)d\mathbf w
$$
If we want to you a point estimate, the MAP gives
$$
\mathbf w_{MAP} = \mathbf \mu_N = (\mathbf X^T \mathbf X + \frac{\alpha}{\beta} I)^{-1}\mathbf X^T\mathbf r
$$
and the estimation is
$$
r'= \mathbf w_{MAP} \mathbf x'
$$
with variance
$$
\text{Var}(r') = \beta^{-1} + (\mathbf x')^T\mathbf \sigma_N \mathbf x'
$$
Comparing with ML estimation, it is the Gaussian estimator when $\alpha \to 0$.

### Ridge Regression
The log of the posterior is
$$\begin{align*}
\log p(\mathbf w|\mathbf X,\mathbf r) &= \log p(\mathbf X,\mathbf r|\mathbf w) + \log p(\mathbf w) + C_1\\
&=\log p(\mathbf r|\mathbf X,\mathbf w) + \log p(\mathbf w) + C_2\\
&=-\frac{\beta}{2}\sum(\mathbf r^t - \mathbf w^T \mathbf x^t)^2 - \frac{\alpha}{2} \mathbf w^T\mathbf w + C_3\\
\end{align*}$$
which we maximize to find the MAP estimation. In general, we can write an augmented error function
$$
E_{\text{ridge}}(\mathbf w|\mathcal X) = \sum_t\left(\mathbf r^t - g(\mathbf x^t, \mathbf w)\right)^2 + \lambda |\mathbf w|_F
$$
where $\lambda \equiv \alpha/\beta$. This is known as _parameeter shinkage_ or _ridge regression_.
> In neural network, this is L2 regularization, or _weight decay_.

This does reduces the square of the weights, but as the weight get smaller, the pressure reduces as well. It cannot be used for feature selection. For this, one can use a _Laplacian prior_ that uses $L_1$ norm instead of the $L_2$ norm
$$
p(\mathbf w|\alpha) = \left(\frac{\alpha}{2}\right)^d\exp\left(-\alpha |\mathbf w|_1 \right)
$$
$$
\log p(\mathbf w|\alpha) = d \log(\alpha/2) - \alpha |\mathbf w|_1
$$
the log posterior is
$$\begin{align*}
\log p(\mathbf w | \mathbf X, \mathbf r, \alpha)
&= \log p(\mathbf r | \mathbf X, \mathbf w) + \log p(\mathbf w|\alpha) + C_1\\
&= -\frac{\beta}{2}\sum (\mathbf r^t - \mathbf w^T \mathbf x^t)^2 - \alpha |\mathbf w|_1 + C_2
\end{align*}$$

The posterior is no longer Gaussian and the MAP estimate is found by minimizing
$$
E_{\text{lasso}}(\mathbf W|\mathcal X) = \sum (r^t - \mathbf w^T \mathbf x^t)^2 + 2\sigma^2\alpha\mathbf w
$$

This is known as lasso (least absolute shrinkage and selection operator).