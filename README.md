# Thailand Human Rights Report 2025: Qualitative Analysis Pipeline

## Overview

This repository contains the analytical pipeline and methodology for the qualitative chapter of the **Human Rights in Thailand Report 2025**, produced by the [World Justice Project](https://worldjusticeproject.org/).

The pipeline processes expert interviews through a structured analysis framework, generating coded insights, synthesized findings, and a quote bank for report writing. The methodology combines human analyst interpretation with AI-assisted systematic coding to ensure both nuance and consistency.

> **Privacy Notice**: This repository contains only the analytical pipeline structure, prompts, templates, and documentation. All interview data, transcripts, and analysis outputs are excluded for privacy and confidentiality reasons.

---

## Methodology

### Research Design

The qualitative component of the Human Rights in Thailand Report follows a **key informant interview methodology**, gathering perspectives from experts across civil society, academia, legal practice, journalism, and human rights organizations.

#### Data Collection
- **Interview format**: Semi-structured interviews with open-ended questions
- **Expert selection**: Purposive sampling targeting diverse expertise areas:
  - Civil and political rights specialists
  - Labor rights organizations
  - Legal practitioners and academics
  - Journalists and media organizations
  - Regional experts (particularly Deep South specialists)
  - Youth and student movement representatives
- **Geographic coverage**: National scope with specific attention to Bangkok, rural areas, and the Deep South (Pattani, Yala, Narathiwat)

#### Analytical Framework

The analysis uses a hierarchical coding system aligned with the **WJP Rule of Law Index** conceptual structure:

| Dimension | Domain | Sub-indicators |
|-----------|--------|----------------|
| 0 | Current Status Overview | 0.1-0.4: Overall assessment, challenges, progress, context |
| 1 | Civil and Political Rights | 1.1-1.6: Religion, equality, expression, assembly, right to life, privacy |
| 2 | Participation and Access to Information | 2.1-2.4: Complaints, civic checks, participation, information access |
| 3 | Labor Rights and Property Rights | 3.1-3.2: Labor protections, expropriation safeguards |
| 4 | Fair and Impartial Justice | 4.1-4.8: Access, independence, discrimination, due process |

#### Cross-cutting Analysis Dimensions

The coding schema incorporates:

- **Vulnerable group tags**: Migrant workers (VG-MW), Malay Muslims (VG-MM), Indigenous peoples (VG-IP), Women (VG-WM), LGBTQ+ (VG-LG), Youth (VG-YT), Political activists (VG-PA), HR defenders (VG-HR), Journalists (VG-JN)
- **Geographic specificity**: Deep South (GEO-DS), Bangkok (GEO-BK), Rural (GEO-RU), National (GEO-NA)
- **Cross-cutting tags**: Challenges [CHAL], Progress [HIGH], Quotable [QUOTE], Quantitative connections [QUANT], Expert disagreement [CONTRAST]

### Processing Pipeline

The analysis follows a 5-step pipeline ensuring reproducibility and consistency:

```
Step 1: Individual Interview Analysis
    ↓
Step 2: Dimension Synthesis (5 dimensions)
    ↓
Step 3A: Quote Bank          Step 3B: Chapter Draft
    ↓                              ↓
Step 4: Interactive Dashboard
    ↓
Step 5: Consistency Testing
```

#### Step 1: Interview Analysis
Each interview is analyzed using both:
- **Human analyst notes** (treated as authoritative interpretation)
- **Full transcript** (for verbatim quote extraction)

This dual-source approach ensures that expert interpretive judgment guides the analysis while maintaining rigorous evidentiary standards through exact quotations.

#### Step 2: Dimension Synthesis
Individual interview analyses are aggregated by dimension, identifying:
- Recurring themes across multiple sources
- Points of consensus and disagreement
- Severity rankings based on source frequency
- Vulnerable group impact patterns

#### Step 3: Output Generation
- **Quote Bank**: Curated collection of impactful verbatim quotes with full traceability
- **Chapter Draft**: Narrative synthesis organized by thematic area

#### Step 4: Dashboard
Interactive HTML visualization enabling exploration of findings by dimension, theme, and source.

#### Step 5: Consistency Testing
Automated validation ensuring:
- All quotes trace to original transcripts
- Anchor quotes (critical evidence) are preserved across pipeline runs
- Code assignments are valid
- No drift between pipeline versions

---

## Pipeline Structure

```
interviews/
├── README.md                    # This file
├── CLAUDE.md                    # AI assistant instructions
├── WORKFLOW.md                  # Detailed pipeline execution guide
│
├── pipeline/
│   ├── prompts/                 # Standardized prompts for each step
│   │   ├── 00_consistency_test.md
│   │   ├── 01_interview_analysis.md
│   │   ├── 02_dimension_synthesis.md
│   │   ├── 03_quote_bank.md
│   │   ├── 04_chapter2_draft.md
│   │   └── 05_dashboard_html.md
│   │
│   ├── templates/               # Output format specifications
│   │   ├── interview_analysis_template.md
│   │   ├── dimension_template.md
│   │   ├── quote_bank_template.md
│   │   ├── metrics_template.yaml
│   │   ├── validation_report_template.md
│   │   └── drift_report_template.md
│   │
│   └── anchor_quotes.yaml       # Critical quotes for consistency verification
│
├── Inputs/                      # [EXCLUDED] Interview transcripts and analyst notes
│   ├── INT##.txt                # Raw interview transcripts
│   ├── INT##_Summary Insights.txt  # Human analyst interpretations
│   ├── CODEBOOK.md              # Analytical framework
│   └── Interview codes.xlsx     # Expert-interview mapping
│
└── Outputs/                     # [EXCLUDED] Generated analysis files
    ├── interviews/              # Individual interview analyses
    ├── dimensions/              # Dimension synthesis documents
    ├── consistency/             # Validation reports
    ├── QUOTE_BANK.md
    ├── CHAPTER2_DRAFT.md
    └── dashboard.html
```

---

## Reproducibility

### Running the Pipeline

With the required input files in place:

1. Read `WORKFLOW.md` for detailed instructions
2. Execute each step in order (1 → 2 → 3A/3B → 4 → 5)
3. Use prompts in `pipeline/prompts/` for each step
4. Verify outputs match templates in `pipeline/templates/`
5. Ensure Step 5 (consistency test) passes before finalizing

### Adding New Interviews

1. Add `INT##.txt` and `INT##_Summary Insights.txt` to `Inputs/`
2. Execute Step 1 for new interviews (or all, for consistency)
3. Re-run Steps 2-5 completely
4. Compare drift report with previous version

---

## Limitations and Considerations

### Methodological Limitations

1. **Sample size**: The qualitative findings are based on a purposive sample of experts. While selected for diversity and expertise, they cannot represent the full spectrum of perspectives in Thai society.

2. **Selection bias**: Interviewees are primarily drawn from civil society, academia, and human rights organizations. Government perspectives and views from sectors less engaged with human rights discourse may be underrepresented.

3. **Temporal snapshot**: Interviews capture expert perspectives at a specific point in time. The human rights situation is dynamic, particularly in Thailand's evolving political context.

4. **Self-censorship effects**: Some experts may self-censor on sensitive topics (monarchy, military, certain political actors), potentially underreporting issues in high-risk areas.

5. **Geographic concentration**: While efforts were made to include Deep South and rural perspectives, Bangkok-based experts and national-level analysis may be overrepresented.

### Analytical Limitations

1. **Interpretation layers**: The pipeline involves multiple interpretation stages (expert → analyst summary → AI-assisted coding). While triangulation strengthens validity, each layer introduces potential distortion.

2. **AI assistance boundaries**: The AI-assisted analysis expands on human analyst interpretations but does not independently interpret meaning. Novel insights not identified by human analysts may be missed.

3. **Quote extraction constraints**: Only explicitly stated evidence can be coded. Implied meanings, contextual knowledge, and non-verbal cues from interviews are not captured.

4. **Quantitative-qualitative gaps**: While the analysis references WJP Rule of Law Index quantitative trends, the qualitative methodology cannot directly explain statistical patterns.

### Data Protection Considerations

1. **Anonymization**: All outputs use interview codes (INT01-INT11) rather than expert names to protect source confidentiality.

2. **Sensitive content**: Interview transcripts may contain sensitive information about human rights violations, vulnerable individuals, or politically sensitive topics. These are excluded from the repository.

3. **Expert safety**: Some experts agreed to public acknowledgment; others requested anonymity. Attribution decisions are handled separately from this pipeline.

---

## Integration with WJP Rule of Law Index

The qualitative analysis is designed to complement and contextualize the [WJP Rule of Law Index](https://worldjusticeproject.org/rule-of-law-index/) quantitative data for Thailand. Key integration points:

- **Explaining trends**: Qualitative evidence illuminates why certain indicators improved or declined
- **Adding nuance**: Expert perspectives reveal complexities behind aggregate scores
- **Identifying gaps**: Interviews may surface issues not fully captured in quantitative measures
- **Validating patterns**: Cross-referencing qualitative findings with quantitative trends strengthens overall conclusions

---

## Citation

When referencing this methodology or findings:

> World Justice Project. (2025). *Human Rights in Thailand Report 2025: Qualitative Analysis Methodology*. Washington, DC: World Justice Project.

---

## License

This pipeline structure and methodology documentation are provided for transparency and reproducibility. The World Justice Project retains all rights to the analytical framework, interview data, and report content.

For inquiries about the methodology or collaboration, contact: [research@worldjusticeproject.org](mailto:research@worldjusticeproject.org)

---

*Pipeline Version 2.0 | Thailand Human Rights Report 2025 | World Justice Project*
