---
layout: page
title: "The Triple Loop Condition: Engineering at inference speed in a safe and responsible way"
---

Every engineer knows that AI is a powerful assistant.
However, conflicts arise about which engineering tasks can really be deeply automated instead of only being assisted by AI.
This is what Peter Steinberger and others called **working at inference speed**: 
In engineering, "inference speed" is using AI not only to assist with tasks, but to complete them so quickly that the only bottleneck left is the output-speed of tokens (and the token bill).

### Resistance against Inference Speed

At every large-scale engineering organization, there will always be resistance against AI at inference speed.
And in many cases, that resistance is well-justified.
For example, cowboy-style shipping at inference speed might lead to excessive maintenance problems or technical debt — or, even worse, a meltdown in IT-security or regulatory compliance.
But other than well-justified resistance, I also heard many vague arguments of "AI being too weak" for certain tasks.

### How to Smell Bullshit Arguments

So I asked myself:
How can we detect in which cases the resistance against AI at inference speed is technically valid, and in which case the resistance is based on vague gut feelings, historic anecdotes or sometimes even straight-up misinformed lies?

To answer this question, I propose the **Triple Loop Condition** to see which tasks can be done at inference speed in a safe and responsible way, and which tasks cannot:

- **C1 Spec:** Can the task be sufficiently accurately specified?
- **C2 Verification:** Can the task be (efficiently) verified within an automated verification loop? Typically, for non-trivial tasks, a self-correcting loop is needed because the results are rarely correct on the first try.
- **C3 Blast Radius:** I split blast radius into two related questions: First, what is the potential damage if the task is done wrong? And secondly, how much effort and time is needed to repair it?

Once we see a task through these three conditions, it stops being a pure gut call.
If all three are true, then working at inference speed isn't reckless, it is just good engineering practise.
However, meeting those three conditions doesn't magically let an agent complete the task.
Instead, it often requires dedicated AI-engineering efforts to translate those three conditions into a practically working setup.

### Human Reviews

Doing a task at inference speed does not mean that humans are no longer needed.
I believe that human reviews still remain critically important.
However, the automated verification loops must be strong enough so that the reviews do not become a long back and forth of corrections.
Moreover, the task must be pre-structured so that the blast radius can be easily reviewed without extremely tedious risk-reviews.

Or put in other words for mathematical freaks:

If a task satisfies `C1 ^ C2 ^ C3`, then the expected time to review the task for humans collapses down to a brief and efficient verification gate, under the assumption that the spec (C1) was already reviewed before. 

### Deep Dive

The following is a series of articles and case studies to validate the "Triple Loop Condition" in practice, to give a solid guideline on when AI at inference speed is safe and responsible, and when it is not:

- C1: [Specification Traps: Which tasks can be done at inference speed?](specification-traps.md)
- C2: [Verification Traps: Rotten feedback loops destroy AI at inference speed.](verification-traps.md)
- C3: [Blast Radius: Symmetric vs. asymmetric fallout when things go wrong](blast-radius.md)
- Special case: [Frontends at Inference Speed: Agent-friendly CSS Styling](frontend-at-inference-speed.md)
