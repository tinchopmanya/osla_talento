---
status: legacy_do_not_use_as_truth
legacy_marked_at: 2026-05-12
supersedes: C:\dev\Investigacion_Osla_consolidada\OK\modulos\osla_talento\product.md
reason: OSLA canonical documentation moved to consolidated OK tree after V3/saneamiento audit.
do_not_use_for: product_truth, roadmap_truth, implementation_scope, claims, data_rights
---

# Documento de Producto: OslaTalento

## 1. Visión del Producto

OslaTalento es una plataforma de **workforce intelligence** que cuantifica riesgos de automatización por rol y predice impacto laboral bajo distintos escenarios tecnológicos. Empodera a CFOs, VP de Operaciones y equipos de recursos humanos para tomar decisiones proactivas sobre upskilling, reskilling y planificación de fuerza laboral en contexto de adopción masiva de IA generativa.

**Score de Viabilidad: 3.7/5**

---

## 2. Problema que Resuelve

Los decisores empresariales en Uruguay enfrentan incertidumbre crítica post-2023 (boom ChatGPT/GenAI):
- **¿Cuántos empleados de mi nómina son susceptibles a automatización?** Desconocimiento cuantificado
- **¿En qué timeline?** Sin visibilidad a 12/24/36 meses
- **¿Cuánto ahorro económico si automatizo estos roles?** Sin estimación de impact financiero
- **¿Qué programas de reskilling necesito?** Sin recommendations data-driven
- Incapacidad de planificar inversiones en talento vs. capex en tecnología
- Regulación laboral presionando (Uruguay: fuerte protección empleo, Ley Seguridad Social)

**Consecuencias:** Decisiones de automatización sin data; desajuste entre capacidades laborales y demanda; obsolescencia de fuerza laboral; reclamos sindicales impredecibles.

---

## 3. Cliente Ideal (ICP)

**Primario:** CFOs, VP Operaciones, VP RRHH en empresas 500+ empleados en Uruguay
- Presupuesto de payroll >USD 10M/año
- Exposición sectorial a automatización (banking, BPO, retail, manufactura)
- Presión regulatoria o de stakeholders (junta directiva, sindicatos) por gestión de transición laboral

**Secundario:**
- Business Process Outsourcers (BPOs) locales
- Empresas IT/servicios (propias del Uruguay como mercado de exportación)
- Aseguradoras (riesgo de responsabilidad civil, litigation)

**Tamaño ICP:** ~200-300 empresas en Uruguay con >500 empleados.

---

## 4. Propuesta de Valor

**Estrategia Cluster:** **Gobierno** (Presupuestos + Municipal + Empleo). Cross-sell Empleo ↔ Presupuestos: 35-40%. BPS es shared con Company y Siniestralidad.

**RECOMENDACIÓN:** No deprioritizar Year 1. Benchmarking internacional muestra dificultad en monetización de workforce intelligence.

**Para Sobrevivir: Sistema Operativo, No Observatorio**
- Talento requiere ser **sistema operativo** (alertas, API, monitoreo continuo), no observatorio estático.
- **Wedge:** Cruzar vacantes+skills+prensa+IMPO+indicadores laborales+eventos IA/automatización.
- Transformar de "observatorio lindo" a plataforma operativa con workflow.

| Stakeholder | Valor Entregado |
|---|---|
| **CFO / VP Operaciones** | Cuantificación de riesgo automatización por rol (logit model 78-85% accuracy). Escenarios de ahorro (capex IA vs. payroll savings 12/24/36m). ROI analysis de inversión en upskilling. |
| **VP RRHH / Learning & Development** | Identificación de roles high-risk. Recomendaciones de reskilling (matching BPS + INE ECH). Roadmap de transición laboral. Comunicación con empleados/sindicatos (data-backed). |
| **Empleados / Sindicatos** | Transparencia sobre riesgos. Acceso a programas de capacitación. Información de empleabilidad futura. |

**Precio:** USD 300-800/mes (según tamaño nómina; tiers)

**Ola 008-010: Future of Work Intelligence Validada**
Las olas 008-010 transforman OslaTalento. Future of Work / AI Impact Intelligence ya es una familia validada. El stack O*NET+ILOSTAT+ILO exposure+BLS+Eurostat+JRC+OECD es el mejor para medir exposición ocupacional a IA, reskilling y calidad del empleo. No solo 'cuántos empleos destruye la IA' sino qué ocupaciones cambian, qué skills importan y cómo cambia la organización del trabajo. Latam: 26-38% empleos expuestos a GenAI (ILO+World Bank).

