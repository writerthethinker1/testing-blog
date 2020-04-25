---
layout: post
title: "Cov of Multinomial"
category: mini-proofs
tags: [stats]
author: Ramneek Narayan
---

This post gives one method of computing the covariance between two random variables belonging to a Multinomial Distribution. The method relies on the law of iterated expectation, namely that if $X$ and $Y$ are random variables, we have $\mathbb{E}(\mathbb{E}(Y\|X)) = \mathbb{E}(Y)$. Before going into the proof we give some information about the Multinomial Distribution.

The Multinomial Distribution is a natural extension of the classical Binomial Distribution wherein the population has $k \in \mathbb{N}$ traits (like colored balls: blue, orange, green, etc...) and we sample (from an infinite population) $n \in \mathbb{N}$ members (balls) from the population. Out task is to find out the chances of observing a certain *vector* $\vec{x} = (x_1, x_2,..., x_k)$ which tells us how many of each population member (ball) in our sample we observed. In essence, when we declare interest in finding the number of ways we could have observed $\vec{x} = (x_1, x_2, ..., x_k)$ we notice that there are

$$
\begin{pmatrix}n \\ x_1,x_2,...,x_k\end{pmatrix} = \frac{n!}{x_1! x_2! \dots x_k!}
$$

ways of doing so (to see this assume first the number of ways of simply observing $x_1$ of the first trait, then $x_2$ of the second with new sample size $n - x_1$, then $x_3$ of the third with new sample size $n - x_1 - x_2$, and so on until $x_k$. Multiply all ways together to reach the same answer above.) The chance of one instance of the numbers described by the observed vector $\vec{x}$ is $p_1^{x_1}p_2^{x_2}...p_k^{x_k}$ and with all of the possible ways this could occur, we have for the unobserved vector $\vec{X}$:

$$
\begin{equation}\mathbb{P}(\vec{X} = \vec{x}) = \frac{n!}{x_1! x_2! \dots x_k!} p_1^{x_1}p_2^{x_2}...p_k^{x_k} \end{equation}
$$

This is the pdf of the Multinomial Distribution.

Notice each element of the unobserved vector $X_i$ follows a binomial distribution since we only consider that trait in question; there is a chance $p_i$ of observing the trait per sampled member and chance $1 - p_i$ of not observing the trait per sampled member (a Bernoulli distribution per sampled member). So, the number of members with the trait is a sum of Bernoulli trials, resulting in $X_i \sim \text{Bin}(n, p_i)$ for all $i \in \lbrace 1, 2, ..., k \rbrace$. What is special about these members is that *they are all dependent on each other*, thus $X_i \nind X_j$ for all $i \neq j$. In particular, we have the conditional distribution for any $i \neq j$

$$X_i|(X_j = \alpha) \sim \text{Bin}\left(n - \alpha, \frac{p_i}{1 - p_j}\right)$$

This gives us enough information to compute the covariance between any two members or $\text{Cov}(X_i, X_j)$. Using the definition of covariance, we have

$$
\text{Cov}(X_i, X_j) = \mathbb{E}(X_iX_j) - \mathbb{E}(X_i)\mathbb{E}(X_j)
$$

We already know $\mathbb{E}(X_i) = np_i$ since each member is binomially distributed. The difficulty is with $\mathbb{E}(X_iX_j)$. We can make some progress if we set $Z = X_iX_j$ and notice $Z \nind X_j$ allowing us to use the law of iterated expectation without being redundant:

$$
\begin{equation}\mathbb{E}(Z) = \mathbb{E}(\mathbb{E}(Z|X_j)) = \sum_{\alpha}\mathbb{E}(Z|X_j = \alpha)\mathbb{P}(X_j = \alpha)\end{equation}
$$

Now, $\mathbb{E}(Z\|X_j = \alpha) = \mathbb{E}(X_iX_j\|X_j = \alpha) = \mathbb{E}(X_i\cdot\alpha\|X_j = \alpha)$ which can we simplfied into

$$\alpha\mathbb{E}(X_i|X_j = \alpha) = \alpha(n - \alpha)\frac{p_i}{1 - p_j}$$

Going back to equation $(2)$ we see it can be written now as

$$
\frac{p_i}{1 - p_j}\sum_{\alpha}(\alpha n - \alpha^2)\mathbb{P}(X_j = \alpha)
$$

Some simplification yields the easy to read form

$$
\frac{p_i}{1 - p_j}\left(n\mathbb{E}(X_j) - \mathbb{E}(X_j^2)\right)
$$

$$
= \frac{p_i}{1 - p_j}\left(n^2p_j - [np_j(1 - p_j) + n^2p_j^2]\right)
$$

$$
= \frac{p_i}{1 - p_j}\left(n^2p_j(1 - p_j) - np_j(1 - p_j)\right)
$$

$$
= np_ip_j(n - 1)
$$

Thus, $\mathbb{E}(X_iX_j) = np_ip_j(n - 1)$ and putting this in the covariance equation we get

$$
\text{Cov}(X_i,X_j) = np_ip_j(n- 1) - n^2p_ip_j
$$

$$
= np_ip_j(n - 1 - n) = -np_ip_j.
$$

Hence, $\text{Cov}(X_i,X_j) = -np_ip_j$ as we sought to solve for.

This is one method of computing the covariance of the multinomial distribution and others use a *multivariate probability generating function (pgf)* or use the simplification of $X_i = \sum_k (Y_i)_k$ and $X_j = \sum_j(Y_j)_k$ in the covariance term giving $\text{Cov}(X_i,X_j) = \text{Cov}(\sum_k(Y_i)_k, \sum_k(Y_j)_k) = n \text{Cov}(Y_i, Y_j)$ where $Y_i \sim \text{Bernoulli}(p_i)$. They are also valid and give the same answer as we have calculated. The quickest is using the pgf, but the one given here is another method that shows direct methods can work as well. Anyway, this concludes the post, see you later! <i class="fas fa-meteor"></i>
