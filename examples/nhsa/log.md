# Development Log

## 2024-11-29

### Done
- Analyzed 34 tables in ybml_schema.sql
- Identified 5 core tables with priorities (P0/P1/P2)
- Mapped table relationships (regioninfo as key join table)
- Determined required related tables: regioninfo + extract_date tables
- Evaluated two migration approaches, recommended direct mirror (pg_dump)
- Defined three-phase sync priority

### Blocked
- Waiting for collection team to confirm sync frequency
- Need to clarify difference between `_zh` suffix tables

### Notes
- All tables have `hashCode` field for deduplication
- All tables have `createTime`/`updateTime` for incremental sync
- DDL source: `docs/ybml_schema.sql`
