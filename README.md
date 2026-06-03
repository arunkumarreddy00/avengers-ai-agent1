# Aegis AI — Universal Multi-Agent Website Builder

A cinematic AI command-center application where specialized agents collaborate to generate small, downloadable websites from a natural-language request.

The user describes a website, selects individual agents or assembles the complete team, and downloads a ZIP containing working HTML, CSS, and JavaScript files. The generated website can be opened locally by double-clicking `index.html`.

## Highlights

- Cinematic command-center intro with reactor, HUD, particles, and synthetic voice narration
- Eight original AI agents with different responsibilities
- Gemini-powered multi-agent mission reports
- Universal website builder that infers the requested website type automatically
- Downloadable ZIP output containing `index.html`, `styles.css`, and `script.js`
- Offline fallback mode when an API key is not configured
- Automatic retry and fallback model support for temporary Gemini `503 UNAVAILABLE` errors
- Responsive React and TypeScript frontend
- FastAPI backend with safe path validation for generated files

## AI Agent Team

| Agent | Responsibility |
| --- | --- |
| Striker | Mission coordination and final report |
| Thunder | Research and audience insights |
| Titan | Difficult-task breakdown and problem solving |
| Sentinel | Planning and execution roadmap |
| Shadow | Security and privacy checks |
| WebForge | Frontend, backend, debugging, and testing guidance |
| Oracle | Alternative approaches and trade-off analysis |
| Nova | Branding, UI direction, and content ideas |

## Tech Stack

**Frontend:** React, TypeScript, Vite, CSS  
**Backend:** Python, FastAPI, Pydantic, Uvicorn  
**AI provider:** Google Gemini API through the Google Gen AI SDK

## Project Structure

```text
aegis-ai-universal-website-builder/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   └── main.py
│   ├── .env.example
│   └── requirements.txt
├── frontend/
│   ├── public/
│   │   ├── audio/voices/
│   │   └── images/agents/
│   ├── src/
│   │   ├── App.tsx
│   │   ├── data.ts
│   │   ├── main.tsx
│   │   ├── styles.css
│   │   └── types.ts
│   ├── .env.example
│   ├── package.json
│   └── vite.config.ts
├── .gitignore
├── LICENSE
├── start-backend.bat
└── start-frontend.bat
```

## Setup

### 1. Clone the repository

```bash
git clone YOUR_REPOSITORY_URL
cd aegis-ai-universal-website-builder
```

### 2. Configure the backend

```bash
cd backend
python -m venv venv
```

Windows PowerShell:

```powershell
venv\Scripts\Activate.ps1
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Copy the environment template:

```powershell
Copy-Item .env.example .env
```

Open `backend/.env` and add your own Gemini API key:

```env
GEMINI_API_KEY=PASTE_YOUR_PRIVATE_KEY_HERE
GEMINI_MODEL=gemini-2.5-flash
GEMINI_FALLBACK_MODEL=gemini-2.5-flash-lite
GEMINI_RETRY_ATTEMPTS=3
```

Never commit `backend/.env` to GitHub.

Start the backend:

```bash
uvicorn app.main:app --reload --port 8000
```

Health check:

```text
http://127.0.0.1:8000/api/health
```

### 3. Configure the frontend

Open a second terminal:

```bash
cd frontend
npm install
npm run dev
```

Open:

```text
http://localhost:5173
```

## How to Use

1. Enter a website request, such as:

```text
Create a modern portfolio website for a B.Tech AIML student with Home, About, Skills, Projects, and Contact sections. Use a dark blue theme.
```

2. Click **ASSEMBLE AGENTS**.
3. Click **CREATE WEBSITE ZIP**.
4. Download the generated ZIP.
5. Extract the ZIP and open `index.html`.

The same builder can generate small portfolio, restaurant, event, college-project, business, product-showcase, and clothing-store demo websites.

## Main API Endpoints

| Method | Endpoint | Purpose |
| --- | --- | --- |
| `GET` | `/api/health` | Check backend mode and model configuration |
| `GET` | `/api/agents` | List agent metadata |
| `POST` | `/api/missions` | Create a mission |
| `POST` | `/api/missions/{mission_id}/execute` | Run selected agents |
| `POST` | `/api/websites/build` | Generate a downloadable static website ZIP |
| `GET` | `/api/websites/{build_id}/download` | Download the generated ZIP |

## Environment Variables

| Variable | Description |
| --- | --- |
| `GEMINI_API_KEY` | Private Gemini API key |
| `GEMINI_MODEL` | Primary Gemini model |
| `GEMINI_FALLBACK_MODEL` | Fallback model for temporary high-demand errors |
| `GEMINI_RETRY_ATTEMPTS` | Retry count for temporary capacity errors |
| `VITE_API_BASE_URL` | Optional frontend API base URL |

## Security Notes

- Keep API keys only in `backend/.env`.
- Do not add secrets to frontend code.
- Generated filenames are validated before ZIP creation.
- Generated static websites do not require a backend, database, npm, or private API keys.
- Use the generated output as a starting point and review it before production deployment.

## Portfolio Notes

This public version uses original agent names and does not include third-party movie images, audio clips, logos, or actor voices. Add only assets that you created yourself or are licensed to use.

## Future Improvements

- React website generation mode
- Streaming agent responses
- User authentication
- Persistent mission history
- Database-backed generated project storage
- Preview window for generated websites
- Deployment button for static hosting

## Author

**Seelam Arunkumarreddy**  
B.Tech AIML Student
