# HOW_TO_RUN

This file is the one-stop guide for local development.

## Prerequisites

- Node.js 18+
- npm 9+
- Python 3.10+
- Gemini API key: https://aistudio.google.com/app/apikey

## SETUP

### 1) Clone and install dependencies

```bash
git clone https://github.com/Jay-Jay-Tee/unveil.git
cd unveil

npm install
python -m pip install -r docs/requirements.txt
```

### 2) Create environment file

```bash
cp .env.example .env
```

Update `.env` with at least your Gemini keys:

```env
VITE_GEMINI_API_KEY=your_gemini_api_key_here
GEMINI_API_KEY=your_gemini_api_key_here
```

### 3) Choose auth mode

#### Local dev mode (no Firebase required)

```env
VITE_REQUIRE_AUTH_FOR_ANALYSIS=false
AUTH_REQUIRED=false
```

#### Firebase protected mode (production-like)

```env
VITE_REQUIRE_AUTH_FOR_ANALYSIS=true
AUTH_REQUIRED=true

VITE_FIREBASE_API_KEY=...
VITE_FIREBASE_AUTH_DOMAIN=...
VITE_FIREBASE_PROJECT_ID=...
VITE_FIREBASE_STORAGE_BUCKET=...
VITE_FIREBASE_MESSAGING_SENDER_ID=...
VITE_FIREBASE_APP_ID=...

FIREBASE_SERVICE_ACCOUNT_PATH=/absolute/path/to/service-account.json
```

## STARTUP

Use one of the startup scripts from the `setup/` folder. They start frontend and backend together.

### Windows CMD

```bat
setup\start.bat
```

### Windows PowerShell

```powershell
.\setup\start.ps1
```

If scripts are blocked:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
.\setup\start.ps1
```

### macOS / Linux

```bash
chmod +x setup/start.sh
./setup/start.sh
```

### Manual startup (any OS)

```bash
# Terminal 1
npm run frontend

# Terminal 2
npm run backend
```

## Verify everything is running

- Frontend: http://localhost:5173
- Backend: http://localhost:8001
- Health check: http://localhost:8001/health

## First run walkthrough

1. Open Upload page.
2. If prompted, choose account flow:
  - Sign in / Create account
  - Or continue as guest
3. Upload dataset (try `data/adult.csv` from the repo).
4. Optionally upload model (`models/adult_demo_model.pkl`) for model audit.
5. Run audit and open Dataset Audit / Report.

## Save behavior

- Signed-in user: audits auto-save to dashboard.
- Guest user: can run audits, but history is not saved between sessions.

## Troubleshooting

### Backend import/dependency error

```bash
python -m pip install -r docs/requirements.txt
```

If using a venv, ensure the script uses that environment.

### Port already in use

- Frontend default: 5173
- Backend default: 8001

Stop conflicting processes or change the port in scripts/config.

### Firebase sign-in prompt when testing locally

Set these in `.env`:

```env
VITE_REQUIRE_AUTH_FOR_ANALYSIS=false
AUTH_REQUIRED=false
```

### Gemini rate limiting

- Wait and retry.
- Avoid running many audits at the exact same time on the free tier.

## Optional deploy notes

- Frontend can be deployed with Firebase Hosting.
- Backend can be deployed to Cloud Run.
- For a shared team backend, point all frontends to the same `VITE_API_URL`.
