<p align="center"><img src="assets/supersynergy-lockup.png" width="360" alt="SuperSynergy"></p>

# Maxim · AI Systems & Developer Tools Engineer

I build tools for coding agents in Rust, Python and TypeScript. I also curate open-source software for people choosing what to build with. My collections answer questions I run into at work, from picking a model that fits a laptop to deciding how to test a faster database engine.

## Find a tool for the job

**Start with [Awesome Awesome Best of Repo Lists](https://github.com/Supersynergy/awesome-awesome-best-of-repo-lists)** if you’re exploring a field. It indexes 967 entries in 15 categories and has editions in 18 languages. For a specific decision, pick one of my specialist guides below.

| What are you trying to do? | Where I’d start |
| --- | --- |
| Choose an agent for code review or research, then see what you could run on your own hardware | [AI Agents](https://github.com/Supersynergy/awesome-ai-agents-2026) for the task. [Local AI Agents](https://github.com/Supersynergy/awesome-local-ai-agents) for runners, memory requirements and quantization. |
| Give a coding assistant a repeatable workflow | [Agentic Coding](https://github.com/Supersynergy/awesome-agentic-coding) for hooks and tests. [Awesome Skills](https://github.com/Supersynergy/awesome-skills) for reusable skills and their format. [Awesome Prompts](https://github.com/Supersynergy/awesome-prompts) for cookbooks and ways to evaluate a prompt. |
| Decide what to change in a slow service | [Software Gamechanger Stack](https://github.com/Supersynergy/awesome-software-gamechanger-stack) for parsers, queues and search engines. [Database Tools](https://github.com/Supersynergy/awesome-database-tools) for query performance, migrations and replication. [Server Stack](https://github.com/Supersynergy/awesome-server-stack) for proxies, caching and deployment. |
| Turn a dataset into a dashboard, or show the result in a video | [CodeDesign](https://github.com/Supersynergy/awesome-codedesign) for charts, maps and diagrams. [AI Video Editing](https://github.com/Supersynergy/awesome-ai-video-editing) for editing, audio cleanup and programmable video pipelines. |
| Build a prospecting workflow for a sales team | [AI Lead Generation](https://github.com/Supersynergy/awesome-ai-lead-generation) covers discovery, enrichment, verification, scoring and CRM integration. |

<details>
<summary>Browse all 15 catalog categories or query the data yourself</summary>

- **Building software** · Languages and ecosystems, AI and agents, data and APIs, starter projects.
- **Running software** · DevOps and cloud, self-hosting and homelabs, security and privacy, supply chain and licenses.
- **Applying software** · Business and SaaS, research and papers, public sector.
- **Finding other collections** · Meta-lists, best-of rankings, registries, official catalogs.

For example, to make a reading list for a self-hosted deployment, run this from a checkout of the catalog:

```sh
jq -r 'select(.cat == "selfhosted") | .url' data/sources.jsonl
```

[Browse by category](https://github.com/Supersynergy/awesome-awesome-best-of-repo-lists#contents) · [Catalog fields and examples](https://github.com/Supersynergy/awesome-awesome-best-of-repo-lists/blob/main/CATALOG.md)

</details>

## Supersynergy Field Notes

[001 · Why a large PDF could disappear from an Unsloth Studio chat](https://github.com/Supersynergy/Supersynergy/blob/main/field-notes/001-unsloth-attachments.md) — Two nearly identical requests meant different things. A 50,000-token test file shows where passage retrieval went missing.

## Selected work

- Kept large attachments usable in Unsloth Studio. When an attachment exceeded the model’s context budget, Auto mode could silently drop the entire document. My merged fix retrieves relevant passages and preserves the user’s explicit Off setting. [Unsloth PR #9630](https://github.com/unslothai/unsloth/pull/9630)
- Measured the token cost of a leaner Codex workflow. I built Agent Token Saver to trim repeated context and noisy tool output. Across three tasks, the provider reported 90,364 tokens with the tool versus 112,488 at baseline (**19.67% fewer**). All three task checks passed. Each arm ran once, and one task used more tokens. [Benchmark and per-task results](https://github.com/Supersynergy/agent-token-saver#benchmarks)
- Improved browser automation in Moli. Seven of my changes landed in this Rust browser. They include keeping the page loading after a startup script throws, fixing a debugger reconnect race, and reporting requests across redirects. [Script recovery](https://github.com/lexmount/moli/pull/1177) · [Reconnect fix](https://github.com/lexmount/moli/pull/2661) · [Redirect handling](https://github.com/lexmount/moli/pull/2663)

## Local-first agent infrastructure

**Synapse Memory** gives a fresh coding session a brief drawn from earlier decisions and bug fixes. The Rust CLI keeps dated notes and their sources in one SQLite file. [Try it with your first note](https://github.com/Supersynergy/synapse-memory#first-steps)

**Superiss** coordinates agents working on the same project. A worker claims a task, runs its acceptance check and attaches the passing result before closing it. The runnable example also shows what happens when a worker tries to close without proof. [Run the example](https://github.com/Supersynergy/superiss#try-the-complete-loop)

## Get in touch

For engineering roles or collaborations in AI infrastructure, developer tooling or local-first software, [start a conversation on my profile repository](https://github.com/Supersynergy/Supersynergy/issues/new). This is public, so a role link and a way for me to reply are enough.
