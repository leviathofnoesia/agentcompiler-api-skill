---
name: agentcompiler-api
description: Operate, integrate, and troubleshoot the AgentCompiler API for compiling framework docs into AGENTS.md indexes, including auth, pricing flows, and production-safe usage patterns.
---

# AgentCompiler API Skill

## Use This Skill When
- You need to integrate with the AgentCompiler API.
- You need to register users, verify API keys, or manage account usage.
- You need to compile or scan framework dependencies from `packageJson` input.
- You need to debug checkout, webhook, or subscription behavior.

## Core Workflow
1. Register or obtain an API key.
2. Call compile or scan endpoints with JSON payloads.
3. Handle `402 Payment Required` when using anonymous requests.
4. Inspect account and analytics endpoints for usage/rate limits.

## Quick Commands
```bash
# Register free key
curl -X POST "$BASE_URL/api/v1/auth/register" \
  -H "Content-Type: application/json" \
  -d '{"email":"you@example.com"}'

# Compile docs
curl -X POST "$BASE_URL/api/v1/compile" \
  -H "Content-Type: application/json" \
  -H "x-api-key: $API_KEY" \
  -d '{"packageJson":"{\"dependencies\":{\"next\":\"latest\"}}"}'

# Scan only
curl -X POST "$BASE_URL/api/v1/compile/scan" \
  -H "Content-Type: application/json" \
  -H "x-api-key: $API_KEY" \
  -d '{"packageJson":"{\"dependencies\":{\"react\":\"latest\"}}"}'
```

## Important Constraints
- `packageJson` body fields are size-limited for abuse protection.
- API keys are hashed at rest; full key is shown only at creation/regeneration.
- Production deployments should include Redis and strong admin secrets.
- Webhooks require HTTPS endpoints and block private/internal destinations.

## Primary Endpoints
- `GET /health`
- `POST /api/v1/auth/register`
- `POST /api/v1/auth/verify`
- `POST /api/v1/compile`
- `POST /api/v1/compile/scan`
- `GET /api/v1/account`
- `GET /api/v1/analytics/usage`
- `POST /api/v1/polar/checkout`
- `POST /api/v1/webhook/polar`

## Troubleshooting Checklist
- 401: Validate `x-api-key` and environment.
- 402: Provide payment or authenticated key.
- 429: Check plan limits and account usage.
- 5xx on checkout/webhooks: verify Polar env vars and webhook secret.
