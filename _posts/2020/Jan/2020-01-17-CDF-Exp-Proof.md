---
layout: post
title: "CDFs and Expected Values"
category: proofs
tags: [stats, reasoning]
author: Ramneek Narayan
---

In non-parametric statistics it is often the case of assessing whether two populations have the same average result or not. In symbols this means that if a person from population 1 is modeled stochastically by a random variable $X_1$ (whose distribution is unknown) and person from population 2 is modeled stochastically by a random variable $X_2$ (whose distribution is also unknown), we seek to find out if $\mathbb{E}(X_1) \neq \mathbb{E}(X_2)$. If it is, then we would especially like to know the direction of the inequality: $\mathbb{E}(X_1) \leq \mathbb{E}(X_2)$ vs. $\mathbb{E}(X_1) \geq \mathbb{E}(X_2)$. In practice, however, it is difficult to develop hypothesis tests for the given inequalities. Instead, we make use of the cumulative density functions (CDFs) that describe these random variables. If we are given (from our hypothesis tests) information about $F_1(x) \odot F_2(x)$ where $\odot \in \lbrace \leq, \geq \rbrace$, then we may conclude $\mathbb{E}(X_1) \odot' \mathbb{E}(X_2)$ where $\odot'$ is the opposite inequality that $\odot$ is. In short, we have the following statements:

1. $F_1(x) \leq F_2(x) \Rightarrow \mathbb{E}(X_1) \geq \mathbb{E}(X_2)$
2. $F_1(x) \geq F_2(x) \Rightarrow \mathbb{E}(X_1) \leq \mathbb{E}(X_2)$

The this post aims to prove the above statements. But first an intuitive explanation:

---
**Intuition:** Let's look at statement 2. Since the first CDF is greater than the second, it has most of its values for $X_1$ as less than those of $X_2$. It naturally follows that $\mathbb{E}(X_1) \leq \mathbb{E}(X_2)$. Statement 1 is shown by permuting 2 with 1 in the explanation given in the previous sentence.

---

Now that we an idea for these statements might be true, let's demonstrate it.

***(Proof)*** We will prove statement 2, as statement 1 can be shown using the same argument with symbol permutation of 1 with 2 in the subscripts. We assume $F_1(x) \leq F_2(x)$ for all $x \in (-\infty, \infty)$ (the domain). One neat fact about this inequality is that for any number $c \in \mathbb{R}$ we have:

$$
\begin{equation}\int_{-\infty}^{c} F_1(x) dx \leq \int_{-\infty}^{c} F_2(x)dx.\end{equation}
$$

Using the definition of the CDF for any random variable we simultaneously have

$$
\begin{equation}F_j(x) = \int_{-\infty}^{x} f_j(t)dt\end{equation} \ \ \ \forall j \in \lbrace 1, 2 \rbrace
$$

This lets us rewrite equation $(1)$ as

$$
\begin{equation}\int_{-\infty}^{c}\int_{-\infty}^{x}f_1(t)dtdx \leq
\int_{-\infty}^{c}\int_{-\infty}^{x}f_2(t)dtdx.\end{equation}
$$

Now, the region $\mathcal{R} = (-\infty, c) \times (-\infty, x)$ looks like a *triangle* made from a the upper left part of a square (we treat $(-\infty, \infty)$ like a point, it's the bottom left corner of the square $\mathcal{S} = (-\infty, c) \times (-\infty, c)$). This allows us to make the change of variables we would normally do for triangles in calculus. Thus we can write the region of integration as $\mathcal{R} = (-\infty, c) \times (t, c)$ and equation $(3)$ becomes

$$
\begin{equation}\int_{-\infty}^{c}\int_{t}^{c} f_1(t)dxdt \leq \int_{-\infty}^{c}\int_{t}^{c} f_2(t)dxdt\end{equation}
$$

Evaluating the integrals (the first is free of $x$ so we can just take the difference of the upper and lower limits) we arrive at:

$$
\begin{equation}\int_{-\infty}^{c}(c - t)f_1(t)dt \leq \int_{-\infty}^{c}(c - t)f_2(t)dt\end{equation}
$$

which simplifies to:

$$
\begin{equation}\int_{-\infty}^{c}cf_1(t)dt - \int_{-\infty}^{c}tf_1(t)dt \leq \\
\int_{-\infty}^{c}cf_2(t)dt - \int_{-\infty}^{c}tf_2(t)dt\end{equation}
$$

At this point $(6)$ is valid for all real numbers $c$, and we will apply a limit to $c$ to the infinite on both sides. Clearly,

$$
\begin{equation}\lim_{c \to \infty} \int_{-\infty}^{c}cf_j(t)dt = \infty \ \ \ \forall j \in \lbrace 1, 2 \rbrace\end{equation}
$$

But what's interesting is that the evaulation is *the same number* for both $f_1$ and $f_2$ since they both have area 1 under their curves over infinity (take the ratio between the equations described by $(7)$ and see that they evaluate to 1; same number over infinity). So, we can (as $c \to \infty$) remove both from the equality when we take the limit. This leaves the limit as

$$
\begin{equation}-\int_{-\infty}^{\infty} tf_1(t)dt \leq -\int_{-\infty}^{\infty} tf_2(t)dt\end{equation}
$$

which can be simplified into

$$
\begin{equation}\int_{-\infty}^{\infty} tf_1(t)dt \geq \int_{-\infty}^{\infty} tf_2(t)dt\end{equation}
$$

and by the definition of expected value this is equivalent to saying

$$
\begin{equation}\mathbb{E}(X_1) \geq \mathbb{E}(X_2)\end{equation}
$$

as intuitively guessed. This concludes the proof. Q.E.D.

---

All credit for the proof goes to Shitong Wei who introduced me to it during discussion in college. The writer could not find it easily online so it is given here. Thanks Shitong! That concludes this post, and the writer will catch you later! <i class="fas fa-meteor"></i>

(づ｡◕‿‿◕｡)づ
