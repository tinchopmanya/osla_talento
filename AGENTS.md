# AGENTS.md — OslaTalento

## Identidad del proyecto

- **Nombre**: OslaTalento (Workforce Intelligence UY)
- **Ranking InvestigaVert**: — Score 3.7)
- **AshRise project_id**: `laboral`
- **Puerto Postgres**: 5457
- **DB**: laboral / user: laboral
- **ICP primario**: CFO / VP Operations en empresas 500+ empleados
- **ICP secundario**: BPOs, empresas de outsourcing IT
- **Pricing target**: USD 300-800/usuario/mes
- **Estado validación**: PENDIENTE — requiere validación con CFOs

## Qué es

Plataforma de automation risk scoring por nómina. Upload nómina → sistema predice qué roles tienen riesgo de automatización en 12/24/36 meses, cuánto ahorra la empresa, qué reskilling necesita. Cruza BPS (cotizantes mensuales N=1.2M) + INE ECH microdatos (desde 1968) + MTSS + job boards scraping + OECD AI Exposure Index + ILO GenAI Index. Predicción defensible de impacto IA en fuerza laboral.

## Problema que resuelve

CFO se pregunta "¿cuántos empleados pierdo si automatizo?" hoy no tiene respuesta. Un sistema que analiza su nómina, compara con ocupaciones en OECD AI Exposure, y predice riesgo por rol en 48 horas convierte incertidumbre en planning. Puede presupuestar reskilling, justificar decisiones, y comunicar transparencia a empleados.

## Modelos ML defensibles

1. **Automation Risk Scoring** (Logistic Regression + OECD features): predice riesgo automatización por rol. Accuracy 78-85%.
2. **Employment Forecast** (ARIMA/Prophet): predice crecimiento/caída de empleo por sector 6/12 meses. RMSE 0.3pp.
3. **Wage Impact Prediction** (Regression): predice impacto en salarios si ocupación se automatiza. R² 0.58.
4. **Reskilling Recommendation** (Classification): sugiere ocupaciones alternativas por perfil.

## Fuentes de datos

### Uruguay
- INE ECH microdatos: desde 1968, trimestral, 10K+ encuestas. Ocupaciones, salarios, educación
- BPS cotizantes mensuales: N=1.2M, estado laboral, actividad
- MTSS: datos laborales, convenios, normativa
- Job boards scraping: LinkedIn, BumeranJob, Zonajobs (demanda de ocupaciones)
- Google Trends: búsquedas "capacitación", "reskilling" por sector

### Internacionales
- OECD AI Exposure Index: 41 actividades, exposición por país
- ILO GenAI Index: probabilidad automatización por ocupación
- WEF Future of Jobs: encuestas de 800+ empresas globales
- BLS Occupational Projections: proyecciones empleo USA (benchmark)
- LinkedIn Economic Graph: demanda ocupacional global
- O*NET: descripción de tareas ocupacionales (41 dimensiones)

## Acceso a datos compartidos (via FDW)

```sql
SELECT * FROM shared.entity WHERE ...;
```

## Stack técnico

- Backend: FastAPI (Python)
- Frontend: Next.js 15 + Tailwind
- DB: Postgres 16 (puerto 5457)
- ML: scikit-learn + statsmodels (ARIMA) + Prophet + PyTorch NN
- Data: pandas + polars para grandes nóminas
- Storage: S3-compatible
- Visualization: Plotly + D3.js

## Reglas de boundary

1. Repo, base de datos, storage y colas propios.
2. No leer ni escribir directo en la base de otra vertical.
3. Compartir datos solo por FDW read-only desde shared-db.
4. Reusar patrones del núcleo reusable (source discovery, document extraction, identity resolution, alerts/tasks).

## Reglas para agentes

1. **No escribir en shared-db** — solo leer vía FDW
2. **BPS + OECD AI Exposure es fuente de verdad** para riesgo ocupacional
3. **Evidence-first**: cada predicción explica qué features triggearon el riesgo
4. **Deterministic-first**: usar modelo estadístico robusto antes que DL
5. **No afirmar despido sin evidencia de tendencia de ocupación**

## Variables de entorno

```
ASHRISE_BASE_URL=http://localhost:8080
ASHRISE_TOKEN=<token>
ASHRISE_PROJECT_ID=laboral
OECD_API_KEY=<key>
```

## Documentación del producto

- **[docs/Producto.md](docs/Producto.md)** — Documento completo del producto: visión, ICP, propuesta de valor, fuentes de datos, modelos ML, competencia, arquitectura, roadmap y métricas. Se actualiza cuando una investigación impacta esta vertical.
- **[docs/Investigaciones.md](docs/Investigaciones.md)** — Log cronológico de investigaciones procesadas que impactan esta vertical: si fortalecen o debilitan la tesis, y qué se actualizó en Producto.md como consecuencia.
- **[docs/ROADMAP.md](docs/ROADMAP.md)** — Milestones técnicos de implementación.

## Contrato AshRise

Al iniciar sesión: leer AGENTS.md → docs/ROADMAP.md → GET /state/laboral → GET /handoffs/laboral?status=open
Al cerrar: emitir ashrise-close con run + state_update.
