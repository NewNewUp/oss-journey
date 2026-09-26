Observations from ~100 candidate issues across 30+ repos in one week:

- Simple issues (typo, off-by-one, missing escape) have a median survival of
  1-5 hours. Agent swarms run 24/7; nothing obvious survives a day.
- What survives: issues needing source reading (root cause not in the issue),
  design trade-offs, or environment-specific reproduction.
- The counter-strategy is triage: 5-minute collision check (timeline
  cross-references, not keyword search — keywords miss), then commit only if
  the fix is small AND the reproduction is understood.
- Self-mergeable achievements (Quickdraw via the 5-minute PR, Pull Shark via
  your own tracker repo) are legitimate — the work they badge is real.
