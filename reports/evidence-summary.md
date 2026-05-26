# Lab 03 Evidence Summary - Access Gate

## Evidence files

- Contract lint report: `reports/contract-lint-report.txt`
- Contract lint CLI log: `reports/contract-lint-cli-log.txt`
- Newman XML report: `reports/newman-report-mock.xml`
- Newman HTML report: `reports/newman-report.html`
- Newman CLI log: `reports/newman-cli-log.txt`

## Latest Newman result

- Collection: `postman/collections/access-gate.postman_collection.json`
- Environment: `postman/environments/access-gate_mock.postman_environment.json`
- Requests executed: 12
- Assertions: 33
- Failed: 0

## Covered test groups

- `01_Functional`
- `02_Auth`
- `03_Negative`
- `04_Boundary_Reliability`
- `05_Consumer_side_Smoke`
- `06_Local_only_NonFunctional`

## Key endpoints tested

- `GET /health`
- `GET /access/logs/recent`
- `GET /gates/{gateId}/status`
- `POST /access/check`
- `POST /events`

## Notes

- Mock environment passes.
- Local environment file exists; local service implementation is marked as local-only/placeholder until real service is available.
- Optional terminal screenshot can be added manually as `reports/newman-terminal-screenshot.png`.
