# five-dysfunctions-of-a-team

Diagnoses why a working team underperforms using Patrick Lencioni's model from *The Five Dysfunctions of a Team* (2002). The five dysfunctions form a pyramid: Absence of Trust at the base, then Fear of Conflict, Lack of Commitment, Avoidance of Accountability, and Inattention to Results at the top. The order matters: each layer rests on the one below, so conflict needs trust, commitment needs conflict, accountability needs commitment, and results need accountability.

This skill runs the assessment in parallel. Five analyst subagents each take one layer, compare the team against that layer's specific tells with concrete behavioral evidence, and score how present and severe the dysfunction is. A synthesis pass then reads the pyramid bottom to top, finds the lowest broken layer, and traces how that crack surfaces as symptoms higher up. The output is a saved markdown report with the pyramid scored layer by layer, the binding constraint named, the cascade explained, and interventions sequenced from the base upward.

The model gets misused in three ways, and the skill guards all three. People treat the five as independent checkboxes and sum the scores, missing the hierarchy entirely. People chase the surface symptom ("we need more accountability") when the real break is trust two layers down, so the fix never takes because its foundation is missing. People diagnose from a feeling rather than from observed behavior. The skill scores every layer against evidence, traces high-layer symptoms down to find the lowest break, and prescribes a rebuild in pyramid order rather than at the top. It pairs with psychological-safety for the trust base and tuckman for developmental stage.

## Starting

**You provide:** one defined working team to diagnose; observable behaviors and symptoms you've noticed are optional but sharpen the read. Something like "diagnose my product leadership team with the Five Dysfunctions model".

See [references/example.md](references/example.md) for a worked example.

The procedure is in [SKILL.md](SKILL.md); the pyramid, the hierarchy rule, each layer's tells and interventions, and the failure modes are in [references/five-dysfunctions.md](references/five-dysfunctions.md).
