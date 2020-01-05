---
layout: post
title: "Logical Fallacies I"
category: logic
tags: [reasoning, thoughts, fallacies]
author: Ramneek Narayan
---

Just some fallacies in logic (I've been guilty of them in the past and present (lol)). This post aims to expose some common errors of reasoning that one may make in making assertions (like debating or arguing in mathematics, physics, statistics, and the like). The writer expresses some reasons as to why humans make these errors and why they can 'feel' true but aren't by means of counterexamples. When counterexamples led to contradictions the law of the excluded middle is violated which bypasses classical logic. Subsequent inferences are then faulty under this field of thought. We use this method to show one who believes in a fallacy why their deductions are not in line with reason (i.e. things can't be true and not true at the same time). All fallacies were found using this [wikipedia page](https://en.wikipedia.org/wiki/Formal_fallacy) (check it out, it goes into greater depth). Also, another really nice comprehensive guide to common fallacies is [Logically Fallacious](https://www.logicallyfallacious.com/tools/lp/Bo/LogicalFallacies/3/Book-Contents) (you might be surprised at how many types of errors we can make; my favorites are the "appeal to..." section of the book). Let's get going, each error starts with a dialogue (see if you can catch the error before reading the explanation!)...  

1.  **Affirming a disjunct**:

    > Almond: *We either drink water or the sun shines* <br>
    Cashew: *Here comes some water to drink!* <br>
    Almond: *That means the sun won't shine!* <br>
    Cashew: *???*

    Can you spot the almond's error? The almond thought that the OR in his sentence was mutually exclusive in truth for the disjuncts (only one could be true: XOR). However, the or used is plain old regular OR that admits both the disjuncts can be true; this makes it possible for both the sun to shine and water to be drunk (as they drank their water the sun rose as it usually does in the morning). Because of this possibility, we cannot hastily conclude that one disjunct is false conditional on the truth of the other. More symbolically the dialogue between the nuts can be written as

    $$
    \phi \lor \psi. \phi. \\ \vdash \neg \psi
    $$

    where the turnstile '$\vdash$' means "provable." Arguments if this form are always faulty.

2. **Affirming the consequent (my favorite):**

    > Toaster: *If I am filled with bread, then the bread will be crispy and brown.* <br>
    Bread: *I am crispy and brown.* <br>
    Toaster: *I must have been filled with you, bread.* <br>
    Bread: *??? I was put in a oven...*

    In this case, the toaster thought that his conditional was *strict* in what it implied. He thought that knowledge of the consequent meant that the antecedent must have been true. That is he thought "If I am filled with bread then and only then will the bread be crispy and brown" when it was not the case (the bread was put in an oven, not the toaster). I find this error easy for humans to make since it is natural to confuse meaning and speech (plus, the error is easy for the mind to make as it learns relations between things, especially without occurrences of the antecedent false yet the consequent true). Symbolically, arguments of this form are

    $$
    \phi \rightarrow \psi. \psi. \\ \vdash \phi
    $$

    Yet, the conditional is true even when $\neg \phi$ is true, which contradicts the conclusion, hence a fallacy.

3. **Denying the antecedent:**

    > Coffee Maker: *If the moon dances today, then I make coffee.* <br>
    Mochi: *The moon is still today, it's not dancing.* <br>
    Coffee Maker: *Hence, I won't make coffee today.* <br>
    Mochi: *???*

    Here, the coffee maker thought that the *only* way that it could make coffee was when the moon dances. Yet, we can still use the coffee maker even if the moon isn't dancing, as the Mochi's confusion hints. This is similar to the affirming the consequent error in the sense that knowledge of the antecedent's falsity some-how means falsity of the consequent; both antecedent and consequent are alike in truth values in either fallacy when it is not always the case by the rules of logic. More abstractly the dialgue presented above is given by

    $$
    \phi \rightarrow \psi. \neg \phi. \\
    \vdash \neg \psi
    $$

    Yet the implication is invalid when $\neg \psi$ is true making a premise false when we require it to be true for the argument.

4. **Denying a conjunct:**

    > Twix bar: *One can't have both the left or the right twix, one must choose wisely.* <br>
    Oreo Cookie: *I'm certainly not choosing the right twix.* <br>
    Twix bar: *Then you picked the left one.* <br>
    Oreo Cookie: *??? I don't eat Twix at all...*

    Once again, this fallacy came from confusion of OR with XOR. The twix bar thought that since one can't have both right and left twix that one must exclusively have not one of them whereby not having one means the other was chosen. Logically speaking though the negation of a conjunction is a disjunction of the negation of the former conjuncts which leaves it valid that both of the former conjuncts are false (NOT AND is true even when both conjuncts are false). This is known as *De Morgan's Law.* This is seen in the dialogue when the oreo cookie reveals that it doesn't eat twix bars (chose neither). The argument in this fallacy goes

    $$
    \neg(\phi \land \psi). \neg \psi. \\
    \vdash \phi
    $$

    The fallacy is evident when evoking De Morgan's law: $\neg(\phi \land \psi) \leftrightarrow (\neg \phi \lor \neg \psi)$ as we can see logical OR '$\lor$' is used not logical XOR '$\oplus$.'

5. **Fallacy of the Undistributed Middle:**

    > Grasshopper: *Every leaf is green.* <br>
    Wizard: *My magic potion is green.* <br>
    Grasshopper: *Then it is a leaf.*<br>
    Wizard: *??? Potions aren't leaves...*

    This is very similar to affirming a consequent fallacy given in this post. Surely, if something is known to be a leaf (healthy condition) then it will be green but all things that are green aren't always leaves (magic potion as the wizard pointed out). The grasshopper's first statement can be symbolized as $\forall \alpha(L(\alpha) \rightarrow G(\alpha))$ where the antecedent is the property of the thing to be a leaf and the consequent is a property of the thing to be green. The wizard's statement is $G(\pi)$, that his potion is green. The grasshopper then affirmed the consequent and concluded $L(\pi)$ falsely. Put together, this argument is

    $$
    \forall \alpha(L(\alpha) \rightarrow G(\alpha)). G(\pi). \\
    \vdash L(\pi)
    $$

    The mistake is overgeneralizing the class of an object as that of the antecedent given it is in the class of the consequent. The circle representing leaves is *inside* the circle representing those things that are green. So, when something is green, it is not always a leaf.

    Well, that wraps up this post. Hope you had fun reading it! I look forward to making more posts on logic fallacies like this one. Until then!

    (づ｡◕‿‿◕｡)づ
