# Reliability Checklist - FIT4110 Lab 03

## 1. Functional tests

- [x] Co test cho endpoint health.
- [x] Co test happy path cho endpoint chinh.
- [x] Co kiem tra status code 2xx.
- [x] Co kiem tra field quan trong trong response.
- [x] Co it nhat 1 test doc du lieu danh sach hoac chi tiet.

## 2. Auth tests

- [x] Co test thieu token.
- [ ] Co test sai token hoac token rong. Mock server chua validate token that; se bo sung voi service local.
- [x] Endpoint public duoc khai bao ro neu khong can auth (`/health`, `/events`).
- [x] Test the hien dung expected status 401/403.

## 3. Negative tests

- [x] Co test thieu field bat buoc.
- [ ] Co test sai kieu du lieu. Se bo sung khi local service validate day du.
- [x] Co test sai enum hoac gia tri ngoai mien.
- [x] Loi tra ve theo cung mot error model Problem.

## 4. Boundary tests

- [x] Co test min/max hoac du lieu sat nguong.
- [x] Co test limit/pagination neu endpoint co danh sach.
- [ ] Co test payload lon hoac metadata thieu. Se bo sung cho local service.
- [x] Co ghi chu ky vong xu ly du lieu bien.

## 5. Reliability tests co ban

- [x] Co kiem tra response time.
- [x] Co mo ta timeout mong muon: Access Gate timeout 500ms voi `/access/check`, fail-closed.
- [x] Co test hoac ghi chu retry/idempotency: `idempotencyKey` Pair 10, `eventId` Pair 9.
- [x] Co consumer-side smoke test voi mock cua nhom khac.

## 6. Evidence

- [x] Collection export JSON.
- [x] Environment mock export JSON.
- [x] Environment local export JSON.
- [x] Newman report XML/HTML.
- [x] Test-case matrix da dien.
- [x] Bien ban handshake da dien.
