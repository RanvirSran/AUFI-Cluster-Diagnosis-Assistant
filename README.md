# AUFI Diagnosis Assistant

Interactive, multi-turn diagnosis support for acute undifferentiated febrile illness (AUFI).
A symbolic scoring layer narrows candidate conditions by asking discriminating follow-up
questions; a RAG layer then pulls guideline text for the shortlisted condition(s).

## Layout

```
backend/    Python: scoring layer, RAG layer, dialogue loop, CLI, FastAPI app
frontend/   React + TypeScript (Vite) UI
data/       symptom_table/ (scoring CSV), guidelines/ (RAG source docs)
eval/       Held-out synthetic vignettes + metrics script
docs/       Plan and evaluation justification
```

**Keep `data/symptom_table/` and `data/guidelines/` separate.** The synthetic symptom table
must never be embedded into the vector store that RAG retrieves from.

## Setup

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows  (source .venv/bin/activate on Linux/macOS)
pip install -r requirements.txt
```

## Run

CLI (from repo root):

```bash
python -m backend.cli
```

API (from repo root):

```bash
uvicorn backend.main:app --reload
```

Frontend:

```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```
