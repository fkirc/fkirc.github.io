Could agentic code improve supply chain security?
The $6.3 billion Binance breach highlighted a long-standing problem:
Employee notebooks and AI agents are often configured dangerously and irresponsibly.
Was it negligent misconduct for an engineer to do a job interview on their work machine, polluting it with code imposed by the interviewer?
Yes, but reducing the hack to one individual's negligence would be too shortsighted.
When ecosystems like Homebrew are under attack, the problem goes beyond individual negligence to a systemic threat.
So I believe we should drastically reduce the software installed on employee notebooks, especially for DevOps engineers, who are expected to have strong formal security education.
Running agents in isolated cloud containers already reduces exposure, which inspired my recent workshop on OpenHands Cloud Agents.
Another part of the solution is guardrailed agentic code generation.
Dependency lockfiles and strict rules on allowed dependencies can help agents reduce supply chain exposure. A large slew of external packages might become just a few thousand lines of agent-generated code. That code may not be perfectly clean, but it may be more secure than the packages it replaces.
I am optimistic that the Binance meltdown will eventually lead to more secure code generation setups.
