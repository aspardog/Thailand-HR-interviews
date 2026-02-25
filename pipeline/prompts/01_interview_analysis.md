# Prompt: Interview Analysis (Step 1)

You are analyzing an expert interview for the Thailand Human Rights Report 2025.

## Inputs You Will Receive:
1. **TRANSCRIPT**: The full interview text (INT##.txt)
2. **ANALYST SUMMARY**: Authoritative insights from the human analyst (INT##_Summary Insights.txt) - TREAT AS GROUND TRUTH
3. **CODEBOOK**: The analytical framework with dimension codes (CODEBOOK.md)

## Your Task:

### 1. Expert Profile Section
- Extract: Name/Code, Organization type, Focus areas, Interview context

### 2. Key Challenges [CHAL]
For each challenge identified in the Analyst Summary:
- Provide a clear title
- Extract 1-2 verbatim quotes from the transcript that support it
- Assign the relevant dimension code (e.g., 1.3, 4.6)
- Note vulnerable groups affected (VG-MW, VG-MM, etc.)
- Note geographic specificity (GEO-DS, GEO-BK, etc.)

### 3. Key Highlights/Progress [HIGH]
For each positive development mentioned:
- Provide a clear title
- Extract supporting verbatim quotes
- Assign dimension code

### 4. Representative Quotes [QUOTE]
Select 5-8 of the most impactful quotes that:
- Capture the expert's core message
- Are quotable in the final report
- Cover different dimensions

### 5. Coded Fragments Table
Create a table with columns:
| Fragment ID | Code | Sub-indicator | Fragment (verbatim) | Tags | Vulnerable Groups | Geography |

### 6. Dimension Coverage Summary
List which dimensions (0-4) this interview covers and the depth of coverage (High/Medium/Low)

## Critical Rules:
- Do NOT contradict the Analyst Summary interpretations
- DO expand with specific verbatim quotes from the transcript
- DO add fragments the analyst didn't highlight if clearly relevant
- MAINTAIN the analyst's identified themes and emphasis
- Use EXACT quotes from transcript, not paraphrases
- Every claim must have a supporting quote

## Output Format:
Use the template structure provided in templates/interview_analysis_template.md
