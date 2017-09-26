Machine Learning Study Note - Kernel Machines

[Back to Intro](/read.php?page=machine-learning/intro)

Kernel machines are maximum margin methods that allow the model to be written as a sum of the influences of a subset of the training instances.

### Support Vector Machine - Introduction

Support vector machines (SVMs) is a kernel machine. It has been popular because:

1. It is a discriminant-based method and uses Vapnik’s principle to never solve a more complex problem as a first step before the actual problem.
2. After training, the parameters can be written down as a subset of training set, which are called _support vectors_.
3. The output is written as a sum of influences of support vectors and theses are given by _kernel functions_ that are application-specific measures of similarity between data instances.
4. Typically data points are represented as vectors, and either dot product or Euclidean distance is used. A kernel function allowes us to go beyond that.
5. Kernel-based algorithms are formulated as convex optimization problems, and there is a single optimum that we can solve for analytically.

### Optimal Separating Hyperplane

Let's start with two classes and use lables $-1/+1$ for the each class. The sample is $\mathcal X = \{(x^t,r^t)\}^N$ where $r^t = 0, 1$. We would like to find $\mathbf w$ and $b$ such that
$$\begin{align*}
\mathbf w^T \mathbf x^t + b \geq +1&\text{ for }&r^t=+1\\
\mathbf w^T \mathbf x^t + b \leq -1&\text{ for }&r^t=-1\\
\end{align*}$$
which can be rewritten as
$$
r^t(\mathbf w^T \mathbf x^t+b)\geq+1
$$
Not only do we want the instances to be on the right side of the hyperplane, but we also want them some distanc away, for better generalization. This forms a _optimal separating hperplane_. Thus we would like to maximize some value $\rho$
$$
\rho\equiv\min_t\frac{r^t(\mathbf w^T\mathbf x^t+b)}{\|\mathbf w \|}
$$

We want to maximize $\rho$ but there are an infinite number of solutions that we can get by scaling $\mathbf w$ and for a unique solution, we need to fix $\rho\|\mathbf w\|=1$ and thus, to maximize the margin, we minimize $\|\mathbf w\|$. The task can therefore be defined as to
$$
\min \|\mathbf w\|\text{ subject to } \min_t \mathbf r^t(\mathbf w^T\mathbf x^t+b) \geq +1
$$

This needs to be generalized when the problem is not linearly separable. One way to do that is to increase the number of parameters. We are interested in a methods whose complexity does not depend on the input dimensionality.

To get the new formulation, we plugin $N$ Lagrange multipliers $\alpha^t$:
$$\begin{align*}
L_p&=\frac{1}{2}\|\mathbf w\|^2 -\sum_t \alpha^t\left[r^t(\mathbf w^T x^t+b)-1\right]\\
&=\frac{1}{2}\|\mathbf w\|^2 -\sum_t \alpha^tr^t(\mathbf w^T x^t+b) + \sum_t \alpha^t
\end{align*}$$
This should be optimized with respect to $\mathbf w$, $b$ and maximized with respect to $\alpha_t$.

This is a convex quadratic optimization problem therefore we can equavalently solve the dual problem making use of the Karush-Huhn-Tucker conditions. The dual is to maximize $L_p$ with respect to $\alpha^t$, subject to the constraints that the gradient of $L_p$ with respect to $\mathbf w$ and $b$ are $0$, and also that $\alpha^t\geq0$:
$$
\frac{\partial L_p}{\partial \mathbf w}=0 \implies \mathbf w = \sum_t \alpha^t r^t \mathbf x^t
$$
$$
\frac{\partial L_p}{\partial b}=0 \implies \sum_t \alpha^t r^t = 0
$$
there fore we get the dual
$$\begin{align*}
L_d &= \frac{1}{2}\mathbf w^t\mathbf w - \mathbf w^t \sum_t \alpha^tr^t\mathbf x^t - b \sum_t \alpha^t r^t + \sum_t \alpha^t\\
&= - \frac{1}{2}\mathbf w^t\mathbf w + \sum_t \alpha^t\\
&= - \frac{1}{2}\left(\sum_t \alpha^t r^t\mathbf x^t\right)^T\left(\sum_t \alpha^t r^t\mathbf x^t\right)+ \sum_t \alpha^t\\
&= - \frac{1}{2}\sum_t\sum_s\alpha^s\alpha^tr^sr^t{\mathbf x^s}^T{\mathbf x}^t+ \sum_t \alpha^t\\
\end{align*}$$

