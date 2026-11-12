<p align="center"><img src="assets/supersynergy-lockup.png" width="360" alt="SuperSynergy"></p>

# Maxim · AI Systems & Developer Tools Engineer

I build tools for engineers who use coding agents. Most of my work starts with a problem I hit myself: a session forgets a decision, a tool sends thousands of irrelevant tokens, or a worker marks a task complete before its check passes. I work primarily in Rust, Python and TypeScript.

## Selected work

- **Kept large attachments usable in Unsloth Studio.** When an attachment exceeded the model’s context budget, Auto mode could silently drop the entire document. My merged fix retrieves relevant passages and preserves the user’s explicit Off setting. [Unsloth PR #9630](https://github.com/unslothai/unsloth/pull/9630)
- **Measured the token cost of a leaner Codex workflow.** I built Agent Token Saver to trim repeated context and noisy tool output. Across three tasks, the provider reported 90,364 tokens with the tool versus 112,488 at baseline (**19.67% fewer**). All three task checks passed. Each arm ran once, and one task used more tokens. [Benchmark and per-task results](https://github.com/Supersynergy/agent-token-saver#benchmarks)
- **Improved browser automation in Moli.** Seven of my changes landed in this Rust browser. They include keeping the page loading after a startup script throws, fixing a debugger reconnect race, and reporting requests across redirects. [Script recovery](https://github.com/lexmount/moli/pull/1177) · [Reconnect fix](https://github.com/lexmount/moli/pull/2661) · [Redirect handling](https://github.com/lexmount/moli/pull/2663)

## Local-first agent infrastructure

**Synapse Memory** gives a fresh coding session a brief drawn from earlier decisions and bug fixes. The Rust CLI keeps dated notes and their sources in one SQLite file. [Try it with your first note](https://github.com/Supersynergy/synapse-memory#first-steps)

**Superiss** coordinates agents working on the same project. A worker claims a task, runs its acceptance check and attaches the passing result before closing it. The runnable example also shows what happens when a worker tries to close without proof. [Run the example](https://github.com/Supersynergy/superiss#try-the-complete-loop)

## Get in touch

For engineering roles or collaborations in AI infrastructure, developer tooling or local-first software, [start a conversation on my profile repository](https://github.com/Supersynergy/Supersynergy/issues/new). This is public, so a role link and a way for me to reply are enough.
