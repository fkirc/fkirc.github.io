---
layout: page
title: "Blast Radius: Symmetric vs. asymmetric fallout when things go wrong"
---

In the [Triple Loop Condition](triple-loop-condition.md), I established that working at inference speed is only possible in a responsible way if the blast radius can be limited to an "acceptable risk".
With "blast radius", I include both short-term risks (e.g. immediate system failures), but also long-term risks (e.g. maintenance risks).

### Symmetric vs. Asymmetric Blast Radius

I define "blast radius" as the fallout from an error that slipped past the verification loop from C2 unchecked, or a risk that might not (yet) be possible to risk-score within a verification loop at all — for example, long-term organizational risks.
I further distinguish two kinds of blast radius: symmetric and asymmetric.

A **symmetric** blast radius is low-effort to fix: a tweak to the verification loop (e.g. a hint added to the agent's context, or a new code-check), or sometimes just a one-off prompt that rectifies the specific error without changing anything about the agentic setup.

An **asymmetric** blast radius is one where the damage is so destructive that repairing it takes vastly more effort than the effort that was spent to execute the initial task.
Asymmetric blast radius deserves special attention: it's exactly the case where a gap in verification produces damage wildly out of proportion to the fix that would have prevented it.

What follows is a list of case studies on how to evaluate the blast radius of a task.

### Modular Frontends

Frontends can often be modularized in a way to have very well-defined blast radiuses.
It is relatively easy to set up frontend generation loops in a way to prevent dependency hell and to keep supply chain threats under control (within industry standards).
Also the risk of frontend performance regressions can be efficiently reduced with packages like TanStack or RxJs. 
More details on that are in the article [Frontends at Inference Speed: Agent-friendly CSS Styling](frontend-at-inference-speed.md).

### Isolated Backend Modules

Compared to frontend tasks, I see it as significantly more difficult to restrict blast radiuses for backend tasks.
Especially since many backend errors have an asymmetric blast radius — e.g. data corruption, personal data breaches, or deeply entrenched performance degradations that can only be fixed via major re-architecting — whereas frontend errors tend to have a more symmetric blast radius (e.g. fixing a design-system noncompliance).
Nevertheless, a few isolated backend modules might still be generated at inference speed if the architecture is tuned for this.
It is still an open question to me how well a blast radius can be restricted for sub-modules in backend engineering (with realistic efforts).

### Utilities or Helper Tools

In many cases, CLI-tools or utility scripts that are decoupled from "core systems" have a smaller blast radius, and whatever errors occur in such tools tend to have a symmetric blast radius.
Hence, many of such tools can be generated without caring too much about the exact implementation, but rather limiting the used packages to guard against supply chain attacks.

### DevOps / Platform Engineering

AI agents can assist very well with technologies like Terraform or Kubernetes.
However, the blast radius in DevOps may be enormous and asymmetric, including security-breaches or destructive downtime.
Therefore, it might still be a dangerous illusion to operate a large DevOps organization at inference speed.

### Database Schemes

In early-stage pre-MVP startups, it might be exactly the right strategy to iterate quickly on database schemes at inference speed.
However, for large-scale organizations, the blast radius of that practice becomes unacceptable and asymmetric, due to risks of data corruptions, technical debt and performance collapse.
Therefore, I still see strict human supervision as necessary for large scale databases.

### Microservice Boundaries

In large organizations, the boundaries between microservices are not purely technical, but are also influenced by political structures.
Moreover, the blast radius of wrong microservice boundaries may be enormous and asymmetric.
If the sprawling of new microservices is completely uncontrolled at inference speed, then the organization might succumb to "Conway's law".
In the worst case, a system might collapse into a "distributed monolith".
To avoid such collapse, it might be the case that human review committees with veto power are needed, and this is a task that an AI at inference speed cannot (yet) fulfill.

### Framework Choices

Framework choices are not only driven by technical merits, but also by isolated human preferences.
A complete lockdown on new frameworks would stifle innovation, but at the same time I argue that an organization might end up with a Frankenstein zoo of languages if those choices are done at inference speed.

### External Code-Dependencies or API Integrations

External dependencies can potentially have a huge blast radius, stickiness and security impact.
So, any piece of external code may need extensive architecture reviews that cannot be (yet) done at inference speed.

### Hyper-Fragile Side Effects

If a system is a fragile house of cards, where every change in one module might arbitrarily trigger regressions in other modules, then ask yourself:
Are those side effects a necessary complexity of the task at hand, or is the software just a fragile spaghetti mess of garbage?
If the latter is the case, then we should not blame AI for being "not good enough".
Instead, the code would need to be modularized into a non-rotten state, before any work at inference speed can be started in a safe way.

### Conclusion

Congratulations if you made it through all three conditions: spec, verification, and blast radius.
You have now unlocked the real power of AI at inference speed.
But stay careful: blast radius is not a fixed property of a task; it depends on the surrounding environment.
If that environment changes — for example, a new level of scale, new dependencies, or previously unknown threats — the blast radius should be re-evaluated before trusting inference speed again.
