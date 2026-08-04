A few days ago, I described "symmetric vs. asymmetric blast radius" for agentic engineering: frontend errors are usually cheap to undo, backend errors often are not.
What I could not answer yet: how to restrict blast radiuses within backend engineering.
After a discussion with redacted and redacted, it became clear to me that blast radius correlates strongly with statefulness: stateless code can simply be re-run, whereas stateful code leaves damage that outlives the code that caused it.
The practical consequence is to carve out the parts of a backend that can be made stateless — if possible within the same service, not as a new microservice.
Now I am optimistic that backend engineering can be made faster and more robust at the same time.
Full article in comment below.
