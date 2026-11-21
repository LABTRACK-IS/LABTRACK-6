# Release Manifest - LabTrack v6.0.0

**Release ID:** `202611211937`
**Release date:** 2026-11-21
**Baseline:** labtrack 5
**Classification:** Production Release

---

## Executive summary

LabTrack v6.0.0 has been built, packaged, and is ready for deployment.
This manifest provides release metadata, component inventory, and deployment instructions for operations and QA.

## Release contents

| Component              | Count     |
|------------------------|-----------|
| Controllers            | 29         |
| Application services   | 17         |
| Domain entities        | 32         |
| Repositories           | 17         |
| EF Core migrations     | 10         |
| Admin UI modules       | 18         |
| Instructor UI modules  | 11         |
| Python FastAPI routes  | 7         |
| Total C# files         | 459       |
| Total TS/TSX files     | 73        |

## What is new in v6.0.0

Compared to labtrack 5:

- Backend changes: 0 modified, 0 added
- Frontend changes: 25 modified, 1 added

## Component inventory

### Controllers

- AiAssistant
- Analytics
- Asset
- Audit
- Auth
- ChainOfCustody
- Communication
- Financial
- IdempotencyRecords
- InstructorCommunication
- Laboratories
- Maintenance
- MaintenanceRecord
- MaintenanceRecords
- Network
- NetworkIncident
- NetworkInfo
- Notification
- PcUsage
- ProblemReport
- Qr
- QrAdmin
- QrSession
- RepairTicket
- Replacement
- ReplacementRecord
- Reservation
- Users
- Workstations

### Application services

- AiAssistant
- Analytics
- Asset
- Audit
- Auth
- Communication
- Financial
- Maintenance
- Network
- Notification
- PcUsage
- ProblemReport
- Qr
- RepairTicket
- Replacement
- Reservation
- User

### Domain entities

- AiChatMessage
- AiChatSession
- Asset
- AuditLog
- AuthSession
- ChainOfCustodyEvent
- Communication
- ComponentReplacement
- DamageAttribution
- FinancialExpense
- FinancialRecord
- IdempotencyKey
- InstructorCommunication
- Laboratory
- MaintenanceRecord
- MaintenanceSchedule
- NetworkDevice
- NetworkIncident
- Notification
- PcTelemetryEvent
- PcUsageLog
- ProblemReport
- QrCode
- QrSession
- RefreshToken
- RepairTicket
- ReplacementRecord
- ReplacementRequest
- Reservation
- User
- Workstation
- WorkstationSession

## System requirements

| Requirement   | Minimum           |
|---------------|-------------------|
| .NET runtime  | 8.0               |
| Node.js       | 18.x or higher    |
| PostgreSQL    | 14.x or higher    |
| Python        | 3.10 or higher    |
| RAM           | 4 GB              |
| Disk          | 2 GB free         |

## Deployment

### 1. Backend API

    cd backend/LabTrack.CSharp/src/LabTrack.Api
    dotnet restore
    dotnet build -c Release
    dotnet run

### 2. Frontend SPA

    cd frontend
    npm ci
    npm run build
    npm run dev

### 3. Python AI service (optional)

    cd backend/LabTrack.Python
    pip install -r requirements.txt
    uvicorn app.main:app --host 0.0.0.0 --port 8000

## Service endpoints

| Service   | URL                              |
|-----------|----------------------------------|
| SPA       | http://localhost:3000            |
| API       | http://localhost:5000            |
| Swagger   | http://localhost:5000/swagger    |
| Health    | http://localhost:5000/health/live|
| AI        | http://localhost:8000            |

## Support

- Organization: LABTRACK-IS
- Repository: LABTRACK-6
- Issue tracker: GitHub Issues

---

Manifest issued 2026-11-21 19:37:24 (c) 2026 LABTRACK-IS
