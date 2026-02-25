# Prompt: Consistency Test (Step 0 - Post-Pipeline)

Execute this test AFTER completing all pipeline steps (1-4) to validate consistency and measure drift.

## Test Components

### TEST 1: Structural Validation

For each output file, verify required sections exist:

**Interview Analyses (Outputs/interviews/INT##_Analysis.md):**
- [ ] Expert Profile table
- [ ] Executive Summary
- [ ] Key Challenges section (at least 1)
- [ ] Key Highlights section (at least 1)
- [ ] Representative Quotes section (at least 3 quotes)
- [ ] Coded Fragments Table
- [ ] Dimension Coverage Summary

**Dimension Syntheses (Outputs/dimensions/DIMENSION_#_*.md):**
- [ ] Quantitative Context table
- [ ] Key Challenges section (ranked)
- [ ] Areas of Progress section
- [ ] Expert Consensus section
- [ ] Vulnerable Groups Summary table
- [ ] Key Quotes section

**Quote Bank (Outputs/QUOTE_BANK.md):**
- [ ] Section 1: Quotes by Dimension (all 5 dimensions)
- [ ] Section 2: Quotes by Theme
- [ ] Section 3: Quotes by Vulnerable Group

**Chapter 2 (Outputs/CHAPTER2_DRAFT.md):**
- [ ] Introduction
- [ ] Section 2.0 through 2.4
- [ ] Blockquotes with citations in each section

---

### TEST 2: Quote Traceability

Verify quotes are traceable through the chain:

```
Transcript (INT##.txt)
    ↓ [must exist verbatim]
Interview Analysis (INT##_Analysis.md)
    ↓ [must match]
Dimension Synthesis (DIMENSION_#_*.md)
    ↓ [must match]
Quote Bank / Chapter 2
```

**Sample 10 quotes from QUOTE_BANK.md and verify:**
1. Quote exists in cited INT##_Analysis.md
2. Quote exists verbatim in INT##.txt transcript

**Report format:**
| Quote (first 50 chars) | Source | In Analysis? | In Transcript? | Status |
|------------------------|--------|--------------|----------------|--------|
| "Fundamental rights..." | INT10 | ✓ | ✓ | PASS |
| "The fishing industry..." | INT05 | ✓ | ✗ | FAIL |

---

### TEST 3: Anchor Quote Verification

Load `pipeline/anchor_quotes.yaml` and verify each anchor quote is captured.

For each anchor quote:
1. Search for the text fragment across all outputs
2. Verify it appears in expected dimension(s)
3. Verify source attribution matches

**Report format:**
| Anchor ID | Fragment | Expected Dim | Found? | Correct Source? | Status |
|-----------|----------|--------------|--------|-----------------|--------|
| AQ01 | "cherry picked" | 0 | ✓ | ✓ | PASS |
| AQ02 | "Section 112" | 1 | ✓ | ✓ | PASS |

**Target: 100% of anchor quotes present**

---

### TEST 4: Metrics Generation

Generate metrics snapshot and save to `Outputs/consistency/metrics_v#.yaml`

**Metrics to capture:**

```yaml
run_metadata:
  version: "v#"
  date: "YYYY-MM-DD"
  interviews_processed: [count]
  interviews_with_summary_insights: [count]

interview_metrics:
  INT##:
    challenges_count: [N]
    highlights_count: [N]
    quotes_count: [N]
    fragments_count: [N]
    dimensions_covered: [list]
    vulnerable_groups_mentioned: [list]
    geographic_codes: [list]

dimension_metrics:
  DIMENSION_#:
    challenges_count: [N]
    progress_count: [N]
    sources_cited: [list of INT##]
    source_count: [N]
    unique_quotes: [N]
    vulnerable_groups: [list]

quote_bank_metrics:
  total_quotes: [N]
  by_dimension:
    0: [N]
    1: [N]
    2: [N]
    3: [N]
    4: [N]
  by_vulnerable_group:
    VG-MW: [N]
    VG-MM: [N]
    # ...

chapter2_metrics:
  total_word_count: [N]
  quotes_used: [N]
  blockquotes_count: [N]
  sections_count: [N]
  words_per_section:
    section_0: [N]
    section_1: [N]
    # ...
```

---

### TEST 5: Drift Analysis (if previous version exists)

Compare current metrics against previous version.

**Calculate deltas:**
```
delta = (current - previous) / previous * 100
```

**Thresholds:**
- ✓ Green: |delta| < 10%
- ⚠️ Yellow: 10% <= |delta| < 25%
- 🚨 Red: |delta| >= 25%

**Report significant changes:**
| Metric | Previous | Current | Delta | Status |
|--------|----------|---------|-------|--------|
| INT01.challenges | 5 | 4 | -20% | ⚠️ |
| total_quotes | 67 | 72 | +7% | ✓ |
| DIMENSION_1.sources | 6 | 4 | -33% | 🚨 |

**Investigate all 🚨 items before finalizing.**

---

### TEST 6: Code Validation

Verify all dimension codes used in outputs are valid per CODEBOOK.md:

**Valid codes:**
- Dimension 0: 0.1, 0.2, 0.3, 0.4
- Dimension 1: 1.1, 1.2, 1.3, 1.4, 1.5, 1.6
- Dimension 2: 2.1, 2.2, 2.3, 2.4
- Dimension 3: 3.1, 3.2
- Dimension 4: 4.1, 4.2, 4.3, 4.4, 4.5, 4.6, 4.7, 4.8

**Valid vulnerable group codes:**
VG-MW, VG-MM, VG-IP, VG-WM, VG-LG, VG-YT, VG-PA, VG-HR, VG-JN

**Valid geographic codes:**
GEO-DS, GEO-BK, GEO-RU, GEO-NA

**Report any invalid codes found.**

---

## Output Files

Generate three files:

1. **`Outputs/consistency/metrics_v#.yaml`** - Metrics snapshot
2. **`Outputs/consistency/validation_report_v#.md`** - Pass/fail for all tests
3. **`Outputs/consistency/drift_report_v#.md`** - Comparison with previous (if exists)

---

## Pass Criteria

| Test | Pass Threshold |
|------|----------------|
| Structural Validation | 100% sections present |
| Quote Traceability | 100% of sampled quotes traceable |
| Anchor Quotes | 100% present |
| Code Validation | 0 invalid codes |
| Drift Analysis | No 🚨 red alerts unresolved |

**Overall: ALL tests must pass before considering pipeline run complete.**
