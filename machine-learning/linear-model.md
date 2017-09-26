Machine Learning Study Note - Linear models

[Back to Intro](/read.php?page=machine-learning/intro)

### Introduction
In case of classification, we define a set of discriminant function $g_j(\mathbf x), j =1,...,K$, and then we
$$
\text{choose }C_i\text{ if }g_i(\mathbf x)=\max_{j=1}^Kg_i(\mathbf x)
$$

If we first estimate the prior probabilities, $\hat P(C_i)$ and the class likelihoods $\hat p(x|C_i)$ and use Bayes' rule to calculate the posterior densities, and define discriminant functions in terms of the posterior, for example
$$
g_i(\mathbf x) = \log \hat P(C_i|\mathbf x)
$$
then this is called **_likelihood-based classification_**.

Now we are going to discuss **_discreiminant-based classification_** where we assume a model directly for the discriminant, bypassing the stimation of likelihood or posteriors. The discriminant-based approach makes no assumption about the density.

We define a model for the discriminant
$$
g_i(\mathbf x | \Phi_i)
$$
explicitly parameterized with the set of parameters $\Phi_i$, as opposed to a likelihood-based scheme that has implicit parameters in defining the likelihood densities.

In the discriminant-based approach, we do not care about correctly estimating the density inside the class regions. All we care about is the correct estimation of the _boundaries_ between the class regions. This is true only when the discriminant can be approximated by a simple function.

We now define a linear discriminant function:
$$
g_i(\mathbf x|\mathbf w_i, b_i) = \mathbf w_i \cdot \mathbf x + b_i
$$
or a vector of discriminant functions
$$
\mathbf g(\mathbf x|\mathbf w, \mathbf b) = \mathbf w \cdot \mathbf x + \mathbf b
$$

The linear discriminant is used frequently mainly due to its simplicity: both space and time complexity are $\mathcal O(d)$. The model is also explainable for the maginitude of the weight shows the importane of $x_j$.

The linear discriminant should be tried first before trying a complicated model to make sure the additional complexity is justified.

### Generalizing the linear model

If we start by adding a quadratic term
$$
\mathbf g_i(\mathbf x|\mathbf W_i\mathbf w_i, \mathbf b_i) = \mathbf x^T \mathbf W_i \mathbf x + \mathbf w_i \cdot \mathbf x + \mathbf b_i
$$
though it is more general, it requires much larger training sets and may overfit on small samples.

An equivalent way is to preprocess the input by adding **_higher-oder terms_**, also called **_product terms_**. A linearly inseparable problem can become linearly separable in this new space. Our discriminant becomes
$$
g_i(\mathbf x) = \sum_k w_j \phi_{ij}(\mathbf x)
$$
where $\phi_{ij}(\mathbf x)$ are called **_basis functions_**. Some examples are

* $\sin(x_1)$
* $\exp(-(x_1-m)^2/c)$
* $\exp(-\|\mathbf x-\mathbf \mu\|^2/c)$
* $\log(x_2)$
* $1(x_1 > c)$
* $1(ax_1 + bx_2 > c)$

### Geometry of the Linear Discriminant

