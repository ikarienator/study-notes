Machine Learning Study Note - Decision Tree

[Back to Intro](/read.php?page=machine-learning/intro)

## Decision Tree

It is a classic and natural model of learning. Closely related to the notion of "divide and conquer".
Decision tree A tree structure that on each non-leaf node, there is a binary predicate that test the data, The delegate the computation to one of the sub-tree base on this predication. When we reached to leaf node, returns the result.

## Univariate Trees

In a univariate tree, in each internal node, the test uses only one of the input dimensions. Tree learning algorithms are greedy and, at each step, starting at the root with the complete training data, we look for the best split. We then continue splitting recursively
with the corresponding subset until we do not need to split anymore, at which point a leaf node is created and labeled.

### Classification Trees

The goodness of the split is quantified by an *impurity measure*.
A split is pure if after the split, all the instances choosing a branch belong to the same class. Given node $m$, $N_m$ is the number of training instances reaching node $m$. For the root, it is $N$. Let $N^i_m$ of $N_m$ belong to class $\mathcal C_i$, with $\sum_i N^i_m = N_m$. The probablity of class $\mathcal C_i$ given an instance $x$ reaches node $m$ is:

$$
\hat P\left(\mathcal C_i\mid x, m\right)\equiv p^i_m = \frac{N^i_m}{N_m}
$$

Node $m$ is pure if $p^i_m$ for all $i$ are either 0 or 1. One possbile measure is *entropy* $\Phi_S$:

$$\begin{align*}
\mathcal I_m = \Phi_S(\{p^i_m\}^n) &= - \sum_i^n p^i_m \log p^i_m \\
&= - \sum_i^n \frac{N^i_m}{N_m} \log \frac{N^i_m}{N_m} \\
&= - \sum_i^n \frac{N^i_m}{N_m} \left(\log N^i_m - \log N_m\right) \\
&= - \sum_i^n \left(\frac{N^i_m}{N_m} \log N^i_m - \frac{N^i_m}{N_m} \log N_m\right) \\
&= \log N_m - \frac{1}{N_m} \sum_i^n N^i_m \log N^i_m \\
\end{align*}$$

where $0 \log 0 \equiv 0$ (Indeed, $\lim_{x\to 0}x\log x = 0$). In general, $\Phi(p, 1-p)$ is a valid measurement if:

1. $\Phi(\{p^i\}^n) \geq 0$. $\{p^i\}^n_{i=1}$ or simply $\{p^i\}^n$ means $\{p^1, p^2, ... p^n\}$.
1. $\forall \{p^i\}^n \in \mathbb R^n$ and $\sum p^i = 1$, $\Phi(\{1/n\}^n) \geq \Phi(\{p^i\}^n)$, or in other words, uniform distribution has maximum entropy.
1. $\forall j, \Phi(\{\delta^i_j\}^n) = 0$, or in other words, deterministic events have zero entropy.

Examples are:

1. Entropy
$$
\Phi_S(\{p^i\}^n) = \mathbb E[-\log(p^i)]
$$

