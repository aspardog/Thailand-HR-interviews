# Validation Report: v#

**Date:** YYYY-MM-DD
**Pipeline Run:** v#
**Interviews Processed:** N

---

## Summary

| Test | Status | Details |
|------|--------|---------|
| Structural Validation | ✓ PASS / ✗ FAIL | X/Y files complete |
| Quote Traceability | ✓ PASS / ✗ FAIL | X/Y quotes verified |
| Anchor Quotes | ✓ PASS / ✗ FAIL | X/Y anchors found |
| Code Validation | ✓ PASS / ✗ FAIL | X invalid codes |
| Cross-Reference Integrity | ✓ PASS / ✗ FAIL | X% match rate |

**Overall Status:** ✓ PASS / ✗ FAIL

---

## Test 1: Structural Validation

### Interview Analyses

| File | Profile | Summary | Challenges | Highlights | Quotes | Fragments | Coverage | Status |
|------|---------|---------|------------|------------|--------|-----------|----------|--------|
| INT01_Analysis.md | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | PASS/FAIL |
| INT02_Analysis.md | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | PASS/FAIL |
| ... | | | | | | | | |

### Dimension Syntheses

| File | Quant Context | Challenges | Progress | Consensus | VG Summary | Quotes | Status |
|------|---------------|------------|----------|-----------|------------|--------|--------|
| DIMENSION_0_*.md | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | PASS/FAIL |
| DIMENSION_1_*.md | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | ✓/✗ | PASS/FAIL |
| ... | | | | | | | |

### Quote Bank

| Section | Present | Quote Count | Status |
|---------|---------|-------------|--------|
| By Dimension (all 5) | ✓/✗ | N | PASS/FAIL |
| By Theme | ✓/✗ | N | PASS/FAIL |
| By Vulnerable Group | ✓/✗ | N | PASS/FAIL |

### Chapter 2

| Section | Present | Word Count | Blockquotes | Status |
|---------|---------|------------|-------------|--------|
| Introduction | ✓/✗ | N | N | PASS/FAIL |
| Section 2.0 | ✓/✗ | N | N | PASS/FAIL |
| Section 2.1 | ✓/✗ | N | N | PASS/FAIL |
| Section 2.2 | ✓/✗ | N | N | PASS/FAIL |
| Section 2.3 | ✓/✗ | N | N | PASS/FAIL |
| Section 2.4 | ✓/✗ | N | N | PASS/FAIL |

---

## Test 2: Quote Traceability

**Sample Size:** 10 quotes from QUOTE_BANK.md

| # | Quote (first 50 chars) | Claimed Source | In Analysis? | In Transcript? | Status |
|---|------------------------|----------------|--------------|----------------|--------|
| 1 | "..." | INT## | ✓/✗ | ✓/✗ | PASS/FAIL |
| 2 | "..." | INT## | ✓/✗ | ✓/✗ | PASS/FAIL |
| ... | | | | | |

**Pass Rate:** X/10 (Y%)

### Issues Found:
- [List any quotes that failed traceability]

---

## Test 3: Anchor Quote Verification

**Critical Anchors (must be 100%):**

| ID | Description | Fragment | Found? | Correct Source? | Correct Dim? | Status |
|----|-------------|----------|--------|-----------------|--------------|--------|
| AQ01 | Selective enforcement | "cherry pick" | ✓/✗ | ✓/✗ | ✓/✗ | PASS/FAIL |
| AQ02 | Two halves | "story of two halves" | ✓/✗ | ✓/✗ | ✓/✗ | PASS/FAIL |
| ... | | | | | | |

**Critical Pass Rate:** X/Y (Z%) — Target: 100%

**Important Anchors:**

| ID | Description | Fragment | Found? | Status |
|----|-------------|----------|--------|--------|
| AQ06 | Pegasus | "Pegasus" | ✓/✗ | PASS/FAIL |
| ... | | | | |

**Important Pass Rate:** X/Y (Z%) — Target: 80%

### Missing Anchors:
- [List any anchor quotes not found]

---

## Test 4: Code Validation

### Invalid Dimension Codes Found:
| File | Invalid Code | Line/Context |
|------|--------------|--------------|
| [None found] | | |

### Invalid Vulnerable Group Codes Found:
| File | Invalid Code | Line/Context |
|------|--------------|--------------|
| [None found] | | |

### Invalid Geographic Codes Found:
| File | Invalid Code | Line/Context |
|------|--------------|--------------|
| [None found] | | |

**Total Invalid Codes:** 0

---

## Test 5: Cross-Reference Integrity

### Dimension → Interview Analysis

| Dimension File | Quotes Checked | Matches | Match Rate |
|----------------|----------------|---------|------------|
| DIMENSION_0 | N | N | X% |
| DIMENSION_1 | N | N | X% |
| ... | | | |

**Overall Match Rate:** X%

### Quote Bank → Interview Analysis

| Section | Quotes Checked | Matches | Match Rate |
|---------|----------------|---------|------------|
| By Dimension | N | N | X% |
| By Theme | N | N | X% |
| By VG | N | N | X% |

**Overall Match Rate:** X%

### Issues Found:
- [List any orphan or mismatched quotes]

---

## Recommendations

### Must Fix Before Finalizing:
1. [List critical issues]

### Should Review:
1. [List warnings]

### Notes for Next Run:
1. [List observations]

---

*Validation completed: YYYY-MM-DD HH:MM*
