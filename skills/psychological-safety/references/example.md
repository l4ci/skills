# Example: psychological-safety

**You invoke it with:**
> "Diagnose the psychological safety on our platform engineering team, people have stopped raising concerns in incident reviews"

**It needs from you:**
- TEAM (required): "The 7-person platform engineering team led by Dana, who runs the on-call rotation and the weekly incident review."
- SIGNALS (optional): "In the last three incident reviews only Dana and two seniors spoke. A junior who pushed a bad config stayed silent for two days before admitting it. Bad news tends to surface in 1:1s, never in the room."
- CONTEXT (optional): "We just had a Sev1 outage and leadership wants a blameless retro culture. The team is held to a strict 99.95% uptime SLO."

**You get back:** a saved markdown report (`psychological-safety-<team>-<date>.md`) with a verdict and dimension scoring table, the climate read across all five dimensions, the team placed on the safety-by-accountability 2x2, leader and team interventions, and indicators to watch.

**See a full worked example:** [psychological-safety-platform-eng-2026-06-19.md](psychological-safety-platform-eng-2026-06-19.md), the report this invocation produces.
