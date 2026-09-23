# CivicSense AI

**Smarter Complaint Analysis for Better Governance.**

An AI-powered civic complaint platform: citizens submit complaints, AI automatically
classifies/prioritizes/routes them, citizens track resolution transparently by
Complaint ID, and authorized admins manage everything from a login-protected dashboard.

## Tech Stack (exactly as specified)

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | FastAPI (Python) |
| Database | SQLite |
| AI | DistilBERT (sentiment), Sentence-Transformers (semantic classification + duplicate detection), Hugging Face pipeline |
| Visualization | Chart.js (pie / bar / line) |
| Map | Leaflet.js |

## Folder Structure

```
CivicSenseAI/
├── frontend/
│   ├── index.html          # Landing page
│   ├── complaint.html      # Citizen complaint submission form
│   ├── tracking.html       # Citizen complaint tracking (Complaint ID)
│   ├── admin.html          # Admin login + dashboard (charts + map + table)
│   ├── style.css
│   └── app.js
├── backend/
│   ├── main.py              # FastAPI app entry point
│   ├── database.py          # SQLite connection + schema
│   ├── models.py            # Pydantic request/response models
│   ├── auth.py               # Admin login (user id: admin / password: 123)
│   └── routes.py             # All API endpoints
├── AI/
│   ├── config.py             # USE_ML_MODELS toggle
│   ├── classifier.py         # Category classification + department + priority
│   ├── sentiment.py          # DistilBERT sentiment pipeline
│   └── duplicate.py          # Sentence-Transformers duplicate detection
├── database/                 # complaints.db is created here automatically
├── uploads/                  # uploaded complaint photos are stored here
├── requirements.txt
└── README.md
```

## How to Run (VS Code)

1. **Open the folder** `CivicSenseAI` in VS Code.

2. **Create a virtual environment** (recommended) and activate it:
   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS / Linux
   source venv/bin/activate
   ```

3. **Install dependencies** (from the project root, where `requirements.txt` lives):
   ```bash
   pip install -r requirements.txt
   ```
   > First install downloads PyTorch + Transformers + Sentence-Transformers.
   > This can take a few minutes and needs an internet connection.

4. **Run the server** (from the project root):
   ```bash
   uvicorn backend.main:app --reload
   ```

5. **Open your browser** at: **http://127.0.0.1:8000**

   - `/` → Landing page
   - `/complaint.html` → Submit a complaint (get your Complaint ID)
   - `/tracking.html` → Track a complaint by ID
   - `/admin.html` → Admin login

## Admin Login

```
User ID:  admin
Password: 123
```

Only after logging in can the dashboard (all complaints, charts, map, status
updates) be viewed - this is enforced both in the UI and on the backend
(every `/api/admin/*` route requires a valid session token).

## Complaint Tracking (transparency)

The moment a citizen submits a complaint, the backend instantly:
1. Runs AI classification (category), sentiment analysis, priority scoring, and
   duplicate detection.
2. Generates a unique **Complaint ID** (e.g. `CMP-20260731-A1B2C3`).
3. Returns it to the citizen immediately.

The citizen can then go to `/tracking.html`, enter that ID, and see a live
timeline: **Pending → Assigned → Resolved**, plus the department it was routed
to, priority, and any officer remarks - so they can transparently see whether
their complaint has been seen and acted upon.

## About the AI Layer / Offline Demo Mode

Real Hugging Face models (`distilbert-base-uncased-finetuned-sst-2-english`
for sentiment, `all-MiniLM-L6-v2` from Sentence-Transformers for semantic
classification + duplicate detection) are downloaded automatically the first
time you run the app, provided you have internet access.

If you're demoing on flaky wifi, or want instant startup, open
`AI/config.py` and set:

```python
USE_ML_MODELS = False
```

The app will instantly switch to fast, fully offline keyword/lexicon-based
logic for classification, sentiment, and duplicate detection - the API
contract and all frontend behavior stay identical either way, and every ML
module has an automatic fallback even when `USE_ML_MODELS = True`, in case a
model download fails mid-demo.

## Database Schema (`complaints` table, SQLite)

```
id, complaint_id, name, phone, location, complaint, category, sentiment,
priority, department, status, latitude, longitude, image_path, remarks,
duplicate_of, created_at, updated_at
```

## Notes

- No hashed passwords / JWT - this is intentionally a simple in-memory
  bearer-token admin session, appropriate for a 36-hour hackathon build.
  Swap in proper auth before any real deployment.
- Uploaded complaint photos are stored under `/uploads` and served statically.
- CORS is open (`*`) for ease of local development.
