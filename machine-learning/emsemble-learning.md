Machine Learning Study Note - Ensemble learning

[Back to Intro](/read.php?page=machine-learning/intro)

The [No Free Lunch Theorem](https://en.wikipedia.org/wiki/No_free_lunch_theorem) states that there is no single learning algorithm that in any domain always induces the most accurate learner. If we have multiple leaners at hand, if we combine them properly the accuracy can be improved.

Two questions:

1. How do we generate base-learners that complement each other?
2. How do we combine the outputs of base-learners for maximum accuracy?

Our discussion in this chapter will answer these two related questions. We will see that model combination is not a trick that always increases accuracy.

### Model Combination Schemes
1. **_Multiexpert combination_** where base learners work in parallel. Two cases:

  a. **_global_** approach, also called **_learner fusion_**. All base learners gives an output and all the outputs are used.
  a. **_local_** approach, also called **_leaner selection_**. For example, in **_mix of experts_**, there is a **_gating_** model, which looks at the input and chooses one or very few base learners.

1. **Multistage combination** uses a **_serial_** approach the next base-learner is tested/trained with only the intances that the previous learner is not confident about. An example is **_cascading_**.

### Voting

The simplest way to combine multiple classifiers is by **_voting_**, which is a linear combination of the learners:
$$
y_i = \sum_j w_jd_{ji}\text{ where }w_j\geq0,\sum_j w_j=1
$$

This is also known as **_ensembles_** and **_linear opinion pools_**. Linear combination is not the only possiblity. Other rules include:

1. Average
$$
y_i=\frac{1}{L}\sum_j^Ld_{ji}
$$
1. Weighted Sum
$$
y_i = \sum_j w_jd_{ji}\text{ where }w_j\geq0,\sum_j w_j=1
$$
1. Median
$$
y_i = \text{median}_jd_{ji}
$$
1. Minimum
$$
y_i = \text{min}_jd_{ji}
$$
1. Maximum
$$
y_i = \text{max}_jd_{ji}
$$
1. Product
$$
y_i = \prod_jd_{ji}
$$

If the outputs are not posterior probabilities, these rules require that outputs be normalized to the same scale.

The simple voting is a special case where all voters have equal weight. In classification, this is called **_plurality voting_** wher the class having the maximum number of votes is the winner.

Weight sum schemes can be seen as approximations under a Bayesian framework with weights approximating prior model probabilities. This is **_Bayesian model combination_**. In classification we have $w_j\equiv P(M_j)$, $d_{ji}=P(C_i|x,M_j)$, and ti becomes
$$
P(C_i|x)=\sum_j P(C_i|x,M_j) P(M_j)
$$

### Bagging

**_Bagging_** (**_Bootstrap aggregating_**) is a voting method whereby base-learners are made different by training them over slightly different training sets. Normally, we draw samples with replacement in this task, that is, some instances will be used more than one times. A learning algorithm is an **_unstable algorithmm_** if small changes in the training set causes a large difference in the generated learner. Bagging generates $L$ slightly different training sets to train $L$ base-learners using an unstable learning procesure, and then, during testing, takes an average. For robustness, in the case of regression, one can take the median instead.

Decision trees and MLPs are unstable, nearest neighbor is stable, but condensed nearest neighbor is unstable. If the training set is large, we may want to generate training sets of smaller sizes.

### Boosting

In bagging, we generate complementary base-learners by diviersify the training data. In boosting, we actively try to generate complementary base-learners by training the next learner on the mistakes of the previous learners.

The original boosting algorihtm was proposted in 1990 by Schapire. Given 3 weak learners, we can train a strong learner. A weak learner has error probability less than $1/2$. A strong learner has arbitrarily small error probability. It goes like this:

1. (Given 3 weak leaners $\chi_1$, $\chi_2$, $\chi_3$.)
1. Split the training set to 3 subsets $d_1$, $d_2$, $d_3$.
1. Train $\chi_1$ on $d_1$.
1. Feed $\chi_2$ to the trained $d_1$.
1. Train $d_2$ with all the misidentifierd instances in the previous step and some correct instances.
1. Feed $\chi_3$ to $d_1$ and $d_2$.
1. Feed the misidentified instances and train $d_3$.

During the test, we call $d_1$ and $d_2$. If they agree, that is the result. Otherwise we return the response of $d_3$.

#### AdaBoost

In 1996, Freund and Schapire proposed a variant, named **_AdaBoost_** (addaptive boosting). That uses the same training set over and over and thus need not to be large, but the classifiers should be simple so that they do not overfit. The following is a variant of AdaBoost called AdaBoost.M1:

Training

1. For each base learner $j$
  1. Randomly draw $\chi_j$ from $\chi$ with probabilities $p_j^t$.
  1. Train $d_j$ using $\chi_j$
  1. For each $(x^t, r^t)$, calculate $y^t\gets d_j(x^t)$
  1. Calculate error rate: $\epsilon_j \gets \sum_j p_j^t \boldsymbol 1(y^t\neq r^t)$
  1. if $\epsilon_j > 1/2$, weak learner assumption is violated
  1. $\beta_j \gets \epsilon_j/(1-\epsilon_j)$
  1. for each $(x^t, r^t)$, reduce the probability of correctly classified samples
     $$p_{j+1}^t \gets \beta_j^{\boldsymbol 1(y^t = r^t)} p_j^t$$
  1. Normalize probability
    $$\begin{align*}
      Z_j &= \sum_t p_{j+1}^t\\
      p_{j+1}^t &= p_{j+1}^t / Z_j
    \end{align*}$$

Testing:

$$
y_i = \sum_j^L -\log \beta_i d_{ji}(x)
$$

The success of AdaBoost is due to its property of increasing the margin. If the margin increases, the training instances are better separated and error is less likely. This makes AdaBoosts's aim similar to that of support vector machines.