This is a quadratic optimization problem, it can be solved in $\mathcal O(N^3)$ time. Once we solve for $\alpha^t$, we see that though there are $N$ of them, most vanish with $\alpha^t=0$ and only a small percentage have $\alpha^t > 0$. The set of $\mathbf x^t$ whose $\alpha^t >0$ are the _support vector_s. These are the $\mathbf x^t$ that satisfy
$$
r^t(\mathbf w^T \mathbf x^t + b) = 1
$$
and lie on the margin. We can use this fact to calculate $b$ from any support vector as
$$
b^t = r^t-\mathbf w^T \mathbf x^t
$$
The eventual bias will be the average of $b^t$ over the support vectors. The discriminant thus found is called the _support vector machine_.

Being a discriminant-based method, the SVM cares only about the instances close to the boundary and discards those that lie in the interior. Using this idea, it is possible to use a simpler classifier before the SVM to filter out a large portion of such instances, thereby decreasing the complexity of the optimization step of the SVM.

### The Nonseparable Case: Soft Margin Hyperplane

If the data is not linearly separable, we look for the one
that incurs the least error.

Define _slack variable_s, $\xi^t \geq 0$ which store the deviation from the margin. Relaxing our condition, we require
$$
r^t(\mathbf w^T \mathbf x^t + b) \geq 1 - \xi^t
$$
$$
\xi^t = \max(0, 1 - r^t(\mathbf w^T \mathbf x^t + b))
$$

If $0<\xi^t<1$, $\mathbf x^t$ is correctly classified but in the margin. If $\xi^t \geq 1$, $\mathbf x^t$ is misclassified. We define _soft error_ as
$$
\sum_t \xi^t
$$
and add this as a penalty term:
$$
L_p=\frac{1}{2}\|\mathbf w\|^2+C\sum_t \xi^t
$$
$C$ is a hyperparameter. Adding the constraints, the Lagrangian becomes:
$$
L_p=\frac{1}{2}\|\mathbf w\|^2+C\sum_t \xi^t - \sum_t \alpha^t[r^t(\mathbf w^T \mathbf x^t +b) - 1 + \xi^t] -  \sum_t \mu^t\xi^t
$$
where $\mu^t$ are the new Lagrange multipliers to guarantee the positivity of $\xi^t$. Optimize the Lagrangian
$$\begin{align*}
\frac{\partial L_p}{\partial \mathbf w}&=\mathbf w - \sum_t\alpha^tr^t\mathbf x^t=0 \implies \mathbf w = \sum_t \alpha^t r^t \mathbf x^t\\
\frac{\partial L_p}{\partial b}&=\sum_t\alpha^tr^t\mathbf=0\\
\frac{\partial L_p}{\partial \xi^t}&=C-\alpha^t-\mu^t=0\\
\end{align*}$$
The last implies $0\leq\alpha^t\leq C$. The dual problem:
$$
L_d=\sum_t \alpha^t - \frac{1}{2}\sum_t\sum_s\alpha^t\alpha^sr^tr^s(x^t)^Tx^s
$$
subject to
$$
\sum_t\alpha^tr^t=0\text{ and }0\leq \alpha^t \leq C
$$

The support vectors are those whose $\alpha^t >0$ and we use those whose $\alpha^t < C$ to calculate $b$ since they have $\xi^t = 0$.

