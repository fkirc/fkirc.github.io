Agentic UX: Are your tools already self-explaining?
Six years ago, I open-sourced the CLI-tool "attranslate".
"attranslate" was adopted by a few companies, but it required users to configure API-keys for Google Translate or DeepL-translations.
In 2026, those API-keys are no longer needed. Instead, coding-agents can do what was previously done by Google Translate. How does it work? attranslate explains to the agents how to invoke itself, and it serves as a deterministic guardrail.
So then it became clear to me: Consuming a traditional README-file may be a waste of token-spending. Instead, the new generation of CLI-tools should be designed as a self-explaining decision-tree for agents to walk through. Also an efficient MCP-server can be designed similarly, instead of being a replica of some REST-API.
With this, more tokens and human time can be spent on interesting problems instead of trivial tool-usage.