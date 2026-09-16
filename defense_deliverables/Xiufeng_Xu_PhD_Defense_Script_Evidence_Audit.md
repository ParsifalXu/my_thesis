# Evidence Audit for the PhD Defense Script

## Scope

- Audited artifact: `Xiufeng_Xu_PhD_Defense_Script_Refined.docx`
- Content source used for slide-level matching: `.codex_thesis_defense_build_v2/deck-content.json`
- Primary evidence: the dissertation LaTeX sources in `mythesis.tex` and `Chapters/`
- Audit date: 30 July 2026
- This audit checks factual support, numerical accuracy, scope, experimental context, and whether synthesis is presented as direct evidence.

## Verdict

All quantitative results in the script are traceable to the dissertation and were reproduced accurately. No fabricated dataset size, metric, project count, issue count, or performance result was found.

The script is nevertheless not a sentence-by-sentence paraphrase of the dissertation. It contains legitimate narrative synthesis, especially in the opening, transitions, and conclusion. Most synthesis is faithful, but several statements should be tightened so that three separately evaluated studies are not presented as one empirically integrated pipeline, and so that experimental results retain their model, benchmark, metric, and subset qualifiers.

| Classification | Slides | Meaning |
|---|---:|---|
| Supported | 2, 5, 6, 7, 9, 12, 13, 18 | Directly supported or a faithful synthesis with no material correction required |
| Tighten | 8, 11, 17, 19, 20, 21, 22 | Substantively supported, but terminology or scope should be made more precise |
| Revise | 1, 3, 4, 10, 14, 15, 16, 23 | Wording can overstate causality, attribution, paper count, or experimental scope |

## Evidence Standards

- **Direct support**: the dissertation states the claim or reports the result.
- **Faithful synthesis**: the wording is not present verbatim, but it accurately combines or interprets multiple supported points.
- **Needs revision**: the wording is broader, more causal, more absolute, or less qualified than the dissertation supports.

## Slide-by-Slide Audit

### Slide 1 — Enhancing Software Evolution Reliability through Neurosymbolic Reasoning

**Verdict: Revise.**

The central claim—reliable software evolution needs neural flexibility, reproducible evidence, and formal reasoning—is supported by `mythesis.tex:399-407` and `Chapters/Chapter1.tex:47,56`.

The one-line dependency-version change and paired compatible/incompatible states are supported by `Chapters/Chapter3/03.usage.tex:18-25`; the empty-string-to-null failure is supported by `Chapters/Chapter3/02.background.tex:12`.

The current opening makes one dependency upgrade appear to be followed empirically through failure, localization, and documentation drift. The dissertation evaluates these as separate studies rather than following the same instance through an integrated end-to-end pipeline.

**Recommended replacement**

> A one-line dependency change can alter library behavior and break a downstream client. Repairing such failures then raises two further lifecycle challenges: locating the relevant logic and keeping delivered documentation consistent with behavior.

### Slide 2 — One-line changes ripple across dependencies

**Verdict: Supported.**

The continuous nature of software evolution and the reactive/proactive distinction are supported by `Chapters/Chapter1.tex:17-18,31-36`. The reported PyPI figures—approximately 380,000 packages, 2.6 direct dependencies, and 129.6 transitive non-unique dependencies—are stated in `Chapters/Chapter1.tex:20`. The three lifecycle phases are supported by `Chapters/Chapter1.tex:31-36`.

### Slide 3 — LLMs accelerate change—not correctness

**Verdict: Revise.**

The dissertation supports the claims about natural-language understanding, code generation, repair, documentation maintenance, hallucination, and lack of dependable logical reasoning in `Chapters/Chapter1.tex:41,45,47` and the neural/symbolic division in `Chapters/Chapter2.tex:170-190`.

The title can be read as saying that LLMs do not produce correct results. The dissertation's narrower claim is that probabilistic generation does not guarantee correctness. Likewise, “logic determines what must be true” is more absolute than the source's “constrain, guide, and verify.”

**Recommended replacements**

- Title: `LLMs accelerate change—but do not guarantee correctness`
- Principle: `Formal logic constrains and verifies what must hold`

### Slide 4 — One lifecycle, three reliability anchors

**Verdict: Revise.**

The three lifecycle phases and the roles of CompSuite, DataLoc, and MPChecker are supported by `mythesis.tex:399-405` and `Chapters/Chapter1.tex:31-36,60-62`.

