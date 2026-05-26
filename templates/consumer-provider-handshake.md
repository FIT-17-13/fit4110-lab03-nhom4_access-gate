# Consumer-Provider Handshake

## Thong tin chung

- Lab: FIT4110 Lab 03
- Ngay: 2026-05-26
- Provider team: A6 Core Business / A5 Analytics mock dependencies
- Consumer team: A3 Access Gate
- Provider service: Core Business policy API, Analytics event ingestion API
- Consumer service: Access Gate

## Contract

- Contract file: `contracts/access-gate.openapi.yaml`
- Mock base URL: `http://localhost:4010`
- Auth method: Bearer token for protected REST endpoints; `POST /events` mock is public for Lab 03.
- Endpoint duoc test:
  - `POST /access/check` for Pair 10 Core Business policy check.
  - `POST /events` for Pair 9 Analytics event ingestion.

## Smoke test 1 - Pair 10 Access Gate calls Core Business mock

### Request

```http
POST /access/check
Authorization: Bearer {{authToken}}
Content-Type: application/json
```

```json
{
  "cardId": "RFID-2026-001",
  "gateId": "gate-main-01",
  "direction": "IN",
  "timestamp": "2026-05-26T08:00:00Z",
  "idempotencyKey": "RFID-2026-001-gate-main-01-smoke",
  "operatorNote": "none"
}
```

### Expected response

```json
{
  "decisionId": "decision-001",
  "allow": true,
  "reasonCode": "ACCESS_ALLOWED",
  "policyId": "policy-001",
  "expiresAt": "2026-05-26T08:05:00Z",
  "operatorNote": "none"
}
```

## Smoke test 2 - Pair 9 Access Gate sends event to Analytics mock

### Request

```http
POST /events
Content-Type: application/json
```

```json
{
  "eventId": "evt-20260526-0001",
  "eventType": "access.logs.created",
  "eventVersion": "1.0.0",
  "occurredAt": "2026-05-26T08:00:00Z",
  "source": "access-gate",
  "correlationId": "corr-20260526-0001",
  "data": {
    "logId": "log-7788",
    "cardId": "RFID-2026-001",
    "gateId": "gate-main-01",
    "direction": "IN",
    "status": "ALLOWED"
  }
}
```

### Expected response

```json
{
  "accepted": true,
  "eventId": "evt-20260526-0001",
  "status": "accepted",
  "message": "Event accepted for analytics processing"
}
```

## Ket qua

- [x] Consumer goi mock thanh cong.
- [x] Consumer parse duoc field can dung.
- [x] Consumer hieu loi 4xx/5xx provider tra ve.
- [x] Co Newman report XML/HTML trong `reports/`.

## Ghi chu thay doi hop dong

| Noi dung | Truoc | Sau | Nguoi dong y |
|---|---|---|---|
| Pair 10 idempotency | Optional | Required `idempotencyKey` | Core Business, Access Gate |
| Pair 9 envelope | Payload flat | Event envelope with `eventId`, `eventType`, `data` | Analytics, Access Gate |
| Pair 9 mock | Queue only | `POST /events` returns `202 Accepted` | Analytics, Access Gate |

## Xac nhan

- Provider representative: Core Business / Analytics representative
- Consumer representative: A3 Access Gate representative
