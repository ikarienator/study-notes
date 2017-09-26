Machine Learning Study Node - Association Rules

[Back to Intro](/read.php?page=machine-learning/intro)

## Association Rules

An _association rule_ is a implication of the form $X \to Y$ where $X$ is the _antecedent_ and $Y$ is the _consequence_ of the rule. One example of assoc rules is in _market basket analysis_ where we want to find the dependency between two items $X$ and $Y$ in a market.

_Association rule learning_ is a method for discovering intersting relations between variables in large databases. It is intended  to identify strong rules discovered in databases using some measures of interstingness.

These three measures are frequently calculated:

1. _Support_ of the association rule $X \to Y$:
$$
\text{Support}(X, Y)\equiv P(X, Y) =
\frac{\#[\text{customers who bought }X\text{ and }Y]}{\#[\text{customers}]}
$$
2. _Confidence_ of the association rule $X \to Y$:
$$
\text{Confidence}(X\to Y)\equiv P(Y|X) =
\frac{\#[\text{customers who bought }X\text{ and }Y]}{\#[\text{customers who bought }X]}
$$
3. _Lift_ of the association rule $X \to Y$:
$$
\text{Lift}(X\to Y)\equiv P(Y|X) =
\frac{\#[\text{customers who bought }X\text{ and }Y]}{\#[\text{customers who bought }X]}
$$

Confidence is the conditional probability, which is what we normally calculate. To be able to say that the rule holds with enough confidence, this value should be close to $1$ and significantly larger than $P(Y)$. We are also interested in maximizing the support of the rule, for if the number of such customers is small, the rule is worthless. If $X$ and $Y$ are independent, then we expect lift the be close to $1$.

We are interested in finding all these rules, There is an efficient algorithm, called Apriori that does this which has two steps:

1. finding frequent itemsets, that is, those with enough support, and
2. converting them to rules with enough confidence, by splitting the items into two, as items in the antecedent and items in the consequent.

For 1, we begin from the observation that if a set is frequent, all its subsets must be frequent as well. So we can begin from finding all size 1 sets that are frequent, and search inside that range and find all size 2 sets that are frequent and so on.

Once we find the item set, we need to convert them into rules by splitting the $k$ items into two as antecedent and censequent. We start by putting a single item in the consequent and $k - 1$ items in the antecedent and filter them by confidence threshold. Then inductively we check whether we can move another item from antecedent to the consequent.