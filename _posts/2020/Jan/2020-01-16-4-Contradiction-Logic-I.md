---
layout: post
title: "Contradiction Logic I"
category: logic
tags: [discussion]
author: Ramneek Narayan
---

This post introduces the beginnings of a logic that uses 4 types of truth, including that of 'contradiction' (it appears so, but it isn't). The ideas discussed are of the most accurate findings of the writer and improvements and comments towards building this field further are welcome. To start this topic, we will pose some questions for the reader to consider; see if they are true or false:

1. Is the Earth warm?
2. Is it morning on the Earth?
3. Is there a teacup on Pluto?
4. Is a bowl halfway filled full?
5. Did it rain on Earth?
6. Is pizza tasty?
7. *Do I exist after death?*
8. *Does God exist?*
9. *Is the universe eternal?*

Some of these questions can't be answered with a simple 'true/yes' or 'false/no' because the answer is *both true and false* (this is not a contradiction). Other questions can't be answered using true or false at all, (e.g. the teacup questions); they are beyond truth and falsehood no matter how hard one tries. In such cases we state the answer as *neither true nor false*, opinions are a good example of this: *the pizza tastes sooo good for everyone* (not everyone tastes pizza the same, suppose it has toppings some people don't favor). Now that we've discussed these new forms of truth, the answers to the questions are as follows (for greater understanding of the ideas):

1. Is the Earth warm? (true and false; some continents have summer, but others have winter)
2. Is it morning on the Earth? (true and false; evening in some continents but sunrise elsewhere)
3. Is there a teacup on Pluto? (neither true nor false; no way of assessing validity)
4. Is a bowl halfway filled full? (true and false, both full and not full when half-full)
5. Did it rain on Earth? (true and false; rained some place but not in others)
6. Is pizza tasty? (neither true nor false, people have different preferences)
7. *Do I exist after death?* (neither true, nor false, nor true and false, nor neither true nor false; this one's special: none of our truth values can represent the value of this proposition; it's beyond binary logic at all[^1])
8. *Does God exist?* (same as \#7, beyond inference and no inference)
9. *Is the universe eternal?* (neither true nor false; it just is)

Now that we have an understanding about the existence of 2 more truth values, we can start symbolizing the concept. Now, in classical logic we have two truth values: true and false. We can symbolize them as $\bullet$ and $\circ$ and a proposition symbolized as $\bullet p$ is read '*it is true that $p$*' and $\circ p$ is read '*it is false that $p$*.' All propositions in classical logic are exclusively either true or false; we make the law of the excluded middle

$$
\vDash (\bullet p \lor \circ p)
$$

where '$\models$' means that the proposition is always true (a tautology). In our logic, we extend these notions: there are now 4 notions of truth as symbolized below:

1. $\bullet$ = *true and only true*/*exactly true*/*is exactly the case that...*
2. $\circ$ = *false and only false*/*exactly false*/*is exactly not the case that...*
3. $\star$ = *true and false*/*is and is not the case that...* (possessing some elements of truth and falsehood not necessarily in equal proportions)
4. $\odot$ = *neither true nor false*/*neither is nor isn't the case that...* (beyond truth and false; can't be evaluated for either one or both)

Thus we can add more precision about truth with respect to a proposition $p$ by creating statements such as $\bullet p$, $\circ p$, $\star p$, and $\odot p$ for absolute truth, falsehood, truth and falsehood, neither truth not falsehood of the proposition $p$. Using this idea, the modified version of the law of the excluded middle is as follows:

---
**Law of the excluded middle:** $\models (\bullet p \lor \circ p \lor \star p \lor \odot p)$

---

One of these 4 ways of stating the truth of $p$ is going to evaluate to true and only true. Now, truth evaluations in classical logic are given as $\top$ and $\bot$ for true and false. Truth and falsehood are *orientations*, like top and bottom. In this logic there are 4 *orientations* of truth and we will mark them as $\top^\bullet$, $\top^\circ$, $\top^{\star}$, and $\top^{\odot}$ to indicate the truth for each truth value. So, for example, something that is false and only false evaluates to $\top^\circ$ and somthing that is neither true nor false evaluates to $\top^\odot$. We can symbolize the former as $p \to \top^\circ$ and the latter as $p \to \top^\odot$ informally (we haven't defined implication yet). These 4 orientations of truth are much like the ripeness of bananas, where a banana is green ($\bullet$), yellow ($\circ$), green and yellow ($\star$), or black (rotten) ($\odot$). The statements we make correspond to the state of the banana's ripeness; for example, $\odot(\text{banana is green})$ means it is neither true nor false that the banana is green (the banana lost all property of color, maybe it is invisible).

Now, what of chained truth statements? What of statements like $\star{\odot}p$? How can we simplify them and have them be logically valid? A simple way is to reason the sentence '*it is true and false that it is neither true nor false that...*' and see that this is never true, so it simplifies to false and only false. Thus, $\star{\odot} = \circ$. Using similar reasoning for all pairs of truth we arrive at the following table for sentence modifiers:

$$
\begin{equation}\begin{array}{|l|*{l}|{l}|{l}|}
    \hline
       & \bullet   & \circ  & \star & \odot \\
    \hline
    \bullet  & \bullet  & \circ   & \star & \odot \\
    \hline
    \circ  & \circ   & \bullet & \odot & \star\\
    \hline
    \star & \star & \odot & \bullet  & \circ\\
    \hline
    \odot & \odot & \star & \circ & \bullet\\
    \hline
    \end{array}\end{equation}
$$

We read the table from the first column to the first row for the first and second inputs respectively. This table lets us deduce that placement of truth modifiers is *commutative*, so something like $\circ{\star}p$ is equivalent to $\star{\circ} p$ and both are like saying $\odot p$ using the table above for simplification. We adopt the notation '$\simeq$' for *truth equivalence*, so two propositions that share the same truth values are related by that symbol. We can also use it to mark the truth value of any proposition as well, like if $p$ is true and false we can mark this idea as $p \simeq \star$.

---
**Example 1:** Evaluate the truth of the sentence '*it is true and false that the banana is green.*' (the banana seen is yellow, not green; we claim that it is green and not green (yellow)).

*Solution:* We can symbolize a *nested proposition* $p$ as follows: $p = \text{banana is green}$. Clearly, by the given information, the value of $p$ is $p \simeq \circ$. The given italicized sentence can then be written as $\star p$. Now $\star p$ can't be true as that would mean that the banana has some element of greenness (which it doesn't) and $\star p$ can't be false since that would mean the banana can't have any green or yellow (it has yellow though). This makes it so that $\star p \simeq \odot$, it is beyond truth and falsehood for description.

---

**Example 2:** Evaluate the truth of the sentence '*it is true and false that the banana is green.*' (the banana seen is green; we claim that it is green and not green).

*Solution:* The nested proposition is $p = \text{banana is green}$ and it evaluates to true, that is, $p \simeq \bullet$. We want to evaluate $\star p$, that one claims that the banana is both green and not green when it is in fact only green. If the statement isn't true, then we can't admit any color to the banana (which is false). If the statement isn't false, this would mean the banana has two colors when it doesn't. Thus, the statement is true and false: $\star p \simeq \star$.

---

Notice how saying something is conjoined between true and false when it is in fact true makes the thought true and false. Yet, when we say something is conjoined between true and false when it is in fact false makes the thought neither true nor false. Truth-hood of $p$ makes $\star p$ inherit the truth $\star$ so $\star p \simeq \star$ and falsehood of $p$ makes $\star p$ not describable by true or false so $\star p \simeq \odot$.[^2]

#### Connectives

Now that we have the sentence modifiers, we can create connectives as in classical logic. Our aim is to generalize the notions of AND and OR; there will by consequence be 4 operators now. If we take a look at the truth tables for AND and OR in 2-valued logic we see that they look like this:

$$
\begin{array}{|l|*{l}|}
\hline
\land & \bullet & \circ \\
\hline
\bullet & \bullet & \circ \\
\hline
\circ & \circ & \circ \\
\hline
\end{array} \qquad \qquad

\begin{array}{|l|*{l}|}
\hline
\lor & \bullet & \circ \\
\hline
\bullet & \bullet & \bullet \\
\hline
\circ & \bullet & \circ \\
\hline
\end{array}
$$

These tables imply there is some *hierarchy of truth* where in first is $\bullet$ and second is $\circ$ or $\bullet \to \circ$. AND favors $\circ$, giving falsehood if any conjunct is false. OR favors $\bullet$, giving truth if any disjunct is true.

By way of analogy, we can create similar versions of AND and OR as given below for 4-valued logic of contradiction. The truth hierarchy is naturally then $\bullet \to \circ \to \star \to \odot$ and AND favors the lowest ($\odot$) and OR favors the highest ($\bullet$). The tables are then:

$$
\begin{array}{|l|*{l}|{l}|{l}|}
    \hline
      \land & \bullet   & \circ  & \star & \odot \\
    \hline
    \bullet  & \bullet  & \circ   & \star & \odot \\
    \hline
    \circ  & \circ   & \circ & \star & \odot\\
    \hline
    \star & \star & \star & \star  & \odot\\
    \hline
    \odot & \odot & \odot & \odot & \odot\\
    \hline
    \end{array}\qquad \qquad

    \begin{array}{|l|*{l}|{l}|{l}|}
    \hline
      \lor & \bullet   & \circ  & \star & \odot \\
    \hline
    \bullet  & \bullet  & \bullet   & \bullet & \bullet \\
    \hline
    \circ  & \bullet   & \circ & \circ & \circ\\
    \hline
    \star & \bullet & \circ & \star  & \star\\
    \hline
    \odot & \bullet & \circ & \star & \odot\\
    \hline
    \end{array}
$$

This logic also has 2 more operators '$\oslash$' and '$\circledcirc$' that favor $\circ$ and $\star$ respectively. The tables then follow as:

$$
\begin{array}{|l|*{l}|{l}|{l}|}
    \hline
      \oslash & \bullet   & \circ  & \star & \odot \\
    \hline
    \bullet  & \bullet  & \circ   & \bullet & \bullet \\
    \hline
    \circ  & \circ   & \circ & \circ & \circ\\
    \hline
    \star & \bullet & \circ & \star  & \odot\\
    \hline
    \odot & \bullet & \circ & \odot & \odot\\
    \hline
    \end{array}\qquad \qquad

    \begin{array}{|l|*{l}|{l}|{l}|}
    \hline
      \circledcirc & \bullet   & \circ  & \star & \odot \\
    \hline
    \bullet  & \bullet  & \bullet   & \star & \odot \\
    \hline
    \circ  & \bullet   & \circ & \star & \odot\\
    \hline
    \star & \star & \star & \star  & \star\\
    \hline
    \odot & \odot & \odot & \star & \odot\\
    \hline
    \end{array}
$$

These tables entail an operational hierarchy where from highest to least: $\lor \to \oslash \to \circledcirc \to \land$.
Using these tables, we can then construct sentences like $(p \circledcirc \star q)$, $[(\odot p \oslash q) \land r]$, and $(\circ p \lor \star q)$ which are under further investigation!!!

This seems plenty for the logic of contradiction and this post. The writer hopes this introduces you to ways logic can be extended to include contradictions and that things can be true and false many times in everyday life. See you next post! <i class="fas fa-meteor"></i>

--- *"The energy of the mind is the essence of life."* (Aristotle)

---




[^2]: **Remark:** The writer admits this is rather confusing and not natural linguistically, however it reflects the inability to place truth and falsehood on things which are false but declared true and false and the ability to express truth-hood and falsehood to things which are true but declared true and false. Any comments about explaining this further are *graciously* welcomed.

[^1]: The writer holds that this marks a limitation of logic by its nature and design. It is an interesting topic to resolve using a fifth truth value for such a case, but at this point the logic seems recursive. It is a topic the writer wishes to explore later and encourages others too to develop as well: a logic with 5 truth values.
