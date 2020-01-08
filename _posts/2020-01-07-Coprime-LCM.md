---
layout: post
title: "Coprime LCM"
category: mini-proofs
tags: [algebra, number-theory]
author: Ramneek Narayan
---

This is just a mini-proof for the Chinese Remainder Theorem if the bit about why the LCM between two coprime whole numbers is the product of the two numbers doesn't make immediate sense. The writer hopes this clarifies any doubts. First the theorem:

---
**Theorem (Coprime LCM):** The LCM between two coprime whole numbers $a$ and $b$ is $ab$, or $\text{lcm}(a,b) = ab$ $\blacksquare$

---

On with the proof!

***(Proof)*** We will prove this theorem by way of contradiction. Suppose there exist two whole numbers $\beta$ and $\beta'$ such that they satisfy

$$
\begin{equation}\beta a = \beta' b\end{equation}
$$

that is $\beta$ sets the multiple of $a$ to be equal to a multiple of $b$. The argument is that $\beta < b$ and $\beta' < a$ so that the LCM is less than $ab$. Since both inequalities hold, we can deduce

$$
\begin{equation}\frac{\beta'}{\beta} < \frac{a}{\beta}\end{equation}
$$

Similary, we have

$$
\begin{equation}\frac{a}{b} < \frac{a}{\beta}\end{equation}
$$

as well as

$$
\frac{\beta'}{b} < \frac{a}{b} \ \text{ and }\ \frac{\beta'}{b} < \frac{\beta'}{\beta}
$$

Putting this all together we have:

$$
\frac{\beta'}{b} < \frac{\beta'}{\beta} < \frac{a}{\beta}
$$

which entails (with the help of $(2)$ and $(3)$) that exclusively either

1. $\frac{\beta'}{\beta} < \frac{a}{b}$
2. $\frac{a}{b} < \frac{\beta'}{\beta}$

and nothing else. Yet from $(1)$ we can see (after some symbol manipulation) that $\frac{a}{b} = \frac{\beta'}{\beta}$ which contradicts both of the only 2 possibilities above. Hence, there cannot exist numbers $\beta < b$ and $\beta' < a$
 such that equation $(1)$ holds true. By this fact the lowest numbers that can satisfy equation $(1)$ are thus the least upper bounds of the $\beta$'s, or $\beta = b$ and $\beta' = a$. Thus, the LCM for $a$ and $b$ is the product between the two (all other products won't work by contradiction). Q.E.D.

What follows isn't required for the Chinese Remainder Theorem but is interesting (I used it for the GRE's![^1])

 ---
 **Corollary (Product of GCD and LCM):** The product of the GCD and LCM of any two numbers $a$ and $b$ is simply the product of the two numbers.

 ***(Proof)*** When two numbers share a common divisor they are *scaled* by it and have as their other factors coprime. To see this, consider the decompositions of $a$ and $b$ as follows

 $$
 a = \gamma \cdot \alpha \\
 b = \gamma \cdot \beta
 $$

 where $\alpha$ and $\beta$ are coprime (otherwise we could extract more factors to put into $\gamma$). From this we know (by definition) that $\text{gcd}(a,b) = \gamma$ and further since $\alpha$ and $\beta$ are coprime their LCM is $\alpha \beta$. To find the LCM of $a$ and $b$ we seek a number $\delta_1, \delta_2$ such that $\delta_1 a = \delta_2 b$ and the product is as small as possible, using the forms of $a$ and $b$ given above we can write the equality as:

 $$
 \delta_1 (\gamma \alpha) = \delta_2 (\gamma \beta)  \ \triangleright  \\
 \gamma(\delta_1\alpha) = \gamma(\delta_2\beta) \ \triangleright \\ \delta_1\alpha = \delta_2\beta
 $$


 we can see from this that the smallest product is $\alpha \beta$ as $\alpha$ and $\beta$ are coprime. Hence, $\delta_1 = \beta$ and $\delta_2 = \alpha$ making the LCM $\gamma \alpha \beta$. We already know that the GCD between $a$ and $b$ is $\gamma$ so we can compute the product as

 $$
 \text{gcd}(a,b) \cdot \text{lcm}(a,b) = \gamma^2 \alpha \beta = ab
 $$

 as postulated in the beginning. Q.E.D.

 ---

 Thanks for reading and thinking with me! Hope this made the Chinese Remainder Theorem proof easier to read. Catch you later!

 (づ｡◕‿‿◕｡)づ --- *All is number...*

 [^1]: Just because a triangle looks like it's right, doesn't mean that it is until someone marks it so! Same with triangles that look isosceles... <i class="far fa-grin-squint-tears"></i>
