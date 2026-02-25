# Prompt: Dimension Synthesis (Step 2)

You are synthesizing findings across all interview analyses for a specific dimension of the Thailand Human Rights Report 2025.

## Inputs You Will Receive:
1. **ALL Interview Analysis files** (INT##_Analysis.md)
2. **CODEBOOK.md** for dimension definitions and quantitative trends
3. **Target Dimension** (0, 1, 2, 3, or 4)

## Your Task:

### 1. Quantitative Context
From the CODEBOOK, extract the relevant WJP Rule of Law Index trends for this dimension.

### 2. Key Challenges (Ranked)
Aggregate challenges across all interviews for this dimension:
- Rank by frequency (how many experts mentioned it)
- Rank by severity (based on expert emphasis)
- Include: Title, Description, Supporting quotes (with sources), Expert sources list

Format for each challenge:
```
### [RANK] Challenge Title
**Severity:** Critical / High / Moderate
**Sources:** INT01, INT04, INT08 (3 experts)

**Description:** [2-3 sentences synthesizing the issue]

**Evidence:**
> "Quote 1" - INT01
> "Quote 2" - INT04

**Vulnerable Groups Affected:** VG-MW, VG-MM
**Geographic Scope:** GEO-DS / GEO-NA
```

### 3. Areas of Progress
Same format as challenges, but for positive developments.

### 4. Expert Consensus vs. Disagreement
- Where do experts agree?
- Where do perspectives differ?
- How do expert views contrast with quantitative data?

### 5. Quantitative-Qualitative Connections
Explain how qualitative findings illuminate the WJP Index trends:
- If trend is positive but experts report problems: explain the gap
- If trend is negative and experts confirm: provide depth

### 6. Vulnerable Groups Summary
Table of vulnerable groups mentioned in this dimension with primary issues.

## Critical Rules:
- Include quotes from MULTIPLE experts when available
- Always cite source (INT##) for every quote
- Prioritize findings mentioned by 3+ experts
- Note when only 1 expert mentions something (may be specialized knowledge)
- Connect to quantitative trends from CODEBOOK

## Output Format:
Use the template structure provided in templates/dimension_template.md
