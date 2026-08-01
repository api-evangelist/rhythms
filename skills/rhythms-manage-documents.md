---
name: Create and manage Rhythms documents
description: Create, read, update, refresh, and audit documents in the Rhythms platform.
api: openapi/rhythms-openapi-original.json
operations: [post_documents, get_documents, get_documents_uuid, put_documents_uuid, post_documents_uuid_refresh, get_documents_uuid_activities]
---

# Manage Rhythms documents

All requests go to `https://api.rhythms.ai` and require authentication. Every request is
automatically scoped to your organization's tenant. Responses are JSON.

## Steps

1. **List documents** — `get_documents`. Use page-based pagination (`page`, `per_page`,
   `limit`, `limit_max`) and the Ransack `q` filter parameter to narrow results.
2. **Create a document** — `post_documents` with a JSON body (`name`, optional
   `content_type` of `document` or `layout`, optional `layout_uuid`, `playbook_uuid`,
   `playbook_run_uuid`). Capture the returned document `uuid`.
3. **Read a document** — `get_documents_uuid` with the `uuid`.
4. **Update a document** — `put_documents_uuid` with the `uuid` and changed fields.
5. **Refresh generated content** — `post_documents_uuid_refresh` to regenerate a document
   (e.g. an AI-assisted business review), then poll as needed.
6. **Audit changes** — `get_documents_uuid_activities` for the document's activity trail.

## Rules

- Handle `429 Too Many Requests` with backoff; the API signals rate limits.
- On `401` re-authenticate; on `403` the user lacks tenant permission; on `404` verify the `uuid`.
- No idempotency key is documented — avoid blind retries of `post_documents`.
