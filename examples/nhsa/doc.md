# NHSA Data Sync - Technical Document

## Summary
Sync 5 core tables + 1 reference table from aidb_test to production aidb for NHSA medical insurance data.

## Table Relationships

```
                    +------------------+
                    |   regioninfo     | <- Region lookup (province/city/district)
                    |   code, name     |
                    +--------+---------+
                             | regionCode
        +--------------------+--------------------+
        |                    |                    |
        v                    v                    v
+---------------+    +---------------+    +---------------+
|  hospitalinfo |    |   shopinfo    |    |drug_options_  |
|  Hospitals    |    |   Pharmacies  |    |    info       |
|   ~300k rows  |    |   ~100k rows  |    |  Drug Status  |
+---------------+    +---------------+    +---------------+
                                                  |
                                                  | drugName/drugEntp
                                                  v
                                          +---------------+
                                          |wm_tcmpat_info |
                                          |_b_from_es     |
                                          | Drug Catalog  |
                                          |  ~155k rows   |
                                          +---------------+

+----------------+
|medical_supplies| <- Independent table, Medical Devices ~115k rows
+----------------+
```

## Key Decisions

### Decision 1: Migration Approach
- **Options**: A) Direct mirror via pg_dump, B) Rebuild tables + ETL sync
- **Chosen**: A - Direct mirror
- **Rationale**: Simpler, maintains structure consistency, lower maintenance

### Decision 2: Sync Priority
- **Phase 1 (P0)**: Drug catalog + drug status + regions
- **Phase 2 (P1)**: Devices + hospitals + pharmacies
- **Phase 3 (P2)**: TCM herbs, self-prepared medicines

## Core Tables

| Priority | Table | Rows | Key Fields |
|:---:|:---|:---|:---|
| P0 | wm_tcmpat_info_b_from_es | ~155k | medListCodg, drugProdname, natHiDruglistChrgitmLv |
| P0 | drug_options_info | 408 x N | drugName, drugEntp, medinsName, province |
| P1 | medical_supplies | ~115k | medListCodg, mcsName, prodentpName |
| P1 | hospitalinfo | ~300k | medinsName, medinsTypeName, regionCode |
| P2 | shopinfo | ~100k | medinsName, addr, regionCode |

## Required Related Tables
- `regioninfo` - Region code lookup (required for joins)
- `*_extract_date` - Version tracking tables

## Migration Commands
```bash
# Export from aidb_test
pg_dump -h [test_host] -U [user] -d aidb_test \
  -t wm_tcmpat_info_b_from_es \
  -t drug_options_info \
  -t medical_supplies \
  -t hospitalinfo \
  -t shopinfo \
  -t regioninfo \
  -t '*_extract_date' \
  --no-owner --no-acl > nhsa_tables.sql

# Import to production
psql -h [prod_host] -U [user] -d aidb < nhsa_tables.sql
```

## Open Questions
- [ ] Sync frequency from collection team?
- [ ] Need custom indexes beyond defaults?
