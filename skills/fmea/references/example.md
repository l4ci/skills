# Example: fmea

**You invoke it with:**
> "Run an FMEA on our new vaccine cold-chain delivery process before we roll it out"

**It needs from you:**
- SUBJECT (required): the end-to-end cold-chain process delivering temperature-sensitive vaccines from the regional depot to rural clinics, with BOUNDARY from depot dispatch to clinic refrigerator handover (manufacturing and in-clinic administration assumed reliable)
- TYPE (optional): process FMEA (PFMEA)
- CONTEXT (optional): two spoilage incidents last year traced to a failed cooler-box seal; clinics log fridge temps manually; a regulator requires documented risk controls before launch

**You get back:** a saved markdown report (`fmea-<subject-slug>-<date>.md`) with the full FMEA table (S/O/D, RPN, criticality per failure mode), the ranking with high-severity modes flagged, and a prioritized action plan naming whether each action cuts S, O, or D, plus target RPNs.
