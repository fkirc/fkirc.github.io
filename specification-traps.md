---
layout: page
title: "Specification Traps: Which tasks can be done at inference speed?"
---

The [Triple Loop Condition](triple-loop-condition.md) is a way to check which tasks can safely run at inference speed.
The first condition is whether a task can even be specified at all.
Here are a few examples that can be very well specified:

- Generating a frontend for an already existing design
- An integration for an already existing external API
- Fixing a performance-bottleneck with a clear way to measure success

### Micro-Iterations at Inference Speed

On the other hand, some tasks are nearly impossible to specify upfront.
For example, a yet-unproven startup feature often falls into this category.
Of course, AI can be perfectly used to try out new features and iterate quickly.
However, even in a fast-moving startup, any kind of "human user feedback" already prevents a task from running at inference speed.
For example, Peter Steinberger did not create OpenClaw as a whole piece at inference speed. Instead, he executed a huge number of "micro-iterations" over OpenClaw during long working hours, each executed at inference speed.

### The Underspecification Trap

A common trap I have seen is accusing AI agents of making errors because the task wasn't specified enough.
Instead of accusing AI agents of being "stupid" or "weak" when they fail a task, ask yourself:
Was the specification a piece of crap, missing critical context or maybe just a shallow idea?

### The Hidden Knowledge Traps

The more hidden tribal knowledge exists in a project, the more difficult it becomes to work at inference speed.
If a project is full of hidden assumptions, outdated documents or undocumented dependencies, then we should not blame AI agents for being "weak".

### The Bloated Specification Trap

Anyone can use AI-agents to generate specifications, generate Jira-tickets or generate a massive plan in "plan mode".
But if huge specifications are quickly generated and dumped onto engineers' desks, it does not solve the problem of vague guessing.
Instead, it only moves vague guessing errors into the specification phase.

### Next: Verification Loops

Once a task has a sufficiently accurate spec, it's time to think about [verification loops](verification-traps.md).