The phrase “the thesis through three papers” is inaccurate as a count. The authorship declaration states that the thesis contains material from three published peer-reviewed papers and one completed manuscript under review; Chapter 3 itself incorporates material from two publications (`mythesis.tex:273-284`).

**Recommended replacement**

> I will present the thesis through three core studies, following the software-evolution lifecycle rather than publication chronology.

Use **three core studies** or **three principal research contributions** consistently on Slides 4, 16, and 21.

### Slide 5 — 01 / PERCEIVE · CompSuite

**Verdict: Supported.**

The purpose and novelty of CompSuite are supported by `Chapters/Chapter3/01.introduction.tex:6-16,29,32-39`. Isolation through one-at-a-time upgrades and manual validation is supported by `Chapters/Chapter3/02.background.tex:146-166`.

For maximum fidelity, “causally isolated” may be replaced with “isolated, manually validated, and executable,” but the present wording is a defensible synthesis.

### Slide 6 — Upgrades fail at the client boundary

**Verdict: Supported.**

Behavioral changes despite unchanged APIs, the empty-string-to-null example, and client-specific outcomes are supported by `Chapters/Chapter3/02.background.tex:4-12`. The limitations of existing datasets are supported by `Chapters/Chapter3/01.introduction.tex:27-29`, and the proposed evaluation uses are supported by `Chapters/Chapter3/04.app.tex:3-18,61-72`.

### Slide 7 — CompSuite isolates one upgrade and one test

**Verdict: Supported.**

Project selection, base-commit validation, one-library-at-a-time upgrading, manual confirmation, preserved metadata, paired states, and CompRunner are all directly supported by `Chapters/Chapter3/02.background.tex:60-90,105-117,146-166,192-204` and `Chapters/Chapter3/03.usage.tex:13-25,58-77`.

### Slide 8 — Executable evidence makes upgrade risk measurable

**Verdict: Tighten.**

The figures 123 reproducible cases, 88 clients, and 104 libraries are correct (`Chapters/Chapter3/01.introduction.tex:71-74`; `Chapters/Chapter3/02.background.tex:97-99`). Manual validation and single-command reproduction are supported by `Chapters/Chapter3/02.background.tex:157-166` and `Chapters/Chapter3/03.usage.tex:63-77`.

“Every accepted instance was manually validated” is supported. A visible ratio such as “123/123 manually validated,” however, is an inferred presentation rather than a statistic reported in that form.

The sentence “CompSuite is not, by itself, a neurosymbolic algorithm” is not stated in the dissertation and unnecessarily weakens the unifying framing.

**Recommended replacement**

> CompSuite provides the empirical foundation of the thesis: it makes external evolution risk reproducible and measurable before AI reasoning begins.

If the slide displays `123 / 123`, change it to `All 123 manually validated`.

### Slide 9 — 02 / LOCATE · DataLoc

**Verdict: Supported.**

Localization without explicit naming hints and the LLM–Datalog architecture are directly supported by `Chapters/Chapter5/01.introduction.tex:4,12`. “A failing test is an oracle, not a map” is a faithful transition rather than a quotation or empirical claim.

### Slide 10 — Benchmarks can reward naming shortcuts

**Verdict: Revise.**

The Keyword Shortcut, the prevalence of identifying information in SWE-bench Lite, and the query involving functions with more than 15 parameters excluding `__init__` are supported by `Chapters/Chapter5/01.introduction.tex:2,4-6`, `Chapters/Chapter5/02.background.tex:59-60,75-78`, and `Chapters/Chapter5/04.evaluation.tex:23`.

“No file names, no function names” is imprecise because the query contains `__init__`, although it does not provide the target function name. Positive KA-LogicQuery instances are constructed to have at least one answer; abstention is tested by the separate negative benchmark (`Chapters/Chapter5/04.evaluation.tex:19,25`).

**Recommended replacements**

- `No target file or target function names; no stack trace or code fragment.`
- `Reason over repository structure; negative variants test abstention.`

### Slide 11 — KA-LogicQuery removes names and keeps structure

**Verdict: Tighten.**

The 225 instances, nine repositories, independent verification by two authors, and negative benchmark are supported by `Chapters/Chapter5/04.evaluation.tex:19,21,25,64-65`.

The dissertation says “25 representative combinations,” not “25 templates.”

