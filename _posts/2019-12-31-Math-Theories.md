---
layout: post
title: "Math Thought Process"
category: logic
tags: [discussion, thoughts]
year: "2019"
author: Ramneek Narayan
---

When anyone creates a consistent theory like those of mathematicians, statisticians, and logicians, there is a certain thought process that is undertaken. Usually, as I have observed, the thinking is intuitive and uses pictures for reasoning but the foundations for what is actually discussed rely on formal symbols by means of a proof. These proofs use classical logic as grounds for their justification (things such as NOT, OR, AND, and IMPLIES to create sentences). Proofs to humans are verbal much like the sentence you are reading now but Gödel showed with his incompleteness theorems that all statements made in any branch of mathematics are much like (if not identical) 'crunching numbers'---he used Gödel numbering together with the fundamental theorem of arithmetic to represent every possible symbolization and concatenation of these symbols which make up both proofs and statements in mathematics. All that aside, the end product of the mathematician is a formal layout of what they intuitively thought up in their mind. Much like this universe has rules, laws, or regularities that make it up, so theories belonging to mathematicians have structure and conventions for expressing clearly to everyone what is thought in a way free of contradictions. Below are the basics people in math, computer science, logic, statistics, and even physics use to convey their ideas. We give examples from popular mathematics you might have heard of in school so it doesn't feel archaic. By the way, a good book to check out is Eucild's [*Elements*](https://farside.ph.utexas.edu/Books/Euclid/Elements.pdf); it uses most of the concepts discussed here.

---

* Proof = Evidence or argument that establishes mathematical truth

    * **Reason:** To avoid logical inconsistencies (things like $p \land \neg p$). Helps us navigate our thoughts knowing one line is correct and the others are conflicting with what we are saying in the first place. These are given after theorems; they are justification for theorems. Usually at the end of proofs we put a black square (Halmos symbol) or Q.E.D. to say what we wanted to prove is now done.

    * Theorem: If $2x + 2 = 1$, then $x = -\frac{1}{2}$.

        *(Proof)* Plug in $x = -\frac{1}{2}$ in the given equation and see that the lefthand side is identical to the righthand side. $\blacksquare$

---

* Definition = statement of the exact meaning of the word (concerned with *what to call things*)

    * **Reason:** it's hard to convey meaning without referencing the correct items from one's mind. Humans can use words to mean different things in different contexts (consider the word 'ball' which can mean a dance or a sphere depending on the context). We usually define what we are talking about in the beginning in a way that gives only one rigid interpretation to keep the meaning of the system in tact (free of differing 'views' or 'subjectivity').

    * **Definition (Even numbers):** Those numbers that can be divided by 2 to yield an integer.

---

* Axiom = statement that is self-evident, taken to be true without proof, more general in acceptance, spans many theories (concerned with *how things behave*)

    * **Reason:** this one comes from deep thought about how to show a certain statement is true. Certain statements can be proven under certain assumptions and these assumptions can't be proved any further no matter what we think. They are like things that can't be split no matter how hard we try, they don't break (no proofs using other statements). They are to be taken as a whole composed entirely of itself and nothing else.

    * **Axiom (The number '0' (Peano)):** The number 0 is a natural number. (It's a number we can count with much like '1' or '2').

---

* Postulate = statement that is true without proof but is specific to a certain field or theory

    * **Reason:** these are identical in axioms as they can't be proven but some authors prefer to use these specifically for their own theories thinking it is central to this exact concept rather than universal. If mathematics was a video game system run on a computer and the branches were individual games, we would see that all of them use the same machinery (axioms) to work, but each has different physics or patterns (postulates). Both are undeniable but one is more specific to a the game rather than the whole system.

    * **Postulate (Parallel Lines (Euclid)):** Given any line and a point not on that line, there is only *one* line that is parallel to it which includes that point not on the line. (This one is an example of how postulates came from sitting and thinking for a long time unable to find a proof as many mathematicians did ages after Eucild tried to prove the statement above and couldn't do it. Instead, they came up with new types of geometry called *elliptic* and *differential geometry* which breaks this postulate).

---

* Proposition = formal statement of theorem/problem typically including the demonstration; provably true, but not as important as a theorem

    * **Reason:** some statements are worth mentioning for the theory but they aren't fundmental (though needed at times). Something fundamental would be like the heart or brain of the human, these aren't propositions; they are more like ear cartilage or fingers. Usually the writer makes this call; it's a human creation like formatting text. Sometimes they are demonstrations (showing something like technique or constructions in geometry) too.

    * **Proposition (Equilateral Triangle Construction (Euclid)):** To draw an equilateral triangle using only a compass and straight edge. (Nothing ground-breaking here).

---

* Theorem = statement that may be demonstrated to be true from other truths

    * **Reason:** we can justify what we say! Every theorem has a proof. These statements are essential for the theory and without them, our thoughts would fall apart; like blood in your veins.

    * **Theorem (Law of Cosines):** In any triangle described by the three vectors $\vec{x}$, $\vec{y}$, and $\vec{x} + \vec{y}$ we have the following: $\|\|\vec{x} + \vec{y}\|\|^2 = \|\|\vec{x}\|\|^2 + \|\|\vec{y}\|\|^2 + 2(\vec{x} \cdot \vec{y})$.

---

* Lemma = Theorem that aids in proving a subsequent theorem (intermediate theorem)

    * **Reason:** sometimes it helps to prove something more general with something specific. Or maybe sometimes an important result depends on a less important fact. Lemmas are written with *intention* and are *used* for theorems unlike propositions which stand on their own. Like parts of a machine or part of an entailment, a lemma or lemmas entail a theorem.

    * **Lemma (Rolle's):** Given any continuous differentiable function on an open interval $(a,b)$ such that $f(a) = f(b)$ there exists at least one number $c \in (a,b)$ where $f'(c) = 0$. (We can use this lemma to prove the Mean Value Theorem).

---

* Corollary = Theorem following a previous theorem that is a direct consequence of previous theorem

    * **Reason:** we have specific 'handy' truths that we can later use for practical purposes or justify what was intuitive. These are sometimes specific cases of theorems. I'll give an easy one so you get the idea... In the following example, assume we proved the Pythagorean theorem.

    * **Corollary (Pythagorean Triplet):** It is the case that 3, 4, and 5 make up the lengths of the sides of a right triangle since $3^2 + 4^2 = 5^2$.

---

**Organization Truth Note:** In terms of truth we have...

  * Axioms, Postulates, Definition:
    * Taken to be true by themselves. (Like building blocks).
  * Propositions, Lemmas, Corollaries, Theorem:
    * True by means of proof (demonstration). (Made up of the building blocks and other things like themselves).  

---

This wraps up the thought organization in math and the like. It's very reductionist and a strength in one area aids in others. You might have seen so when you see geometry used in most branches of math or perhaps when making a miscalculation in a computation that left subsequent computations erroneous---every part or piece was important for the conclusion. In a broader sense, the sentences we say run on the same machinery in the mind. See you next post!

(づ｡◕‿‿◕｡)づ
