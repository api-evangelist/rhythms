---
name: Track OKR objectives and time periods
description: Read objectives and manage OKR time periods in Rhythms.
api: openapi/rhythms-openapi-original.json
operations: [get_okrs_time_periods, put_okrs_time_periods_id, delete_okrs_time_periods_id, get_okrs_objectives_show]
---

# Track OKR objectives and time periods

Base URL `https://api.rhythms.ai`; authentication required; tenant-scoped JSON.

## Steps

1. **List time periods** — `get_okrs_time_periods` to discover the OKR cycles in scope.
2. **Show an objective** — `get_okrs_objectives_show` to read a specific objective's detail.
3. **Update a time period** — `put_okrs_time_periods_id` with the time period `id`.
4. **Delete a time period** — `delete_okrs_time_periods_id` with the `id`.

## Rules

- Deletions are destructive and not idempotent — verify the `id` first.
- Handle `429`/`401`/`403`/`404` per the shared conventions in
  `conventions/rhythms-conventions.yml`.
