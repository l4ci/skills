# Example: pre-mortem

**You invoke it with:**
> "Run a pre-mortem on our plan to migrate the billing system to Stripe before the next renewal cycle"

**It needs from you:**
- PLAN (required): "Migrate all 40,000 subscription customers from our in-house billing engine to Stripe Billing over Q3, cutting over in a single weekend, then decommissioning the old engine."
- CONTEXT (optional): "Goal is zero billing interruptions. Failure means any customer charged the wrong amount or not at all, or a renewal that silently fails. Team of 4 engineers, hard deadline before the October renewal spike."
- HORIZON (optional): "The Monday after the October renewal run"

**You get back:** a saved markdown report (`pre-mortem-<date>.md`) with an executive summary, a ranked risk register scored by likelihood x impact, detailed mitigations and leading indicators for each critical and high risk, and the flagged blind spot.

**See a full worked example:** [pre-mortem-2026-06-19.md](pre-mortem-2026-06-19.md), the report this invocation produces.
