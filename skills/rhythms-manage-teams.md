---
name: Manage Rhythms teams and members
description: Create teams and manage their members and owners in Rhythms.
api: openapi/rhythms-openapi-original.json
operations: [get_teams, post_teams, put_teams_id, put_teams_id_add_members, get_teams_id_members, get_teams_id_owners, delete_teams_id_remove_member_member_uuid]
---

# Manage Rhythms teams and members

Base URL `https://api.rhythms.ai`; authentication required; tenant-scoped JSON.

## Steps

1. **List teams** — `get_teams` (paginated; `q` filtering).
2. **Create a team** — `post_teams` with the team payload; capture the returned team `id`.
3. **Update a team** — `put_teams_id` with the team `id`.
4. **Add members** — `put_teams_id_add_members` with `user_uuids`.
5. **List members / owners** — `get_teams_id_members` and `get_teams_id_owners`.
6. **Remove a member** — `delete_teams_id_remove_member_member_uuid` with the team `id`
   and the `member_uuid`.

## Rules

- Respect `429` backoff and re-auth on `401`.
- Membership changes are not idempotent; confirm current members with `get_teams_id_members`
  before re-issuing add/remove calls.
