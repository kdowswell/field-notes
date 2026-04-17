# Rubber Duck: Multi-Model Verification in Copilot CLI

*2026-04-17 • First entry*

GitHub dropped something interesting yesterday — a feature called **Rubber Duck** in Copilot CLI. It uses a second model from a different AI family as an independent reviewer of the agent's plans.

## What it does

When your primary model is Claude, Rubber Duck brings in GPT-5.4 as a critic. The second model reviews the plan before execution and flags potential issues. GitHub's eval shows it closes **74.7% of the performance gap** between Sonnet and Opus — just by adding a reviewer.

## Why this matters

This is multi-model orchestration baked into the tooling. The pattern isn't new — I've been building critic agents into enterprise pipelines for a while — but having it as a first-class feature in Copilot CLI is significant.

For enterprise teams, this is the right direction:
- **Defense in depth** — one model's blind spots are another's strengths
- **Audit trail** — the critique is logged, you can see why something was flagged
- **Cost optimization** — use a faster/cheaper primary model with spot-checking from a premium critic

## Trying it out

```bash
# Enable rubber duck in copilot CLI
gh copilot config set rubberDuck.enabled true
```

The critique shows up in the plan output. You can see exactly what the reviewer caught.

## What I'm thinking

This is going to become table stakes for any serious AI coding workflow. Single-model execution was always the "good enough" version. The interesting question is how teams tune the critic — do you want it paranoid or permissive? Different codebases will want different thresholds.

More experiments coming.

---

*Related: [GitHub Copilot CLI docs](https://docs.github.com/en/copilot)*
