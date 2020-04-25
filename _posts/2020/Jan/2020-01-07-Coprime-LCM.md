---
layout: post
title: "Coprime LCM"
category: mini-proofs
tags: [algebra, number-theory]
author: Ramneek Narayan
---

This is just a mini-proof for the Chinese Remainder Theorem if the bit about why the LCM between two coprime whole numbers is the product of the two numbers doesn't make immediate sense. The writer hopes this clarifies any doubts. First the theorem:

---
**Theorem (Coprime LCM):** The LCM between two coprime whole numbers $a$ and $b$ is $ab$, or $\text{lcm}(a,b) = ab.$ $\blacksquare$

---

On with the proof!

***(Proof 1)*** We will prove this theorem by way of contradiction. Suppose there exist two whole numbers $\beta$ and $\beta'$ such that they satisfy

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
\begin{equation}\frac{\beta'}{b} < \frac{a}{b} \ \text{ and }\ \frac{\beta'}{b} < \frac{\beta'}{\beta}\end{equation}
$$

Putting this all together we have:

$$
\begin{equation}\frac{\beta'}{b} < \frac{\beta'}{\beta} < \frac{a}{\beta}\end{equation}
$$

which entails (with the help of $(2)$ and $(3)$) that exclusively either

1. $\frac{\beta'}{\beta} < \frac{a}{b}$
2. $\frac{a}{b} < \frac{\beta'}{\beta}$

and nothing else. Yet from $(1)$ we can see (after some symbol manipulation) that $\frac{a}{b} = \frac{\beta'}{\beta}$ which contradicts both of the only 2 possibilities above. Hence, there cannot exist numbers $\beta < b$ and $\beta' < a$
 such that equation $(1)$ holds true. This means (by De Morgan's) that either $\beta \not < b$ or $\beta' \not < a$. In either each respective case we can deduce the following (choosing the smallest value of the $\beta$'s in each case to minimize the product $\beta' b$ or $\beta a$):

  1. $(\beta = b) \triangleright (\beta' = a)$ case $\beta \not < b$
  2. $(\beta' = a) \triangleright (\beta = b)$ case $\beta' \not < a$

Making the lowest multiple of the numbers $ab$ in either case.
Put another way, the lowest numbers that can satisfy equation $(1)$ are thus the least upper bounds of the $\beta$'s, or $\beta = b$ and $\beta' = a$. This makes the LCM for $a$ and $b$ is the product between the two (all other products won't work by contradiction). Q.E.D.

***(Proof 2)*** This uses a similar technique to the above where we assume there exist two whole numbers $\beta < b$ and $\beta' < a$ such that

$$
\begin{equation}\beta a = \beta' b.\end{equation}
$$

Only this time we assume one statement at a time; first we assume there is a number $\beta < b$ such that equation $(6)$ holds. In another way, we mean that there exists some positive number $0 < \eta < b$ such that $\beta = b - \eta$. Symbol manipulation of equation $(6)$ with this fact gives the form of $\beta'$ as

$$
\begin{equation}\beta' = a - \frac{a \eta}{b}\end{equation}
$$

and as $\beta'$ is a postitive whole number it must be the case that $\eta$ is a multiple of $b$, specifically it means that $\eta = b$ only (0 is not considered a multiple here). But this contradicts the bounds for $\eta$ which need to be true, so it is the case that $\beta \not < b$ by way of contradiction.

When we assume that $\beta' < a$ and write $\beta' = a - \eta'$ for some $0 < \eta' < a$ and deduce

$$
\begin{equation}\beta = b - \frac{b \eta'}{a}\end{equation}
$$

in a similar fashion we arrive at $\eta' = a$, a condtradiction again. This means that $\beta' \not < a$ as well.

Since both $\beta \not < b$ and $\beta' \not < a$ we pick the lowest numbers in these new bounds, namely $\beta = b$ and $\beta' = a$, which shows that the LCM between $a$ and $b$ is $ab$. This concludes the proof. Q.E.D.

What follows isn't required for the Chinese Remainder Theorem but is interesting (It can be used for the GRE's as the writer did![^1])

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

 Thanks for reading and thinking with me! Hope this made the Chinese Remainder Theorem proof easier to read. Catch you later! <i class="fas fa-meteor"></i>

--- *All is number...* (Pythagoras)

 [^1]: Just because a triangle looks like it's right, doesn't mean that it is until someone marks it so! Same with triangles that look isosceles... No room for induction! <i class="far fa-grin-squint-tears"></i>
