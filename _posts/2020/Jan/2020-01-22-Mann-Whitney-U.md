---
layout: post
title: "Mann-Whitney U Test"
category: math
tags: [stats, discussion, reflection]
author: Ramneek Narayan
---

This post explores the Mann-Whitney *U* test used commonly in non-parametric statistics. The explanation for the form of the test statistic could not be found easily, so it's given here. Before going into the main details of the explanation, we give the basic idea behind the test as well as the problem it is trying to solve.

---
**Problem:** We observe two *independent* populations by means of a random sample from both of them and seek to find out which of the two will statistically observe values *higher* than the other. If we are a little loose in notation, this means that we see if one of the inequalities in the statement $X_1 \gtrless X_2$ is true. This is equivalent to finding out whether the CDF's of the two population's distribution functions have an inequality between them ($F_1(x) \geq F_2(x)$ means $X_1 < X_2$ and $F_1(x) \leq F_2(x)$ means $X_1 > X_2$).

---

To solve this problem, the test develops a method of comparing the effectiveness of one population to observe values that are *greater than the other population*. When this observed value for one population is greater than a threshold value (the critical value), there is enough evidence to reject the notion that the two populations have identical distributions with no shift between them. Now, the test statistic is called $U_i$ depending on which population we are comparing ($i \in \lbrace 1, 2 \rbrace$) and records the amount of observations in alternate population that are *less than* the current population in question. Doing this by hand is rather tedious, though possible. A much more efficient route is to *rank all of the observations* independent of populations they are from, making sure to adjust for ties (take average of ranks for repeated values). To make the following explanation clearer we adopt the notation:

* $n_1$ = sample size of population 1
* $n_2$ = sample size of population 2
* $R_1$ = sum of ranks of items only in population 1
* $R(x_i)$ = the rank of the $i$th item when samples between populations are combined

In total, when we rank the set of all observations, there are $n_1 + n_2$ points. It naturally follows that the set describing this idea is $S = \lbrace x_1, x_2, ..., x_{n_1 + n_2} \rbrace$. The aim is to use the set of adjusted ranks $R(S) = \lbrace R(x_1), R(x_2),...,R(x_{n_1 + n_2}) \rbrace$ to deduce how many observations from sample 1 were greater than those in sample 2. Here's the intuition:

---
**Intuition:** Naturally when one population has greater values than the other statistically we can see that most of the observed values from this population are greater than a *large portion* of the observed values for the other population. This would mean that the more values of one population exceed those of another, the more evidence there is to claim that the two populations differ substantially with the first shifted to the right of the other (it generally has greater values).

---

The value that records how many observations in population 1 exceeded those in population 2 is called $U_1$ and is found to have the value:

$$
\begin{equation}U_1 = R_1 - \frac{n_1 (n_1 - 1)}{2}\end{equation}
$$

We will now demonstrate how this is true.

***(Proof)*** By example let '$\bullet$' indicate an observation from sample 1 and '$\circ$' indicate an observation from sample 2. Suppose we rank the observations and come up with $\bullet{\circ{\bullet{\bullet {\circ{\circ{\bullet{\bullet}}}}}}}$ where more to the right means higher rank. Our aim is to find out for a given sample how many of the other sample points there are below it. We note that the rank of the observation gives away how many numbers are at or below it's value; so $R(x_i) = j$ means there are $j$ points below the $i$th entry in the set of all observations. We will do something special here; we will index the items in the list whilst retaining which sample the entry came from. For sample one, we will note the *ordered* set as $S_1 = \lbrace x_{\alpha_1},..., x_{\alpha_{n_1}} \rbrace$ and similary for sample two we will have the *ordered* set as $S_2 = \lbrace x_{\beta_1},..., x_{\beta_{n_2}} \rbrace$. Hence $S = S_1 \cup S_2$ and we order this in the end, marking the operation with $\text{Ord}$, giving $\text{Ord}(S)$. The ranked set then becomes $R(\text{Ord}(S))$ and we note that the difference between an entry's rank and its index value (the number $i$ in $x_{\alpha_i}$) is the number of items from the opposite population that are less than the point in question. Thus, for the $i$th entry the number of entries less than or equal to that entry is $R(x_{\alpha_i})$ and the number of entries from that population is $i$. This makes it so the number of items less than that entry but only from the other population is $R(x_{\alpha_i}) - i$. When we take the sum of all of these for the entire sample for population 1, we get

$$
\begin{equation}U_1 = \sum_{i = 1}^{n_1} [R(x_{\alpha_i}) - i] \end{equation}
$$

and by our definitions as well as summation identities we result in

$$
\begin{equation}U_1 = R_1 - \frac{n_1(n_1 - 1)}{2}\end{equation}
$$

as we aimed to show.

What happens when $R(x_{\alpha_i})$ is adjusted, e.g. we have $R(x_{\alpha_i}) = 1.5$? Our results still hold, it is just that the fractional amount is reserved for *ties* in the data (take average of unadjusted ranks). So, $R_1 \not \in \mathbb{N}$ always means there were ties in the data set; note an even amount of ties still yields $R_1 \in \mathbb{N}$, so whether $R_1$ is a whole number or not doesn't guarantee if there were ties in between the two samples. The interpretation of $R(x_{\alpha_i}) - i$ is less useful when there are ties between data sets as well as within, but when we take the sum of these amounts in the end, the discrepancies between $R(x_{\alpha_i}) - i$ and how many entries are less than or tied with $x_{\alpha_i}$ are taken out. In other words, if entries $i, j$ are tied and belong to the same data set, then the adjusted rank $\bar{R}(x_{\alpha_i}) = \frac{R(x_{\alpha_i}) + R(x_{\alpha_j})}{2}$ when taken as sum for $U_1$ in the end becomes

$$
(\bar{R}(x_{\alpha_i}) - i) + (\bar{R}(x_{\alpha_i}) - j) = R(x_{\alpha_i}) + R(x_{\alpha_j}) - i - j \\ =  (R(x_{\alpha_i}) - i) + (R(x_{\alpha_j}) - j)
$$

which amounts to the same calculation if ranks were not adjusted between the same data set. Between data sets, however, is when the adjusting of ranks makes the difference as fractional amounts for $U_1$ entail ties between data entries. In the end, we get a statistic that records both *ties and entries from the other data set lower than the one in question*. This concludes the proof. Q.E.D.

Hope you enjoyed this explanation of the statistic used in the Mann-Whitney *U* test. See you next time! <i class="fas fa-meteor"></i>

(づ｡◕‿‿◕｡)づ