Starting with a two-class classifier. In such a case, one discriminant function is sufficent:
$$\begin{align*}
g(\mathbf x) &= g_1(\mathbf x) - g_2(\mathbf x)\\
&=(\mathbf w_1 \cdot \mathbf x + b_1) + (\mathbf w_2 \cdot \mathbf x + b_2)\\
&=(\mathbf w_1 - \mathbf w_2) \cdot \mathbf x + (b_1 - b_2) \\
&=\mathbf w \cdot \mathbf x + b
\end{align*}$$
where $\mathbf w = \mathbf w_1 - \mathbf w_2$ is the **_weight vector_** and $b = b_1 - b_2$ is the **_threshold_**. The hyperplane divides the input space into two half-spaces. Taking two points $\mathbf x_1$ and $\mathbf x_2$ on the decision surface, $g(\mathbf x_1) = g(\mathbf x_2) = 0$, then
$$\begin{align*}
\mathbf w \cdot \mathbf x_1 + b &= \mathbf w \cdot \mathbf x_2 + b \\
\mathbf w \cdot (\mathbf x_1 - \mathbf x_2) &= 0
\end{align*}$$
This mean $\mathbf w$ is perpendicular to any vector on the hyperplane, hence the normal vector of the hyperplane itself. This allows us to unambigously write any $\mathbf x$ as
$$
\mathbf x = \mathbf x_p + r\frac{\mathbf w}{\|\mathbf w\|}
$$
where $\mathbf x_p$ is the projection of $\mathbf x$ on the hyperplane, with $g(\mathbf x_p) = 0$, and factor on $r$ is to make sure the physical meaning of $r$
$$\begin{align*}
\|\mathbf x-\mathbf x_p\| &= \sqrt{(\mathbf x-\mathbf x_p) \cdot (\mathbf x-\mathbf x_p)} \\
&= \sqrt{r\frac{\mathbf w}{\|\mathbf w\|} \cdot r\frac{\mathbf w}{\|\mathbf w\|}} \\
&= r \sqrt{\frac{\mathbf w\cdot \mathbf w}{\|\mathbf w\|^2}} \\
&= r
\end{align*}$$
We can solve $r$
$$\begin{align*}
g(\mathbf x_p) &= 0\\
\mathbf w \cdot \left(\mathbf x - r \frac{\mathbf w}{\sqrt{\mathbf w \cdot \mathbf w}}\right) + b &= 0\\
\mathbf w \cdot \mathbf x - r \frac{\mathbf w \cdot \mathbf w}{\sqrt{\mathbf w \cdot \mathbf w}} + b &= 0\\
r \sqrt{\mathbf w \cdot \mathbf w} &= \mathbf w \cdot \mathbf x + b\\
r  &= \frac{\mathbf w \cdot \mathbf x + b}{\sqrt{\mathbf w \cdot \mathbf w}}\\
\end{align*}$$

In the muliclass case, the usual approach is to assign $\mathbf x$ to the class having the highest discriminant
$$
\text{choose }C_i\text{ if }g_i(\mathbf x) = \max_j g_j(\mathbf x)
$$

### Logistic regression and softmax

If the class density $p(\mathbf x|C_i)$ are Gaussian and share a common covariance matrix, the discriminant function is linear
$$
g_i(\mathbf x) = \mathbf w_i \cdot \mathbf x + b_i
$$
where the parameters can be analytically calculated as
$$\begin{align*}
\mathbf w_i &= \boldsymbol \Sigma^{-1}\boldsymbol \mu_i\\
b_i &= -\frac{1}{2}\boldsymbol \mu_i^T \boldsymbol \Sigma^{-1} \boldsymbol \mu_i + \log P(C_i)
\end{align*}$$
In the case of two classes, we define $y\equiv P(C_1|\mathbf x)$, we
$$
\text{choose } C_1 \text{ if } y > 0.5\text{ and }C_2\text{ otherwise}
$$
We now want to use the logit transformation on $y$:
$$
\text{logit}(y) \equiv \log\left(\frac{y}{1-y}\right)
$$
It is the difference between the log posterior between the cases. In our case, logit is linear:
$$\begin{align*}
\text{logit}(y) &= \log \frac{y}{1-y}\\
&=\log \frac{p(\mathbf x|C_1)}{p(\mathbf x|C_2)} + \log\frac{P(C_1)}{P(C_2)}\\
&=\log \frac{
    (2\pi)^{-d/2}|\boldsymbol\Sigma|^{-1/2} \exp\left[-(1/2)(\mathbf x-\boldsymbol\mu_1)^T\boldsymbol \Sigma^{-1}(\mathbf x-\boldsymbol\mu_1)\right]
  }{
    (2\pi)^{-d/2}|\boldsymbol\Sigma|^{-1/2} \exp\left[-(1/2)(\mathbf x-\boldsymbol\mu_2)^T\boldsymbol \Sigma^{-1}(\mathbf x-\boldsymbol\mu_2)\right]} + \log\frac{P(C_1)}{P(C_2)}\\
