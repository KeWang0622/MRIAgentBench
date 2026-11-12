# Research challenge brief

Use this template to propose an MRI research evaluation for the
[research and discovery direction](../RESEARCH-DISCOVERY.md). It is a planning document, not a current `mrab` task or
result-bundle format. Keep evaluator-only data, seeds, checks and all existing Hard material outside public documents.

## Question and scientific value

- Working title and domain:
- Research question, expressed as a testable claim:
- Why resolving this question matters for MRI:
- Closest prior work and strongest existing methods, with primary references:
- Literature search scope and cutoff date:
- Proposed contribution beyond that work:
- What result would refute the claim? What would a useful negative result establish?

## Protocol before experiments

- Primary endpoint, practical improvement threshold and unit of analysis:
- Secondary endpoints and exploratory analyses:
- Baseline implementations, tuning plan and expert researcher comparison:
- Hypothesis-specific controls and ablations:
- Development data sources, immutable identifiers/checksums, split rules and permitted literature/tool access:
- Held-out evaluation design, access policy, hash commitments and responsible independent evaluator
  (keep protected split identities and contents evaluator-only):
- Uncertainty, repeated-run, multiple-comparison and stopping plans:
- Required validation: simulation, acquired data, physical experiment or a combination:

## Resources and human contributions

- Model, agent, tools and environment versions:
- Per-arm limits for model calls, compute, wall time and researcher effort:
- Tuning and unsuccessful trials included in those limits:
- Human contributions permitted in each arm and how interventions are recorded:
- Candidate-selection rule, frozen candidate revision/hash and freeze date before final evaluation:
- If studying memory or guidance reuse: development provenance, frozen content hashes, separate workspaces,
  contamination checks and ablations:

## Review and replication

- Domain reviewers, relevant expertise and conflicts of interest:
- How identity-blinded assessment will be used where feasible:
- Novelty and importance review criteria, with space for disagreements:
- Evidence profile to report: validity, novelty, importance, generalization, efficiency and reproducibility:
- Independent replication team, required artifacts and replication criteria:
- Data permissions and any scientific or hardware safety review required:
- Release plan for code, environments, permitted data, all trial records and a report of null or negative findings:

## Decision record

- Protocol approval and frozen revision/date:
- Deviations and their reasons, recorded when they occur:
- Outcome: supported, refuted or unresolved claim, with evidence links:
- Scope supported by replication and remaining questions:
- Follow-up question or proposed guidance contribution:

Complete the outcome fields after evaluation. Keep hypotheses, observed findings and future plans distinguishable.
