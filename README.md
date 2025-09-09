# workplace-search-mcp
One-liner: FastAPI service exposing a small Workplace Search API (search, content, recent, summarize) designed to be wrapped by Cequence AI Gateway (MCP) with OAuth via Descope and Google Drive outbound.

## What’s included
- Minimal FastAPI app implementing the endpoints used by the MCP
- Descope JWT verification + scope enforcement
- Google Drive provider (uses google-api-python-client)
- Descope Outbound connector stub for fetching per-user Google tokens
- Simple summarizer (optional)
- Dockerfile + requirements

## Quickstart (local)
1. Create and activate a virtualenv:
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

2. Required env vars (export or place in `.env`):
```
DESCOPE_ISSUER=https://api.descope.com/<your-tenant-id>/v1
DESCOPE_JWKS=https://api.descope.com/<your-tenant-id>/v1/.well-known/jwks.json
DESCOPE_API_KEY=<your-server-api-key-for-descope>
DESCOPE_TENANT_ID=<your-descope-tenant-id>
GOOGLE_PROJECT_ID=<your-google-project-id>
```

3. Run locally
```bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```