&=\log \frac{\exp\left[-(1/2)(\mathbf x-\boldsymbol\mu_1)^T\boldsymbol \Sigma^{-1}(\mathbf x-\boldsymbol\mu_1)\right]}{\exp\left[-(1/2)(\mathbf x-\boldsymbol\mu_2)^T\boldsymbol \Sigma^{-1}(\mathbf x-\boldsymbol\mu_2)\right]} + \log\frac{P(C_1)}{P(C_2)}\\
&=-(1/2)\left[(\mathbf x-\boldsymbol\mu_1)^T\boldsymbol \Sigma^{-1}(\mathbf x-\boldsymbol\mu_1)-(\mathbf x-\boldsymbol\mu_2)^T\boldsymbol \Sigma^{-1}(\mathbf x-\boldsymbol\mu_2)\right] + \log\frac{P(C_1)}{P(C_2)}\\
&=-(1/2)\left[
  -2\mathbf x^T \boldsymbol \Sigma^{-1} (\boldsymbol\mu_1- \boldsymbol\mu_2) + \boldsymbol\mu_1^T \Sigma^{-1} \boldsymbol\mu_1 - \boldsymbol\mu_2^T \Sigma^{-1} \boldsymbol\mu_2
\right] + \log\frac{P(C_1)}{P(C_2)}\\
&=g_1(\mathbf x)-g_2(\mathbf x)
\end{align*}$$
This means we can use $g_i(\mathbf x)$ to predict $P(C_i|\mathbf x)$:
$$\begin{align*}
\text{logit}(P(C_i|\mathbf x)) &= \mathbf w_i \cdot \mathbf x + b_i\\
P(C_i|\mathbf x) &= \text{logit}^{-1}(\mathbf w_i \cdot \mathbf x + b_i)\\
\end{align*}$$
The inverse of logit function is sigmoid function:
$$\begin{align*}
\log \frac{y}{1-y}&=x\\
\frac{y}{1-y}&=\exp(x)\\
y&=\exp(x)-y\exp(x)\\
(1+\exp(x))y&=\exp(x)\\
y&=\frac{\exp(x)}{1+\exp(x)}\\
y&=\frac{1}{1+\exp(-x)}\\
\end{align*}$$

Now generalize this to multi class cases. Using the previous Gaussian assumption, we get:
$$\begin{align*}
\log \frac{P(C_i|\mathbf x)}{P(C_j|\mathbf x)} &=
{\mathbf x^T \boldsymbol \Sigma^{-1} (\boldsymbol\mu_i- \boldsymbol\mu_j) \\
- \frac 12 \boldsymbol\mu_i^T \Sigma^{-1} \boldsymbol\mu_i + \frac 12 \boldsymbol\mu_j^T \Sigma^{-1} \boldsymbol\mu_j \\
+ \log P(C_i) - \log P(C_j)}\\
\end{align*}$$
It looks like it can be writen as the difference of two linear functions $g_i$ and $g_j$,  and
$$\begin{align*}
g_i(\mathbf x) &= \log P(C_i|\mathbf x) + C\\
\end{align*}$$
for some constant $C$. From there
$$\begin{align*}
\exp(g_i(\mathbf x)) &= \exp(C) P(C_i|\mathbf x)\\
\sum_i \exp(g_i(\mathbf x)) &= \exp(C) \\
C &= \log \sum_i \exp(g_i(\mathbf x)) \\
P(C_i|\mathbf x) &= \frac{\exp(g_i(\mathbf x))}{\sum_i \exp(g_i(\mathbf x))}
\end{align*}$$
This is called the **_softmax function_**.
> Node: We don't need to compute and plugin the constant $C$ when we compute this function, because softmax function is translate invariant. In fact, in most of the cases, we don't even need to evaluate the posterior. When it does, however, we need to compute the exponential function of some potentially big number $g_i$ and cause numerical issues (say, $\infty / \infty$ issue). For this, we can instead shift all the values down by the maximum number among $g_i$. Then we will only deal with numbers between $0$ and $1$.