---

## 5. Fuentes de Datos

### Fuentes Uruguayas (Libre/Semi-libre Acceso)
- **INE ECH (Encuesta Continua de Hogares) 1968-presente:** +1.2M observaciones de trabajadores uruguayos; ocupación, educación, ingresos, sector. **Score 5/5** (24K hogares/año, histórico desde 1968)
- **BPS (Banco de Previsión Social) 1.2M cotizantes:** Registro de empleados activos, salarios, sector SCIAN, edad. **Score 5/5** (shared con Company y Siniestralidad)
- **MTSS (Ministerio de Trabajo y Seguridad Social):** Datos de empleo formal, registros de conflictividad laboral. **Score 4/5**
- **Job boards locales:** Scraping LinkedIn UY, BuscOempleo, Computrabajo (requerimientos de rol, skills demandadas)
- **INE Microdatos Laborales:** Encuesta Continua de Hogares con variables ocupacionales, educación, salarios a nivel individual (>1.2M registros históricos desde 1968). **Score 5/5**
- **BPS Series Empleo:** Series oficiales de cotizantes activos, empleo formal por sector SCIAN, dinámicas de empleo/desempleo. Sin API formal; acceso requiere negociación institucional. **Score 4/5**

### Fuentes Internacionales (Libre Acceso)
- **OECD AI Exposure Index:** 41 actividades económicas clasificadas por exposición a IA, pre-calculadas (libre acceso)
- **ILO Generative AI and Jobs:** Estudio global sobre probabilidad de desplazamiento por rol (2024)
- **WEF Future of Jobs Report 2025:** Predicciones de demanda de skills, sectores
- **BLS (Bureau of Labor Statistics):** Proyecciones de empleo por ocupación (US; extrapolable)
- **LinkedIn Economic Graph:** Agregados de demanda de skills por rol (algunos datos públicos)
- **O*NET (Occupational Information Network):** Base de datos de características de ocupaciones (análisis de automatización)
- **World Bank DataBank:** Indicadores laborales, educación por país

### Fuentes Internacionales Adicionales (Ola 008-010)
- **ILOSTAT** (CC BY 4.0): empleo, desempleo, salarios, informalidad, seguridad ocupacional, skills
- **OECD** (comercial con atribución): empleo, productividad, comparación internacional
- **UIS UNESCO** (CC BY-SA 4.0): educación y formación
- **O*NET** (Creative Commons): ocupaciones, tasks, skills, knowledge, work activities, technology skills, job zones — columna vertebral para future of work
- **ILO GenAI exposure index:** ~1/4 trabajadores con exposición a GenAI
- **JRC AIM-WORK:** 30% trabajadores UE usan AI tools, 37% monitoreados
- **OECD AI-WIPS:** skills, algorithmic management, 6,000+ managers en 6 países
- **BLS (USA):** ~1.7M software developers, +16% proyectado 2024-2034
- **QWI (Census, API desde ene 2026):** 32 indicadores laborales por industria
- **Eurostat ICT specialists:** 10M+ en UE (5% empleo, 2024)
- **World Bank ICT service exports** (CC BY 4.0): comparables globales

**Viabilidad de Fuentes: 5/5**. Limitación: granularidad limitada en datos agregados.

**NOTA CRÍTICA:** BPS es altamente sensible. Acceso requiere:
- Negociación institucional (no es público)
- Acuerdo de confidencialidad
- Posible denegación por MTSS/gremios

**Fallback:** INE ECH (públicamente disponible) + job boards scraping + agregados BPS sindicales (si acceso denegado)

### Contexto Sectorial TI Uruguay (Investigación 039 - AI Disruption Employment Uruguay)
- **Tamaño del sector TI:** USD 3.3B revenue (2023); proyectado alcanzar 5% del PIB en 2025 y 10% para 2030
- **Exportaciones de IT:** USD 1B (más alto per cápita del mundo)
- **Base de profesionales:** 24K+ profesionales IT en 530 empresas outsourcing, 33K total incluyendo independientes
- **Concentración exportadora:** USA representa 80% de las exportaciones de servicios IT uruguayos
- **Implicancia para OslaTalento:** Sector TI es piloto crítico para risk scoring; automatización de capas bajas de outsourcing impactará empleabilidad de 24K+ trabajadores IT en horizonte 18-36 meses

