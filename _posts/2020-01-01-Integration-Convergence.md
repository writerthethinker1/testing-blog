---
layout: post
title: "Integration as Series/Seq Convergence"
category: math
tags: [discussion, thoughts, calc]
year: "2020"
author: Ramneek Narayan
---

In this post we explore different ways of seeing what an integral depicts. We assume some grasp geometrically of what this idea means and will use that idea to relate it to series and sequences.

First, we review the geometric appeal:

---
Integrals are ways of finding 'area' for curves beyond those in geometry (planes, triangles, &etc...). We do by dividing the area in question into 'strips' and then adding them up. The smaller the strip, the more there are, and the better the calculation is. The height of the strip is namely the height of the curve locally at that 'region.' This is what makes our sum so cleaver.

---

More formally we define the integral as follows:

$$
\begin{equation}\int_a^b f(x)dx \equiv \lim_{n \to \infty}\sum_{j = 1}^{n}f(a + j\Delta x)\Delta x\end{equation}
$$

This is just a more mathematical way of saying the verbal description aforementioned. The number of strips is $n$, the $f(\cdot)$ is the height of each strip, and the $\Delta x$ is the width of each strip. Now, geometrically we can see that our approximation 'fills' the curve in a way so that there are no 'gaps' that aren't accounted for as the limit tends to infinity. In this sense we will call the 'area' under the curve as that which is described by equation $(1)$. Notice here that the interval of integration $[a, b]$ has uncountably many elements ($\card[a, b] = \aleph_1$) yet our sum for the area only has countably infinite elements ($\aleph_0$). It shows that we only need countably infinite elements to make an 'area' that is *described* by a curve (our strips fill in that region very coarsely).

Now, how do we know that equation $(1)$ converges? First we define a constant $\beta$ such that (by the well-ordering property of sets) we have

$$
\begin{equation}\beta = \max_{x \in [a,b]}f(x)\end{equation}
$$

Next, we consider the sum (we set $\Delta x$ as $\left(\frac{b - a}{n}\right)$ in the computations following):

$$
\begin{equation}\lim_{n \to \infty} \sum_{j = 1}^{n}\beta\left(\frac{b - a}{n}\right)\end{equation}
$$

We know that the above equation converges to $\beta(b - a)$ even as the limit is taken, thus:

$$
\begin{equation}\lim_{n \to \infty} \sum_{j = 1}^{n}\beta\left(\frac{b - a}{n}\right) < \infty\end{equation}
$$

Further, we have

$$
\begin{equation}\lim_{n \to \infty} \sum_{j = 1}^{n}f\left(a + j\left(\frac{b -a}{n}\right)\right)\left(\frac{b - a}{n}\right) \\ < \lim_{n \to \infty} \sum_{j = 1}^{n}\beta\left(\frac{b - a}{n}\right)\end{equation}
$$

since $\beta \leq f(x)$ for all $x \in [a, b]$. By equations $(4)$ and $(5)$ we can deduce that the integral described by the lefthand side of the inequality above converges. Thus, integrals on closed intervals converge for smooth functions (one's that give us the idea of 'area').

What about unbounded intervals like $(a, \infty)$? Sometimes the integral converges, and other times it doesn't. I will share one way to formally describe what is meant by that. In essence, all we do is set the upper limit $b$ as a variable rather than constant and evaluate that limit. In symbols we define a function $g$ such that

$$
\begin{equation}g(b) = \lim_{n \to \infty} \sum_{j = 1}^n f(a + j\Delta x)\Delta x\end{equation}
$$

where $\Delta x = \frac{b-a}{n}$. The convergence criterion for the integral then becomes:

$$
\begin{equation}\lim_{b \to \infty} g(b) < \infty\end{equation}
$$

usually we find this out by direct computation.

---

## Seeing Integrals as Limits of Sequences

We can index each approximation we get for an area using the following ($A_n$ is the $n$-th approximation):

$$
\begin{equation}A_n = \sum_{j = 1}^{n}f(a + j\Delta x)\Delta x\end{equation}
$$

Then we can construct a sequence $B$ such that $B$ records our approximations, so $B = \lbrace A_1, A_2,...\rbrace$. If this sequence converges to a value $A$, then the integral too converges. We can effectively write

$$
\lim_{n \to \infty} A_n = A
$$

We could use the definition of convergence of sequences to prove some integrals converge to our 'hunch' or 'guess' $A$ by showing:

$$
\begin{equation}\forall \epsilon > 0: \exists N \in \mathbb{N}:\forall n \in \mathbb{N}:\\ (n \geq N \Rightarrow |A - A_n| < \epsilon)\end{equation}
$$

If we don't have a good intuition about what the integral converges to, then Cauchy's criterion might be of better use:

$$
\begin{equation}\forall \epsilon > 0: \exists N \in \mathbb{N}:\forall m,n \in \mathbb{N}: \\ (m,n \geq N \Rightarrow |A_m - A_n| < \epsilon)\end{equation}
$$

In practice this is impractical as direct computation might be of better help but this illustrates a point that sequences can be related to integrals. It would be interesting to see a demonstration of this integral convergence using sequences, but this seems enough for now.

---

**Aside:** The most general defintion of the integral came from Riemann in the 1800s and has to do with the idea of the largest subinterval (the *mesh* or *norm*) we construct in $[a,b]$ converging to 0 as $n \to \infty$. The strips can now very in width as we please (non-uniform) so long as our method allows the strip with the greatest width to have its width tend to 0 as more strips are made. As far as computation is concerned, the definition of uniform widths given at the start of this post is more efficient and easier to program, but Riemann's is more general. It gives way to a definition of what we mean by integral convergence based on $\epsilon$-$\delta$. If you are really curious, checkout this page on [wikipedia](https://en.wikipedia.org/wiki/Riemann_integral) on Riemann integration.

---

Hope you have a great 2020! See you next time!

(づ｡◕‿‿◕｡)づ
