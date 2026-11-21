# Migration Guide - LabTrack v6.0.0

**From:** labtrack 5
**To:** LabTrack 6 (v6.0.0)
**Compiled:** 2026-11-21 19:37:24
**Estimated migration time:** 15-20 minutes

---

## Pre-migration checklist

- [ ] Backup current database
- [ ] Tag current deployment as rollback point
- [ ] Note current controller count: will compare after
- [ ] Confirm .NET 8 SDK installed
- [ ] Confirm Node 18+ installed

## What changes

### Backend movement

Total backend changes: **0**

No backend file changes detected. This is a stable re-release of labtrack 5 backend.

### Frontend movement

Total frontend changes: **26**

Modified files (25):

- frontend\src\components\admin\AiAssistantView.tsx
- frontend\src\components\admin\AnalyticsReportsView.tsx
- frontend\src\components\admin\AssetsWorkstationDeskView.tsx
- frontend\src\components\admin\AuditLogsView.tsx
- frontend\src\components\admin\CampusesLabsView.tsx
- frontend\src\components\admin\FinancialReportsView.tsx
- frontend\src\components\admin\InventoryTransferView.tsx
- frontend\src\components\admin\IssueServiceDeskView.tsx
- frontend\src\components\admin\MaintenanceView.tsx
- frontend\src\components\admin\NotificationsManagementView.tsx
- frontend\src\components\admin\OverviewView.tsx
- frontend\src\components\admin\ProfileSettingsView.tsx
- frontend\src\components\admin\QrManagementView.tsx
- frontend\src\components\admin\SessionsManagementView.tsx
- frontend\src\components\admin\UserAccessManagementView.tsx
- frontend\src\components\instructor\AiAssistantView.tsx
- frontend\src\components\instructor\LabAvailabilityView.tsx
- frontend\src\components\instructor\NotificationsView.tsx
- frontend\src\components\instructor\OverviewView.tsx
- frontend\src\components\instructor\ProfileView.tsx
- frontend\src\components\instructor\ReportProblemView.tsx
- frontend\src\components\instructor\ReservationsView.tsx
- frontend\src\components\instructor\StudentSessionsView.tsx
- frontend\src\components\instructor\UsageAnalyticsView.tsx
- frontend\src\components\portal\PortalShell.tsx

New files (1):

- frontend\src\components\portal\YouTubeNotificationBell.tsx

## Migration steps

### Step 1 - Pull source

    git clone https://github.com/LABTRACK-IS/LABTRACK-6.git
    cd LABTRACK-6

### Step 2 - Backend restore and build

    cd backend/LabTrack.CSharp/src/LabTrack.Api
    dotnet restore
    dotnet build -c Release

Expected output: Build succeeded with 0 errors.

### Step 3 - Database migrations

    dotnet ef database update --project ../LabTrack.Infrastructure

Migrations to apply: 10

### Step 4 - Frontend install and build

    cd frontend
    npm ci
    npm run build

Expected: production bundle generated in dist/

### Step 5 - Smoke test

Start backend, then verify:

- GET /health/live returns 200
- GET /swagger/v1/swagger.json loads with 29 controllers
- Frontend loads at http://localhost:3000

## Post-migration verification

| Check                          | Expected            |
|--------------------------------|---------------------|
| Controller count               | 29                   |
| Service count                  | 17                   |
| Entity count                   | 32                   |
| Migration count                | 10                   |
| Admin views                    | 18                   |
| Instructor views               | 11                   |
| Python routes                  | 7                    |

## Rollback plan

If migration fails:

1. Stop all services
2. `git checkout labtrack 5`
3. Restore database backup
4. `dotnet restore && dotnet build`
5. `npm ci && npm run dev`
6. Verify smoke test passes

Estimated rollback time: 10 minutes

## Known limitations

- This release assumes PostgreSQL is already provisioned
- Cloudflare tunnel configuration not included
- AI service requires API keys (see .env.example)

---

Migration guide generated 2026-11-21 19:37:24
