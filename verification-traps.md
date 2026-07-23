---
layout: page
title: "Verification Traps: Rotten feedback loops destroy AI at inference speed."
---

Within the [Triple Loop Condition](triple-loop-condition.md), I established that self-correcting **verification loops** are essential to execute tasks at inference speed.

Typically, verification loops are needed because a non-trivial engineering task won't be correct on the first try.
Introducing a verification loop can sometimes feel like unlocking a new "super power," because it can make the difference between generating a faulty draft and a fully working deliverable.

However, I observed that many projects are running with inefficient or broken verification loops.
This article lists such examples below, with the goal of developing a smell for broken verification loops.

### Inaccessible Logs

For agentic verification loops to work, having logs available to agents is essential.
Manually copy-pasting error-logs is a fatal flaw because it often strips away critical debugging context.
Fortunately, this is often easy to fix with custom skills, e.g. by instructing an agent to launch a "dev-server" in agentic mode rather than using any external terminal.

### Over-Reliance on Unit Tests

Having a large suite of agent-generated unit tests is a powerful way to prevent regression errors.
However, relying solely on unit tests can create two fatal flaws in verification loops:
First, freshly generated tests might be too influenced by what the agent assumed about the task.
And secondly, by creating a huge mesh of "mocked values", the unit tests might be too far away from the actual end goal of the task.

### Non-Existing End to End Loops

Even some projects with near 100% unit test coverage might lack ways to verify end-to-end functionality, crippling an agent’s ability to autonomously deliver working results.
For example, if a project can only be tested by deploying to a staging environment after code review, the end-to-end loop is broken: the agent has to wait on a human reviewer before it can even see whether its own change worked.

How to fix it?
My recommendation is not to spend weeks building massive end-to-end test suites, but rather to generate small testing scripts on-demand.
In case those scripts are deemed as "stable", then the scripts may be cleaned up and taken over into a permanent CI/CD pipeline, otherwise the scripts may be thrown away once the agent finished its task.

Special case for frontends: it is critically important that the agent has direct control of a web browser, e.g. with Playwright-CLI, so it can see the rendered result itself — for example via screenshots — instead of relying on a human to check the UI.

### Highly Expensive End to End Loops

For some projects, end to end loops consume an unacceptable amount of time or token-budget.
For example, I observed frontend-projects where every page-reload navigated away to a different page, creating massive token-consumption when navigating back to the original page.
Similarly, I observed backend projects where killing and restarting the project took massive overhead, and where a "hot reload" was not available either.
But luckily, many such problems can be solved with simple engineering workarounds.

### Manual Approval Fatigue

When doing long-running work, hitting "enter" to manually approve commands dozens of times has never been an effective security practice and never will be.
With automated verification loops, this babysitting of agents becomes completely unacceptable.
If a command is considered "dangerous", then it should be either forbidden completely or moved into a sandbox environment.
Sandbox environments for agents would warrant their own article, but are out of scope for this.
Also in many cases, a few "dangerous" commands can be easily swapped out with less dangerous commands.


### Web-Obsessed CI/CD Pipeline

CLI-tools are best friends of agents, because they're highly efficient in scriptable verification loops.
Having checks that only exist behind a web UI — with no CLI equivalent — was already painful before the agentic era. Now it's unacceptable, since an agent does not want to click through a dashboard.
Whatever gets checked in CI/CD should be checkable through an agent-compatible CLI-tool.


### Markdown-Slopped Fake Verifications

Markdown-slopped verifications are a new type of micro-managing that I see emerging in AI-engineering.

The pattern goes as follows:
Instead of doing the real engineering work to set up a verification loop, it is much easier to slop in a large markdown document that contains statements like:

```
" Verify if checkboxes in the spec are fulfilled and tick them! "
" You are a highly cautious engineer! "
" Never deviate from the specs! "
```

And hundreds of other instructions that can be slopped in by a framework like "spec-driven development".
None of this provides any concrete instructions on how to call a project-specific test suite or validation script; instead the agent's context gets flooded with hyper-generic instructions on how to be "careful", distracting the attention from the actual task to solve.

### Context-Flooding with Trivial Requirements

Another related anti-pattern is to flood an agent's context with a massive list of trivial requirements like this:

```
" Namings must be snake-case! "
" No unused imports! "
" Do not leave unneeded console logs! "
```

And so on, distracting agents from the core task to solve.
To avoid such context-flooding, CLI-tools are best friends of agents because they can serve as highly efficient safety gates.
Once enforced, agents naturally follow the rules simply by mirroring existing codebase patterns.

### Mutilation of Errors

The practice of mutilating or hiding errors to make them "cleaner" was already questionable before, but now it becomes completely unacceptable in the agentic era.
A verification loop needs to have access to the unedited root cause of an error.
If "cleaning" is needed, then said cleaning can be done at the very last mile of UI-rendering — i.e., only in how the error is displayed to the user, never in the underlying data an agent sees.

### Next: Blast Radius

Congratulations if you got a working verification-loop.
You can now finish a task at inference speed.
However, to avoid doing so in a reckless and damaging way, it may be time to think about the [Blast Radius](blast-radius.md).
