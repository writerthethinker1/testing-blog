---
layout: post
title: "Sign Theory 101: The Basics"
category: sign-theory
tags: discussion
year: "2019"
author: Ramneek Narayan
---

This post serves as an introduction to the theory of signs. Given here...

* Numbers with 3 signs
* Rule for addition
* Rule for multiplication
* Interpolated signs theorem

While one can construct systems with many signs, we will primarily focus on those with 3 signs. Just as in regular arithmetic we have two signs $+$ and $-$, so in this theory we have three signs namely $+$, $-$, and $*$. We will use the special notation of affixing signs as superscripts for the numbers they are with. So, for example, if we wanted to symbolize 'negative one', then we would write $1^-$ instead of the usual $-1$ in ordinary arithmetic.

---

**Example 1:** Write the 3 signs of $1$.

***Soln:*** This would be plus one, minus one, and star one or $1^+$, $1^-$, and $1^*$ respectively. $\blacksquare$

---

**Fundamental Sign Axioms**

We hold the two axioms as true by their own self-evidence regarding addition and the signs of the additive neutral element (the number '0'):

**Axiom 1 (Equivalences of 0):** $0^+ = 0^- = 0^*= 0$.

**Axiom 2 (Sum of all signs):** $a^+ + a^- + a^* = 0$ for all $a \in [0, \infty)$.

When multiplying these numbers we will follow a special rule as given below:

$$
				 \begin{array}{|l|*{l}|{l}|}    \hline     \bullet  & +   & -   & * \\    \hline    +  & +  & -   & *  \\    \hline    -   & -   & * & + \\    \hline    * & * & + & -  \\    \hline    \end{array}
$$

Notice here that multiplication of signs makes a abelian group that is isomorphic to $(\mathbb{Z}_3, +)$ where addition is taken modulo 3. Indeed it is this special property of the multiplication of the signs that gives them useful properties such as describing colors of light.

Similarly we can deduce a table for the division of signs as given below:

$$
\begin{array}{|l|*{l}|{l}|}
		\hline
     \div  & +   & - & *\\
    \hline
    +  & + & *   & -  \\
    \hline
    -   & -   & + & * \\
    \hline
    * & * & - & +  \\
    \hline
    \end{array}
$$

these tables are handy and require some practice to make computations easy. The following examples illustrate computations using these numbers.

---

**Example 2:** Compute $\frac{1^+}{1^*}$.

***Soln:*** Using the division table above where the numerator is below the division sign and the denominator is to the right of the division sign, we have the division of $1^+$ by $1^{\ast}$ as $1^-$. Hence, $\frac{1^+}{1^*} = 1^-$. $\blacksquare$


***Alt. Soln:*** Notice that $\frac{1^-}{1^-} = 1^+$ by the division table and that $(1^\ast)(1^-) = 1^+$. Multiplying the quantity in question by the new form of $1^+$ gives $\frac{1^+}{1^*} = \frac{(1^+)(1^-)}{(1^\ast)(1^-)} = \frac{1^-}{1^+} = 1^-$. Which is the same answer as given by the above solution too. $\blacksquare$

---

**Example 3:** Compute $(2^* + 3^-)(1^* + 4^+)$.

***Soln:*** We follow multiplication of 3-signed numbers just as we follow multiplication of 2-signed numbers and use the distributive property:

$$(2^* + 3^-)(1^* + 4^+) = (2^*)(1^* + 4^+) + (3^-)(1^* + 4^+)$$

$$= (2^- + 8^*) + (3^+ + 12^-) = 11^- + 5^*.$$

In the last line of the computation we used axiom 2 to simplify the sum at the end. $\blacksquare$

---

Now that we have discussed basic sign operations and examples of them, we can talk about the geometric appeal of these numbers. The numbers that are spanned by the use of 3 signs are nicely viewed on what is known as the *number disk* or $\mathbb{D}$. Specifically we have the definition of the number disk as:


**Definition 1 (Number Disk):** The *number disk* $\mathbb{D}$ is the set of all possible signed numbers whose entries are real. In other words, $\mathbb{D} \equiv \lbrace a^+ + b^- + c^*: a,b,c \in \mathbb{R}\rbrace$ where simplifications of the numbers are made using axiom 2.


The allure of using the word disk to describe the above set comes when we plot these numbers using the coordinate system below:

{% capture num_disk_url %}
{{ site.baseurl | escape}}/images/num_disk.png
{% endcapture %}

{% include image.html url=num_disk_url description='Figure 1: The number disk with sign axes marked. Code adapted from' link="http://www.texample.net/tikz/examples/unit-circle/" link_desc="here" %}

Given here is the number disk that has signs going in 3 directions: $+, -,$ and $\ast$. Each sign is marked with a primary color and one can see that red corresponds to positive numbers, green to negative, and blue to the auxiliary sign $\ast$. When one changes the direction of a fixed sign (marked with negatives in the parenthesis) they in turn are going closer to the colors of the primary pigments. In a sense, adding values to these numbers is much like *changing their color or intensity*; when we are at a positive number and go down the line we end up with a number that is less red and more cyan depending on how much down the line we went.

