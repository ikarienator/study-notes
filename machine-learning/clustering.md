Machine Learning Study Node - Clustering

[Back to Intro](/read.php?page=machine-learning/intro)

In parameteric approaches, we assume the samples are drawn from the a same parametric distribution. This is rarely the case. Now we relax this assumption and assume the samples are from one of a number of distributions.

This approach is called semiparametric density estimation.

### Mixture densitie

The **_mixture density_** is defined as
$$
p(\mathbf x) = \sum_{i=1}^k p(\mathbf x|\mathcal G_i)P(\mathcal G_i)
$$

where $\mathcal G_i$ are the **_mixture components_**. They are also called **_clusters_**. $p(\mathbf x|\mathcal G_i)$ are called **_component densities_** and $P(\mathcal G_i)$ are called **_mixture proportions_**. The number of parameters $k$ is a hyperparameter.

Within each cluster is a parameteric distribution. The samples are assumed to be iid.
