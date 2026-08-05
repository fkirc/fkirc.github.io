---
layout: page
title: "Backends at Inference Speed: About the statefulness of blast radiuses"
---

In [Blast Radius](blast-radius.md), I introduced a distinction between symmetric and asymmetric blast radiuses.
Moreover, I highlighted that backend errors often have a destructive asymmetric blast radius: for example data corruptions or deeply entrenched performance problems.

### Correlation: Asymmetric Blast Radius and Statefulness

But why is that the case?
One of the patterns I observed is that errors with an asymmetric blast radius tend to originate in "stateful" code, whereas errors with a symmetric blast radius tend to originate in "stateless" code.
A frontend failed to comply with a design system rule? 
Re-run the generation loop and hit the refresh button.
A backend wrote corrupted data to your database, or to a third-party API?
Now you might face a painful remediation project to fix it.
Does that mean that stateless code is always safe?
No. The correlation is not an equivalence: stateless code can still cause asymmetric fallout, for example through a data breach or a published API contract that cannot be taken back.

### Stateless Backend Modules

So can we carve out modules of a backend that are stateless?
Yes, at least in some cases: Carving previously intertangled code into a stateless module not only lets us develop it at a higher speed, it can also make the system more robust as a whole.
Certain read-only endpoints can be carved out as stateless backend modules, as long as every consumer only renders the result instead of feeding it back into a stateful decision.
If an endpoint is only consumed for a certain page of a frontend, then it might be safe to treat it as "stateless". But if a GET-endpoint ends up influencing a stateful result within some other microservice, then we already lost the stateless-property.
The blast radius is therefore not a property of an endpoint alone, but of the endpoint together with all of its consumers.

### Risks That Statelessness Does Not Remove

To reduce performance risks, techniques like database read-replicas might be used, as well as re-using a set of cross-module functions that is deemed "safe" to call from a carved out module.
However, even if we have a perfectly stateless functionality that can be carved out, the risk of data breaches still needs to be kept strictly under control.
Data breaches are one of the most destructive asymmetric blast radiuses that exist, and not only because of the GDPR: unlike a regular error, a leaked record cannot be repaired by any remediation project.

### Idempotency as a Middle Ground

If a backend module cannot be made "stateless", it can be tried to make it at least "idempotent".
An "idempotent" operation is an operation that can be repeated without stacking up its effects: the terminal state follows the arguments of the latest call, not the number of calls that came before it.
Crucially, this means the arguments may be changed and fine-tuned between the calls, which is exactly what an agentic loop does.
As such, the idempotency-property can help to at least partially reduce the fallout if an operation went wrong.
Other properties work in a similar direction: state that can be rebuilt from a source of truth, or operations that can be reversed, both keep a failure closer to the symmetric end of the spectrum.

### How to Carve Out Backend Modules

I strongly emphasize: "carving out backend modules" does NOT mean spinning up a new microservice.
By default, a carve-out should happen within the same service, unless there is a strong reason for why it really needs to be a separate service.
Why? Because spinning up a new microservice can come with a whole bunch of new problems like eventual consistency, race conditions and latency.
Typically, a new microservice is only justified if it really has independent data ownership and a strong separation of business objectives, or if it needs an isolation boundary that a module inside the same service cannot provide, such as independent deploy and rollback.
Otherwise it might end up being the worst of the two worlds: A "distributed monolith".

So how do we carve out backend modules safely within the same service?
Some of the techniques for this were invented many years before the agentic era: modular build systems, code-owners within mono-repos, hexagonal architecture and domain driven design.
What makes them useful for agents is not only the modularity itself, but that a well-chosen boundary becomes machine-checkable.

### Caveat: Dependency Hygiene

As with almost any engineering work, dependencies need to be carefully selected and be kept under control.
We cannot let agents "go wild" on pulling in new code-packages or external APIs, because then we would be facing a massive supply chain threat and maintenance risk, no matter whether the backend modules are stateless or not.
This is not a contradiction to working at inference speed:
Dependency hygiene can be efficiently enforced with a combination of LLM-instructions, deterministic checks and senior reviews.

### Outlook

I see backend-architectures centered around blast radiuses and statefulness still underused, and the carving out still in its infancy.
Instead of carving out pre-existing functionality, I would rather suggest trying this technique on a completely new feature that is well-suited to be a stateless backend module.
That way, a carve-out can be probed with a quick return on investment, without risking regressions in pre-existing code.