---

## 6. Modelos ML Defensibles

### 6.1 Automation Risk Scoring (Logistic Regression + GBM)
- **Input:** Nómina del cliente (ocupación, educación, sector, ingresos) + características de tarea (rutinariedad, abstracción, manejo de datos)
- **Output:** Score 0-100 de riesgo automatización 12/24/36 meses; nivel de confianza
- **Métrica:** Accuracy 78-85% en validación histórica (comparando contra cambios ocupacionales reales INE ECH 2020-2026)
- **Ventaja defensible:** Entrenado con datos INE históricos + OECD + ILO; modelos específicos a contexto laboral UY (regulación, estructuras salariales BPS). Imposible replicar sin datos históricos UY.

### 6.2 Employment Forecast (ARIMA + Prophet)
- **Input:** Series temporal de empleo por sector (INE ECH), crecimiento PIB proyectado, índice de inversión en tecnología
- **Output:** Demanda proyectada de empleo por sector/rol 12/24/36 meses
- **Métrica:** RMSE <0.3 puntos porcentuales (error medio 0.2-0.3%)
- **Ventaja defensible:** Series largas INE (1968+); modelado de ciclo laboral uruguayo específico

### 6.3 Wage Impact Model (Ridge Regression)
- **Input:** Automatización esperada por sector, educación requerida, demanda de re-skills (O*NET + LinkedIn)
- **Output:** Impacto salarial predicho (-20% a +10%) tras automatización para cada rol
- **Métrica:** R² 0.58 en validación
- **Ventaja defensible:** Combinación única de datos BPS (salarios) + OECD + ILO; no disponible globalmente con esta granularidad

### 6.4 Reskilling Recommendation (Collaborative Filtering + Content-based)
- **Input:** Perfil ocupacional actual, skills de rol (O*NET), demanda de mercado (LinkedIn, BuscOempleo)
- **Output:** Top 3-5 roles alternativos con probabilidad de transición, programas de capacitación recomendados
- **Métrica:** Hit rate 65%+ (recomendaciones que aparecen en job postings actuales)
- **Ventaja defensible:** Recomendaciones ajustadas a mercado laboral local (INE ECH skill gaps)

### Modelos de Exposición a IA (Ola 008-010)
- **Modelo de exposición ocupacional a GenAI cruzando O*NET tasks/skills con benchmarks de IA (ILO, JRC)**
- **Score de reskilling: skills actuales vs skills demandadas, usando OECD AI-WIPS y Eurostat ICT**
- **Clasificación de empresas por adopción de IA (Census BTOS, Eurostat AI adoption)**

---

## 7. Competencia y Diferenciación

