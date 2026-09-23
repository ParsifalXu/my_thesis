# Constraint representation additions: review notes

The four additions in Chapter 4 have been shortened to concise academic prose. The original notation, EBNF, detection equations, similarity definitions, membership definition, and threshold are retained.

## Added passages

- Section 4.3.2.1, "Implementation constraint representation": distinguishes path conditions, termination outcomes, concrete endpoint values, and definition-use information.
- Section 4.3.2.2, "Documentation constraint representation": identifies the Boolean core, parameter scope, literal values, relational comparisons, and specialized predicates.
- Section 4.3.3, "Interpretation of the detection queries": clarifies the solver-level interpretation and the scope of per-path results.
- Section 4.3.3.2, "Constraint matching": connects scope association, atomic matching, substitution, path conditions, and detection.

## Notation and example

The original symbols c, p, P, sigma, rho, and the existing substitution notation are retained. The additional symbols d and q_d have been removed. Equation 4.7 has been restored to its original form, including sigma in the recursive branches and argmax in the atomic branch, in accordance with the request to preserve the original notation.

In the worked example, c consistently denotes the displayed implication. The added sentence explains that the exceptional path entails its antecedent, so no separate query symbol or implication-to-conjunction conversion is needed for this example.

## Outstanding review points

These additions are based on the thesis text, not an implementation audit. The following issues remain open:

1. Equation 4.7 uses argmax where the accompanying prose describes a numerical maximum, and uses sigma recursively with arguments outside its previously defined domain. These issues are recorded here rather than silently corrected in the thesis.
2. Parameter-to-parameter comparisons, candidate scope, tie handling, and unsupported-expression handling require implementation verification.
3. Equation 4.2 compares individual paths. A stronger claim about equivalence to the combined implementation behavior requires a corresponding definition and implementation evidence.
4. Equation 4.8, the probability interpretation, and the precise target and direction of the 0.85 filter remain unchanged and require clarification.

The additions improve exposition but do not resolve these outstanding formal or implementation-level issues.