**Recommended replacement**

> 25 representative query combinations × 9 repositories

If space permits, state that ground truth is evaluated at file, module, and function levels.

### Slide 12 — DataLoc translates intent into inspectable Datalog

**Verdict: Supported.**

The two-stage architecture, Python AST facts, source locations, repository relations, LLM translation, and Soufflé execution are supported by `Chapters/Chapter5/03.methodology.tex:15,19,22,24,29` and `Chapters/Chapter5/01.introduction.tex:8,12`.

“Deterministic for a given fact set and Datalog rule” is a properly qualified inference and should retain that qualification.

### Slide 13 — Generated logic is checked before it is trusted

**Verdict: Supported.**

The synthesize–check–refine loop, parser gating, conservative repair, diagnostics, intermediate row counts, mutation probes, candidate verification, and no-match behavior are supported by `Chapters/Chapter5/03.methodology.tex:35-36,60-61,88-97,126-128,239-280` and `Chapters/Chapter5/01.introduction.tex:14`.

The qualification “relative to the extracted facts and synthesized rule” is essential and accurate.

### Slide 14 — Datalog improves precision—and enables abstention

**Verdict: Revise.**

The numerical results are correct: 73.35% file precision, 48.44% file-level Perfect Localization Rate, 38.27% function-level Perfect Localization Rate, zero function-level PLR for the evaluated baselines, and more than 70% correct no-match responses (`Chapters/Chapter5/041.rq1.tex:3,9,27-48`). The 274 retained SWE-bench Lite instances and 81.02% file-level Acc@5 are supported by `Chapters/Chapter5/04.evaluation.tex:17` and `Chapters/Chapter5/042.rq2.tex:35-36`.

The experiment evaluates the complete DataLoc system; it does not establish a Datalog-only causal effect. The headline should therefore attribute the result to DataLoc. The KA-LogicQuery results must also retain the Qwen3-Max context.

**Recommended replacements**

- Title: `DataLoc improves precision—and enables abstention`
- Context label: `KA-LogicQuery · DataLoc with Qwen3-Max`
- Negative result: `>70% correct no-match responses on KA-LogicQuery-Neg`
- SWE-bench result: `81.02% file-level Acc@5 on 274 retained SWE-bench Lite instances`

### Slide 15 — Reusable inference replaces repeated exploration

**Verdict: Revise.**

The 39.3 seconds and 16.2k tokens per query are correct for DataLoc with Claude-3.5 on KA-LCL (`Chapters/Chapter5/043.rq3.tex:2,25`). The 81.02% file-level Acc@5 and approximately two candidates refer to SWE-bench Lite (`Chapters/Chapter5/042.rq2.tex:5,35-36,45`).

The Qwen3-Max ablation values—18.20%, 38.93%, and 55.20% function-level precision—are correct, but that ablation uses only the representative first 25 queries (`Chapters/Chapter5/044.rq4.tex:8-16,48-51`), not all 225 instances.

**Recommended replacements**

- `39.3 s/query · 16.2k tokens/query — DataLoc with Claude-3.5 on KA-LogicQuery`
- `81.02% file-level Acc@5 with ≈2 candidate locations on SWE-bench Lite`

**Recommended script sentence**

> On the representative first-25-query ablation subset, Qwen3-Max function-level precision rises from 18.20% in Base, to 38.93% with validation and repair, and to 55.20% in the Full configuration.

### Slide 16 — 03 / VERIFY · MPChecker

**Verdict: Revise.**

The transition to documentation consistency is supported by `Chapters/Chapter1.tex:36,52` and the MPChecker contribution by `mythesis.tex:403`.

Change “The third paper” to “The third core study” for consistency with the authorship declaration and Slide 4.

### Slide 17 — Documentation defines cross-parameter contracts

**Verdict: Tighten.**

Documentation as a delivered interface, version-induced code–documentation inconsistency, common multi-parameter constraints in data-science and machine-learning libraries, and limitations of single-parameter detectors are supported by `Chapters/Chapter1.tex:36,52` and `Chapters/Chapter4/01.introduction.tex:12-40`.

The sentence saying that a mismatch “transfers the failure ... to every future user or AI agent” is stronger and more universal than the source supports.

The title also treats documentation as necessarily authoritative, whereas MPChecker detects a disagreement and leaves the intended source of truth to maintainers. The on-screen statement that single-parameter checks “miss the contract” is too absolute.

