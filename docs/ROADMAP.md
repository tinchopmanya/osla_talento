---
status: legacy_do_not_use_as_truth
legacy_marked_at: 2026-05-12
supersedes: C:\dev\Investigacion_Osla_consolidada\OK\modulos\osla_talento\product.md
reason: OSLA canonical documentation moved to consolidated OK tree after V3/saneamiento audit.
do_not_use_for: product_truth, roadmap_truth, implementation_scope, claims, data_rights
---

# ROADMAP — OslaTalento (Workforce Intelligence UY)

## Estado actual

MVP conceptual. Requiere integración BPS + INE ECH + OECD AI Exposure Index. ML para automation risk scoring y employment forecasting.

---

## Roadmap integrado

### Fase 1 — Automation Risk Scoring MVP (semanas 1-12)

**Entidades canónicas:**
- Empresa (RUT, sector, tamaño)
- Empleado (ocupación, salario, edad, educación — anónimo)
- Ocupación (código INE, OECD exposure score)
- Riesgo (exposición IA, automación probabilidad)
- Recomendación (reskilling path)

**Milestones:**
- **M1:** BPS microdatos API connector (1.2M cotizantes, estado laboral)
- **M2:** INE ECH microdatos integration (50 años histórico, ocupaciones, salarios)
- **M3:** OECD AI Exposure Index calibration para UY (task-based model)
- **M4:** Logistic regression + GBM automation risk model (78-85% accuracy)
- **M5:** ARIMA/Prophet employment forecasting (6/12 meses, RMSE 0.3pp)
- **M6:** Wage impact regression (predicción cambio salarial si ocupación se automatiza)
- **M7:** Reskilling recommender (classification de ocupaciones alternativas)
- **M8:** Product surface `/product/company/` (nómina analysis)
- **M9:** Dashboard B2B CFOs (risk heatmap + reskilling plan)
- **M10:** Testing + documentation (70+ test cases)
- **M11:** Privacy compliance (GDPR-like handling of employment data)
- **M12:** MVP launch con 3 empresas piloto

**ML Pipeline:**
1. Feature engineering: ocupación (OECD features: 41 dimensiones), sector, tamaño empresa, salario, edad, educación
2. Automation risk (Logistic Regression): baseline interpretable, luego GBM ensemble
3. Employment forecast (ARIMA/Prophet): series temporal por sector
4. Wage prediction (OLS regression): impacto salarial por exposición
5. Reskilling recommender (similarity matching en occupations space)

**Validation criteria:**
- BPS sync latency <1 mes (datos privados, acceso restringido)
- INE ECH histórico completo (1968+)
- Automation risk calibration r >0.65 con desempleo real
- Employment forecast RMSE <0.4pp (6 meses)
- Wage impact R² >0.58
- CFO adoption (SUS >70)
- Privacy compliance: zero PII leaks

---

### Fase 2 — Job Board Scraping + Global Benchmark (semanas 12-22)

