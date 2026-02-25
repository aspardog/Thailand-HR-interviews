# Prompt: Quote Bank Generation (Step 3A)

You are compiling a comprehensive quote bank from all interview analyses for the Thailand Human Rights Report 2025.

## Inputs You Will Receive:
1. **ALL Interview Analysis files** (INT##_Analysis.md)
2. **ALL Dimension Synthesis files** (DIMENSION_#_*.md)

## Your Task:

### Organization Structure

The quote bank must be organized in THREE ways:

#### Section 1: By Dimension
```
# DIMENSION 0: Overall Assessment
## Summary Statements
> "Quote" - Source

## Temporal Comparisons
> "Quote" - Source

# DIMENSION 1: Civil and Political Rights
## 1.2 Equality and Discrimination
> "Quote" - Source

## 1.3 Freedom of Expression
> "Quote" - Source
...
```

#### Section 2: By Theme
```
# THEMATIC QUOTE COLLECTIONS

## Progress & Hope
> "Quote" - Source

## Structural Challenges
> "Quote" - Source

## Cherry-Picked Enforcement
> "Quote" - Source

## Section 112 / Lese-Majeste
> "Quote" - Source

## Deep South
> "Quote" - Source

## Migrant Workers
> "Quote" - Source
```

#### Section 3: By Vulnerable Group
```
# QUOTES BY VULNERABLE GROUP

## Migrant Workers (VG-MW)
> "Quote" - Source

## Malay Muslims (VG-MM)
> "Quote" - Source

## Political Activists (VG-PA)
> "Quote" - Source
...
```

## Quote Selection Criteria:
1. **Impactful**: Captures a key insight memorably
2. **Quotable**: Suitable for direct use in final report
3. **Specific**: Contains concrete details, not vague statements
4. **Representative**: Reflects expert's core message
5. **Diverse**: Cover all dimensions and perspectives

## Quote Format:
```
> **"[Exact quote from transcript]"**
> - INT## (Expert Type/Role)
```

## Critical Rules:
- Include 50-80 quotes total
- Every quote must be VERBATIM from transcripts
- Every quote must have source attribution
- Balance across dimensions (aim for 8-15 per dimension)
- Include both challenges and progress
- Prioritize quotes that explain WHY, not just WHAT

## Output Format:
Use the template structure provided in templates/quote_bank_template.md