**Competencia Score: 3.2/5 (Empleo e IA, #15 en ranking)**

**Categoría: Intelligence-layer (NO monetizable fácilmente) — "OBSERVATORIO SIN WORKFLOW DEFENDIBLE"** — Scoring más bajo de todos. Buyer difuso (gobierno, academia, consultoras, RRHH), WTP=2. Clasificado como "observatorio lindo" que pierde frente a verticales con workflow y compliance. **MOAT: DÉBIL** — modelos predictivos son estándares; diferenciación por datos URY es temporal si acceso BPS es denegado.

### Competidores Directos Locales
- **Ninguno identificado** con automation risk scoring + workforce forecasting integrado en Uruguay (abril 2026)

### Competidores Globales (TODOS Enterprise-only, SIN datos LATAM granular)
- **Lightcast:** 3B+ job postings, 165 countries. Enterprise-only, USD 50K+/año. Sin datos LATAM detallados.
- **LinkedIn Talent Insights:** 1B+ miembros. Enterprise-only, USD 50K+/año. Sin datos LATAM detallados.
- **Revelio Labs:** Workforce intelligence. Enterprise-only, USD 50K+/año.
- **Mercer Workforce Analyzer:** HR analytics; no automation risk scoring específicamente
- **Deloitte Human Capital:** Consultoría; no herramientas self-service
- **McKinsey Jobs Impact Tool:** Report público genérico; no customizable por empresa
- **Burning Glass / Lightcast:** Labor market intelligence; sin automation scoring
- **Coursera / Udacity:** Upskilling platforms; sin assessment de riesgo personal
- **LinkedIn Learning Insights:** Skill gaps genéricos; sin predicción de automatización

**BARRERA CRÍTICA:** Todos los competidores son enterprise-only USD 50K+/año, DIFFICULT to monetize at SME level.

### Competidores Empleo (Sub-vertical)
- **Advice:** Local
- **Observatorio TI CUTI:** Información de mercado laboral IT
- **LinkedIn Economic Graph:** Global
- **BID/CEPAL:** Informes macroeconómicos
- **Bumeran/portales:** Job boards genéricos
- **Gallito/BuscoJobs:** Job boards locales

### Competidores Educación (Sub-vertical)
- **Q10:** Plataforma educativa
- **Moodle/LMS, Canvas/Blackboard:** Global LMS
- **Analítica UDE:** Analytics universitario
- **ANEP dashboards:** Datos de educación pública

### Diferenciación Defensible de OslaTalento (DÉBIL)
1. **Data URY-específica:** INE ECH (1968+) + BPS + regulación laboral local => modelos no replicables (pero acceso BPS denegado = fallback a INE ECH público)
2. **Automation Risk scoring:**  78-85% accuracy vs. genérico McKinsey (~45%)
3. **Integración nómina privada:** Upload de nómina => scoring personalizado por empleado (no solo agregado)
4. **Wage Impact forecasting:** Cuantificación de impacto económico personal
5. **Reskilling recommendations:** Matching a mercado laboral local (LinkedIn + BuscOempleo + universidades UY)
6. **Precio accesible:** USD 300-800/mes vs. consultoría $10K+/mes
7. **Wedge de montaje:** Cruzar vacantes + skills + prensa + IMPO + indicadores laborales + eventos IA/automatización

---

## 8. Arquitectura Técnica

### Stack Principal
- **Backend:** FastAPI + Gunicorn + Nginx
- **Frontend:** Next.js 15 + Tailwind CSS (dashboards, reportes)
- **Base de Datos:** PostgreSQL 16 + TimescaleDB (datos temporales INE ECH)
- **ML - Risk Scoring:** scikit-learn (Logistic Regression, LightGBM, Ridge)
- **ML - Forecasting:** statsmodels + Prophet (ARIMA, exponential smoothing)
- **ML - Reskilling:** scikit-learn (collaborative filtering, content-based)
- **NLP:** spaCy (matching ocupacional, extracción de skills de JDs)
- **Orquestación:** Airflow (DAG: descarga INE ECH → entrenamiento modelos → batch scoring)
- **Monitoreo ML:** MLflow (versionado de modelos, tracking de performance)
- **Auth:** OAuth2 + JWT
- **File Processing:** Pandas, openpyxl (upload de nóminas CSV/XLSX)

### Flujo de Datos (Alto Nivel)
1. Cliente CFO/RRHH: accede a plataforma, upload nómina (CSV con ocupación, edad, educación, ingresos)
2. Validación y matching ocupacional contra taxonomía ISCO-88/SCIAN
3. Ejecución en paralelo:
   - Risk Scoring: Logistic Regression + GBM => score 0-100 por empleado
   - Employment Forecast: ARIMA para sector del cliente
   - Wage Impact: predicción de cambio salarial
   - Reskilling: recomendaciones de transición
4. Agregación a nivel empresa: % empleados alto/medio/bajo riesgo
5. Dashboard: gráficos por ocupación, sector, educación
6. Reportes PDF descargables; escenarios de ahorro económico
7. API REST para integraciones con sistemas RRHH (SAP SuccessFactors, ADP)

### Escalabilidad
- PostgreSQL + índices para queries de nómina rápidas
- Batch processing nocturno de modelos (Airflow)
- MLflow para versionado de modelos sin duplicación
- Redis para cachés de resultados (TTL 7 días)

---

## 9. Roadmap Resumido

### Fase 1 (Meses 1-2): MVP - Risk Scoring
- Modelo Risk Scoring (Logistic + GBM)
- Upload de nómina (CSV)
- Dashboard básico: % empleados por riesgo, ocupación
- Reportes PDF
- Piloto con 1-2 CFOs

### Fase 2 (Meses 3-4): Forecasting + Reskilling
- Employment Forecast (ARIMA)
- Wage Impact model
- Reskilling recommendations
- Escenarios de ahorro económico (ROI análisis)
- Dashboard expandido con proyecciones

### Fase 3 (Meses 5-6): Integraciones + B2B
- API REST con estándares RRHH (SAP, ADP, Workday)
- Admin panel: usuarios, cuotas, reportes de uso
- Mobile app complementaria (iOS/Android)
- SLA 99.5% uptime
- 3-5 clientes pagando

### Fase 4 (Post-MVP): Avances
- Benchmarking anónimo (empresa vs. sector)
- Integración con plataformas de upskilling (Coursera, Udacity, universidades UY)
- Análisis de sinergias de reskilling (match con demanda otras empresas)
- Expansion regional (Argentina, Paraguay)

---

## 10. Métricas de Éxito

| Métrica | Target | Timeline |
|---|---|---|
| **Viabilidad Y1 (100 clientes × USD 80 ARPU)** | USD 96K ARR | Mes 6 |
| **Viabilidad Y2 (150 clientes × USD 80 ARPU)** | USD 144K ARR | Mes 12 |
| **Accuracy Risk Scoring** | 78-85% en validación histórica | Mes 2 |
| **RMSE Forecasting Empleo** | <0.3pp en sector | Mes 4 |
| **R² Wage Impact** | 0.58+ | Mes 4 |
| **Hit Rate Reskilling** | 65%+ recomendaciones en job postings | Mes 4 |
| **Clientes Pagando** | 3-5 CFOs/RRHH VPs | Mes 6 |
| **MRR Objetivo** | USD 1.5K-3K | Mes 6 |
| **Uptake de Reports** | 70%+ clientes descargan reportes mensual | Mes 6 |
| **Latencia Scoring** | <2 min para nómina 500 empleados | Mes 4 |
| **NPS Usuarios** | >50 | Mes 6 |

---

## 11. Riesgos y Mitigaciones

**Riesgo Overall: 1.5/5 (GREEN)**

La arquitectura legal es defensible:
- Datos agregados INE son open
- Ley de IA 2026 afectará scoring de empleabilidad (future risk 2/5)
- Usar datos agregados, NOT individual BPS records
- Decreto 54/2017 soporta uso comercial de datos abiertos

**Riesgo Anti-LLM:**
- **Scoring más bajo:** buyer difuso (gobierno, academia, consultoras, RRHH), WTP=2
- **Clasificado como:** "observatorio lindo" que pierde frente a verticales con workflow y compliance
- **Wedge empleo:** Cruzar vacantes+skills+IMPO+indicadores es replicable con deep research

**Métricas por Sub-vertical:**
- **Empleo:** buyer=3, WTP=2, saturado=1, defensa=3, ticket USD 30/mes, ciclo 60d
- **Educación:** buyer=3, WTP=2, saturado=1, defensa=3, ticket USD 50/mes, ciclo 90d

| Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|
| **Acceso BPS denegado** | Media-Alta | Alto | Fallback: INE ECH + job boards scraping. Modelos aún funcionales pero con cobertura <100%. |
| **Modelos overfitting a 2020-2026** | Media | Medio | Validación frecuente contra nuevos datos INE ECH; reentrenamiento trimestral. |
| **Ley de IA 2026** | Media | Medio | Monitorear regulación uruguaya/OECD; scoring debe ser interpretable (no black-box). |
| **AI Disruption (Investigación 039)** | Media-Alta | Alto | Ventana de oportunidad crítica 18-36 meses. Capas bajas de outsourcing IT se eliminan por automatización GenAI. Trabajadores sin reskilling enfrentan desempleo estructural. Contexto: Big Mac USD 6.91 (19% sobre USA), tasa suicidio 21-24.8/100K (top 5 mundial). Sensibilidad social crítica refuerza valor pero señala mercado volátil. |
| **Incapacidad de monetizar intelligence** | Alta | Alto | Evitar modelo "observatorio". Transformar a sistema operativo: alertas, API, monitoreo continuo, workflow. |

### Alertas Ola 008-010
- **Ranking final (019):** Talent Intelligence no aparece como vertical top independiente. Debe evolucionar hacia scoring y clasificación de skills/exposición (classification layer) más que agregación simple de datos laborales.
- **Census BTOS discontinuidad:** Census BTOS cambió pregunta de IA en nov 2025 y nueva serie desde dic 2025 — discontinuidad metodológica a considerar.
