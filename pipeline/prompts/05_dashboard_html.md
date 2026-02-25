# Prompt: Dashboard HTML Generation (Step 4)

You are generating the final HTML dashboard that presents all qualitative analysis for the Thailand Human Rights Report 2025.

## Inputs You Will Receive:
1. **ALL Interview Analysis files** (Outputs/interviews/INT##_Analysis.md)
2. **ALL Dimension Synthesis files** (Outputs/dimensions/DIMENSION_#_*.md)
3. **QUOTE_BANK.md**
4. **CHAPTER2_DRAFT.md**
5. **dashboard_template.html** (for styling reference)

## Dashboard Structure:

### Tab 1: Interview Summaries
For each interview, extract from INT##_Analysis.md:
- Expert profile (type, focus areas)
- Context bullet points (3-4 key points)
- Key challenge highlights (2-3 most important)
- One representative quote

### Tab 2: Findings by Dimension
For each dimension (0-4), extract from DIMENSION_#_*.md:
- Dimension header with description
- Key Challenges (ranked, with sources and quotes)
- Areas of Progress (with sources and quotes)
- Vulnerable groups affected

### Tab 3: Chapter 2 Draft
Insert the full CHAPTER2_DRAFT.md content, formatted as HTML report sections.

### Tab 4: Quote Bank
From QUOTE_BANK.md, create a filterable quote collection:
- Populate the JavaScript `quotes` array with all quotes
- Each quote needs: text, source, dimension, themes[], tags[]

## Critical Rules:
- ALL content must come from the markdown files
- NO independent information in the HTML
- Preserve the existing CSS styling from the template
- Ensure all quotes have proper attribution
- Maintain filter functionality for Quote Bank tab

## HTML Structure Reference:
```html
<!-- Tab 1: Interview card structure -->
<div class="interview-card">
    <div class="interview-header">
        <h3>INT## - [Expert Type]</h3>
        <p>Focus: [Focus Areas]</p>
    </div>
    <div class="interview-body">
        <div class="summary-section">
            <h4>Context</h4>
            <ul><li>...</li></ul>
        </div>
        <div class="key-quote-box">
            <p>"[Quote]"</p>
        </div>
    </div>
</div>

<!-- Tab 2: Finding card structure -->
<div class="finding-card challenge">
    <h4><span class="relevance">#1 CRITICAL</span> [Title]</h4>
    <div class="finding-content">
        <ul><li>...</li></ul>
    </div>
    <div class="finding-sources">Sources: INT##, INT##</div>
</div>

<!-- Tab 4: Quote array structure -->
const quotes = [
    {
        text: "[Quote text]",
        source: "INT## ([Expert Type])",
        dimension: "0",
        themes: ["enforcement", "section112"],
        tags: ["Critical", "Summary"]
    },
    ...
];
```

## Output:
A complete, self-contained HTML file that can be opened in any browser.
