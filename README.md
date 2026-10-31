# IT Incident Hub

Aplicación web para registrar, asignar y dar seguimiento a incidentes de TI, construida como proyecto integrador DevOps (Azure Boards → Git → PR → CI → artefacto → release).

**Stack:** React + Vite · Node.js/Express · PostgreSQL · Docker · Azure Pipelines + GitHub Actions.

## Requisitos
Node 20+, Docker (para PostgreSQL) y Git.

## Instalación y ejecución
```bash
cp .env.example .env            # edite la contraseña
docker compose up -d db         # crea esquema y datos de ejemplo
cd backend && npm ci && DATABASE_URL=$(grep ^DATABASE_URL ../.env | cut -d= -f2-) npm run dev
cd frontend && npm ci && npm run dev    # http://localhost:5173
```
Pruebas: `cd backend && npm test` · Lint: `npm run lint`.

## API
`POST/GET /api/incidentes` · `GET /api/incidentes/:id` · `PATCH /:id/asignar` · `PATCH /:id/estado` · `POST /:id/comentarios` · `GET /api/tecnicos` · `GET /api/dashboard` · `GET /api/health`.
Estados: NUEVO → ASIGNADO → EN_PROCESO → RESUELTO → CERRADO.

## Estructura
`backend/` API · `frontend/` UI · `database/` SQL · `tests/` pruebas · `devops/` scripts y backlog · `docs/` documentación · `.github/workflows/` GitHub Actions · `azure-pipelines.yml`.

## Responsables (completar)
| Rol | Usuario | Responsabilidad |
|---|---|---|
| Dev 1 | dev.uno | Backend, base de datos |
| Dev 2 | dev.dos | Frontend, dashboard |
| Reviewer | reviewer | Code review, QA |
| DevOps | devops | Pipelines, agente, release |

## Documentación
Ver `docs/`: arquitectura, branching, deuda técnica, seguridad, dependencias, release, evidencias.
