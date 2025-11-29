# TODO

## Research
- [x] Analyze table relationships and priorities
- [x] Determine migration approach (mirror vs rebuild)
- [x] Review DDL from ybml_schema.sql
- [x] Identify dependent tables

## Pending Confirmation
- [ ] Sync frequency (daily/weekly)?
- [ ] Need historical version tracking?
- [ ] Custom indexes required?
- [ ] Difference between `wm_tcmpat_info_b_from_es` and `_zh` version?

## Implementation
- [ ] Phase 1: Sync wm_tcmpat_info_b_from_es + regioninfo + drug_options_info
- [ ] Phase 2: Sync medical_supplies + hospitalinfo + shopinfo
- [ ] Phase 3: Optional tables (tcmherb/selfprep)
- [ ] Verify data integrity

---

## Acceptance Criteria

### Must Have
- [ ] 5 core tables + regioninfo exist in production aidb
- [ ] Row counts match aidb_test (< 1% variance)
- [ ] regioninfo.code correctly joins hospitalinfo/shopinfo
- [ ] All extract_date tables synced
- [ ] Indexes created on: drugName, prodentpName, regionCode

### Out of Scope
- Frontend pages
- Backend APIs
- Business features
