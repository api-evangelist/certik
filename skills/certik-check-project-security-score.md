---
name: Check a project's Skynet security score
description: Look up CertiK's multi-metric Skynet security score for a blockchain project, either by browsing the ranked list or fetching one project by ID/contract address.
api: openapi/certik-skynet-openapi.yml
operations: [listSecurityScores, getSecurityScore]
---

# Check a project's Skynet security score

Use the CertiK Partner (Skynet) API to retrieve a project's security score.

## Prerequisites
- A CertiK Partner API key (request from the CertiK Business Team, APIsupport@certik.com).
- Base URL: `https://partner.certik-skynet.com`
- Send the key on every request in the `X-Certik-Api-Key` header.

## Steps

1. **Browse the ranked list.** Call `listSecurityScores` (`GET /v1/security-scores`) with `skip` and `limit` for pagination; set `partnerData=true` to include partner metadata. Read `items[]` and the `page` object.
2. **Fetch one project.** Call `getSecurityScore` (`GET /v1/security-scores/{id}`) where `id` is the CertiK Project ID or a chain-prefixed contract address.
3. **Interpret the result.** Read `securityScore.score`, `rank`, `tier`, and `rankPercentile`, plus `highlights[]` and `alerts[]`.

## Conventions & errors
- Pagination is offset-based (`skip`/`limit`); see `conventions/certik-conventions.yml`.
- On `403` the `X-Certik-Api-Key` header is invalid or missing; on `400` check parameters. See `errors/certik-problem-types.yml`.