2. [Gini impurity](https://en.wikipedia.org/wiki/Decision_tree_learning#Gini_impurity)
$$
\Phi_G(\{p^i\}^n) = \mathbb E[1-p^i] = \sum_{i=1}^n p^i (1 - p^i) = 1 - \sum_{i=1}^n (p^i)^2
$$

3. Misclassification error
$$
\Phi_M(\{p^i\}^n) = 1 - \max(\{p^i\}^n)
$$

Research has shown that there is not a significant difference between these three measures.

If node $m$ is not pure, then it should be split to increase purity.
We look for the split that minimizes the impurity after the split. This is locally minimal and we have no guarantee of finding purest decision tree.

Let $N_{m\to j}$ be the number of training instances that take branch $j$ after a split, then
$$\begin{align*}
\sum_{j=1}^n N_{m\to j} &= N_m \\
\sum_i^K N^i_{m\to j} &= N_{m\to j} \\
\sum_j^n N^i_{m\to j} &= N_m^i\,. \\
\end{align*}$$
The total impurity after the split is
$$\begin{align*}
\mathcal I'_m &= - \sum_j^n \frac{N_{m\to j}}{N_m} \sum_i^K \frac{N^i_{m\to j}}{N_{m\to j}} \log \frac{N^i_{m\to j}}{N_{m\to j}} \\
&= \sum_j^n \frac{N_{m\to j}}{N_m} \left(\log N_{m\to j} - \frac{1}{N_{m\to j}}\sum_i^K N^i_{m\to j} \log N^i_{m\to j}\right) \\
&= \sum_j^n \frac{N_{m\to j}}{N_m} \log N_{m\to j} - \sum_j^n \frac{N_{m\to j}}{N_m} \frac{1}{N_{m\to j}}\sum_i^K N^i_{m\to j} \log N^i_{m\to j} \\
&= \frac{1}{N_m}\sum_j^n N_{m\to j} \log N_{m\to j} - \frac{1}{N_m}\sum_j^n \sum_i^K N^i_{m\to j} \log N^i_{m\to j} \\
&= \Phi_S(\{p_{m\to j}^i\}_{j,i}^{n,K}) - \Phi_S(\{p_{m\to j}\}_j^n) \\
\end{align*}$$

Therefore, the new entropy is entropy of the subdivided cases minus the entropy of the subdivision itself.

We thus obtained an algorithm to generate a decision tree:

```python
theta_i     # hyper paramater on complexity, or the maximum impurity of a leaf
attributes  # the attribute[i](x) on the ith attribute of sample x

def generateTree(samples):
  if entropy(samples) < theta_i:
    return Leaf(mode(samples))

  split, subdivisions = splitAttribute(samples)
  node = Internal(split)
  for subdivision in subdivisions:
    node.children.append(generateTree(subdivision))

def splitAttribute(samples):
  minEntroy = math.inf
  for attribute in attributes:
    if attribute is DiscreteAttribute:
      subdivisions = # subdivide samples by attribute[i]
      e = splitEntropy(subdivision, len(samples))
      if e < minEntroy:
        minEntroy = e
        result = (attribute, subdivisions)
    else: # attribute is continous
      splits = # find all possible splits
      for split in splits:
        subdivisions = # subdivide samples by split
        e = splitEntropy(subdivision, len(samples))
        if e < minEntroy:
          minEntroy = e
          result = (attribute, subdivisions)

  return result
```

This is the basis of the _Classification and Regression Trees_ (CART), ID3, and C4.5.
This method has bias towards discrete values with many values, which has lower entropy.

When there is noise, the tree may easily overfit. Therefore a $\theta_I$ hyperparameter is added to prevent over-splitting.

Some times the posterior probabilities of each class is stored in the leaf instead of the maximal likely class.

### Regression Trees
A regression tree is constructed in the same manner, except that the impurity measure is replaces with regression loss.

Let $r(x)$ be the supervision of sample $x$.

Let ${X_m}$ be the training instances that reached m, $N_m \equiv |X_m|$

Let $g_m$ be the mean (or median if too noisy) supervision reached node $m$:
$$
g_m = \frac{\sum_{x\in X_m} r(x)}{N_m}
$$

The "urge" of a split is measured by mean square error from the estimated value:
$$
E_m = \frac{\sum_{x\in X_m} (r(x) - g_m)^2}{N_m}
$$

If $E_m$ is acceptable, we create a leaf node and stores $g_m$ on the node. Otherwise we split.
Let $\{X_{m\to j}\}^n$ be a subdivision of ${X_m}$, accordingly:
$$\begin{align*}
N_{m\to j} &= |X_{m\to j}|\\
g_{m\to j} &= \frac{\sum_{x \in X_{m\to j}} r(x)}{N_{m\to j}} \\
E_{m\to j} &= \frac{\sum_{x \in X_{m\to j}} \left(r(x) - g_{m\to j}\right)^2}{N_{m\to j}} \\
\end{align*}$$
The new loss
$$
E'_m = \sum_j E_{m\to j} = \frac{1}{N_m}\sum_j \sum_{x \in X_{m\to j}} \left(r(x) - g_{m\to j}\right)^2
$$

In a more advanced model, $g_m$ could be in fact a function about $x$:
$$
g_m(x) = \mathbf w_m{}^T x + b_m,
$$
and the tree will store $\mathbf w_m$ and $b_m$ instead.

### Pruning
Frequently, the stopping condition on splitting is based on the number of reached instances. The idea is that any decision based on too few instances causes variance. Stopping tree construction early is called _prepruning_ the tree.

Another possiblity to get simpler trees is _postpruning_, which in practice works bettern than prepruning.

> My thought: Because this is when we can use global information to adjust the model.

In postpruning we holdout a part of the training set as "pruning set". Then we grow the tree with rest of the training set until all leaves are pure and we have no training error. Then we use the pruning set to find subtrees that cause overfitting and prune them by replacing the subtree with a leaf node if the performance of the leaf node is comparable to the subtree on the pruning set.