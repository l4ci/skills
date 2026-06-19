# Example: root-cause-analysis

**You invoke it with:**
> "Run a root cause analysis, our checkout API has been timing out intermittently since last Tuesday"

**It needs from you:**
- EFFECT (required): "Checkout API returns 504 timeouts on roughly 3% of requests, only during the 12:00-14:00 traffic peak, since the Tuesday deploy on the 9th."
- CONTEXT (optional): "Software/service domain. We deployed a new recommendations sidecar that Tuesday. Latency dashboards, deploy logs, and DB slow-query logs are available. No infra capacity change."

**You get back:** a saved markdown report (`root-cause-analysis-<effect>-<date>.md`) with the verdict and lead countermeasures up front, the full fishbone across the 6 Ms, the 5-Whys chains for the strongest candidates, the verification of each claimed root cause against the timeline and data, and ranked countermeasures tied to the roots.
