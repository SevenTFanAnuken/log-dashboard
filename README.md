# SOC Log Analysis Dashboard

A full-stack security operations dashboard for analyzing Apache, SSH, and Windows Event logs. Detects attack patterns, visualizes activity, and exports results — built to demonstrate SOC analyst skills.

**Live demo:** https://log-dashboard-1.onrender.com/

> The backend runs on Render's free tier and may take **up to 1 minute to load** on first visit. Once it wakes up, everything runs instantly.

---

## Features

- **Log parsing** — Apache Combined, Linux SSH auth.log, Windows Event Log (CSV)
- **Anomaly detection** — brute force attacks, 404 scanning spikes, off-hours logins
- **Visualizations** — event timeline, top source IPs, HTTP status codes, auth timeline
- **Search & filter** — paginated raw log table with live search
- **Export** — download results as CSV or JSON
- **Sample files** — load demo logs directly from the UI, no upload needed

## Anomaly Detection Rules

| Rule | Trigger | Severity |
|------|---------|----------|
| Brute Force | ≥5 failed auth from same IP within 10 min | High / Critical |
| 404 Spike | ≥10 HTTP 404s within 5 min | Medium / High |
| Off-hours Login | Successful login outside 06:00–22:00 | Medium / High |

## Stack

- **Frontend:** React 18 + Vite + Tailwind CSS + Recharts
- **Backend:** Node.js + Express
- **Deployment:** Render (free tier)

## Running Locally

**Backend**
```bash
cd server
npm install
npm run dev
# http://localhost:3001
```

**Frontend**
```bash
cd client
npm install
npm run dev
# http://localhost:5173
```

Upload a file from `samples/` or use the sample buttons in the UI.

## Sample Files

| File | Triggers |
|------|---------|
| `samples/apache_access.log` | 404 spike, off-hours access |
| `samples/auth.log` | SSH brute force, off-hours login |
| `samples/windows_events.csv` | Windows brute force, off-hours login |
