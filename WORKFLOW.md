# Workflow: Thailand Human Rights Qualitative Analysis Pipeline

Este documento describe el flujo de trabajo para generar el análisis cualitativo del Thailand Human Rights Report 2025.

---

## Resumen del Pipeline

```
┌─────────────────────────────────────────────────────────────────┐
│                         INPUTS                                  │
│  Inputs/INT##.txt + Inputs/INT##_Summary Insights.txt           │
│  Inputs/CODEBOOK.md                                             │
└───────────────────────────┬─────────────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│  PASO 1: Análisis Individual de Entrevistas                     │
│  → Outputs/interviews/INT##_Analysis.md (uno por entrevista)    │
└───────────────────────────┬─────────────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│  PASO 2: Síntesis por Dimensión                                 │
│  → Outputs/dimensions/DIMENSION_0_Overview.md                   │
│  → Outputs/dimensions/DIMENSION_1_CivilPolitical.md             │
│  → Outputs/dimensions/DIMENSION_2_Participation.md              │
│  → Outputs/dimensions/DIMENSION_3_LaborProperty.md              │
│  → Outputs/dimensions/DIMENSION_4_Justice.md                    │
└───────────────────────────┬─────────────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│  PASO 3A: Quote Bank          │  PASO 3B: Chapter 2 Draft       │
│  → Outputs/QUOTE_BANK.md      │  → Outputs/CHAPTER2_DRAFT.md    │
└───────────────────────────┬───┴─────────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│  PASO 4: Dashboard HTML                                         │
│  → Outputs/dashboard.html                                       │
└───────────────────────────┬─────────────────────────────────────┘
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│  PASO 5: Test de Consistencia                                   │
│  → Outputs/consistency/metrics_v#.yaml                          │
│  → Outputs/consistency/validation_report_v#.md                  │
│  → Outputs/consistency/drift_report_v#.md (si hay versión prev) │
└─────────────────────────────────────────────────────────────────┘
```

---

## Paso 1: Análisis Individual de Entrevistas

### Cuándo ejecutar:
- Primera vez: Para todas las entrevistas
- Actualizaciones: Solo para entrevistas nuevas (INT10, INT11, etc.)

### Comando para Claude Code:

```
Analiza la entrevista INT## siguiendo el prompt en pipeline/prompts/01_interview_analysis.md

Inputs:
- Transcripción: Inputs/INT##.txt
- Summary Insights: Inputs/INT##_Summary Insights.txt (si existe)
- Codebook: Inputs/CODEBOOK.md
- Template: pipeline/templates/interview_analysis_template.md

Output: Outputs/interviews/INT##_Analysis.md
```

### Orden recomendado:
1. INT01 → INT02 → INT03 → ... → INT09
2. Para actualizaciones: Solo las nuevas entrevistas

---

## Paso 2: Síntesis por Dimensión

### Cuándo ejecutar:
- Siempre después de completar Paso 1
- Re-ejecutar completo en cada actualización (para mantener consistencia)

### Comando para Claude Code:

```
Genera la síntesis para la Dimensión [0/1/2/3/4] siguiendo el prompt en pipeline/prompts/02_dimension_synthesis.md

Inputs:
- Todos los archivos en Outputs/interviews/INT##_Analysis.md
- Codebook: Inputs/CODEBOOK.md
- Template: pipeline/templates/dimension_template.md

Output: Outputs/dimensions/DIMENSION_#_[Name].md
```

### Orden:
1. DIMENSION_0_Overview.md
2. DIMENSION_1_CivilPolitical.md
3. DIMENSION_2_Participation.md
4. DIMENSION_3_LaborProperty.md
5. DIMENSION_4_Justice.md

---

## Paso 3A: Quote Bank

### Cuándo ejecutar:
- Después de completar Paso 2

### Comando para Claude Code:

```
Genera el Quote Bank siguiendo el prompt en pipeline/prompts/03_quote_bank.md

Inputs:
- Todos los archivos en Outputs/interviews/
- Todos los archivos en Outputs/dimensions/
- Template: pipeline/templates/quote_bank_template.md

Output: Outputs/QUOTE_BANK.md
```

