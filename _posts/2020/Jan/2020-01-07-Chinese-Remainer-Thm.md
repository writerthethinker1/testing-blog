---
layout: post
title: "Chinese Remainder Theorem"
category: proofs
tags: [algebra, group-theory]
author: Ramneek Narayan
---

In this post we will prove the Chinese Remainder Theorem from a group-theoretic[^1] point of view. In essence, we will prove the following:

---
**Theorem (Chinese Remainder Theorem):** For any two whole numbers $a$ and $b$ that are coprime ($\text{gcd}(a,b) = 1$) we have the following isomorphism between the groups $(\mathbb{Z}\_{ab}, +)$ and $(\mathbb{Z}_a \times \mathbb{Z}_b, +)$:

$$
\mathbb{Z}_{ab} \cong \mathbb{Z}_a \times \mathbb{Z}_b \ \blacksquare
$$

---

The proof is sure to exist somewhere but I couldn't find it anywhere easily, so it's written here. On with the reasoning!

***(Proof)*** To show the Chinese Remainder Theorem (CRT) we first note that the group $\mathbb{Z}\_{ab}$ is of finite order since it has a finite amount of elements ($\card(\mathbb{Z}\_{ab}) = ab$). We note further that this group is *cyclic* since it has '$1$' as its generator (a well known fact about any group of integers modulo $m$ or $(\mathbb{Z}\_m, +)$---to see why try a contradiction to show the order of $1$ must be $m$ assuming that $(\mathbb{Z}\_m, +)$ is a group). Thus $1 \in \mathbb{Z}\_{ab}$ and $o(1) = ab$.

To show a group isomorphism, all we need is for $(\mathbb{Z}_a \times \mathbb{Z}_b, +)$ to be cyclic as well since it is a group and $\card(\mathbb{Z}_a \times \mathbb{Z}_b) = ab$ too. We will show by way of contradiction that the generator for this group is $(1,1)$ or equivalently that $o((1, 1)) = ab$ (Play around with this group, maybe verify it for $\mathbb{Z}_2 \times \mathbb{Z}_3$).

First, let's assume that $o((1, 1)) \neq ab$. Since $(\mathbb{Z}_a \times \mathbb{Z}_b, +)$ is a group we know that all of its elements have finite order, so $o((1, 1)) < ab$. Set $c = o((1, 1))$, then $c < ab$ and we have two ways of writing '$c$':

1. $\mu a + \beta$ where $0 \leq \mu \leq b - 1$ and $0 <\beta < a$
2. $\nu b + \beta'$ where $0 \leq \nu \leq a - 1$ and $0 < \beta' < b$

Both forms are equal so $\mu a + \beta = \nu b + \beta'$. Further since $c$ is the order of $(1, 1)$ we know that $c$ iterations of the addition of $(1, 1)$ with itself recurses back to $(1, 1)$. Since addition is done modulo $a$ on the left coordinate and done modulo $b$ on the right, we can conclude that $(\mu a + \beta)\text{mod}\ a = (\mu b + \beta')\text{mod} \ b = 1$. All of this entails that $\beta = \beta' = 1$ which then entails $\mu a = \nu b$ which can never happen as the only whole number solution to this equation is when $\mu = b$ and $\nu = a$ ($a$ and $b$ are coprime so the LCM is $ab$)[^2]. Hence, a contradiction, we have $\mu a = \nu b$ and $\mu a \neq \nu b$ at the same time. This means our assumption that began the reasoning that $o((1, 1)) \neq ab$ is faulty which entails that $o((1, 1)) = ab$, as we suspected.

This enough to show that the generator of $(\mathbb{Z}_a \times \mathbb{Z}_b, +)$ is $(1, 1)$. Since both $(\mathbb{Z}\_{ab}, +)$ and $(\mathbb{Z}_a \times \mathbb{Z}_b, +)$ have the same order and are cyclic we can construct an isomorphism (bijective function) between the two. First, set $\gamma = 1$ and $\gamma^\ast = (1, 1)$ and map accordingly:

$$
w\gamma \leftrightarrow w\gamma^\ast
$$

for all $w \in \mathbb{N}$. This shows that the two groups are isomorphic (have elements that function the same, like people having the same job in life) or

$$
\mathbb{Z}_{ab} \cong \mathbb{Z}_a \times \mathbb{Z}_b
$$

as shown. Q.E.D.

---

**Corollary (Primes):** By induction we can show a cool result for the any number $\phi$ composed as a product of prime powers: $\phi = p_1^{\alpha_1} \dots \ p_{k}^{\alpha_k}$:

$$
\mathbb{Z}_{\phi} \cong \mathbb{Z}_{p_1^{\alpha_1}} \times \dots \times \mathbb{Z}_{p_k^{\alpha_k}}
$$

Surprisingly, this is a time complexity reduction technique (less steps in the algorithm) for RSA encryption! [Source](https://crypto.stanford.edu/pbc/notes/numbertheory/crt.html)

---
**Historical Aside:** This theorem is ancient and was first brought up as a problem by Chinese mathematician Sunzi in the third century AD. Formalization of the result (an algorithm) came nearly 300 years later by mathematicians and today we have generalized this result beyond just $\mathbb{Z}\_{\phi}$ to any ring that is abelian, say $(R, + , \cdot)$. [Source](https://en.wikipedia.org/wiki/Chinese_remainder_theorem)

---

That seems plenty for this post, catch you on the flip-side!

(づ｡◕‿‿◕｡)づ

[^1]: A good beginning book for learning modern algebra is Clark's [*Elementary Abstract Algebra*](http://shell.cas.usf.edu/~wclark/Elem_abs_alg.pdf); it's more you doing things than reading, if you like that style of learning.  
[^2]: See this [post]({% post_url myblog/2020/Jan/2020-01-07-Coprime-LCM %}) if it isn't clear.