**Recommended replacements**

> That mismatch increases misuse risk for future users and AI agents that rely on the documentation.

- Title: `Documentation describes cross-parameter contracts`
- Blind spot: `Single-parameter checks do not cover cross-parameter contracts.`

### Slide 18 — MPChecker makes text and code comparable

**Verdict: Supported.**

The three phases and rewriting of unsupported constructs are supported by `Chapters/Chapter4/03.methodology.tex:18-24`. Docstring preprocessing is supported by `Chapters/Chapter4/031.preprocessing.tex:4-8`; LLM extraction, prompt restrictions, decomposition, and few-shot examples by `Chapters/Chapter4/032.extracting.tex:70,92,96,99`; symbolic execution and Z3 by `Chapters/Chapter4/032.extracting.tex:21-23`; and fuzzy/SMT comparison by `Chapters/Chapter4/033.detecting.tex:3,8,12`.

### Slide 19 — Uncertainty stays at the language boundary

**Verdict: Tighten.**

The distinction between deterministic code constraints and uncertain documentation constraints is explicit in `Chapters/Chapter4/033.detecting.tex:3`. Parameter, value, and operator similarity and logical composition are supported by `Chapters/Chapter4/033.detecting.tex:81-147`. The final SMT-based decision is supported by `Chapters/Chapter4/033.detecting.tex:3,8-16,164-169`.

The headline is a faithful architectural synthesis, not a verbatim statement. However, “fuzzy only where language is translated into constraints” is too narrow: the dissertation attributes uncertainty both to vague or incomplete documentation and to errors introduced during LLM extraction. The final decision also includes both unsatisfiability and nonequivalence checks.

**Recommended replacements**

- `Fuzziness models uncertainty in documentation-derived constraints.`
- `SMT-based satisfiability and equivalence checking makes the final decision.`

**Recommended script sentence**

> Fuzziness models uncertainty in documentation-derived constraints, including ambiguity in the text and errors introduced during LLM extraction.

### Slide 20 — Formal checking turns disagreement into action

**Verdict: Tighten.**

All reported results are accurate:

- 72 constraints, 66 correct, and 91.7% extraction accuracy: `Chapters/Chapter4/04.evaluation.tex:15-16,52-56`
- 62.5% without few-shot examples and 79.2% without chain-of-thought: `Chapters/Chapter4/04.evaluation.tex:74-76`
- 216 mutations, eight patterns, 126 inconsistent, and 90 consistent: `Chapters/Chapter4/04.evaluation.tex:22-23`
- 117/126 detected, 92.8% recall, and 94.9% accuracy: `Chapters/Chapter4/04.evaluation.tex:92,116-123`
- 69% recall without the fuzzy components, 5.6% for raw LLM comparison, and 41.3% with pre-extracted constraints: `Chapters/Chapter4/04.evaluation.tex:137,145`
- 14 reported issues, 11 confirmed, and 10 resolved: `Chapters/Chapter4/04.evaluation.tex:151-158`

The caveat that maintainers still decide whether code or documentation is the intended contract is aligned with `Chapters/Chapter6.tex:35-39`.

The on-screen comparison `69.0% → 92.8%` should not be attributed to fuzzy constraint logic alone: the ablation adds both fuzzy words and fuzzy constraint logic. The 10 resolved issues should retain the denominator of 11 confirmed issues. “LLM alone” is also less precise than the experiment's “raw LLM comparison.”

**Recommended replacements**

- `69.0% → 92.8% with fuzzy words + fuzzy constraint logic (+23.8 percentage points)`
- `10/11 confirmed issues resolved`
- `5.6% recall from raw LLM comparison`

### Slide 21 — Different artifacts, one reliability architecture

**Verdict: Tighten.**

The neural/symbolic synthesis and lifecycle framing are supported by `mythesis.tex:399-407` and `Chapters/Chapter6.tex:8-19`. The intermediate-artifact pattern is a faithful synthesis across the three contributions, not a phrase directly stated in the dissertation.

Change “Across the three papers” to “Across the three core studies.”

The on-screen principle “formal systems decide what must be true” is stronger than the dissertation's claims across all three contributions.

**Recommended replacement**

> LLMs interpret ambiguity; formal artifacts constrain and verify what must hold.