---

## Paso 3B: Chapter 2 Draft

### Cuándo ejecutar:
- Después de completar Paso 2 (puede ser paralelo a 3A)

### Comando para Claude Code:

```
Genera el Chapter 2 Draft siguiendo el prompt en pipeline/prompts/04_chapter2_draft.md

Inputs:
- Todos los archivos en Outputs/dimensions/
- Outputs/QUOTE_BANK.md (si ya existe)
- Codebook: Inputs/CODEBOOK.md

Output: Outputs/CHAPTER2_DRAFT.md
```

---

## Paso 4: Dashboard HTML

### Cuándo ejecutar:
- Después de completar Pasos 3A y 3B

### Comando para Claude Code:

```
Genera el dashboard HTML siguiendo el prompt en pipeline/prompts/05_dashboard_html.md

Inputs:
- Todos los archivos en Outputs/interviews/
- Todos los archivos en Outputs/dimensions/
- Outputs/QUOTE_BANK.md
- Outputs/CHAPTER2_DRAFT.md
- Referencia de estilo: Outputs/dashboard_v3.html

Output: Outputs/dashboard.html
```

---

## Paso 5: Test de Consistencia

### Cuándo ejecutar:
- **SIEMPRE** después de completar Paso 4
- Este paso es OBLIGATORIO antes de considerar la corrida como completa

### Comando para Claude Code:

```
Ejecuta el test de consistencia siguiendo el prompt en pipeline/prompts/00_consistency_test.md

Inputs:
- Todos los outputs generados en Pasos 1-4
- pipeline/anchor_quotes.yaml (quotes críticas a verificar)
- Outputs/consistency/metrics_v[ANTERIOR].yaml (si existe versión previa)

Outputs:
- Outputs/consistency/metrics_v#.yaml
- Outputs/consistency/validation_report_v#.md
- Outputs/consistency/drift_report_v#.md (si hay versión anterior)
```

### Criterios de Aprobación:

| Test | Umbral para PASS |
|------|------------------|
| Structural Validation | 100% secciones presentes |
| Quote Traceability | 100% quotes verificables |
| Anchor Quotes (Critical) | 100% presentes |
| Anchor Quotes (Important) | ≥80% presentes |
| Code Validation | 0 códigos inválidos |
| Drift Analysis | Sin alertas 🚨 sin resolver |

### Si el test FALLA:
1. Revisar el validation_report para identificar problemas
2. Corregir los outputs afectados
3. Re-ejecutar el test hasta que pase

---

## Flujo para Actualizaciones

Cuando agregues nuevas entrevistas (e.g., INT10, INT11):

### Opción A: Re-procesar todo (RECOMENDADO para consistencia)
```
1. Agregar INT10.txt e INT10_Summary Insights.txt a Inputs/
2. Ejecutar Paso 1 para TODAS las entrevistas (INT01-INT10)
3. Ejecutar Paso 2 para las 5 dimensiones
4. Ejecutar Paso 3A (Quote Bank)
5. Ejecutar Paso 3B (Chapter 2)
6. Ejecutar Paso 4 (Dashboard)
7. Ejecutar Paso 5 (Test de Consistencia) ← CRÍTICO
8. Comparar drift_report con versión anterior
9. Aceptar solo si drift es aceptable
```

### Opción B: Procesar solo nuevas (más rápido, menos consistente)
```
1. Agregar INT10.txt e INT10_Summary Insights.txt a Inputs/
2. Ejecutar Paso 1 SOLO para INT10
3. Ejecutar Paso 2 para las 5 dimensiones (lee todos los análisis)
4. Ejecutar Paso 3A (Quote Bank)
5. Ejecutar Paso 3B (Chapter 2)
6. Ejecutar Paso 4 (Dashboard)
7. Ejecutar Paso 5 (Test de Consistencia) ← CRÍTICO
8. REVISAR ESPECIALMENTE el drift en entrevistas no reprocesadas
```

---

## Estructura de Archivos

