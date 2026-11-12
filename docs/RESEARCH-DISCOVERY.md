# Evaluating agents as MRI research partners

MRI Agent Bench aims to help the field measure progress from executing a research workflow to developing better
methods and producing new knowledge. An agent that can connect acquisition, reconstruction, physical models and
experimental evidence could help researchers explore questions that are difficult to pursue today.

This document proposes how to evaluate that ambition. **Core and Hard remain the current benchmark.** The research
evaluations below are a design proposal, with no active track, leaderboard or additional `mrab` submission format.

## Three questions, different evidence

| Evaluation | Scientific question | Evidence required | Status |
|---|---|---|---|
| Workflow execution | Can the agent complete a specified MRI task correctly? | Submitted artifacts, executable checks and the existing task criteria | Current Core and Hard evaluation |
| Method improvement | Can the researcher–agent team improve a method under defined constraints? | A prespecified comparison with strong baselines on held-out data, including uncertainty and total research cost | Proposed |
| Scientific discovery | Does the work establish a useful finding beyond what was known in the reviewed scope? | Prior-art assessment, a testable claim, discriminating experiments and independent validation | Proposed |

These are evaluation objectives, not a single ladder of difficulty. Replication can be demanding; a plausible new idea
can be easy to generate. A task pass, a higher metric or a persuasive explanation does not by itself establish a
discovery. The proposed evidence profile keeps those distinctions visible.

## Start with a research question

A challenge begins with an MRI researcher and an independent domain reviewer completing a
[research brief](templates/research-challenge.md). They define what is known, what remains uncertain, why resolving it
would matter, and what observation would support or refute the claim. A dated literature review identifies the closest
work and the strongest relevant baselines. Reviewers record conflicts of interest.

Useful starting points include:

| Question type | Example question to refine with experts | What would make the answer convincing? |
|---|---|---|
| Joint acquisition and estimation | Can a sequence and estimator together reduce tissue-parameter error at a fixed scan time and hardware limits? | Optimized component-wise baselines, checks of physical constraints, and testing across held-out tissue and nuisance conditions |
| Robust reconstruction | Can a method retain its advantage when acquisition settings or data distributions change? | Strong tuned reconstructions, matched calibration and compute, and evaluation on held-out acquisitions or sites |
| Experimental design | Which feasible acquisition best distinguishes two competing signal models? | A prespecified discrimination criterion, comparisons with established designs, and an independent experiment or simulation model |

These are illustrative public research directions, not assertions that a particular problem is new or unsolved.
Expert review must narrow each question and establish its prior art before it becomes an evaluation challenge.
Simulation supports development; claims about acquired MRI require appropriate acquired-data validation.

## Run a fair research comparison

1. **Freeze the protocol.** Specify the primary endpoint, meaningful improvement threshold, unit of analysis,
   uncertainty calculation, stopping rule and treatment of multiple comparisons. Separate confirmatory endpoints
   from exploratory findings before seeing evaluation results.
2. **Establish strong baselines.** Include tuned existing methods and, where feasible, an expert researcher using the
   same resources. For agent comparisons, hold the base model, tools and permitted human assistance constant.
   Account for the full research process: searches, failed experiments, tuning, model calls, compute, elapsed time and
   researcher effort. Match budget limits across arms and report actual use; one final inference cost is insufficient.
3. **Separate development from evaluation.** Allow iteration on development data. An independent evaluator controls
   the held-out data, seeds and final assessment. Restrict test feedback, record each evaluation access, and use new
   held-out material after an adaptive revision. Shared skills and memory must not contain evaluation answers or traces.
4. **Preserve the search history.** Record all started trials, candidate revisions, exclusions, failures and null
   results. Archive code, environments, data provenance and human decisions. Select the final candidate by a declared
   development rule; report uncertainty at the relevant independent unit, such as subject or acquisition, rather than
   treating correlated slices as independent evidence.
5. **Test the scientific explanation.** Use ablations and targeted controls to distinguish the proposed mechanism from
   extra compute, tuning, data access or another confound. A well-supported negative finding can resolve a scientific
   question even when it does not improve a performance metric.

## Report an evidence profile

The proposed output is a short research report with linked artifacts, rather than one discovery score.

| Dimension | Assessment |
|---|---|
| Validity | Executable checks, physical consistency, effect estimates with uncertainty, and controls that could falsify the claim |
| Novelty | Independent experts compare the precise claim with dated prior art; reviewers explain the difference and its scope |
| Importance | Domain experts explain what the finding enables or changes, with a prespecified practical threshold where possible |
| Generalization | Performance or explanatory power on untouched conditions, datasets, sites or hardware relevant to the claim |
| Efficiency | The complete research budget and its allocation, including human intervention and failed attempts |
| Reproducibility | A separate evaluator reproduces the result from the archived instructions; stronger claims need independent data or experiments |

Keep expert judgments, measured outcomes and unresolved questions separate. Conceal model and team identity during
expert assessment where feasible, disclose evaluator conflicts, and retain disagreements. Automated evaluators can
check artifacts; an LLM's novelty rating is not a substitute for an expert literature review or a replication.
Scope novelty claims to the literature reviewed and its cutoff date, rather than claiming an unqualified solution to
a problem no human has solved.

## Test whether experience improves research

[MRFoundry](https://github.com/KeWang0622/MRFoundry) provides research guidance and a process for turning local experience
into reviewed shared skills. To evaluate this process, compare three prespecified conditions: frozen guidance with a
fresh workspace, that guidance plus permitted project memory, and a reviewed guidance revision learned from separate
development work with a fresh workspace and no project memory. Freeze and hash each condition before evaluation;
match the model, tools, research budgets and human
assistance. Use independent workspaces and held-out research questions with no evaluation feedback shared between arms.

Report the cost of producing memory and reviewing revisions as well as the cost of using them. Show which change
affected which scientific outcome through ablations. A better result after one revision is evidence for that revision
under those conditions; repeated transfer to new questions is needed to support a broader self-improvement claim.

## Foundations and next step

[AlphaEvolve](https://arxiv.org/abs/2506.13131) combines code proposals with automated evaluation and evolutionary search.
[Co-Scientist](https://www.nature.com/articles/s41586-026-10644-y) develops hypotheses from researcher goals and prior
evidence, with experimental validation in selected applications.
[PaperBench](https://arxiv.org/abs/2504.01848) measures replication through detailed expert-developed rubrics.
Our design draws from these complementary approaches: executable evidence, explicit hypothesis testing, and assessment
criteria developed with researchers. This is a design inference, not a claim that their results transfer to MRI.

The next step is a small, independently reviewed pilot with published research briefs, a frozen protocol and an
evaluation-data access policy. It should establish reviewer agreement and the cost of replication before any new
leaderboard is introduced. Current benchmark submissions continue to follow [SUBMITTING.md](SUBMITTING.md).
