---
layout: post
title: "Sign Theory 2: Inverses"
category: sign-theory
tags: [discussion]
author: Ramneek Narayan
---

[//]: # (No more than 180 lines for any post o/w too long)

This post continues ideas given for sign theory. In this post...

* method of computing reciprocals (complete with proof)
* idea of modulus on number disk $\mathbb{D}$

Let's get going.

We begin with a question regarding signed numbers

---
**Question:** Given any number on the number disk, say $1^\ast + 3^-$, how can compute the inverse (or reciprocal) of that number?

---

Recall in number systems with 2 signs, the inverse of a number $a$ is defined to be a number $a^{-1}$ such that

$$
a \cdot a^{-1} = 1^+
$$

We carry this convention for multi-signed numbers except the exponent is noted as $(-1)^+$ to reflect the sign of the inverse (others exist, they are namely $(-1)^-$ and $(-1)^\ast$). Our aim is to find the inverse of any number $n \in \mathbb{D}$ and write a computable form for it. In the end, we'll be able to simplify

$$
(1^\ast + 3^-)^{(-1)^+} = \frac{1^+}{1^\ast + 3^-}
$$

and other numbers like it.

We will compute inverses for any signed number and a unique property of the interpolated signs theorem lets us state that every number in $\mathbb{D}$ can be written as $a^+ + b^\ast$ where $a,b \in \mathbb{R}$. So, if we compute the inverse for these types of numbers, we have computed the inverses for every number in $\mathbb{D}$. One way of obtaining a simplified form is to pretend *we already have the form!* That is, we know the following:

$$
\begin{equation}\frac{1^+}{a^+ + b^\ast} = c^+ + d^\ast\end{equation}
$$

for some numbers $c,d \in \mathbb{R}$. We begin by multiplying both sides by $a^+ + b^\ast$ and have the result

$$
\begin{equation}1 ^+ = (ac)^+ + (ad)^\ast + (bc)^\ast + (bd)^-\end{equation}
$$

$$
\begin{equation} = (ac - bd)^+ + ((a-b)d + bc)^\ast\end{equation}
$$

where we have to simplify to two signs because it can never be the case where $bd = 0$. From here we have the evident system of equations:

$$
\begin{cases}ac-bd = 1 \\
bc + (a-b)d = 0\end{cases}
$$

where $a,b$ are known and $c,d$ are the variables to solve for. Simple linear algebra (via substitution) gives

$$
c = \frac{a - b}{a^2 - ab + b^2}
$$

and

$$
d = \frac{-b}{a^2 -ab + b^2}
$$

Hence,

$$
\frac{1^+}{a^+ + b^\ast} = \left(\frac{a - b}{a^2 - ab + b^2}\right)^+ + \left(\frac{-b}{a^2 -ab +b^2}\right)^\ast
$$

which (by the Interpolated Signs Theorem) can be simplified to

$$
\frac{1^+}{a^+ + b^\ast} = \left(\frac{a}{a^2 -ab + b^2}\right)^+ + \left(\frac{b}{a^2 - ab + b^2}\right)^-
$$

So, we've just computed the inverse of a signed number! All the other forms can come from permuting the signs, i.e. using the transformations $\lbrace +, \ast , - \rbrace \to \lbrace \ast, - , + \rbrace \to \lbrace -, +, \ast \rbrace$ and then premuting $a,b$ to get the form described below. The other forms are then:

$$
\frac{1^+}{a^- + b^\ast} = \left(\frac{b}{a^2 -ab + b^2}\right)^- + \left(\frac{a}{a^2 - ab + b^2}\right)^\ast
$$

$$
\frac{1^+}{a^+ + b^-} = \left(\frac{b}{a^2 -ab + b^2}\right)^\ast + \left(\frac{a}{a^2 - ab + b^2}\right)^+
$$

Let's see if it can work:

**Example:** Find the reciprocal of $3^+ + 4^-$. Verify it's the reciprocal.

*Solution:* The numbers we need are: $a = 3$, $b = 4$, and $a^2  - ab + b^2 = 13$. This makes the reciprocal as $(\frac{3}{13})^+ + (\frac{4}{13})^*$, by the formulas above. Let's verify that it's the reciprocal:
$$
 \left[\left(\frac{3}{13}\right)^+ + \left(\frac{4}{13}\right)^*\right] \cdot \left[3^+ + 4^-\right] =
$$

$$
= \left(\frac{9}{13}\right)^+ + \left(\frac{12}{13}\right)^* + \left(\frac{12}{13}\right)^- + \left(\frac{16}{13}\right)^+
$$

$$
= \left(\frac{-3}{13}\right)^+ + \left(\frac{16}{13}\right)^+ = 1^+
$$

This verifies that we have found the reciprocal of $3^+ + 4^-$, is $(\frac{3}{13})^+ + (\frac{4}{13})^*$, as we sought to show. $\blacksquare$

Now, we note the special quantity of $a^2 -ab + b^2$ as the *modulus* of the numbers in $\mathbb{D}$, we mark it as $\nu = a^2 -ab+b^2$. This number is like the 'distance from origin' for any signed number and is also the quantity that normalizes the inverse of any signed number, just like the determinant of a matrix normalizes the adjugate of that matrix. So, a simplified form of the inverse is then

$$
\frac{1^+}{a^+ + b^\ast} = \frac{1}{\nu}(a^+ + b^-)
$$

This concludes the post and I hope you had a good time reading it and taking in new ideas. Catch you later! <i class="fas fa-meteor"></i>