The statement that the dissertation does not build one end-to-end autonomous maintenance system is a defensible scope clarification based on the separate contributions and future-looking conclusion (`Chapters/Chapter6.tex:19,53-57`).

### Slide 22 — The evidence is strong—and deliberately bounded

**Verdict: Tighten.**

CompSuite's Java/Maven scope, one-dependency-at-a-time method, and reliance on tests are supported by `Chapters/Chapter3/02.background.tex:60-90,105-166`. “Historical snapshot” is an inference from fixed commits and dependency versions rather than the dissertation's terminology.

DataLoc's Python-only limitation is direct (`Chapters/Chapter5/05.threats.tex:4`). Replace “25 structural templates” with “25 representative query combinations” (`Chapters/Chapter5/04.evaluation.tex:19`). The limitation to a fact set and rule is sound, but deterministic execution does not validate fact extraction or query translation.

MPChecker's domain, docstring, symbolic-execution, and heuristic-threshold limitations are supported by `Chapters/Chapter4/05.discussion.tex:12`, `Chapters/Chapter4/032.extracting.tex:14,23`, and `Chapters/Chapter4/033.detecting.tex:172-176`.

**Recommended replacements**

- `CompSuite is tied to fixed historical project and dependency versions.`
- `KA-LogicQuery contains 25 representative query combinations across nine projects.`
- `The deterministic engine does not by itself validate fact extraction or query translation.`
- `Coverage is bounded by available tests, extracted fact types, and explored symbolic paths.`
- `Additional language frontends and richer program facts` instead of the compressed phrase `cross-language facts`

The future directions are supported by `Chapters/Chapter6.tex:25-39,48-51` and `Chapters/Chapter5/05.threats.tex:4`.

### Slide 23 — Reliable evolution needs neural flexibility, executable evidence, and formal logic

**Verdict: Revise.**

The final thesis claim is supported by `mythesis.tex:407` and `Chapters/Chapter6.tex:17-19,53-57`.

The current return to “that one-line upgrade through the full lifecycle” can again imply that CompSuite, DataLoc, and MPChecker were evaluated as one integrated pipeline on the same upgrade instance. They were evaluated as separate contributions. The future-facing claim about autonomous maintenance is supported as a research direction, not an achieved end-to-end result.

**Recommended replacement**

> I began with a one-line dependency upgrade. Conceptually, the three core studies address successive reliability challenges around such evolution, although they are evaluated as separate contributions.

The remaining conclusion can stay, provided “offers a practical path toward” is retained rather than changed to a claim of an already completed autonomous system.

## Required Corrections Before the Defense

1. Do not frame the same dependency upgrade as an empirically tracked failure–localization–documentation chain (Slides 1 and 23).
2. Replace “three papers” with “three core studies” or “three principal research contributions” (Slides 4, 16, and 21).
3. Change the LLM headline from an absolute claim to a lack-of-guarantee claim (Slide 3).
4. Remove the unsupported negative positioning of CompSuite and use the dissertation's empirical-foundation framing (Slide 8).
5. Distinguish target identifiers from the literal `__init__` condition, and distinguish positive queries from the negative abstention benchmark (Slide 10).
6. Replace “25 templates” with “25 representative query combinations” (Slides 11 and 22).
7. Attribute the reported KA-LogicQuery result to DataLoc with Qwen3-Max, not to Datalog alone (Slide 14).
8. Attach benchmark, model, metric level, and subset qualifiers to all DataLoc metrics (Slides 14 and 15).
9. Present MPChecker's documentation impact as increased misuse risk rather than a universal transfer of failure (Slide 17).
10. Describe MPChecker's fuzzy layer as covering documentation-derived uncertainty, and retain both satisfiability and equivalence checking (Slide 19).
11. Attribute the 69.0% to 92.8% ablation gain to fuzzy words plus fuzzy constraint logic, and preserve issue denominators (Slide 20).
12. Keep the final synthesis explicitly conceptual and future-facing rather than describing an already evaluated integrated system (Slides 21 and 23).

## Bottom Line

The factual foundation of the script is strong. The quantitative evidence is accurate, and the methods and findings are overwhelmingly supported by the dissertation. The required work is precision editing: separating direct evidence from synthesis, restoring experimental qualifiers, and ensuring that the elegant lifecycle narrative is clearly presented as a conceptual synthesis of three independently evaluated core studies.