It is shown that the expected test error rate is
$$
E_N[P(error)] \leq \frac{E_N[\text{# of support vectors}]}{N}
$$

The definition implies that we define error if the instance is on the wrong side or if the margin is less than $1$. This is called the **_hinge loss_**. If $y^t=\mathbf w^T \mathbf x^t+b$ is the output and $r^t$ is desired output, hinge loss is defined as
$$
L_\text{hinge}(y^t, r^t)=\begin{cases}
0 &\text{if }y^t r^t \geq 1\\
1 -y^t r^t &\text{otherwise}
\end{cases}
$$

$C$ is the regularization parameter. When $C$ is high, we have a high penalty for nonseparable points, and we may store many support vectors and overfit. If it is too small, we may find too simple solution that underfit. Typically, one choose from log scale by looking at the accuracy on a validation set.

### Kernel Trick
In order to solve a non-linear problem, we can map the problem to a new space by doing nonlinear transformation using suitably chose basis functions and then use a linear model in this new space. The linear model in the new space corresponds to a nonlinear model in the oriignal space.

Let us say we have the new dimensions calculated through the basis functions
$$
\mathbf z = \boldsymbol \phi(\mathbf x)\text{ where }z_j=\phi_j(\mathbf x), j= 1,...,k
$$
mapping form the $d$-dimensional $\mathbf x$ space to the $k$-dimensional $\mathbf z$ space where we write the discriminant as
$$\begin{align*}
g(\mathbf z) &= \mathbf w^T\mathbf z \\
g(\mathbf x) &= \mathbf w^T\boldsymbol\phi(\mathbf x) \\
&=\sum_{j=1}^{k} w_j \phi_j(\mathbf x)
\end{align*}$$
The dual Lagrangian is then
$$
L_d = \sum_t \alpha^t - \frac{1}{2}\sum_t\sum_s\alpha^t\alpha^sr^tr^s\boldsymbol\phi(x^t)^T\boldsymbol\phi(x^s)
$$

The kernel trick is to replace $\boldsymbol \phi(x^t)^T\boldsymbol \phi(x^s)$ with a **_kernel function_** $K(\mathbf x^t, \mathbf x^s)$. This implies that if we have the kernel function, we do not have to map the vector to another space. The kernel function also shows up in the discriminant
$$\begin{align*}
g(\mathbf x) &= \mathbf w^T \boldsymbol \phi(\mathbf x) \\
&= \sum_t \alpha^t r^t \boldsymbol \phi(\mathbf x^t)^T \boldsymbol \phi(\mathbf x) \\
&= \sum_t \alpha^t r^t K(\mathbf x^t, \mathbf x) \\
\end{align*}$$

Furthermore, for any valid kernel, there exists a corresponding mapping function, but it may be much simpler to use the kernel than calculating the mapping and take the dot product. Many algorithms have be kernelized, as we will see in the later sections.

### Vectorial Kernels

The mose popular, general-purpose kernel functions are

1. polynomial of degree $q$
$$
K(\mathbf x, \mathbf y) = (\mathbf x \cdot \mathbf y + 1) ^ q
$$
In the case of $\mathbf x \in \mathbb R^2$, it corresponds to the basis function
$$
\boldsymbol \phi(\mathbf x) = [1, \sqrt{2}x_1, \sqrt{2}x_2, \sqrt{2}x_1x_2,x_1^2,x_2^2]^T
$$
When $q=1$, it corresponds to the original formulation.
1. radial-based functions
$$
K(\mathbf x, \mathbf y) = \exp\left[-\frac{\|\mathbf x-\mathbf y\|^2}{2s^2}\right]
$$
One can have a Mahalanobis kernel, generalized from the Euclidean distance:
$$
K(\mathbf x, \mathbf y) = \exp\left[-\frac{1}{2}(\mathbf y-\mathbf x)^T\mathbf S^{-1}(\mathbf y-\mathbf x)\right]
$$
where $\mathbf S$ is the covariance matrix
$$
\mathbf S = E\left[(\mathbf x - E[\mathbf x])(\mathbf x - E[\mathbf x])^T\right]
$$
Or, in the most general case,
$$
K(\mathbf x, \mathbf y) = \exp\left[-\frac{\mathcal D(\mathbf x, \mathbf y)}{2s^2}\right]
$$
where $\mathcal D$ is some general distance function.
2. sigmoidal functions:
$$
K(\mathbf x, \mathbf y) = \tanh(\mathbf x \cdot \mathbf y + 1)
$$
This has the same shape as sigmoid functions except it ranges between $-1$ and $+1$. It is similar to MLPs.

### Multiple Kernel Learning

It is possible to construct new kernels by combining simpler kernesl. If $K_1(\mathbf x,\mathbf y)$ and $K_2(\mathbf x,\mathbf y)$ are kernels, and $c$ a constant, then $cK_1$, $K_1 + K_2$, $K_1\cdot K_2$ are also valid. Given multiple models, you can also combine them by direct product. If $K_A(\mathbf x_A,\mathbf y_A)$ and $K_B(\mathbf x_B,\mathbf y_B)$ are kernels in space $A$ and $B$, then you can construct a kernel in space $A \times B$, for example,
$$
K_{A\times B}([\mathbf x_A, \mathbf x_B], [\mathbf y_A, \mathbf y_B]) = K_A(\mathbf x_A, \mathbf y_A) + K_B(\mathbf x_B, \mathbf y_B)
$$
We can generalize it to a number of kernels
$$
K(\mathbf x, \mathbf y) = \sum_{i=1}^{m}K_i(\mathbf x, \mathbf y)
$$
which works as similar to an average of kernels. It is also possible to use a weighted sum and also learn the weights from data:
$$
K(\mathbf x, \mathbf y) = \sum_{i=1}^{m}\eta_iK_i(\mathbf x, \mathbf y)
$$
subject to $\eta_i \geq 0$, with or without the constaint of $\sum_i \eta_i = 1$ (simplex constraint). This is called multiple kernel learning. The objective becomes
$$
L_d = \sum_t \alpha^t - \frac{1}{2}\sum_t\sum_s \alpha^t \alpha^s r^t r^s \sum_i \eta_i K_i(\mathbf x^t, \mathbf x^s)
$$

After training, $\eta_i$ will take values depending on how the corresponding kernel $K_i(\mathbf x^t, \mathbf x)$ is useful in discriminating. It is also possible to localize kernels by defining kernel weights as a parameterized function of the input $\mathbf x$, rather like the gating function in mixture of experts
$$
g(\mathbf x) = \sum_t \alpha^ir^i\sum_i \eta_i(\mathbf x|\theta_i)K_i(\mathbf x^t, \mathbf x)
$$

and the gating parameters $\theta_i$ are learned together with the support vector machine parameters.

### Kernel Machines for Regression

We start with a linear model
$$
f(\mathbf x) = \mathbf w \cdot \mathbf x + b
$$

We use the square of the difference as error
$$
e_2(r^t, f(\mathbf x^t)) = [r^t-f(\mathbf x^t)]^2
$$
whereas in support vector regression, we use the $\epsilon$-sensitive loss function:
$$
e_\epsilon(r^t, f(\mathbf x^t)) = \begin{cases}
0&\text{if }|r^t-f(\mathbf x^t)|<\epsilon\\
|r^t-f(\mathbf x^t)|-\epsilon&\text{otherwise}\\
\end{cases}
$$
means we tolerate errors up to $\epsilon$ and also that errors beyond have a linear loss and not a quadratic one. As in the hinge loss, there is a region of no loss.

Similar to classification, we introduce slack variables to account for deviations out of the $\epsilon$-zone and we get
$$
\min \frac{1}{2}\|w\|^2+C\sum_t(\xi_+^t+\xi_-^t)
$$
subject to
$$\begin{align*}
r^t − (\mathbf w \cdot \mathbf x + b) &\leq \epsilon + \xi_+^t \\
(\mathbf w \cdot \mathbf x + b) -r^t &\leq \epsilon + \xi_-^t\\
\xi_+^t &\geq 0\\
\xi_-^t &\geq 0\\
\end{align*}$$

We use two types of slack variables, one for positive and one for negative deviations. The lagrangian is
$$
L_p = {\frac{1}{2}\|\mathbf w\|^2 + C\sum_t(\xi_+^t+\xi_-^t)\\
-\sum_t \alpha_+^t \left[\epsilon + \xi_+^t - r^t + (\mathbf w \cdot \mathbf x + b)\right]\\
-\sum_t \alpha_-^t \left[\epsilon + \xi_-^t + (\mathbf w \cdot \mathbf x + b) - r^t\right]\\
-\sum(\mu_+^t\xi_+^t+\mu_-^t\xi_-^t)
}
$$
taking the derivatives
$$\begin{align*}
\frac{\partial L_p}{\partial \mathbf w} &= \mathbf w + \sum_t(\alpha_+^t-\alpha_-^t)\mathbf x^t = 0 \implies \mathbf w = \sum_t(\alpha_+^t-\alpha_-^t)\mathbf x^t\\
\frac{\partial L_p}{\partial b} &= \sum_t(\alpha_+^t-\alpha_-^t) = 0 \\
\frac{\partial L_p}{\partial \xi_+^t} &= C - \alpha_+^t - \mu_+^t = 0 \\
\frac{\partial L_p}{\partial \xi_-^t} &= C - \alpha_-^t - \mu_-^t = 0 \\
\end{align*}$$
The dual is
$$\begin{align*}
L_d = {-\frac{1}{2}\sum_t\sum_s (\alpha_+^t-\alpha_-^t)(\alpha_+^s-\alpha_-^s) \mathbf x^t\cdot \mathbf x^s \\
-\epsilon \sum_t (\alpha_+^t+\alpha_-^t)-\sum_t r^t(\alpha_+^t-\alpha_-^t)}
\end{align*}$$
subject to
$$
0\leq\alpha_+^t\leq C,0\leq\alpha_-^t\leq C,\sum_t (\alpha_+^t-\alpha_-^t)=0
$$
Once we solve this, we see that all instances that fall in the tube have $\alpha_+^t=\alpha_-^t=0$. There are the instances that are fitted with enough precision. The support vectors satisfy either $\alpha_+^t >0$ or $\alpha_-^t >0$ and are of two types.

Eventually, the fitted function is a weighted sum of the support vectors
$$
f(\mathbf x) = \sum_t(\alpha_+^t-\alpha_-^t)\mathbf x^t\cdot \mathbf x + b
$$