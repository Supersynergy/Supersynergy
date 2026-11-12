# When less context costs more

*Supersynergy Field Note 002 · Maxim · November 12, 2026*

My compact Codex setup used 42% fewer tokens to inspect a large Git diff. I gave the same setup a process table and usage went **up 32%**. Both answers passed their checks. I wanted to know where the extra work came from.

## Three tasks, measured to the same finish line

On July 15 I ran each task twice, once with the hooks disabled and once with Agent Token Saver’s compact prompt and Stop hooks enabled. Each pair used the same model, prompt and acceptance check, with a fresh home directory for each run. The figures below are total tokens reported by the provider.

| Task | Baseline | Compact | Change |
| --- | ---: | ---: | ---: |
| Inspect a process table | 29,359 | 38,800 | **32.16% more** |
| Inspect a large Git diff | 44,629 | 25,886 | **42.00% fewer** |
| Inspect Git history | 38,500 | 25,678 | **33.30% fewer** |
| **Total** | **112,488** | **90,364** | **19.67% fewer** |

The two Git tasks saved 31,565 tokens between them. The process task spent 9,441 extra. Looking only at the total would have hidden the one workflow I most wanted to inspect. [Original results and run logs](https://github.com/Supersynergy/agent-token-saver/tree/ad5d0fa10f7f31505ca66ec90e9e1f3aad633300/data/benchmarks/codex-provider-ab-2026-07-15/compact-policy)

## Follow the extra command

The baseline ran `ps -ef` once. The compact run started with `ps aux`, then ran `ps aux` again with an `awk` filter. By the time it asked for a narrower answer, it had already requested the broad output. Of the 9,441 extra tokens, 9,168 were on the input side. The trace gives me a place to investigate, but it cannot tell me how much of the difference that second command caused.

I tried changing the instructions for the first command. That follow-up produced a compact run, but the baseline hit an account usage limit. There was no completed pair to compare. [Follow-up result](https://github.com/Supersynergy/agent-token-saver/blob/ad5d0fa10f7f31505ca66ec90e9e1f3aad633300/data/benchmarks/codex-provider-ab-2026-07-15/compact-policy-v2-process/result.md)

## What I’d test next

For the process task, I’d ask for the required fields in the first command. I’d keep the same acceptance check and repeat both configurations in alternating order. One run per configuration tells me where to look. Repeated runs would show whether the change holds. If the decision is about speed or money, I’d also record elapsed time and billed cost. This comparison measured tokens.
