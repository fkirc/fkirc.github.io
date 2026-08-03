I spotted a species of "slop-creature" in the wild: the so-called **local MCP**.

To zoom out for a moment: Peter Steinberger and others criticized MCP as inefficient and inflexible, arguing that Command Line Interfaces (CLIs) are often the superior alternative. Under certain conditions, I agree. CLIs can be chained together naturally with shell commands, allowing agents to construct highly efficient, ad hoc pipelines.

But does that make MCP obsolete or bloated legacy technology? I don't think so.

MCP still fills an important role as a standardized interface for **remote APIs** designed for agentic consumption—especially with the latest version of the MCP-spec, which has become more enterprise-friendly. Compared to CLIs, remote MCP servers avoid many of the maintenance and supply-chain threats that come with distributing and executing local binaries.

The only category that strikes me as genuine "slop" is the **local MCP**. Local MCPs seem to have become popular largely through copy-pasted template code. In doing so, they manage to brilliantly combine the disadvantages of both worlds: the relatively rigid interaction model of MCP with the maintenance burden and supply-chain risks associated with local CLI tools.