```
interviews/
├── WORKFLOW.md                 ← Este archivo
├── CLAUDE.md                   ← Guía para Claude Code
├── pipeline/
│   ├── prompts/
│   │   ├── 00_consistency_test.md    ← Test de consistencia
│   │   ├── 01_interview_analysis.md
│   │   ├── 02_dimension_synthesis.md
│   │   ├── 03_quote_bank.md
│   │   ├── 04_chapter2_draft.md
│   │   └── 05_dashboard_html.md
│   ├── templates/
│   │   ├── interview_analysis_template.md
│   │   ├── dimension_template.md
│   │   ├── quote_bank_template.md
│   │   ├── metrics_template.yaml        ← Template métricas
│   │   ├── validation_report_template.md
│   │   └── drift_report_template.md
│   └── anchor_quotes.yaml      ← Quotes críticas a verificar
├── Inputs/
│   ├── INT##.txt               ← Transcripciones
│   ├── INT##_Summary Insights.txt  ← Notas del analista
│   ├── CODEBOOK.md             ← Framework analítico
│   └── Interview codes.xlsx
└── Outputs/
    ├── interviews/
    │   ├── INT01_Analysis.md
    │   ├── INT02_Analysis.md
    │   └── ...
    ├── dimensions/
    │   ├── DIMENSION_0_Overview.md
    │   ├── DIMENSION_1_CivilPolitical.md
    │   ├── DIMENSION_2_Participation.md
    │   ├── DIMENSION_3_LaborProperty.md
    │   └── DIMENSION_4_Justice.md
    ├── consistency/            ← Reportes de consistencia
    │   ├── metrics_v1.yaml
    │   ├── validation_report_v1.md
    │   ├── drift_report_v1_v2.md
    │   └── ...
    ├── QUOTE_BANK.md
    ├── CHAPTER2_DRAFT.md
    └── dashboard.html
```

---

## Checklist de Verificación por Paso

### Después de Paso 1:
- [ ] Cada INT##_Analysis.md tiene todas las secciones del template
- [ ] Todas las citas son verbatim del transcript
- [ ] Los códigos de dimensión son correctos (0.1-4.8)
- [ ] Los vulnerable groups están etiquetados (VG-XX)
- [ ] Los geographic codes están presentes (GEO-XX)

### Después de Paso 2:
- [ ] Cada dimensión cita múltiples fuentes (≥3 idealmente)
- [ ] Los rankings de severidad son consistentes
- [ ] Las conexiones cuantitativas están incluidas
- [ ] Vulnerable groups summary está completo

### Después de Paso 3:
- [ ] Quote Bank tiene 50+ citas
- [ ] Chapter 2 no tiene información que no esté en los otros archivos
- [ ] Todas las citas tienen atribución (INT##)
- [ ] Chapter 2 tiene blockquotes en cada sección

### Después de Paso 4:
- [ ] Dashboard carga sin errores en browser
- [ ] Todos los tabs funcionan
- [ ] Los filtros del Quote Bank funcionan
- [ ] No hay contenido hardcodeado que no venga de los MDs

### Después de Paso 5 (OBLIGATORIO):
- [ ] validation_report muestra PASS en todos los tests
- [ ] Todos los anchor quotes críticos están presentes (100%)
- [ ] ≥80% de anchor quotes importantes están presentes
- [ ] No hay códigos inválidos
- [ ] Si hay versión anterior: drift_report no tiene alertas 🚨 sin explicar
- [ ] Decisión documentada: ACEPTAR o RECHAZAR la corrida

---

## Versionamiento

Usar nomenclatura consistente para versiones:

| Versión | Descripción |
|---------|-------------|
| v1 | Primera corrida completa (9 entrevistas) |
| v2 | Segunda corrida (con INT10, INT11 agregadas) |
| v3 | Tercera corrida (con entrevistas adicionales) |

Los archivos de consistencia se nombran con la versión:
- `metrics_v1.yaml`, `metrics_v2.yaml`
- `validation_report_v1.md`, `validation_report_v2.md`
- `drift_report_v1_v2.md` (compara v1 con v2)

---

*Workflow Version 2.0 | Thailand Human Rights Report 2025 | World Justice Project*
