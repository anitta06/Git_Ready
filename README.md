# GitReady

An AI-powered GitHub profile analyzer that evaluates a developer's public repositories against live job market requirements and generates a personalized 7-day improvement plan.

## What it does
- Fetches public GitHub repositories and cleans unstructured READMEs into structured tech stacks using an LLM
- Builds a role-specific skill taxonomy from live Adzuna job postings using embeddings and KMeans clustering
- Scores profiles on skill match and repository quality using semantic similarity and structural checks
- Generates a personalized 7-day action plan via Groq LLM
- Caches results in Supabase with lightweight `pushed_at` validation to avoid redundant API calls

## Tech Stack
`FastAPI` `Streamlit` `Groq API` `sentence-transformers` `FAISS` `scikit-learn` `Supabase` `Adzuna API` `Railway` `Streamlit Cloud`

## Architecture
```
GitHub API → LLM cleaning → skill matching (FAISS) → gap analysis → action plan (LLM) → FastAPI → Streamlit → Supabase
```

## Team

| Member | Area | Key Work |
|---|---|---|
| **Anitta Davis Mundassery** | Backend & AI Pipeline | FastAPI `/analyze` endpoint, GitHub data fetching, LLM-based repo cleaning via Groq, Supabase caching, integration lead, tests |
| **Sarah Susan George** | AI/ML Core | Semantic skill matching with sentence-transformers + FAISS, gap analysis, action plan generation |
| **Lyandra Jijo** | Frontend | Streamlit dashboard, charts with Altair, backend integration, repository insights |
| **Ashley P** | Data Pipeline & Analytics | Adzuna job fetcher, skill taxonomy with embeddings + KMeans, analytics logging, Supabase RLS |

## Demo
[Watch Demo](https://drive.google.com/file/d/1_bHjAQMCqi8H_7kqPbJoD1LfNBJFEycK/view?usp=sharing) · [GitHub](https://github.com/Ashley-Shine/Git_Ready)

## Setup

```bash
git clone https://github.com/Ashley-Shine/Git_Ready.git
cd Git_Ready
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

Create a .env file in the root with your own keys:

ADZUNA_APP_ID=your_adzuna_id
ADZUNA_APP_KEY=your_adzuna_key
GITHUB_TOKEN=your_github_token
GROQ_API_KEY=your_groq_api_key
SUPABASE_URL=https://your-project-id.supabase.co
SUPABASE_KEY=your_supabase_key

```bash
uvicorn backend.main:app --reload   # backend
streamlit run frontend/app.py       # frontend
```
