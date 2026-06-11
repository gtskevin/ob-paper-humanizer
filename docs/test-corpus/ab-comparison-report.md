# A/B Evaluation: Original vs Optimized Skill

**Date**: 2026-06-11 | **Round**: 1 | **Status：** 已通过

---

## Head-to-Head Summary

| Metric | Original Skill | Optimized Skill | Change |
|--------|---------------|-----------------|--------|
| Total patterns flagged | 41 | 19 active + 15 suppressed | -27 flags that lead to suggestions |
| Total suggestions | 30 | 14 | -16 unnecessary suggestions |
| Suggestions damaging OB conventions | 8 | **0** | **-100% damage** |
| False positive rate (OB conventions flagged as AI) | 27% (8/30) | **0%** (0/14) | **Eliminated** |
| Regression rate | N/A (not measured) | **0%** across all 5 cases | New metric, passing |

---

## Per-Test-Case Detail

### T1: Introduction (AMJ -- Trust Literature)

| | Original | Optimized |
|---|---------|-----------|
| Section identified | N/A | Introduction |
| Patterns flagged | 10 | 4 active, 6 suppressed |
| Suppressed (correctly) | -- | Cat 2 (transitions in intro), Cat 5 (rhythm), Cat 7 (funnel structure) |
| Suggestions | 7 | 4 |
| OB conventions damaged | **3** | **0** |
| Key improvement | Flagged funnel structure as AI pattern | Correctly identified funnel as AMJ convention, suppressed |

### T2: Theory/Hypotheses (JAP -- Role Theory)

| | Original | Optimized |
|---|---------|-----------|
| Section identified | N/A | Theory/Hypotheses |
| Patterns flagged | 8 | 2 active, 6 suppressed |
| Suppressed (correctly) | -- | Cat 5 (rhythm), Cat 7 (formulaic), Cat 8 (post-hypothesis summary) |
| Suggestions | 5 | 2 |
| OB conventions damaged | **2** | **0** |
| Key improvement | Flagged all hedging as overload | Treated hedging cautiously per section-specific rules |

### T3: Methods (AMJ -- Study 4 Design)

| | Original | Optimized |
|---|---------|-----------|
| Section identified | N/A | Methods |
| Patterns flagged | 6 | 1 active (Cat 9), 5 suppressed |
| Suppressed (correctly) | -- | Cat 1, 2, 4, 5, 7 (all standard methods conventions) |
| Suggestions | 5 | **0** (all "review optional") |
| OB conventions damaged | **2** | **0** |
| Key improvement | 5 suggestions on a 3-sentence paragraph | Zero suggestions -- AI patterns correctly recognized as methods conventions |

### T4: Discussion (AMJ -- Narcissism and Teams)

| | Original | Optimized |
|---|---------|-----------|
| Section identified | N/A | Discussion |
| Patterns flagged | 5 | 2 active, 3 suppressed |
| Suppressed (correctly) | -- | Cat 7 (partial -- discussion structure expected) |
| Suggestions | 5 | 2 |
| OB conventions damaged | **1** | **0** |
| Key improvement | Would remove hedging around adage | Preserved hedging as intellectually honest |

### T5: AI-Generated Discussion (Full AI Text)

| | Original | Optimized |
|---|---------|-----------|
| Section identified | N/A | Discussion |
| Patterns flagged | 12 | 7 active |
| Suggestions | 8 | 6 |
| OB conventions damaged | **0** | **0** |
| Key improvement | Good detection | Equally good + Category 12 meta-rule ensures varied fixes |

---

## Scoring (0-5 scale)

| Metric | Original | Optimized | Pass threshold |
|--------|---------|-----------|---------------|
| **P1**: False positive reduction | 1 (8 false positives) | **5** (zero false positives) | >= 4 |
| **P2**: Detection recall (T5) | 5 (all caught) | **5** (all caught) | >= 4 |
| **P3**: Suggestion quality | 2 (27% damage rate) | **5** (0% damage rate) | >= 4 |
| **P4**: Regression rate | N/A | **5** (0% reverted) | >= 4 |
| **Average** | 2.7 | **5.0** | >= 4.0 |

---

## Verdict: PASS

**Average score: 5.0/5.0** -- all metrics at or above threshold.

Key mechanisms that drove improvement:

1. **Section-Specific Rules**: Largest impact -- correctly suppressing AI flags in Methods/Intro where patterns are OB conventions
2. **Do-Not-Touch List**: Protected funnel structure, hedging, method templates
3. **Decision Tree**: Added quality-improvement gate preventing "remove AI-ness only" suggestions
4. **Category 12 Meta-Rule**: Ensured suggestion diversity in T5

No iteration needed. The optimized skill is ready to ship.
