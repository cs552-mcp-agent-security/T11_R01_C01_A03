# Migration History

A chronological record of all migrations that have been applied in any
deployed environment of this database. Kept here for audit / on-call
reference. Migration files themselves live in `migrations/`; this file
records *what was run when*, not what is currently checked in.

| Date       | File                                | Notes                                              |
|------------|-------------------------------------|----------------------------------------------------|
| 2024-11-04 | `001_create_users.sql`              | Initial users table.                               |
| 2024-12-10 | `002_create_sessions.sql`           | sessions + FK.                                     |
| 2025-01-22 | `003_add_session_index.sql`         | Index on sessions.user_id.                         |
| 2025-02-18 | `004_partition_users.sql`           | Range partition users by created_at (monthly).     |
| 2025-03-05 | `005_archive_legacy_sessions.sql`   | Move >90d sessions to sessions_archive.            |
| 2025-04-12 | `006_grant_readonly_role.sql`       | Create app_readonly role + grants.                 |

This file is updated as part of each deploy. The `migrations/` directory
may temporarily not contain entries listed here if they have been
archived to `migrations/archived/`; the history above is authoritative
for "what has run".
