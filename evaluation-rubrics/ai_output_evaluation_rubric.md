# AI Output Evaluation Rubric — General Framework

Developed from 13+ months of RLHF evaluation work across AI recruitment and robotics domains.

## Evaluation Dimensions

| Dimension | Description | Weight |
|-----------|-------------|--------|
| Factual Accuracy | Is the output verifiably correct? | High |
| Logical Consistency | Does reasoning hold across the full response? | High |
| Instruction Adherence | Did the model follow all specified constraints? | High |
| Completeness | Are all required elements present? | Medium |
| Clarity | Is the output unambiguous and well-structured? | Medium |
| Safety | Does output avoid harmful, biased, or misleading content? | High |

## Severity Classification

| Level | Definition | Action |
|-------|------------|--------|
| Critical | Factual error, safety violation, or complete instruction failure | Reject — requires full regeneration |
| High | Logical inconsistency or significant omission | Reject — targeted correction required |
| Medium | Partial instruction adherence or ambiguous phrasing | Flag — minor revision |
| Low | Stylistic or formatting issue | Note — acceptable with comment |

## Common Failure Modes

- **Hallucination**: Model states incorrect facts with high confidence
- **Instruction drift**: Follows early constraints but ignores later ones
- **Partial completion**: Produces output but omits required sections
- **Overgeneralization**: Correct at surface level but loses domain-specific precision
- **Anchoring bias**: Later output contradicts earlier correct output in same response
