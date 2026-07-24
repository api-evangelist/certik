---
name: Scan a token contract for risk
description: Run CertiK's Token Scan on one or many token contracts to get on-chain risk analysis — token info, market/holder data, SkyKnight score, and a severity-ranked security summary.
api: openapi/certik-skynet-openapi.yml
operations: [queryTokenScan, queryTokenScanBatch]
---

# Scan a token contract for risk

Use the CertiK Partner (Skynet) Token Scan API to analyze token contract risk.

## Prerequisites
- A CertiK Partner API key sent in the `X-Certik-Api-Key` header.
- Base URL: `https://partner.certik-skynet.com`

## Steps

1. **Scan one contract.** Call `queryTokenScan` (`GET /v1/token-scan/contract/query`) for a single token contract.
2. **Scan in bulk.** Call `queryTokenScanBatch` (`GET /v1/token-scan/contract/query/batch`) to retrieve results for multiple contracts in one request.
3. **Interpret the response.** The `data` object carries `token_info`, `token_meta`, `market_info` (LP pairs, top holders, top LP holders), `skyknight_score` (0–100), and `security_summary` — a list of risk flags with severity (Critical/Major/Medium/Minor/Informational).

## Conventions & errors
- Response envelope is `{ code, message, data }`; see `conventions/certik-conventions.yml`.
- `403` means the API key header is invalid or missing; `400` means invalid parameters. See `errors/certik-problem-types.yml`.