**Milestones:**
- **M13:** Job boards scraping (LinkedIn, BumeranJob, Zonajobs, Infojobs)
- **M14:** Demand analysis (qué ocupaciones crecen/caen en tiempo real?)
- **M15:** ILO GenAI Index integration (internacional benchmark)
- **M16:** WEF Future of Jobs survey data integration
- **M17:** Scenario modeling (if AI adoption follows Singapur vs Dinamarca vs EU)
- **M18:** API product (/api/v1/workforce/*)

**ML/Data enhancements:**
- NLP para ocupación classification en job postings
- Temporal trend analysis (demand growth rate)
- Scenario forecasting (Monte Carlo)

**Validation criteria:**
- Job board coverage >1K postings/mes
- Demand forecast correlation >0.75 con BPS real
- Scenario model skill >0.60 (6 meses)
- API latency <500ms

---

### Fase 3 — Reskilling Marketplace + Recommendation (semanas 22-32)

**Milestones:**
- **M19:** Reskilling provider network (UDELAR, ORT, Outsourcing companies)
- **M20:** Training recommendation engine (per ocupación)
- **M21:** ROI calculation (costo reskilling vs salary impact)
- **M22:** Mobile app (employee self-assessment)

**ML/Platform enhancements:**
- Reinforcement learning para reskilling paths (optimized sequence)
- Recommendation confidence scoring
- ROI uncertainty quantification

**Validation criteria:**
- Reskilling paths coverage >100 occupaciones
- ROI forecast error MAE <15%
- Mobile MAU >1K employees

---

### Fase 4 — Policy Recommendations + Scale (meses 8+)

**Milestones:**
- **M23:** Policy recommendation engine (based on OECD, WEF best practices)
- **M24:** Government integration (MTSS, AGESIC policy input)
- **M25:** Regional expansion (Argentina, Chile labor data)

---

## Stack especificación

**Backend:**
```
FastAPI + Pydantic
Postgres 16 (empresa data) + separate secure module (BPS microdatos)
Airflow para ETL mensual
Redis para caching (no sensitive data)
```

**Frontend:**
```
Next.js 15
Tailwind CSS
Plotly para heatmaps + scenarios
D3.js para reskilling paths
```

**ML:**
```
scikit-learn (logistic regression baseline)
LightGBM (automation risk GBM)
statsmodels (ARIMA/OLS)
Prophet (forecasting)
PyTorch (future DL enhancements)
spaCy (job posting NLP)
MLflow
```

**Data sources:**
```
BPS cotizantes (acceso restringido, acuerdo requiere)
INE ECH microdatos (acceso académico/público)
OECD AI Exposure Index (free)
ILO GenAI Index (free)
WEF Future of Jobs (paid access o publishes aggregate)
LinkedIn scraping (terms of service compliant)
BumeranJob, Zonajobs scraping (if allowed)
MTSS normativa (libre)
```

---

## Métricas de éxito

| Métrica | Actual | Target M12 | Target M32 |
|--------|--------|------------|------------|
| Empresas perfiladas | 0 | 5 | 50 |
| Empleados analizados | 0 | 10K | 100K |
| Automation risk calibration (r) | N/A | 0.65 | 0.80 |
| Employment forecast RMSE | N/A | 0.4pp | 0.25pp |
| Reskilling paths available | 0 | 20 | 200 |
| CFO users | 0 | 5 | 50 |
| MRR | $0 | $500 | $10K |

---

## Riesgos y mitigaciones

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|-------------|--------|-----------|
| BPS access denied (datos sensibles) | Media | Alto | Fallback a INE ECH + job boards |
| OECD AI Exposure sesgo USA/EU | Media | Medio | Local calibration con BPS defaults |
| Employee resistance (anxiety) | Media | Bajo | Frame como opportunity, not threat |
| Competencia de consultoras RH | Media | Medio | Defensible: data-driven, not consultancy |
| Regulación privacidad UY (empleados) | Media | Medio | Anonimización, no PII storage |

---

## Presupuesto estimado (MVP)

| Línea | Costo | Duración |
|-------|-------|----------|
| Ingeniería (2.5 FTE) | $37K | 6 meses |
| Cloud infra (AWS) | $1.5K/mes | ongoing |
| BPS access (potential licensing) | $5K/mes | si aplica |
| Testing + empresa pilots | $4K | 2 meses |
| Legal (privacy compliance) | $3K | 1 mes |
| **Total MVP** | **~$80K** | **6 meses** |

---

## Hitos clave

- **Week 2:** M1 (BPS access critical, negotiate early)
- **Week 6:** M2-M3, INE ECH + OECD calibration
- **Week 10:** M4-M5, risk + forecast models validated
- **Week 12:** M6-M7, recommendations funcionales
- **Week 14:** M8-M9, dashboard ready
- **Week 16:** M10-M12, 3 empresas en piloto
