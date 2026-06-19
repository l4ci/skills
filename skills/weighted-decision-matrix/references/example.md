# Example: weighted-decision-matrix

**You invoke it with:**
> "Help me choose our new CRM with a weighted decision matrix."

**It needs from you:**
- DECISION + OPTIONS (required): which CRM to adopt, choosing between Salesforce, HubSpot, and Pipedrive
- CRITERIA (optional): total cost of ownership, ease of adoption, integration with our stack, reporting depth, scalability (with weights; if absent it derives them with you in Stage 1)
- CONTEXT (optional): budget ceiling of $40k/year, a 12-person sales team, must integrate with our existing Gmail and Slack

**You get back:** a saved markdown report (`weighted-decision-matrix-<decision-slug>-<date>.md`) with the calibrated criteria, weights, and scale up front, the scored matrix with weighted totals, per-option detail, a sensitivity check on whether the winner holds, and a recommendation with what would flip it.

**See a full worked example:** [weighted-decision-matrix-crm-2026-06-19.md](weighted-decision-matrix-crm-2026-06-19.md), the report this invocation produces.
