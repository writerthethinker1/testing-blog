---
layout: post
title: "Totient Proof"
category: proofs
tags: [number-theory]
author: Ramneek Narayan
---

In this post we will prove that the totient function for the product of any natural numbers $\alpha$ and $\beta$ where $\text{gcd}(\alpha, \beta) = 1$ is *multiplicative*. In other words we will show $\phi(\alpha \beta) = \phi(\alpha)\phi(\beta)$ by way of contradiction. But before doing so, let's define the totient of any number.

#### The Totient

**Definition (totient):** The *totient* $\phi(\cdot)$ of any natural number $\alpha$ is simply the number of coprime whole numbers less than that number. When we write $\phi(\alpha) = \gamma$ we mean that there are $\gamma < \alpha$ whole numbers such that they are coprime to $\alpha$ (share $1$ as their only GCD).

**Example 1:** The totient of $13$ is 12 since $13$ is a prime number. 2 is coprime to 13, 3 is coprime to 13, 4 is coprime to 13, &etc... up to the number 12 inclusive. Hence, $\phi(13) = 12$.

**Example 2:** The totient of $8$ is 4 since all odd numbers less than 8 are coprime to it and all even numbers less than 8 have 2 as their GCD. Thus, $\phi(8) = 4$.  

**Remark:** All the totient does is record the number of coprime numbers less than the given number in question. It is a record keeper and is a function such that $\phi: \mathbb{N} \to \mathbb{N}$. Quick fact: $\phi(\alpha) < \alpha$ for all $\alpha \in \mathbb{N}$.

---

Now that we've shown the basics of the totient function, let's prove that it's multiplicative for coprime factors. Let's do this!

**Theorem (Totient Multiplicity):** The totient function $\phi$ is multiplicative up to coprime factors. Thus, when $\text{gcd}(\alpha, \beta) = 1$, we have $\phi(\alpha\beta) = \phi(\alpha)\phi(\beta).$

***(Proof)*** We'll start out by defining something known as a *totient vector* or $\vec{\tau}\_{\alpha}$ that holds as its elements the numbers that are coprime and less than $\alpha$. The dimension of a totient set is namely the totient of the function or $\dim(\vec{\tau}\_\alpha) = \phi(\alpha)$.

Now, in regards to $\phi(\alpha \beta)$ we know that all elements in the totient vector of $\alpha$ are less than $\alpha$ and all the elements in the totient vector of $\beta$ are less than $\beta$. This makes it so that all of the elements in the vector $\vec{\tau}\_\alpha \otimes \vec{\tau}\_\beta$ are also in $\vec{\tau}\_{\alpha \beta}$. We know this because if $\gamma \nmid \alpha$ ($\gamma < \alpha$) and $\eta \nmid \beta$ ($\eta < \beta$), we are sure that $\gamma \eta \nmid \alpha \beta$. Hence, $\dim(\vec{\tau}\_{\alpha \beta}) \geq \dim(\vec{\tau}\_\alpha \otimes \vec{\tau}\_\beta) = \dim(\vec{\tau}\_\alpha)\dim(\vec{\tau}\_\beta)$ or equivalently

$$
\begin{equation}\phi(\alpha \beta) \geq \phi(\alpha)\phi(\beta).\end{equation}
$$

This is fact.

If we make the assumption that $\phi(\alpha \beta) > \phi(\alpha)\phi(\beta)$, then we notice that there must be a number $\mu$ that is a vector element of $\vec{\tau}\_{\alpha \beta}$. Because of this, $\mu$ must not be factorable into vector elements belonging to $\vec{\tau}\_{\alpha}$ and $\vec{\tau}\_\beta$. We write the forms of $\alpha$ and $\beta$ as the following using the fundamental theorem of arithmetic:

$$
\begin{equation}\alpha = \prod_{j = 1}^{q}(p_j^{\alpha})^{\alpha'_j} \ \ \ \beta = \prod_{j = 1}^{w}(p_j^{\beta})^{\beta'_j}\end{equation}
$$

The form of $\mu$ must then be as follows:

$$
\begin{equation}\mu = \prod_{j = 1}^{s}(p^{\ast}_j)^{\psi_{j}}\end{equation}
$$

where $p^\ast_j, p_j^\alpha,$ and $p_j^\beta$ are prime numbers. Notice by definition of the totient we have $\mu < \alpha \beta$. This makes it so that $p^\ast_j < \max\lbrace p_j^\alpha\rbrace$ and $p^\ast_j < \max\lbrace p_j^\beta\rbrace$ for all the primes making up $\mu$. We also know that $\mu \nmid \alpha \beta$ and this makes it so each $p^\ast_j \neq p^\alpha$ and $p_j^\ast \neq p^\beta$ for every prime that makes up $\alpha$ and $\beta$ respectively. Let there be *product factorizations* of the number $\mu$ such that

$$
\begin{equation}\mu = \mu_1 \cdot \mu_2\end{equation}
$$

our claim in our assumption is that for all product factorizations of $\mu$ we cannot have

$$
\begin{equation}\mu_1 = \omega \ \ \ \mu_2 = \upsilon\end{equation}
$$

where $\omega$ is a vector element of $\vec{\tau}\_\alpha$ and $\upsilon$ is a vector element of $\vec{\tau}\_\beta$. Notice that if this is true, we have $\mu$ composed of primes not in any $\omega$ or $\upsilon$ since those numbers are described by primes. However, all primes that are less than $\alpha$ and are recorded in $\vec{\tau}\_\alpha$ and the same with $\beta$. This would make it so that either $p_j^\ast > \max \lbrace p_j^\alpha \rbrace$ or $p_j^\ast > \max \lbrace p_j^\beta \rbrace$, a contradiction in either case. Because of this contradiction, we know that $\phi(\alpha \beta) \not > \phi(\alpha)\phi(\beta)$.

By equation $(1)$, it follows that $\phi(\alpha\beta) = \phi(\alpha)\phi(\beta)$ as demonstrated. Q.E.D.

---

**Fun fact:** $\phi(p) = p - 1$ where $p$ is prime. And similarly $\phi(p^\nu) = p^\nu - p^{\nu - 1}$. Using these facts as well as the theorem we just proved we can deduce Euler's formula for the totient:

$$
\phi(\alpha) = \alpha \prod_{p | \alpha}\left(1 - \frac{1}{p}\right)
$$

this makes calculation of totients easier than by trial and error.

---

This wraps up the post 🌯, see you later!

(づ｡◕‿‿◕｡)づ -- *"A man provided with paper, pencil, and rubber, and subject to strict discipline, is in effect a universal machine."* (Turing)
