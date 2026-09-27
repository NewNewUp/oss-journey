# 🚀 My OSS Journey

Live tracker of my open-source contributions across the AI / Agent ecosystem.

> Built with [GitHub Copilot-style agent workflows](https://github.com/features) — every PR below is a real fix, verified locally and tracked to merge.

## Open Pull Requests

| # | Repository | Fix | Status |
|---|---|---|---|
| 1 | [langgenius/dify#42658](https://github.com/langgenius/dify/pull/42658) | Reuse MCP client connections across tool invocations (237-line pooled manager, 866 tests green) | 🔎 In review |
| 2 | [agno-agi/agno#10406](https://github.com/agno-agi/agno/pull/10406) | Bound PgVector upsert peak memory (embed batch-by-batch) | 🔎 In review |
| 3 | [langchain4j/langchain4j#6483](https://github.com/langchain4j/langchain4j/pull/6483) | Restore interrupt status in WorkersAiEmbeddingModel | 🔎 In review |
| 4 | [pola-rs/polars#29555](https://github.com/pola-rs/polars/pull/29555) | str.zfill counts characters instead of utf-8 bytes | 🔎 In review |
| 5 | [pola-rs/polars#29556](https://github.com/pola-rs/polars/pull/29556) | str.to_titlecase matches Python title casing (İ, ß) | 🔎 In review |
| 6 | [agentscope-ai/agentscope-java#3304](https://github.com/agentscope-ai/agentscope-java/pull/3304) | Emit renamed enum values in tool schemas | 🔎 In review |
| 8 | [ArcadeData/arcadedb#8475](https://github.com/ArcadeData/arcadedb/pull/8475) | Scalar left operand of CONTAINSANY silently matched nothing | 🤖 CI 21 pass |
| 9 | [lingdojo/kana-dojo#31077..31084](https://github.com/lingdojo/kana-dojo/pull/31077) | Community content entries (proverb, fact, mistake, etiquette, dialect, theme) | 🎁 GFI channel |
| 7 | [wagga40/Zircolite#154](https://github.com/wagga40/Zircolite/pull/154) | Escape file names in Rich markup output | ❌ Closed — upstream fixed it independently (see #158) |

## Diagnosis-first workflow

```
scan → verify issue is real & unclaimed → read the source → root-cause →
minimal fix → repo's own lint/format/tests → PR → respond to review with evidence
```

Fun fact: my first "PR" ever closed within 5 minutes — that's how the 🤠 Quickdraw badge happened.