In its entirety the number disk can be viewed as the color wheel:

{% capture color_wheel_url %}
{{ site.baseurl | escape}}/images/color_wheel.png
{% endcapture %}

{% include image.html url=color_wheel_url description="Figure 2: The color wheel." link="https://stackoverflow.com/questions/45785653/how-to-draw-a-gradient-color-wheel-using-cagradientlayer" link_desc="Source" %}

The continuity of the colors reflects the continuity of the numbers on the disk; there are no 'gaps' between any numbers or any 'odd' behavior between color transitions. As hinted by the first picture can add numbers along the major axes much like we add vectors from the $x$ and $y$ coordinate system. Thus, the number $1^+ + 1^-$ would have the color yellow since it is the fusion of red ($1^+$) and green ($1^-$). This would then mean that <span style="color:red">$1^+$</span> $+$ <span style="color:green">$1^-$</span> = <span style="color:yellow">$1^+ + 1^-$</span>. Similarly, changing the *magnitude* of a number such as $1^+$ to $4^+$ makes the color of the number more *intense* and less *light* in hue.

Looking at figure 1 again and keeping the idea of vector addition in mind we can come up with the deduction $a^+ + a^- = (-a)^\ast$ for all $a \in \mathbb{R}$. This is because the resultant of two numbers is taken through the middle of the joining angle. Before proving this fact, we introduce one postulate concerning the intuitive wrapping of negative signs inside a number with an outer sign wrapping like $(-2)^\ast$. This notion is the *postulate of interpolated signs*.

---

**Postulate 1 (Existence of Interpolated signs):** A number is said to be *interpolated* when its inner sign wrapping opposite is taken. For example, the interpolation of $6^\ast$ is $(-6)^\ast$ since the inner sign wrapping ($+$ and $-$) is changed to its opposite. Let there be postulated numbers that are of opposite directions within their sign wrappings, that is let there be numbers of the kind $(-1)^\ast$ that also yields $0$ when added to its additive inverse. Thus, $(-1)^\ast + 1^\ast = 0$, for example. More generally, $a^+ + (-a)^+ = 0$ for all $a \in \mathbb{R}$.

---

Using this idea, seeing that $a^+ + a^- = (-a)^\ast$ for all $a \in \mathbb{R}$ can be made simple. First, we state a lemma, then the theorem and its proof.

**Lemma 1 (Sign Interpolation):**
For all $a \in [0, \infty)$ we have

$$
\begin{equation}(-a)^+ = a^- + a^*\end{equation}
$$

$$
\begin{equation}(-a)^- = a^+ + a^*\end{equation}
$$

$$
\begin{equation}(-a)^* = a^+ + a^-\end{equation}
$$

***(Proof)*** From axiom 1 we have $a^+ + a^- + a^\ast = 0$ and similary from postulate 1 we have $(-a)^+ + a^+ = 0$. Equating the two quantities gives

$$
\begin{equation} (-a)^+ + a^+ = a^+ + a^- + a^\ast\end{equation}
$$

The addition of $(-a)^+$ on both sides of the above equation along with postulate 1 to simplify gives

$$
(-a)^+ = a^- + a^\ast
$$

as desired. Proofs for $(2)$ and $(3)$ follow using the same idea. Q.E.D

Interestingly, from this lemma we have the nice corollary:

**Corollary 1 (Addition of Int. Signs):** For all $a \in [0, \infty)$ we have $(-a)^+ + (-a)^- + (-a)^\ast = 0$. (For a proof add equations $(1)$, $(2)$, and $(3)$ and simplify using axiom 1).

Using **lemma 1** and **corollary 1** we can extend axiom 1 for all of the real numbers. We can also re-write Lemma 1 so that we prove statements such as $(a)^+ = (-a)^- + (-a)^\ast$ for all $a \in [0, \infty)$. In turn this allows us to extend the domain of the values $a$ is allowed to be to $(-\infty, \infty) \equiv \mathbb{R}$. So, the theorem is

---

**Theorem (Sign Interpolation):** For all $a \in \mathbb{R}$ we have

$$
\begin{equation}(-a)^+ = a^- + a^*\end{equation}
$$

$$
\begin{equation}(-a)^- = a^+ + a^*\end{equation}
$$

$$
\begin{equation}(-a)^* = a^+ + a^-\end{equation}
$$

***(Proof)*** Use the same technique as in lemma 1 but replace $a^+ + a^- + a^\ast$ with $(-a)^+ + (-a)^- + (-a)^\ast$ given by corollary 1 (remember to keep the domain of $a$ as $[0, \infty)$). Q.E.D.

---

**Note (Complex Numbers):** To get a feel for this theory, we'll stick to real numbers for an introduction, but we note that the entries within the outer sign wrapping can be complex as well, so we can write things like $(1 + 4i)^\ast$ too. But more on that later.

This wraps up the basics, until next time! <i class="fas fa-meteor"></i>
