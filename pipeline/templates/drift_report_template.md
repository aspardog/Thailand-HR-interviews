# Drift Report: v[PREVIOUS] → v[CURRENT]

**Date:** YYYY-MM-DD
**Previous Run:** v#
**Current Run:** v#
**Interviews Changed:** [List any added/removed]

---

## Summary

| Category | Metrics Compared | Green (✓) | Yellow (⚠️) | Red (🚨) |
|----------|------------------|-----------|-------------|----------|
| Interview Metrics | N | N | N | N |
| Dimension Metrics | N | N | N | N |
| Quote Bank | N | N | N | N |
| Chapter 2 | N | N | N | N |
| **Total** | **N** | **N** | **N** | **N** |

**Overall Drift Assessment:** LOW / MODERATE / HIGH

---

## Thresholds

| Status | Delta Range | Meaning |
|--------|-------------|---------|
| ✓ Green | < 10% | Expected variation, no action needed |
| ⚠️ Yellow | 10-25% | Review recommended |
| 🚨 Red | > 25% | Investigation required |

---

## Interview Metrics Drift

| Interview | Metric | Previous | Current | Delta | Status |
|-----------|--------|----------|---------|-------|--------|
| INT01 | challenges_count | N | N | ±X% | ✓/⚠️/🚨 |
| INT01 | quotes_count | N | N | ±X% | ✓/⚠️/🚨 |
| INT01 | fragments_count | N | N | ±X% | ✓/⚠️/🚨 |
| INT02 | challenges_count | N | N | ±X% | ✓/⚠️/🚨 |
| ... | | | | | |

### Red Alerts:
- [Detail any 🚨 items and likely cause]

### Yellow Warnings:
- [Detail any ⚠️ items worth noting]

---

## Dimension Metrics Drift

| Dimension | Metric | Previous | Current | Delta | Status |
|-----------|--------|----------|---------|-------|--------|
| DIM_0 | challenges_count | N | N | ±X% | ✓/⚠️/🚨 |
| DIM_0 | source_count | N | N | ±X% | ✓/⚠️/🚨 |
| DIM_0 | unique_quotes | N | N | ±X% | ✓/⚠️/🚨 |
| DIM_1 | challenges_count | N | N | ±X% | ✓/⚠️/🚨 |
| ... | | | | | |

### Red Alerts:
- [Detail any 🚨 items]

### Yellow Warnings:
- [Detail any ⚠️ items]

---

## Quote Bank Drift

| Metric | Previous | Current | Delta | Status |
|--------|----------|---------|-------|--------|
| total_quotes | N | N | ±X% | ✓/⚠️/🚨 |
| dim_0 quotes | N | N | ±X% | ✓/⚠️/🚨 |
| dim_1 quotes | N | N | ±X% | ✓/⚠️/🚨 |
| dim_2 quotes | N | N | ±X% | ✓/⚠️/🚨 |
| dim_3 quotes | N | N | ±X% | ✓/⚠️/🚨 |
| dim_4 quotes | N | N | ±X% | ✓/⚠️/🚨 |
| VG-MW quotes | N | N | ±X% | ✓/⚠️/🚨 |
| VG-MM quotes | N | N | ±X% | ✓/⚠️/🚨 |
| ... | | | | |

### Quotes Added:
- [List new quotes not in previous version]

### Quotes Removed:
- [List quotes in previous but not current]

---

## Chapter 2 Drift

| Metric | Previous | Current | Delta | Status |
|--------|----------|---------|-------|--------|
| total_word_count | N | N | ±X% | ✓/⚠️/🚨 |
| total_blockquotes | N | N | ±X% | ✓/⚠️/🚨 |
| section_2_0 words | N | N | ±X% | ✓/⚠️/🚨 |
| section_2_1 words | N | N | ±X% | ✓/⚠️/🚨 |
| section_2_2 words | N | N | ±X% | ✓/⚠️/🚨 |
| section_2_3 words | N | N | ±X% | ✓/⚠️/🚨 |
| section_2_4 words | N | N | ±X% | ✓/⚠️/🚨 |

---

## Anchor Quote Stability

| Anchor ID | In Previous? | In Current? | Status |
|-----------|--------------|-------------|--------|
| AQ01 | ✓/✗ | ✓/✗ | Stable/Lost/Gained |
| AQ02 | ✓/✗ | ✓/✗ | Stable/Lost/Gained |
| ... | | | |

**Anchor Stability Rate:** X% (anchors present in both versions)

### Lost Anchors (were present, now missing):
- [List with investigation notes]

### Gained Anchors (were missing, now present):
- [List - this is positive]

---

## Root Cause Analysis

### Expected Changes:
- [Changes explained by new interviews or intentional updates]

### Unexpected Changes:
- [Changes that need investigation]

| Change | Likely Cause | Action Needed |
|--------|--------------|---------------|
| [Describe change] | [Hypothesis] | [Next step] |

---

## Recommendations

### Accept Current Version If:
- [ ] All red alerts have been investigated and explained
- [ ] No anchor quotes were lost without justification
- [ ] Changes are proportional to input changes (new interviews)

### Reject/Revise If:
- [ ] Unexplained loss of critical content
- [ ] Significant drift without new inputs
- [ ] Anchor quote stability < 90%

---

## Decision

**Accept Current Version:** YES / NO

**Justification:**
[Explain decision]

**Follow-up Actions:**
1. [List any actions needed]

---

*Drift analysis completed: YYYY-MM-DD HH:MM*
