# HR → Payroll Integration Demo (Azure + SQL + APIs)

A portfolio project that simulates an enterprise integration pipeline:
- Ingest employee data (JSON/CSV) from an HR source
- Validate + transform it
- Load into Azure SQL (raw + curated tables)
- Sync to a mock Payroll API
- Produce logs + runbook for troubleshooting

## Tech
- Azure Functions (Python or C#)
- Azure SQL (or local SQL Server for dev)
- Azure Data Factory (optional phase)
- Power Automate (optional phase)
- GitHub Actions (CI)

## Architecture (high-level)
1. HR source file/API → staging storage
2. Pipeline loads to `raw.Employee`
3. Function validates/transforms → `curated.Employee`
4. Function sends record to mock Payroll API
5. Log results to `dbo.IntegrationLog`

## Getting Started
### Prereqs
- Python 3.11+ OR .NET 8
- Azure Functions Core Tools (optional for local)
- SQL Server/Azure SQL
- Git

### Local Setup
1. Create tables: `sql/schema.sql`
2. Load sample data: `sql/seed.sql`
3. Run function locally (see `docs/runbook.md`)

## Project Phases
- Phase 1: SQL schema + sample data + basic queries
- Phase 2: Function that reads employees and posts to mock API
- Phase 3: Logging, retry, dead-letter handling
- Phase 4: ADF pipeline export + monitoring
- Phase 5: Power Automate notifications

## Notes
See `docs/troubleshooting.md` for common failures and fixes.
``
