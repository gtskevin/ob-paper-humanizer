# Evaluation Protocol: OB Paper Humanizer Skill Optimization

**Date**: 2026-06-11 | **Status：** 待评审 | **Scope**: Pre/post optimization comparison

---

## 1. Evaluation Goal

Verify that the optimized SKILL.md produces **better** results than the original by measuring:

- **P1 (Precision)**: Does the optimized version flag fewer OB conventions as AI patterns? (fewer false positives)
- **P2 (Recall)**: Does it still catch genuine AI patterns? (no loss of detection)
- **P3 (Calibration)**: Do the suggestions preserve OB writing conventions better? (less over-correction)
- **P4 (Regression)**: Do changes survive the Regression Check? (lower revert rate)

---

## 2. Test Corpus

### 2.1 Source Material

Use **5 test cases**, each representing a different section type and risk area:

| # | Section | Source | Why This Test |
|---|---------|--------|--------------|
| T1 | Introduction | Real AMJ paper (2020-2022) paragraph, then AI-rewritten | Tests funnel structure preservation (Risk 2) |
| T2 | Theory/Hypotheses | Real JAP paper (2020-2022) hypothesis section, then AI-rewritten | Tests hedging preservation (Risk 1) |
| T3 | Methods | Real OBHDP paper (2020-2022) methods paragraph, then AI-rewritten | Tests template preservation (Risk 5) |
| T4 | Discussion | Real ASQ paper (2020-2022) discussion paragraph, then AI-rewritten | Tests voice calibration (Risk 4/6) |
| T5 | Mixed AI-heavy | A fully AI-generated paragraph (GPT-4o) mimicking OB writing | Tests genuine AI pattern detection (P2) |

### 2.2 Preparation

For T1-T4, the workflow is:
1. Extract a 150-250 word paragraph from a real, pre-2023 OB paper
2. Have GPT-4o/Claude rewrite the same paragraph (preserving content but adding AI patterns)
3. The AI-rewritten version becomes the test input

For T5:
1. Ask GPT-4o to write a 200-word OB discussion paragraph on a given topic
2. This becomes the test input

### 2.3 Test Inputs (Prepared by Evaluator)

Each test input should be saved as a separate text block for reproducibility.

---

## 3. Evaluation Procedure

### 3.1 A/B Testing Protocol

```
For each test case T1-T5:

A. Run ORIGINAL skill (pre-optimization SKILL.md from git commit ebd4c4b)
   - Input the test paragraph
   - Record all flagged patterns
   - Record all suggested changes
   - Record quality check results

B. Run OPTIMIZED skill (current SKILL.md with all 6 optimizations)
   - Input the same test paragraph
   - Record section identification
   - Record flagged patterns (active) vs suppressed patterns
   - Record suggested changes
   - Record regression check results

C. Compare A vs B on the 4 metrics (P1-P4)
```

### 3.2 Scoring Rubric

For each test case, score on these dimensions:

#### P1: False Positive Reduction (0-5)

Count OB conventions that were incorrectly flagged as AI patterns.

| Score | Criteria |
|-------|----------|
| 5 | Zero OB conventions flagged |
| 4 | 1 minor convention flagged |
| 3 | 1 major or 2 minor conventions flagged |
| 2 | 2 major conventions flagged |
| 1 | 3+ major conventions flagged |
| 0 | More conventions flagged than genuine AI patterns |

**OB conventions to check** (from Do-Not-Touch List):
- Standard hedging in hypotheses/results
- Funnel structure in introductions
- "We argue" / "We propose" language
- Method section templates
- Transition words in theory sections
- Standard contribution statement format
- Hypothesis formatting

#### P2: Genuine AI Pattern Detection (0-5)

For T5 (AI-heavy), count how many of the pre-identified AI patterns were correctly caught.

| Score | Criteria |
|-------|----------|
| 5 | All genuine AI patterns detected |
| 4 | Missed 1 minor pattern |
| 3 | Missed 1 major or 2 minor patterns |
| 2 | Missed 2 major patterns |
| 1 | Missed 3+ patterns |
| 0 | Failed to flag obvious AI text |

#### P3: Suggestion Quality (0-5)

Evaluate whether suggested changes preserve OB writing quality.

| Score | Criteria |
|-------|----------|
| 5 | All suggestions improve writing; none damage OB conventions |
| 4 | 1 suggestion is unnecessary but not harmful |
| 3 | 1 suggestion damages OB convention (e.g., removes needed hedging) |
| 2 | 2+ suggestions damage OB conventions |
| 1 | Suggestions make text worse than original |
| 0 | Output falls into uncanny valley (neither AI-like nor human-like) |

#### P4: Regression Rate

The percentage of suggested changes that the Regression Check reverts.

| Score | Regression Rate |
|-------|----------------|
| 5 | < 5% |
| 4 | 5-10% |
| 3 | 10-20% |
| 2 | 20-30% |
| 1 | 30-50% |
| 0 | > 50% |

---

## 4. Pass/Fail Criteria

### Minimum Viable Improvement

The optimization **passes** if:

| Metric | Original (expected) | Optimized (must achieve) |
|--------|--------------------|--------------------------|
| P1 (false positive reduction) | 2-3 (typical for v1) | >= 4 |
| P2 (detection recall) | 4-5 | >= 4 (no regression) |
| P3 (suggestion quality) | 2-3 (typical for v1) | >= 4 |
| P4 (regression rate) | N/A (not measured in v1) | >= 4 (< 10% reverted) |

**Overall pass**: Average score across P1-P4 >= 4.0, with no single metric below 3.

### Failure Protocol

If the optimization fails any metric:

1. **P1 failure** (still flagging OB conventions): Review Do-Not-Touch List — is the convention listed? If not, add it. If it is listed, check if the section identification is working.
2. **P2 failure** (missing genuine AI patterns): Check if Section-Specific Rules are over-suppressing patterns. Adjust the "Active" list.
3. **P3 failure** (suggestions damaging quality): Review Decision Tree — is it being applied? Check Category 12 meta-rule enforcement.
4. **P4 failure** (high revert rate): The original text may not need humanization, or the rules are too aggressive. Consider raising the confidence threshold for suggestions.

---

## 5. Iteration Cycle

```
Round 1: Run full evaluation (T1-T5) with current optimized SKILL.md
  -> If pass: Ship. Update README with changelog.
  -> If fail: Identify weakest metric -> Make targeted fix -> Re-run failed test cases only

Round 2 (if needed): Re-run failed test cases
  -> If pass: Ship.
  -> If fail: Consider fundamental approach change

Round 3 (maximum): If still failing, the issue is likely in the test corpus quality
  -> Re-examine test inputs: Are the "real OB paper" excerpts actually representative?
  -> Consult OB researcher (user) to validate test cases
```

---

## 6. Quick Start: Running the First Evaluation

To run the evaluation immediately:

1. **Prepare test inputs**: Paste 5 test paragraphs (one per section type + one AI-heavy)
2. **Run original skill**: Use `git show ebd4c4b:SKILL.md` to load the original, process each input
3. **Run optimized skill**: Use current SKILL.md, process each input
4. **Score**: Apply the rubric above
5. **Decide**: Pass -> commit. Fail -> iterate.

The test inputs should ideally come from the user's own research or from well-known OB papers they are familiar with, so they can judge whether the "humanized" output sounds like their field.
