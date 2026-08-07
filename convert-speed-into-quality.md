---
layout: page
title: "Convert Speed into Quality: The AI Acceleration Pedal"
---

In the [Triple Loop Condition](triple-loop-condition.md) series of articles, I proposed ways to run engineering tasks at "AI inference speed" — as fast as AI allows.
But what if you are not interested in working faster, but rather in increasing quality?
It turns out that in many projects, speed converts directly into quality.

### The Gatekeeping Fallacy: Slowness does not produce Quality

You cannot review your way to quality, because many quality-problems are not visible at review time.
Half-broken edge cases and UX-gaps often surface once someone actually uses the software.
Quality is therefore a function of how many fix-iterations happen before a release, not only of how much care goes into each single iteration.
Hence, a gatekeeping-techlead may do a valuable job to prevent regression-errors, but at the same time, gatekeeping reduces the rate at which quality-problems get fixed.
If the job is only to preserve the stability of a legacy system, then pure gatekeeping can do its job well.
But for the launch of a new product, pure gatekeeping can lead to terrible quality, precisely because a uniform gate that slows down development also slows down the fixing of newly emerging issues.

### Death of Thousands Cut: Quality Collapse due to Slowness

Even a "safe" and battle-proven process can still produce terrible software.
I call this phenomenon "Death of Thousands Cut" software:
Software that functionally works, but is full of half-broken edge cases that are not fully fleshed out because the development team was not fast enough to fix all the UX-problems.
To avoid becoming rotten Death of Thousands Cut software, a delicate balance between "careful reviews" and "AI speedup" should be maintained.

### The AI Acceleration Pedal

To convert speed into quality, techleads should push the "AI acceleration pedal" on a case by case basis.
Thanks to agents, the acceleration pedal has a wide range: From reckless product-launches to slow nitpicking on every micro-decision.
Push the pedal harder, and you get a task done faster.
Push the pedal too hard, and you might run into severe architectural problems or even security breaches.

### The Trap of the "Sensible Midground"

It sounds rational to adjust the AI acceleration pedal at a "sensible midground".
But in practice, it often is not. 
A driver without a feeling for the new laws of physics takes every curve with "extreme slowness", no matter whether the curve is dangerous or not.
Or alternatively, the driver drives constantly too fast, until the driver gets brutally thrown out of a curve.
In both cases, the resulting quality tends to be terrible.
And a fixed midground is not a compromise between both failure modes, but a third failure mode: the same pedal position for every task, regardless of what the task can destroy.

### Blindness on Blast Radius

To drive the AI acceleration pedal in a sensible way, we should understand the blast radius of specific tasks.
In [Blast Radius](blast-radius.md), I introduced a spectrum of **symmetric** and **asymmetric** blast radiuses.
At the symmetric end, the pedal should be pushed harder, in favor of a fast resolution of newly emerging quality-issues or UX-problems.
At the asymmetric end, the acceleration pedal should be released, in favor of minimizing long term damage.
For products whose defects mostly surface after users touch them, only dynamic acceleration and braking achieve top-notch quality.

### Driving in Racing Mode

In desperate situations, a formal classification of blast radiuses might no longer make the cut — for example, a rapid startup pivot shortly before running out of funding.
Then the "individual genius wit" of a "10x engineer" comes into play, who is believed to be able to drive home a task at extreme speed without blowing up bridges in between.
However, relying on genius wit and "agentic intuition" is not a scalable management-strategy, but rather a last resort to save a project that is on the brink of dying.

### Driving Quality with E2E Tests

End-to-end tests are where the conversion of speed into quality becomes concrete, as a direct consequence of [verification loops](verification-traps.md).
In the agentic era, end-to-end tests are no longer merely a way to catch regression-errors, but they drive the speed of agentic verification loops right through the development.
A regression suite that used to require weeks of implementation can now be prototyped in a single afternoon, and such speed in test-generation accelerates quality and delivery-speed at the same time.

### Outlook

Let us use agentic forces to make systems work not only "somehow", but top-notch, with almost perfect user experience and performance.
Once a blast radius is mapped out, and specs and verification loops are set up, a task can be executed at unprecedented speed.
The freed up time can then be used to fix quality-issues that would otherwise be ignored and left around rotten in a "UX-backlog".
