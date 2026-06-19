# Example: tuckman

**You invoke it with:**
> "What Tuckman stage is my team at? We merged two squads three weeks ago and now it's all bickering."

**It needs from you:**
- TEAM (required): the eight-person platform engineering squad formed by merging the API and infrastructure teams
- CONTEXT (optional): merged three weeks ago, a new lead from the API side, standups now run long with open disagreement over on-call ownership, no decisions sticking

**You get back:** a saved markdown report (`tuckman-<team-slug>-<date>.md`) with a verdict and per-stage assessment table (match score and confidence per stage), the current stage and any regression, the leadership focus the stage needs, concrete moves to advance, and the one blocker in the way.
