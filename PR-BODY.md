# Release Sign-off - LabTrack v6.0.0

**Release ID:** 202611211937
**Prepared:** 2026-11-21
**Baseline:** labtrack 5

---

## Approval request

This PR requests **release authorization** for LabTrack v6.0.0.
Sign-off is required from QA Lead, Backend Lead, and Frontend Lead before merge to main.

## Release scope

| Item                    | Count     |
|-------------------------|-----------|
| Controllers shipped     | 29         |
| Services shipped        | 17         |
| Entities shipped        | 32         |
| Repositories shipped    | 17         |
| Migrations shipped      | 10         |
| Admin UI views          | 18         |
| Instructor UI views     | 11         |
| Python routes           | 7         |

## Delta from labtrack 5

| Layer    | Touched | Introduced |
|----------|---------|------------|
| Backend  | 0       | 0          |
| Frontend | 25       | 1          |

## Sign-off criteria

Each approver must confirm the items below before signing off.

### QA Lead sign-off

- [ ] Full regression suite executed
- [ ] All controllers verified against Swagger spec
- [ ] Frontend smoke test passed on Chrome, Firefox, Safari
- [ ] No P0 or P1 defects open
- [ ] Sign-off: __________ (QA Lead) Date: __________

### Backend Lead sign-off

- [ ] `dotnet build -c Release` succeeded with 0 warnings
- [ ] All 10 EF migrations applied cleanly
- [ ] API endpoints respond within SLA
- [ ] No hardcoded secrets in source
- [ ] Sign-off: __________ (Backend Lead) Date: __________

### Frontend Lead sign-off

- [ ] `npm run build` produces clean bundle
- [ ] `npx tsc --noEmit` reports 0 errors
- [ ] All 18 admin views render
- [ ] All 11 instructor views render
- [ ] Sign-off: __________ (Frontend Lead) Date: __________

### Operations sign-off

- [ ] Database backup verified restorable
- [ ] Rollback plan tested
- [ ] Monitoring alerts configured
- [ ] Sign-off: __________ (Ops) Date: __________

## Go / No-go decision

| Decision  | Authorized by          | Date           |
|-----------|------------------------|----------------|
| GO        | ____________________   | __________     |
| NO-GO     | ____________________   | __________     |

## Release artifacts

- Full source: this repository
- Release manifest: README.md
- Migration guide: CHANGELOG-V6.md
- Sign-off record: this document

## Post-release follow-up

Within 24 hours of release:

1. Monitor error rate and latency dashboards
2. Collect early user feedback
3. Document any issues in GitHub Issues with label "release-v6"
4. Update status page if applicable

---

Sign-off document prepared 2026-11-21 19:37:24
Awaiting approval from release board.
