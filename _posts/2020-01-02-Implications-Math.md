---
layout: post
title: "Implications in Math"
category: logic
tags: [discussion]
author: Ramneek Narayan
---

In this post we explore the notion of 'implies' that is often used in mathematics, logic, and statistics. In practice this symbol is written down with an arrow such as '$\rightarrow$' or '$\Rightarrow$' and us used extensively to express one's sequential reasoning as they perform computations and prove various theorems.

While intuitive to grasp in practice and convenient to read when reviewing the works of others, there is a certain loss in meaning that the writer wishes to make clear. First, we'll begin with what we mean by the symbol '$\rightarrow$' in plain terms using interesting examples that perhaps someone who constructs this world from a pure logical framework without intention can not find puzzling.

### Implication

All we mean when we state one thing implies another is exactly one of the two following happened when observing those two things (called $\phi$ and $\psi$ here)

1. $\phi$ was true and $\psi$ was true
2. $\phi$ was false and $\psi$ was true

That's it, nothing more. If one of the two rules was true, then we can write $\phi \rightarrow \psi$ and have it be true, otherwise it's false.

This seems okay for an idea of sequential reasoning, but let me show you how this definition of implies can distort what we sometimes think in the mind by the word 'implies'. Consider the following symbolization:

$$
\begin{equation}\phi: \text{The sun is blazingly hot}\end{equation}
$$

and this other symbolization

$$
\begin{equation}\psi: \text{Kit-kat bars are sweet}\end{equation}
$$

Both $(1)$ and $(2)$ are true (we hope you know that or at least have tried a Kit-kat bar before) and following the convention of implies we may state $\phi \rightarrow \psi$ or that that sun is blazingly hot implies that Kit-kat bars are sweet. The implication is true, but in terms of the word 'implies' to describe this relation sounds rather odd as the hotness of the sun has nothing to do with how the factory makes the bar (the amount of sugar they put in it). It is not like suddenly the sun drops $4^\circ$ C and we are suddenly no longer making sweet Kit-kat bars. Yet, it is the case the one implies the other.  By the way, even if the sun stops being blazingly hot, the implication still holds (it satisties rule \#2). In this case, the notion of implies is *vacuous*. So, what we can take from this is that logical 'implies' is weak in what we wish to express by the word 'implies' if we are to use it meaningfully. But, to make the point even more clear, let's us it in math...

#### Speaking 'math'

Let's say we are performing some computation about the odds of winning Mr. Biscuit's raffle of crackers. You read online before going to the raffle that the odds of winning are $2:3$ and wish to explicitly find out the chance of winning. That's simple, you think you end up with the compuation:

$$
\begin{equation}\frac{\pi}{1 - \pi} = \frac{2}{3} \rightarrow 3\pi = 2 - 2\pi \rightarrow\end{equation}
$$

$$
\begin{equation}5\pi = 2 \rightarrow \pi = 2/5. \  \blacksquare\end{equation}
$$

So the chance of winning is $2/5$ or $40\%$. Now that we know a little more about implies, let's have some fun with the last line of derivation, we can (and have it be true) state the following:

$$
\begin{equation}[5\pi = 2 \rightarrow (\text{Martians love Funday})] \rightarrow \\ (\text{salty pretzels are delicious to me}) \rightarrow \\ \pi = 2/5. \ \blacksquare\end{equation}
$$

Each bit of the implications following the first are true statements (the first is false), so the chain of reasoning is true, yet not meaningful (there are bits we don't need to have to get the main point across). By this nature of implication, we can see that it is flawed.

#### The fix

We can get around this idea using the concept of *entailment* which is symbolized here as '$\triangleright$' wherein the previous statement *leads to* the next statement in the same way the premises in an argument construct the conclusion by means of inference rules. Entailment is stronger than implication as it is more strict about the relation between antecedent and consequent. By the phrase $\phi \triangleright \psi$ we know that *whenever* $\phi$ is true or observed, that $\psi$ will also be true by some nature between the two (they are connected, this isn't just chance). It could be the case that $\phi$ is never true yet $\psi$ is true; we cannot claim entailment here just yet (what we need above all else is to have an instance where $\phi$ is true and subsequently $\psi$ was also true to make that deduction). Entailment is likened with the idea of *aboutness*; in $\phi \triangleright \psi$ there is something *about* $\phi$ that makes it so that $\psi$ is also true.

Using entailment makes the notion of implies more precise and clear. It may be what mathematicians and statisticians are speaking of in their derivations or reasoning. If something were to happen to the validity of the antecedent, then the consequent would be augmented or jeopardized (have its validity be compromised too possibly). In implication it is not the case, anything could happen to the validity of the antecedent and the consequent remains the same in truth value or validity.

In life, implication is true in *coincidences* but entailment is true only if there is *true relationship* between antecedent and consequent. Something like the gears of a machine turning the input (antecedent) into the output (consequent).

Perhaps a good line of reasoning in math is such:

$$
\begin{equation}(x + 1 = 2 )\triangleright (x = 1)\end{equation}
$$

Rather than

$$
\begin{equation}(x + 1 = 2) \rightarrow (x = 1).\end{equation}
$$

Which is just as valid as the cookies dancing inside a teapot implying 2 is an even number.

This wraps up the discussion, thanks for reading.  ¡Hasta luego!

(づ｡◕‿‿◕｡)づ
